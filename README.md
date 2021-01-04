# Sunrise Ghost Theme

### Remaining Todos

- Add a welcome or intro panel to the homepage
- Add a categories (tag list) page
- Add search
# Development

Styles are compiled using Gulp/PostCSS to polyfill future CSS spec. You'll need [Node](https://nodejs.org/), [Yarn](https://yarnpkg.com/) and [Gulp](https://gulpjs.com) installed globally. After that, from the theme's root directory:

```bash
# Install
yarn

# Run build & watch for changes
yarn dev
```

Now you can edit `/assets/css/` files, which will be compiled to `/assets/built/` automatically.

The `zip` Gulp task packages the theme files into `dist/<theme-name>.zip`, which you can then upload to your site.

```bash
yarn zip
```

### Local Server Setup for Development

Follow [this guide](https://nicogreve.de/developing-themes-for-ghost/) to setup
LiveReload to make it easier to develop a theme locally.

Follow the [official Ghost local installation guide](https://ghost.org/docs/install/local/) to install Ghost.

Run `ghost start` to start the local Ghost instance that will be available at http://localhost:2368

Run `ghost run --development` to tail the logs of the running Ghost instance.

&nbsp;

### Configuration

Ghost template configuration sucks. The variables defined in package.json get filtered out, and
I haven't found a way to quickly inject variables from the admin interface so there is some hardcoded
content throughout.

### Custom Pages

Adding a `page-<slug>.hbs` template in the root folder will route anything from
`/slug/` to that custom template.

Ghost will need a page created in the admin interface with that slug for this to work,
and you'll need to restart your server after creating the template.

### Forms

Email subscription form is handled via Mailchimp.

Contact Us form is handled via Formspree.

#### SVG Icons

Makes use of [Simple Icons](https://simpleicons.org/) and [Apple SF Symbols](https://developer.apple.com/design/human-interface-guidelines/sf-symbols/overview/).

####  PostCSS Features Used

- Autoprefixer - Don't worry about writing browser prefixes of any kind, it's all done automatically with support for the latest 2 major versions of every browser.
- [Color Mod](https://github.com/jonathantneal/postcss-color-mod-function)

&nbsp;

# Boilerplate Ghost Content

Ghost uses a simple templating language called [Handlebars](http://handlebarsjs.com/) for its themes.

We've documented our default theme pretty heavily so that it should be fairly easy to work out what's going on just by reading the code and the comments. Once you feel comfortable with how everything works, we also have full [theme API documentation](https://themes.ghost.org) which explains every possible Handlebars helper and template.

**The main files are:**

- `default.hbs` - The main template file
- `index.hbs` - Used for the home page
- `post.hbs` - Used for individual posts
- `page.hbs` - Used for individual pages
- `tag.hbs` - Used for tag archives
- `author.hbs` - Used for author archives

One neat trick is that you can also create custom one-off templates just by adding the slug of a page to a template file. For example:

- `page-about.hbs` - Custom template for the `/about/` page
- `tag-news.hbs` - Custom template for `/tag/news/` archive
- `author-ali.hbs` - Custom template for `/author/ali/` archive

&nbsp;


### Search Functionality

https://github.com/TryGhost/Dawn/blob/master/assets/js/lib/elasticlunr.min.js

https://github.com/TryGhost/Dawn/blob/master/assets/js/main.js#L314

https://forum.ghost.org/t/expand-search-on-dawn-to-include-pages/18846

https://forum.ghost.org/t/dawn-theme-dawn-search-index-error/18099

