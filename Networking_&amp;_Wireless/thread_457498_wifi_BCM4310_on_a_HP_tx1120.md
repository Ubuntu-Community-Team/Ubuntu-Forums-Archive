---
title: "wifi BCM4310 on a HP tx1120"
date: 2007-05-28
forum: Networking &amp; Wireless
---

### Post by dphipps on 2007-05-28
I can not get my wireless to work on my laptop a HP tx1120 with a Broadcom BCM 4310.  First I tried to use the bcm43xx driver but this did not work.  Now I have the ndiswrapper with driver installed but it is still using the bcm43xx driver.  What can I do about this.

```
user@laptop:~$ sudo ndiswrapper -l
bcmwl6 : driver installed
        device (14E4:4312) present (alternate driver: bcm43xx)
```

---

### Post by hollowhead on 2007-05-29
If you are using feisty then pull down the preferences menu (cannot remember what exactly it is called) and select wireless settings or something very bottom of the menu anyway (sorry I'm on winblows) there seems to be a ndiswrapper control applet which allows setup and removal of ndiswrapper stuff.  I followed this guys guide and used his script which has worked perfectly for me both on dapper and feisty [http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+4318)

Hope this helps.

---

### Post by dphipps on 2007-05-29
I am using Feisty.  The thing is the ndiswrapper seems to be installed correctly it Linux just isn't using it.  I think that what I need is some way to remove the bcm43xx driver.

---

### Post by dphipps on 2007-05-30
*  *  *

---

### Post by dphipps on 2007-06-03
Anyone have any other ideas?

---

