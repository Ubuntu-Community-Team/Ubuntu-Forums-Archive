---
title: "e1405 card reader not working"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by paulchinnz on 2009-01-28
Hi my 5-in-1 removable memory card reader isn't reading at all in Ubuntu i.e. when I insert a card the card doesn't appear as something to mount, in fact, as far as I can tell, nothing happens.

---

### Post by Boomhauer on 2009-01-28
try running ```
sudo modprobe sdhci
``` from a terminal, and then put in your sd card.  if modprobe sdhci returns errors paste them back here.  my e1705 mounts an sd card to /media/disk by default, if you dont see anything there, check /dev/mmcblk0p1

---

### Post by paulchinnz on 2009-01-28
Thanks.  Tried the code, checked in that folder, nothing.  I can access the memory stick in XP though, so hardware seems okay otherwise.  Any other ideas?

---

### Post by paulchinnz on 2009-01-31
Just to clarify, I don't have that mmcblk0p1 file in /dev; should I?

---

### Post by paulchinnz on 2009-02-16
Anyone have any other ideas?

---

### Post by paulchinnz on 2009-02-22
Bump again

---

