---
title: "drive mounting"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by Possom on 2009-07-10
I've loaded portable Ubuntu on a flash drive and can launch it on  my XP system but am baffled as to how to access my Windows files. I've tried from a browser using /mnt/moose/c (the name of my machine) and also just /mnt/c as a location input but doesn't play. As a complete newby to Penguinland I could sure use some specifics.

---

### Post by halitech on 2009-07-10
haven't done much with the flash install but if it works the same as a normal install, this should help

open a terminal and post the results of
```
sudo fdisk -l
```and ```
mount
```

---

### Post by jdackle on 2009-07-10
On a normal Ubuntu (haven't tried the Mobile Ubuntu) your Windows drive is NOT automatically mounted on session startup.

However, it IS automatically mounted if you go to menu "Places" (between "Applications" and "System") and click on your drive label (or something like "Disk 1" if it has no label).
A Nautilus windows should pop-up automatically then.
You should also find the drive more likely under "/media" than "/mnt" (Ubuntu is pretty unusual in this, as most other distros do mount hard-disks under "/mnt" and only removable ones under "/media" (or sometimes all under "/mnt")).

---

