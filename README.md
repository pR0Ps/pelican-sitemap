Sitemap
=======

This plugin generates plain-text or XML sitemaps. You can use the `SITEMAP`
variable in your settings file to configure the behavior of the plugin.

The `SITEMAP` variable must be a Python dictionary and can contain these keys:

- `format`, which sets the output format of the plugin (`xml` or `txt`)
- `priorities`, which is a dictionary with three keys:
  - `articles`, the priority for the URLs of the articles and their
    translations
  - `pages`, the priority for the URLs of the static pages
  - `indexes`, the priority for the URLs of the index pages, such as tags,
     author pages, categories indexes, archives, etc...

  All the values of this dictionary must be decimal numbers between `0` and `1`.

- `changefreqs`, which is a dictionary with three items:
  - `articles`, the update frequency of the articles
  - `pages`, the update frequency of the pages
  - `indexes`, the update frequency of the index pages

  Valid frequency values are `always`, `hourly`, `daily`, `weekly`, `monthly`,
  `yearly` and `never`.

- `exclude`, which is a list of regular expressions

  If a page matches any of these regular expressions, it will not be included in
  the site map.

If a key is missing or a value is incorrect, it will be replaced with the
default value.

The sitemap is saved in `<output_path>/sitemap.<format>`.

Note that `priorities` and `changefreqs` are information for search engines.
They are only used in the XML sitemaps.

More information on sitemaps: <http://www.sitemaps.org/protocol.html#xmlTagDefinitions>

Usage
-------

Clone the plugin to a directory in `PLUGIN_PATHS` and add it to the `PLUGINS` list in your settings file.

Here is an example configuration (it's also the default settings):

```python
PLUGINS=['sitemap',]

SITEMAP = {
    'format': 'xml',
    'priorities': {
        'articles': 0.5,
        'indexes': 0.5,
        'pages': 0.5
    },
    'changefreqs': {
        'articles': 'monthly',
        'indexes': 'daily',
        'pages': 'monthly'
    },
    'exclude': []
}
```
