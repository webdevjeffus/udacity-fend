# Build a Portfolio Site
**Created by Jeff George, December 2018**<br>
**for Udacity Front-End Development Program**<br>
**Unit 2: Building Blocks of Front-End Development**
<hr>

## Assignment
The assignment was to create a one-page portfolio using HTML5 and CSS3. Required elements included:
* at least 4 images
* title text (h1, h2, etc.)
* paragraph text
* a logo
* Structural HTML organized using semantic tags such as &lt;header&gt;, &lt;footer&gt;, &lt;article&gt;, and &lt;section&gt;
* Grid-based layout using **flexbox**
* Cross-device compatibility, with responsive content that displays on all devices

A design mock-up was provided as an example, but students were encouraged to create their own design, rather than simply implementing the mock-up.

## Content
Rather than creating a web-design portfolio displaying hypothetical work samples, I opted to build a page focused on my actual work in another field: tabletop game design. The final section of the portfolio refers to [printandplaygamer.com](https://printandplaygamer.com), a blog I maintain covering downloadable PDF products designed for tabletop roleplayers and wargamers.

## Resources
In creating this portfolio, I utilized the following resources:
* [Google Fonts](https://fonts.google.com/). Fonts used: Baloo (headings) and Tinos (body text).
* [Normalize.css](http://necolas.github.io/normalize.css/). CSS reset, standardizing display of content across browsers.
* [Favicon Generator](https://www.favicon-generator.org/). Automatically creates a favicon from an existing logo image, and generates necessary code for inclusion in HTML &lt;head&gt; element.

## Implementation
### File Structure
**HTML** for the project consists of a single file, **index.html**, in the root directory.

**CSS** is contained in three files, saved in the **css** directory, and loaded in this order:
* **normalize.css** - downloaded from the [Normalize.css](http://necolas.github.io/normalize.css/) webpage, used without any edits
* **styles.css** - general styling for the page, assuming a maximum screen-width of 400px, in keeping with the mobile-first design paradigm
* **responsive.css** - responsive styling using media queries to establish breakpoints necessary to make the content display attractively on all devices larger than 400px

**Content images** are saved in a dedicated **img** directory.

**Favicon images** are kept in their own directory, **favicon**, to keep from cluttering the working **img** directory.

### Resets
As mentioned above, **normalize.css** was included to standardize the display of content across all display types and browsers. For ease of reference, the **normalize.css** stylesheet is served locally and in non-minimized form; had this website been intended for real-world deployment, a minimized version of **normalize.css** would have been linked from a popular CDN.

For consistent, intuitive sizing of elements, the **box-sizing: border-box** rule was applied to all elements using the &#42; selector.

### Layout
The page implements a responsive design using **flexbox**. On smaller screens (phones and smaller tablets), all content is arranged in a single column. On mid-sized screens (full-sized tablets and smaller laptops), the final section&mdash;_Print and Play Gamer Blog_&mdash;is rearranged to form a 2x2 grid.

On larger screens (full-sized laptops and desktops), the middle section&mdash;_Tabletop Game Work_&mdash; and the final section are moved side-by-side, in a main-column-and-sidebar layout. At this size, the blog section returns to a single-column format. The page's content is capped at 1200px; at screen sized larger than that, the content is centered and a contrasting margins are added on either side.

### Semantic HTML
All elements in the HTML code were created using semantically-meaningful tags, making the structure of content clear even in a text editor. The content is arranged in three large elements: a &lt;header&gt; containing the banner masthead; a &lt;main&gt; element containing the meat of the page; and a &lt;footer&gt; containing project attribution.

The &lt;main&gt; element is further divided into three &lt;section&gt; elements, each identified with a unique and meaningful class name: **.hero**, **.projects** or **.blog**. Content within each section was further divided into &lt;article&gt; elements, which generally contain a header, an image, and a paragraph of text.

&lt;div&gt; elements were used only when necessary to group content elements for **flexbox** implementation; they impart no other semantic meaning.

Horizontal lines between articles within a section are design elements, without semantic meaning. As such, they were implemented as borders in the rulesets applied by CSS to &lt;article&gt; elements, rather than by inserting semantically-unnecessary &lt;hr&gt; elements into the HTML code.

### CSS Selectors
Generally, elements were selected for styling using selectors with an **element-type.class-name** format. This allows class names to be short and semantically meaningful, and affords a slight specificity advantage over rules contained in user-agent and normalize.css stylesheets.

Where possible&mdash;especially within the &lt;header&gt; and &lt;footer&gt; elements&mdash;selectors were written without classes, typically using an **element-type** or **element-type element-type** format. This formulation is semantically clear without cluttering elements in the HTML file with unnecessary class attributes.

IDs were avoided as CSS selectors in all cases, for two reasons. First, the use of IDs as CSS selectors can create specificity issues which complicate the application of styling rules to elements. Second, avoiding the use of IDs in CSS reserves them for use in Javascript, and allows the Javascript coder to apply names to IDs that are meaningful within the context of that Javascript code. Even if a single, unique element needs to be selected within the CSS code, a single-use class name is no less convenient than an ID to the CSS coder, and avoids specificity inflation while allowing the Javascript coder maximum flexibility in assigning meaningful IDs to elements.

### Typography
Font-sizes are specified using **rem** units, to ensure consistent and predictable rendering. A base font-size of 16px is set in **styles.css**, and the type is scaled up using media queries to maintain readability and keep line lengths within an acceptable range. At certain breakpoints, text elements within the &lt;header&gt; are further fine-tuned for size and spacing using **font-size** styling rules.

### Responsive Images
Images are made responsive in two ways.

**Hero Image**. The large image in the first section of the page (not counting the masthead) is placed using the **background-image** rule. This allows the placement of type directly on the image. The image is cropped differently for the various screen configurations, with a roughly square version used on phones and other small devices, and a more panoramic, horizontal crop used on tablets and PCs. Separate image files for the hero section are served for various devices using media queries.

**Other Content Images**. The images in the remaining sections of the page are served as conventional &lt;img&gt; elements. Responsiveness is implemented using the _srcset_ and _sizes_ attributes, providing the browser with multiple versions of each image, and sufficient image to choose the appropriately-sized version for the display window. Sizes for the images are set using **width** rules in the CSS; heights are left unspecified, so that the browser maintains the aspect-ratio of the images as it scales them. All versions of each image have the same aspect ratio, to keep the design consistent at all screen sizes.

**Logo.** Since the logo is a small image whose size varies little across the range of devices, a single 4 KB file is stored in the **img** folder. The logo is saved as a **.png** file so that it can have a transparent background.