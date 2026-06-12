---
title: "firefox opens to last page viewed instead of homepage"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by Lvcoyote on 2010-06-04
I have the options set to open my home page when Firefox starts, but it always opens to the last page I was on before closing it.  Anyone else having this problem??

---

### Post by Kellemora on 2010-06-04
Hi LVC

You may have accidentally hit the "use current page" button.
Click on the "Restore Defaults" button and make sure it says "Show my Home Page" in the top box.

I did that myself and it took me forever and a day to figure out what was wrong.  Mainly because it said "Show my Home Page" in the top box and had the ubufox website in the Home Page bar.....

TTUL
Gary

---

### Post by Stormtrooper42 on 2010-06-05
Type *about:config* in the address bar, and look for **browser.startup.page** 
It should be set to 1 if you want to open your homepage on startup.

(According to _[this article]("http://kb.mozillazine.org/Browser.startup.page")_, I'd say yours is currently set to 2)

---

### Post by 29732 on 2010-06-06
I occasionally find it a useful feature only when I want to save the page and it only does that if I shutdown the PC without closing Firefox. Then it just restores what I have.

---

