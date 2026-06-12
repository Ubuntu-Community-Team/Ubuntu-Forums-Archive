---
title: "Firefox Back Arrow Issue"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by 29Tudor on 2009-01-18
I'm having an intermittent problem with my Firefox browser. There are times when my back arrow is not an option. It doesn't highlight nor does it work. Any ideas?

---

### Post by ithanium on 2009-01-18
maybe you are in a new tab or window :|

---

### Post by stderr on 2009-01-18
Funny you should mention this. I've noticed a similar problem with Firefox under Fedora. Is it the case that if you right-click on the back button, you do actually get the back list?

---

### Post by 29Tudor on 2009-01-19
This is really bothering me.I post on a few woodworking and old car forums, whenever I open a picture, or a link, it opens in the same tab but the back and forward arrows are not operable (dimmed out.) Right click does nothing.
I have to close the tab, which closes the browser, and start over.

Please help, I'm ALMOST ready to go back to Windows!

---

### Post by ikisham on 2009-01-19
You can try right-clicking the link and choosing to open in a new tab or window. Also check the Tabs part under Edit>Preferences.

---

### Post by redseventyseven on 2009-01-19
Can you give us an example of a site where this happens?
It would help if we could try it ourselves and see if we can reproduce the problem.

---

### Post by kansasnoob on 2009-01-19
> **29Tudor said:**
> This is really bothering me.I post on a few woodworking and old car forums, whenever I open a picture, or a link, it opens in the same tab but the back and forward arrows are not operable (dimmed out.) Right click does nothing.
I have to close the tab, which closes the browser, and start over.

Please help, I'm ALMOST ready to go back to Windows!

I've not experienced your exact problem but I wonder if the official Mozilla build of Firefox would work any better?

The easiest way to accomplish this is with Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/#tochome6](http://ubuntuzilla.wiki.sourceforge.net/#tochome6)

It really is as simple as downloading Ubuntuzilla to the desktop then double clicking the .deb to install to the repos, and then running in terminal:

```
ubuntuzilla.py -a install -p firefox
```

NOTE: Firefox must be closed while doing the installation!

---

### Post by 29Tudor on 2009-01-19
This has happened on 4 different forums, or most anything that has a link. Once I open the pic, or click on the link, there's no going back.

---

### Post by MickS on 2009-01-19
Try middle clicking on the link, that should force it to open a new tab.

Mick

---

### Post by nanotube on 2009-01-19
try starting with a fresh firefox profile (back up your bookmarks and stuff first, of course).

if that fails, you could also try the official Mozilla build of firefox using ubuntuzilla as kansasnoob suggests.

---

### Post by 29Tudor on 2009-01-22
Problem solved...my fault, too accustomed to Windows. 
Thanks to all that responded

---

### Post by nanotube on 2009-01-22
> **29Tudor said:**
> Problem solved...my fault, too accustomed to Windows. 
Thanks to all that responded

Good news. :)
Please share what your solution was so that others who run into the same thing know what to do.

---

### Post by JohnWesleyMethodist on 2009-01-22
> **29Tudor said:**
> Please help, I'm ALMOST ready to go back to Windows!

 I fail to see how that would help. I am thinking back to all the weird problems I saw over the years with IE...

---

