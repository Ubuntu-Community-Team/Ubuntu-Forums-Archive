---
title: "[SOLVED] Networking has no ad-hoc"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by borobudur on 2007-02-16
Hi all, I just installed the 6.10 amd64 version on my laptop. I'm trying to connect to my desktop by using the ad-hoc mode (by iwconfig) but there is an error saying that this mode is not supported. 

It worked fine before with the regular 6.06 version (not amd64) but I had to change because there were some annoying keyboard jumping problems after a while.

Thanks for your help,
borobudur

---

### Post by gradedcheese on 2007-02-16
some cards require an extra step to enable ad-hoc mode (you only have to do it once).  As I recall, you have to edit a file somewhere in /sys  ...it might be different for each card.  I'll take a look at mine and see if I find anything.

---

### Post by borobudur on 2007-02-18
Anyone, please help!

---

### Post by borobudur on 2007-02-20
Okay, here I have some more details. I restart my network: 

/etc/init.d/networking restart 

Then I get the following error:

Error for wireless request "Set Mode" (8B06) : SET failed on device ra0; Function not implemened...

---

### Post by borobudur on 2008-03-01
My hardware environment looks different by now. So I set this thread as solved

---

