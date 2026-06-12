---
title: "domain names with dashes don't work!"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by grj23 on 2010-01-05
Hi all

Got a weird problem.  Not sure why, if it's Ubuntu, Firefox, or my router.

Was trying to look up some birthday cake designs, and found that pages with a dash in the domain name didn't work:
[www.coolest-birthday-cakes.com](www.coolest-birthday-cakes.com)
[www.easy-birthday-cakes.com](www.easy-birthday-cakes.com)
[www.coolest-kid-birthday-parties.com](www.coolest-kid-birthday-parties.com)

Dashes in the url didn't matter:  eg
[http://www.parenting.com/recipes-article/Child/Recipes/How-to-make-a-lion-cake/](http://www.parenting.com/recipes-article/Child/Recipes/How-to-make-a-lion-cake/)
worked fine!

I also tried the above three sites on an iPhone with Safari attached to the same wireless router, and found that they did NOT work there either.

I don't really know what to make of it.  

Tried to access one of the with ipython
```
In [1]: import urllib2

In [2]: url='www.coolest-birthday-cakes.com'

In [3]: url='http://www.coolest-birthday-cakes.com'

In [4]: req=urllib2.Request(url)

In [5]: resp=urllib2.urlopen(req)
---------------------------------------------------------------------------
URLError                                  Traceback (most recent call last)

```

No joy!  Okay, so obviously it's possible that all three don't work for some reason.  That would be a weird coincidence.  But any suggestions would be welcome!

---

### Post by audiomick on 2010-01-05
I don't have a problem getting to those addresses, either by clicking on the links in your post, or typing them into the address field in firefox.

---

### Post by grj23 on 2010-01-05
Hi.  It seems I can access these links from work.  So I guess it's our router/service provider?  How odd!

Is there another way of writing a dash in an url.  Like %XXX or something that I might try?  Otherwise I guess I better ask my service provider what's going on...

---

