---
title: "Formatting Micro SD card"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by L Campbell on 2011-04-01
I'm hoping to format a 2 GB Micro SD card for a 'Key Chain' camera and I would like to know if I should make it FAT 32, or ?

I have installed Gparted from the Ubuntu Software Center but am having trouble finding my card.

TIA

---

### Post by KeLa on 2011-04-01
I think FAT32 is safe choice for the format. If it doesn't work then try something else.

---

### Post by seawolf167 on 2011-04-01
FAT caps at 2GB, so FAT32 would be the format of choice.

Your device will probably show up as an external hard drive or USB drive, easiest way to check is just to plug it in, refresh GParted and see what the new entry is.

If that doesn't work, you can find the entries by looking at the differences between either

```
lsusb
```

or 

```
lshw -class disk
```

before and after the SD card insertion

---

