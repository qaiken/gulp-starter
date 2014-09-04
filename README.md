# Forty Sass Framework Template

Simply put, there's no fancy magic behind the Forty Sass Framework Template. We've certainly worked with existing popular frameworks in the past. But they felt cumbersome, bloated, and produced a lot of overhead. More importantly, you're locked into their pattern and thought process.

Our template exists to give you a light and base level toolkit to build off of. We're not here to tell you how to write or handle your project. After all, no two are the same.

We're certainly versed and familiar with [OOCSS](http://oocss.org/) and [SMACSS](http://smacss.com/), and we have hints of that sprinkled throughout the template. So if you want to take the [BEM](http://bem.info/method/), [OOCSS](http://oocss.org/), or [SMACSS](http://smacss.com/) approach, the choice is yours.

Do what works best for you and your team.

##**Template Structure**
```
sass/
|
|– app/
|   |- global               # Styles that apply globally on application
|   |– ie                   # Styles specific to Internet Explorer
|   ...                     # Application css
|
|– helpers/
|   |– fonts                # Contains all your @imports, @font-face, and third-party fonts
|   |– functions            # Application mixins & functions
|   |– js-breakpoints       # Syncs up our CSS Media Queries to work with [MQ Sync](https://github.com/40Digits/jquery-mq-sync)
|   |– media-queries        # Media query mixin
|   |– reset                # Browser reset stylesheet
|   |– utilities            # Utilities, %placeholders and %extends to dev faster & easier
|
|– layout/
|   |– footer               # Stypes that apply to the footer of application
|   |– header               # Styles that apply to the header of application
|   |– nav                  # Styles that apply to the navigation of application
|   |– sidebar              # Styles that apply to the sidebars of application
|   |– wysiwyg              # Styles that apply to wysiwyg content specific areas
|
|– modules/
|   |– cms-wordpress        # Styles used within the Wordpress Wysiwyg editor
|   |– forms                # Base styles for all form elements
|   |– keyframes            # CSS keyframes for CSS animations
|   |– print                # Print specific styles, although most will be inline with Sass
|   |– responsive-grid      # Starter grid system to get you started
|   |– typography           # Base styles for headings, paragraphs, lists, global styles, etc.
|
|- variables/
|   |– color                # Color values used throughout the application
|   |– settings             # Font variables, Media Query definitions
|
|- vendor/
|   |– gravity-forms        # Stripped down version for Gravity Forms
|   ...                     # Vendor css
|
`– style                    # primary Sass file
```

***

##**Recommended Usage**

####app/

The [app/](https://github.com/40Digits/forty-sass/tree/master/app) folder contains all of your application styles. These styles vary anywhere from small partials to templates to pages. In order to keep consistency going, especially in Wordpress projects. Please use the following prefix method.

| Prefix        | Usage                                                  |
| :------------ | :----------------------------------------------------- |
| page-         | pages                                                  |
| temp-         | template specific files                                |
| block-        | modular blocks that get re-used throughout application |
| cpt-          | anything that is a custom post type                    |

Your [global.scss](https://github.com/40Digits/forty-sass/blob/master/app/_global.scss) file should contain any and all global layout styles that do not fit in a specific style-sheet. Any and all IE styles that can't be written inline, should reside inside the [ie.scss](https://github.com/40Digits/forty-sass/blob/master/app/_global.scss) style-sheet.

####helpers/

The [helpers/](https://github.com/40Digits/forty-sass/tree/master/helpers) folder generally contains tools which help with formatting of your application. They either give you ways to sync with javascript, give you functions, or help with resets. In most cases you won't be making many edits here, unless you are adding mixins and functions that are project specific. In that case, you would be making modifications to [functions.scss](https://github.com/40Digits/forty-sass/blob/master/helpers/_functions.scss) and [utilities.scss](https://github.com/40Digits/forty-sass/blob/master/helpers/_utilities.scss).

| File            | Usage                                                  |
| :-------------- | :----------------------------------------------------- |
| fonts           | When using third-party fonts, it's recommended that you utilize the font mixin. For services such as typekit, you do not need to add in a @font-face. Where as for services such as fonts.com, which have an odd font-weight association, it's recommended you utilize an @font-face for best results. See file for usage examples. |
| functions       | You should place all of your project specific mixins in here. |
| js-breakpoints  | Syncs up our CSS Media Queries to work with [MQ Sync](https://github.com/40Digits/jquery-mq-sync) |
| media-queries   | Should not be edited as it contains the mixin necessary to make all of the media queries work. |
| utilities       | Contains helper classes which not only will speed up your development, but also make it faster and easier on you. |

######utilities.scss

| Sample Usage & Comments                                          |
| :--------------------------------------------------------------------------------------- |
| `@include font-smoothing;`   The body class comes with font-smoothing already applied. However, font-smoothing does not carry over to input fields and buttons. |
| `@include abs-center;`   Absolute center an element, this only works if there is a width and height on element. For other ways to center, read [Centering in CSS: A Complete Guide](http://css-tricks.com/centering-css-complete-guide/) |
| `@include placeholder {}`   Takes your @content and applies correct vendor prefixes for placeholder. See [forms.scss](https://github.com/40Digits/forty-sass/blob/master/modules/_forms.scss) for usage example. |
| `@include keyframes(name) {}`   Takes your @content and applies correct vendor prefixes for animations. The prefixes inside specific keyframes are handles by auto-prfixer. See [keyframes.scss](https://github.com/40Digits/forty-sass/blob/master/modules/_keyframes.scss) for usage example. |
| `@extend %visually-hidden;`   Hide an element from the screen, but still keep it for screen readers. Very handy and recommended instead of utilizing text-indent method. |
| `@include rgba(#000, .3);`   Gives you a cross browser alpha channel background color. Mostly used for IE8. |
| `@include opacity(.4);`   Gives you a cross browser opacity that works in IE8 |
| `@extend %bg-cover;`   Gives you background-size:cover support in IE8 |
| `@extend %naked-list;`   Sometimes you need a list without any formatting. Instead of resetting it on the base level, this is a much cleaner and safer approach to use when needed. |
| `@extend %naked-button;`   | As with the list, this resets the <button> styles to bare bones. It's extremely handy for mobile devices as they tend to apply native UI styles. |

####layout/

The [layout/](https://github.com/40Digits/forty-sass/tree/master/layout) folder contains styles which are specific to the layout or skeleton structure of your application. In this case think footer, header, navigations, sidebars, and wysiwyg styles.

####modules/

When you think [modules/](https://github.com/40Digits/forty-sass/tree/master/modules), it's not necessarily what you'd expect them to be. They're not modules from an Object Oriented Programming approach, instead think of modules as alittle extras that add to your application. Not every project will require a grid, nor will most project require keyframes. That being said, you are free to include these as you fit.

####variables/

The [modules/](https://github.com/40Digits/forty-sass/tree/master/variables) folder contains all your settings throughout the site. The most important file to take a look around would be the [settings.scs](https://github.com/40Digits/forty-sass/blob/master/variables/_settings.scss) and make any adjustment necessary for your application.

The settings.scss file also houses your media query settings. In here you will be able to define additional media queries which should be necessary for your project. You are welcome to make adjustment to the breakpoints already defined, but we highly recommend against editing the small, medium, and large breakpoints.

Our breakpoints are defined in a way that don't depend on devices specificity. Instead we see them scaling depending on the medium. This gives us room to define breakpoints that fit our application.

Please note that we utilize mobile-first in all of our development.

```css
// Media query - min-width
$mq-min-mini:       em(480);
$mq-min-small:      em(600);
$mq-min-medium:     em(768);
$mq-min-large:      em(960);
$mq-min-xlarge:     em(1220);
$mq-min-xxlarge:    em(1440);

// Media query - max-width
$mq-max-tiny:       $mq-min-mini - em(1);
$mq-max-mini:       $mq-min-small - em(1);
$mq-max-small:      $mq-min-medium - em(1);
$mq-max-medium:     $mq-min-large - em(1);
$mq-max-large:      $mq-min-xlarge - em(1);
$mq-max-xlarge:     $mq-min-xxlarge - em(1);

$mq: (
  'mini'            : ( min-width: $mq-min-mini ),
  'small'           : ( min-width: $mq-min-small ),
  'medium'          : ( min-width: $mq-min-medium ),
  'large'           : ( min-width: $mq-min-large ),
  'xlarge'          : ( min-width: $mq-min-xlarge ),
  'xxlarge'         : ( min-width: $mq-min-xxlarge ),

  'max-tiny'        : ( max-width: $mq-max-tiny ),
  'max-mini'        : ( max-width: $mq-max-mini ),
  'max-small'       : ( max-width: $mq-max-small ),
  'max-medium'      : ( max-width: $mq-max-medium ),
  'max-large'       : ( max-width: $mq-max-large ),
  'max-xlarge'      : ( max-width: $mq-max-xlarge ),

  'print'           : ( print ),
  'tab-port'        : ( screen and (min-device-width: $mq-min-medium) and (max-device-width: $mq-max-medium) and (orientation: portrait) ),
  'tab-land'        : ( screen and (min-device-width: $mq-min-medium) and (max-device-width: $mq-tablet-landscape) and (orientation: landscape) )
);
```

To use a media query:

```css
@include mq(medium) {
  // styles that get added to a medium breakpoint
}
@include mq(large) {
  // styles that get added to a large breakpoint
}
@include mq(max-medium) {
  // styles that get added from large breakpoint down
}

// In this example, we are starting off with a red font color and a font-size of 10px.
// Once we hit the medium breakpoint, the font-size changes to 15px/
// When we view this style in print mode, the color is changed to black, but note that the color is red.
.style {
  color: red;
  font-size: em(10);
  @include mq(medium) {
    font-size: em(15);
  }
  @include mq(print) {
    color: #000;
  }
}
```

To add a new media query breakpoint:

```css
// Inside $mq map, define any additional breakpoints after 'tab-land'.
$mq: (
  ...
  'tab-land'        : ( screen and (min-device-width: $mq-min-medium) and (max-device-width: $mq-tablet-landscape) and (orientation: landscape) ),

  'custom-mq'       : ( (min-width: 500px) and (max-width: 600px) )
);
```

####vendor/

All [vendor/](https://github.com/40Digits/forty-sass/tree/master/vendor) specific stylesheets should go into their own folder. The framework comes with a stripped down gravity-forms style guide for usage.


***

##**Styleguide**

####General Rules
* When possible, avoid using ID's, use classes as much as possible.
* Don't over-qualify selectors.
* Don't get crazy with nesting of rules.
* Media queries belong right after pseudo-classes.
  - Min-Width - smallest to largest
  - Max-Width - largest to smallest
* Use auto prefixer, check for settings in the gruntfile.js
* Break into as many small files as it makes sense:
  - Produces easier to maintain styles.
  - Easier to find rules.
* Be generous with comments and as descriptive as possible.

####Properties
* CSS rules should be comma seperated and reside on new lines.
* Order of CSS properties:
  - Positioning
  - Display & Box Model
  - Color
  - Text
  - Transform
  - Animations
  - Z-index
* Order of Sass extends and properties:
  - @extend(s)
  - @include(s)
  - "regular" styles
* Nest all pseduo-classes directly beneath base properties and values.
* Use z-index scale found in utilities.scss

####Naming Conventions
* Classes and IDs are lowercase with words separated by a dash.
* Variablize all colors, numbers, etc.
  - $color-blue
  - $color-azure
  - $color-purple
* Images
  - Image file names are lowercase with words separated by a dash.
  - Image file names are prefixed with their usage.
    - icon-home.png
    - bg-home.png
    - hero-about.png
* .js- prefixed class names for elements relying upon javascript
* .is- prefixed class names for stateful classes
  - .is-active
  - .is-enabled

####Style Scoping
All of your styles should be reusing general component level styles defined below. Page level name-spaces however can be helpful for overriding generic components in very specific contexts.

Page level overrides should be minimal and under a single page level class nest.

Component level name-spacing:

* nav
* nav-bar
* header-global
* header-about
* section-hero
* section-welcome
* module-wysiwyg
* module-accordion

####Comments
Use comments to seperate logical groups of styles within a document. This also allows us to convert from .scss <-> .sass without any hikcups. To get uniforminity with comments, please use the following three.

* The top level of your sass file should contain the name in all uppercaps
* Inside your sass file, divide sections up with a comment header
* And for single properties, use //

```
//=================================
// GLOBAL STYLES
//=================================

//---------------------------------
// Section Comment Header
//---------------------------------

// Property commments
```