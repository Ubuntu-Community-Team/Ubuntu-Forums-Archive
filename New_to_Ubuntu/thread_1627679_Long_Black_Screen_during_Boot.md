---
title: "Long Black Screen during Boot"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by slixz85 on 2010-11-21
Hi, I am using 10.04 lts i get a long black screen when the computer boots up it seems like 4 minutes or so but when the desktop finally comes on everything is completely loaded already and this is a freshly installed lts. no boot load graphics show or anything. how can i get this to boot faster. its a dell inspiron mini 10

---

### Post by Rubi1200 on 2010-11-22
Hi,
how much RAM do you have and what graphics card is installed?

---

### Post by slixz85 on 2010-11-22
[http://www.technotalks.com/reviews/dell-inspiron-mini-10v-netbook-reviews/](http://www.technotalks.com/reviews/dell-inspiron-mini-10v-netbook-reviews/) here is the laptops specs troublesome video card i have checked on net but everything looks good to me once loaded up just no boot screens show

---

### Post by Rubi1200 on 2010-11-22
Just out of curiosity, try this at boot time:

When the GRUB menu appears and the entry for Ubuntu is highlighted, press "e" to edit.

Navigate using the cursor keys to the line that ends with > quiet splash
Remove quiet splash and type this in it's place: i915.modeset=1

Then, "Ctrl" + "x" to boot.

Let us know if the boot time is faster or if you see any error messages that may lead us in the right direction.

---

