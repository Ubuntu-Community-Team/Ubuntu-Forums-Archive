---
title: "System is not booting"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by msidhard on 2009-03-02
Last time i have a power failure. Now when i started my system the grub says error 15 file not found. And i tried my ubuntu 8.10 live cd it says 'buffer i/o error on device dev sda logical block zero'. My live cd is perfect. It works good.

---

### Post by sandyd on 2009-03-02
ive seen this before......

but heres the weird thing

at school, i work as support tech, so i go and see the same problem, except that its a windows system

booted livecd and see the same error as you

just run a disk check on your system and everything should be fine and dandy. (i used chkdsk in windows, but its only for NTFS and FAT32 partitions, not ext2/3)

---

### Post by msidhard on 2009-03-03
But the system has windows. The grub hangs in error 15 . So i cant enter the windows too.

---

### Post by Crafty Kisses on 2009-03-03
So I'm confused with this issue. What's your default OS? Windows or Ubuntu? Are you dual booting?

---

### Post by lisati on 2009-03-03
> **msidhard said:**
> But the system has windows. The grub hangs in error 15 . So i cant enter the windows too.

Probably means booting up with a livecd (if it works) and doing your troubleshooting from there. The "Error 15" message refers to some problem locating your OS.... there are several threads on the forums dealing with "Grub error XX" - good luck finding the one which helps.

---

### Post by msidhard on 2009-03-03
MY SYSTEM IS HAVING UBUNTU 8.10 AND WINDOWS. BUT LInux IS DEFAULT

---

### Post by msidhard on 2009-03-03
But grub error 15 may be fixed with reinstalling the grub. I have a doubt that my hard disk is damaged or not . I think that the error says it cant read the hard disk mbr is that right.

---

