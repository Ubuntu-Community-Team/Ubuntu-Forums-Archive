---
title: "No more Disk space?"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by sxmac on 2010-10-04
Hi i have 2 hard drives on my computer, and i wasent using one of em at all, so i installed ubuntu onto my other drive, i know for a fact this drive has 500 gigs in it but for some reason it says the disk is full and everytime i try to download something while im logged in ubuntu it says disk full. Also i am duel booting windows and linux, im sure this has something to do with it because windows shows it as having about 400 gigs free.

---

### Post by CharlesA on 2010-10-04
Run this please:

```
sudo fdisk -l
```

```
df -h
```

```
du -h --max-depth=1 /
```

Post the output (minus permission denied messages).

---

### Post by Goolie on 2010-10-05
We need to take a look at that ^.  

But it seems to be possible that you installed Ubuntu side by side on the same drive instead of on the other drive.

---

### Post by emoguitarist06 on 2010-10-05
have you looked at what gParted says? or if you don't have gparted installed you can install it from the software center

---

