---
title: "i need help please EW-7318ug"
date: 2007-07-15
forum: Networking &amp; Wireless
---

### Post by Drunken Piggy on 2007-07-15
ok i am just utterly s**t with this whole terminl thing so could some one with some experience tell me what drivers  to use for the edimax card and how to download them and how to instal them properly so i can pick up my wireless and use this silly tower please.

tis the edimax card EW-7318Ug wireless USB card plugged into a small pentium run tower.

any help at all would be apreciated thank you

---

### Post by odiseo77 on 2007-07-15
According to [this link]("http://www.linuxquestions.org/hcl/showproduct.php/product/3712"), it seems the card uses the Ralink RT73, so I would be surprised it didn't work on ubuntu.

Anyway, could you tell us what's the output of ***lsusb*** (with the card plugged in) and ***iwconfig*** ??

Regards.

P.S.: there's a howto here in the forum about RT73 based cards, just have to look for it.

EDIT: [found it]("http://ubuntuforums.org/showthread.php?t=400236").

---

### Post by rodica.balasa on 2008-01-18
I managed to make it work using Edimax drivers, only on inconvinence: it is seen as a wired connection by network manager (using gutsy):

[http://www.len.ro/work/tools/old-new-i8000-2]("http://www.len.ro/work/tools/old-new-i8000-2")

---

