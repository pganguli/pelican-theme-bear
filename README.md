# Pelican theme based on [Bear Blog](https://bearblog.dev)

- The CSS is the exact same as the one used on Bear Blog.
- Most other UI elements default to being faithful to Bear Blog,
  but several of these can be configured:
    - Whether to display Modified Time on article view
    - Whether to display Authors List on article view
    - Whether to display Article Summary on index
    - Position of Tags on index
    - Default date format
- An additional Jinja filter is provided in the sample pelicanconf.py below
  which allows sorting tags by article count.

# Installation

1. Clone this repo to the directory 'pelican-theme-bear'.

```sh
git clone 'https://github.com/pganguli/pelican-theme-bear'
```

2. Set the pelican theme path to the cloned directory.

pelicanconf.py

```python
THEME = '/path/to/pelican-theme-bear'
```

# Usage

pelicanconf.py:

```python
from functools import partial

JINJA_FILTERS = {
    'sort_by_article_count': partial(sorted,
                                     key=lambda tags: len(tags[1]),
                                     reverse=True
                                    )
}

DEFAULT_DATE_FORMAT = '%d %b, %Y' # default date format on Bear Blog
ROBOTS = 'noindex, nofollow'

DISPLAY_MODIFIED = False # modified time on article view
DISPLAY_AUTHORS = False  # authors list on article view
DISPLAY_SUMMARY = False  # article summary on index
TAGS_POSITION = None     # position of tags on index; 'top' or not
```
