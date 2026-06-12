---
title: "system disk error"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by DarinB on 2010-10-13
my ubuntu locked up while using firefox. I tried control alt backspace to log out i got a system check every thing was ok but i had a gdm binary failure, now I can't reboot I get system disk error I am using a live cd any ideas what to do???

---

### Post by Temposs on 2010-10-13
I would suggest that you open System->Administration->Disk Utility. Click on your hard drive in that program and then click on "Check Filesystem". It should then scan your drive and tell you if there's anything wrong with it. If it tells you there are errors on that drive, then you probably are experiencing hard drive failure and you'll have to get a new one.

---

### Post by DarinB on 2010-10-13
I imagine \I am to do this using the live cd...will i have a choice to which drive to check

---

### Post by Temposs on 2010-10-13
Yes, you will do it from the livecd. It displays all your drives on the left side panel, and you just choose the right one and choose "Check Filesystem"

---

### Post by DarinB on 2010-10-13
no disk utilities in admin I use linux mint and I am able to access all my files with a live cd????

---

### Post by Temposs on 2010-10-13
You would be able to access all your files with a LiveCD

If you don't have Disk Utilities, then you'll have to open a terminal and run fsck on the drive you want to check.

---

### Post by AndyM3 on 2010-10-13
Mint has that SuSE-ish menu. Try typing "disk utility" in the search box there.

If that doesn't work, use "sudo fdisk -l" in a Terminal to see what drives you have on your system and then "sudo fsck /dev/sda1", replacing /dev/sda1 with the partition you want to check.

---

