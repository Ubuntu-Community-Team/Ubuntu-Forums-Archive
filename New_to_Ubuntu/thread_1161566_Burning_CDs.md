---
title: "Burning CDs"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by goldblattster on 2009-05-16
I need to make a GParted CD for my friend. I downloaded the .iso, and inserted a blank disc. Then I open "CD/DVD Creator" from the menu. When the window opens, I cannot find any way to burn .iso files? how do I do this?

---

### Post by Locutus_of_Borg on 2009-05-16
open terminal
enter:

cdrecord dev=/dev/sr0 /path/to/gparted.iso

your optical drive should be /dev/sr0 unless its really really old

---

### Post by yanceypd on 2009-05-16
Usually you can right click on ISO image and select burn to disk.

---

### Post by Electron on 2009-05-16
Use Brasero for an iso image or gnomebaker

---

### Post by goldblattster on 2009-05-16
Thank you! That worked!

---

