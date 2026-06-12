---
title: "OpenOffice - Setting paper size to A4 PERMANENTLY"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by suomalainen on 2010-08-26
Ubunteros,

How is the paper size permanently set in OpenOffice so that each time the program is launched it doesn't need to be manually set to A4???

Thanks

---

### Post by Ichtyandr on 2010-08-26
I think you should change the default template, the openoffice help describes how to do that (search for "default template"), I never tried it though

---

### Post by Verbeck on 2010-08-26
[LIST=1]
[*]Create a new document, add or  modify styles, and change other settings as you desire.
[*]From the  File menu, choose Templates -> Save.
[*]Give the template a  name.
[*]Select a category in the Categories list (for example, My  Templates).
[*]Click OK to save the template.
[*]Choose File  -> Templates -> Organize.
[*]In the Categories list,  double-click on the My Templates folder.
[*]Right-click on the  template you want to use and choose Set as Default Template from the  menu.
[*]Click the Close button.
[/LIST]

source :
```
http://user.services.openoffice.org/en/forum/viewtopic.php?f=71&t=1161
```

---

### Post by suomalainen on 2010-08-26
Thanks Verbeck. Everything is cool now.....

By the way. I moved from U.S. to Finland. Currency is different $ to €, one clock is 12 hour the other 24 hour. One uses metric the other inches... Paper is A4 usa it is 8 x11.. 

Is there a place all this can be changed all at one??

thanks again....

---

### Post by Vaphell on 2010-08-26
check what your locale settings are
```
locale
```
you probably need to change it to fi_FI.utf-8 or something to use finnish notation.

[http://myy.helia.fi/~karte/english_in_finland_on_ubuntu.html](http://myy.helia.fi/~karte/english_in_finland_on_ubuntu.html)
[http://www.digipedia.pl/man/doc/view/update-locale.8/](http://www.digipedia.pl/man/doc/view/update-locale.8/)

---

