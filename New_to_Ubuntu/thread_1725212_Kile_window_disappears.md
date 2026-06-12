---
title: "Kile window disappears"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by yyxt11a on 2011-04-09
Hi, I am using Kile to write my Latex document. When I tried to adjust the file window panel with the mouse, the panel disappeared. I have reinstalled Kile since, but the problem still exist.  Is this problem in Kile or in Ubuntu? Thanks

---

### Post by rosencrantz on 2011-04-13
try deleting ~/.kde/share/config/kilerc
Also, check whether you have the latest kile. Beta 5/2.0.86 fixed some bugs for me, but I had to get it from the project page;
[http://kile.sourceforge.net/download.php](http://kile.sourceforge.net/download.php)
 according to 
apt-cache policy kile
the Maverick Universe package is still beta 4.
My installation log:
[http://eumenidae.blogspot.com/2011/01/kile-kde-46-and-autocomplete.html](http://eumenidae.blogspot.com/2011/01/kile-kde-46-and-autocomplete.html)

---

