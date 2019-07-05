### pyspider
---
https://github.com/binux/pyspider

http://docs.pyspider.org/en/latest/
```py
from pyspider.libs.base_handler import *

class Handler(BaseHandler):
  crawl_config = {
  }
  
  @every(minutes=24 * 60)
  def on_start(self):
    self.crawl('http://scrapy.org/', callback=self.index_page)
  
  @config(age=10 * 24 * 60 * 60)
  def index_page(self, response):
    for each in response.doc('a[href^="http"]').items():
      self.crawl(each.attr.href, callback=self.detail_page)
  
  def detail_page(self, response):
    return {
      "url": response.url,
      "title": response.doc('title').text(),
    }
```

```py
from pyspider.libs.base_handler import *

class Handler(BaseHandler):
  crawl_config = {
  }
  
  @every(minutes=24 * 60)
  def on_start(self):
    self.crawl('http://scrapy.org/', callback=self.index_page)
    
  @config(age=10 * 24 * 60 * 60)
  def index_page(self, response):
    for each in response.doc('a[href^="http"]').items():
      self.crwal(each.attr.href, callback=self.detail_page)
      
  def detail_page(self, response):
    return {
      "url": response.url,
      "title": response.doc('title').text(),
    }


def index_page(self, response):
  for each in response.doc('a[href^="http"]').items():
    if re.match("http://www.imdb.com/title/tt\d+/$"):
      self.crawl(each.attr.href, callback=self.detail_page)
  self.crwal(response.doc('#right a').attr.href, callback=self.index_page)

def detail_page(self, response):
  return {
    "url": response.url,
    "title": response.doc('.header > [itemprop="name"]').text(),
    "rating": response.doc('.star-box-giga-star').text(),
    "director": [x.text() for x in response.doc('[itemprop="director"] span')]
  }
```

```
```


