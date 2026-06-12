---
title: "How to start usbserial w/ options on startup?"
date: 2007-10-19
forum: Networking &amp; Wireless
---

### Post by jimbojones on 2007-10-19
I recently did a fresh install to 7.10 from feisty.  I used to have a line added in  **/etc/modules  **of  **usbserial vendor=0×413c product=0×8114 **
This was to load the usbserial driver to my embedded verizon wireless card.  I tried this in Gutsy and for some reason it doesnt seem to have the same effect...is there somewhere else I should add this setting to?  I am at a loss.
Manually inputting  **sudo modprobe usbserial vendor=0×413c  product=0×8114 **  still works fine, its getting it to automatically happen on startup that is not working as it once used to.  Thanks

---

### Post by jimbojones on 2007-10-19
Nm.  Seems to work now.  I removed my changes and re edited the files, now it works.  :)   Probally a typo of some sort

---

