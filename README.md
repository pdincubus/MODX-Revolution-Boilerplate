#MODX Revolution Boilerplate basics

Now on the [MODX extras respository](http://modx.com/extras/package/modxrevolutionboilerplate)!

This is mostly a duplicate of the original MODX Revo Boilerplate that I created - but altered to work the way I mostly actually work. This repo *only* has templates, chunks, snippets and a few bits of useful stuff. There are *no* assets provided any more. I use a separate project skeleton repo to get my base LESS/SCSS/JS stuff all grunt-ed.

##MODX Post Installation Checklist

Stuff you should probably run through manually to make sure things are in tip-top condition. [Checklist](https://github.com/pdincubus/MODX-Revo-Boilerplate/blob/master/Post-Installation-Checklist.md)


##ClientConfig

I've set global placeholders in certain places, the easiest way to get these set up is to use ClientConfig. Alternatively, and more painful (and also only available in the context you add them to) you can set them up as context setting placeholders.

The placeholders you'll need to set up and add values for are:

* [[++templateFolderName]]
* [[++searchResultsLandingPage]]
* [[++googleSiteVerificationId]]
* [[++msSiteVerificationId]]
* [[++gaSiteCode]]
* [[++twitterHandle]]
* [[++sharerImage]]
* [[++facebookAppId]]

If you don't use/want/need any of the above, just set a value directly in the relevant chunk or remove the block of code no longer needed.

##Template variables

I've made reference in the [[$site.head]] chunk to a template variable called 'mainImg' - this is usually one of the first TVs I'll add to a new site. If you don't want this, change it in the chunk.


##Templates

All the templates set placeholders for their ultimate parent's link attributes to allow a 'section' class to be added to the body tag. Useful.

All templates also pull in the same site.head and site.foot chunks.

* Default

    This will likely be the "standard" template for any default text content page
* Contact

    With configurable FormIt call
* Article & ArticleContainer

    For sites using Articles or any form of blog/news section that may use some of the components of Articles, you'll definitely want new templates for the layout in that section. There's also an [[$articles.aside]] chunk with stuff not in the main [[$site.aside]] chunk.
* SearchResults

    Create a page, set this template for any searches made from the articles.aside chunk, or anywhere else you set a search form up.
* PageNotFound

    Create a page, set this template, add the system setting for Error Page to point to this new resource

##Chunks

* site.head and site.foot

    Beginning and end of the templates. See section further up for global placeholders you'll need to get these working.

    [[+bodyClass]] is useful for complex sites and when passed into the [[$site.head]] will add that class name to the body tag. Can help save a bunch of extra templates (sometimes).
* articles.aside

    Contains most things that were pulled out of the stock Articles templates but are repeated on both container and article template. Nicely wrapped in an aside chunk.
* fi.contact-email and fi.contact-form

    Install the FormIt extra, and with these two simple chunks you can easily drop a working contact form on any page with little to no customisation required.
* pm.row and pm.outer

    Wayfinder's/pdoMenu's default setup for outputting a menu item needs a bit of tweaking since we've used the link_attributes to apply a class to the body tag.
* quip.comment, quip.add-comment, articles.latest-post-tpl, articles.archive-group-by-year, articles.article-row-tpl, articles.archive-row

    Replacement, lovely and trimmed down version of the standard Quip chunk. I'll no longer be maintaining the quip chunks as I don't like quip so much, and if I absolutely have to drop some commenting into a site, I'll generally add [Disqus](https://disqus.com/).


##Snippets

* copyYears

    Works out the copyright for the footer.
* createSelectOptions

    This takes the values from a TV and allows output as select options.
* currentUrl

    Clue is in the name
* dateFilters

    This is here so I don't lose it. Output some placeholders for next and previous months.
* fiProcessArrays

    See: http://forums.modx.com/thread/47606/formit-how-to-use-checkbox-array#dis-post-275189
* formatSearchUrl

    Some preformatting for passing to the SimpleSearch on the Page Not Found error page.
* getUrlParam

    Ronseal. Gets a key and value from the current URL.


##Content Pages

* robots

    Points out the URL of the sitemap (edit this to your URL). You'll need to install the GoogleSiteMap extra to make the sitemap.xml file, or alternatively use pdoTools which has a pdoSitemap snippet that does the exact same thing.
* humans

    You can pretty much do what you want in this file, but point out developer, designer, technology used, etc.
* Other pages

    There's a few default pages you'll probably need to add that aren't worth adding to this package:

    * Page not found
    * Search results
    * Privacy Policy
    * Cookie policy
    * Site terms and conditions
    * sitemap.xml


##Extras

You're going to need the following extras to make all the basics here work:

* [FormIt](http://rtfm.modx.com/extras/revo/formit). For form sending/validation, etc
* [setPlaceholders](https://github.com/oo12/setPlaceholders/). Performs a combination of features from [getResourceField](http://modx.com/extras/package/getresourcefield), [UltimateParent](http://modx.com/extras/package/ultimateparent) and others. Really flexible package and well documented!
* [SimpleSearch](http://rtfm.modx.com/extras/revo/simplesearch). For use on the Page Not Found error page.
* [pdoTools](http://modx.com/extras/package/pdotools). This is a package that includes several useful almost drop-in replacements for a few of the most commonly used snippets: pdoMenu == Wayfinder, pdoSitemap == GoogleSiteMap, pdoResources == getResources, and others. It's worth noting that although I use pdoTools a lot it's not an exact replacement for [getResources](http://rtfm.modx.com/extras/revo/getresources), so sometimes I still do use that.

Things you're more than likely going to need:

* [pThumb](https://github.com/oo12/phpThumbOf). Crop, thumbnail and alter images automagically. Offers improvements (especially in speed!) over the original phpThumbOf.
* [CodeMirror](http://modx.com/extras/package/codemirror). Syntax highlighting and stuff for anything that isn't a standard content page.
* [VersionX](https://github.com/Mark-H/VersionX2). Content / chunk version tracker extra. Useful for rolling back to a previous version of something.
* [TinyMCE](http://modx.com/extras/package/tinymce). Pretty much the only choice you have for a reasonable text editor in MODX Revo. There is a CKEditor extra but the last time I tried it out it didn't have internal link integration like TinyMCE does. Shame because it's a much nicer RTE.
* [Redactor from ModMore](https://www.modmore.com/?via=231) - I would heartily recommend this because it's so much nicer, has great integration and is much better overall than either of the other options. It's a paid-for extra, but it's seriously worth every penny.

If you want to set up basic blogging and want something you can just drop in:

* [Articles](http://rtfm.modx.com/extras/revo/articles). This in turn installs a load of extras it needs. Useful for simple blogs.
* [getRelated](http://rtfm.modx.com/extras/revo/getrelated). Goes and sees if it can find content related to the page you're on. Useful in Articles pages.

Other recommendations:

* [ClientConfig](https://www.modmore.com/extras/clientconfig/). Lets you set up global placeholders that your clients can edit easily.
* [JSONDerulo](http://modx.com/extras/package/jsonderulo). Pulls in and outputs JSON feeds for common social feeds.
* [Collections](http://modx.com/extras/package/collections). Hide child pages in the resource tree and gives you a grid for easy searching/viewing of the child pages.


##Transport Package

Now available on the MODX Extras repo: [MODX-Revo-Boilerplate](http://modx.com/extras/package/modxrevoboilerplate)


##Additional

* Thanks (as usual) to [Mister John](https://github.com/johnnoel) for a couple of the snippets which accompany the SimpleSearch on the Page Not Found error page.
* The background-size polyfill is from: [Louis Remi on Github](https://github.com/louisremi/background-size-polyfill)
* The box-sizing polyfill is from: [Schepp on Github](https://github.com/Schepp/box-sizing-polyfill)

