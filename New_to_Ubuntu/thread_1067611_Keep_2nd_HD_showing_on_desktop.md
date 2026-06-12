---
title: "Keep 2nd HD showing on desktop"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by kelscmi on 2009-02-12
My computer has two HD, and I keep all my files on the second HD.  Is there a way to "lock" the icon for the second HD to my desktop?  If so how would I do it and would it cause any problems with the M$ files which are also on the second HD?

---

### Post by logos34 on 2009-02-12
run this in a terminal:

> gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible "true"

this will show icons for all partitions on the 2nd disk, as well as the first except for /  (and /home if separate)

---

### Post by DerHesse on 2009-02-12
Hi Kelscmi,
by default icons show up, if mounted under /media/xxx only.
 
Greetz

---

### Post by kelscmi on 2009-02-21
The drive shows up in /media but the icon issue is having it load up on the desktop when logging in.  It is not a big problem, I was just hoping to find a way to not have to places > removable media to access the folders.  I only have to do it when I first start up the computer, after that the icon remains on the desktop until I shut the system down.
Thank you for your support.

---

