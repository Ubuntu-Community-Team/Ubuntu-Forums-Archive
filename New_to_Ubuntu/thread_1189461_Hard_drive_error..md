---
title: "Hard drive error."
date: 2009-06-16
forum: New to Ubuntu
---

### Post by icyest on 2009-06-16
Hi, I'm having some problems installing windows 7 on my machine which currently runs Ubuntu 9.04. 

Details:
-When I try to boot from CD, it says that hard drives are not recognized as NTSF (I don't know what that means).
-Did linux do something to my hard drive that I don't know about?
-My goal here is to replace Ubuntu 9.04 completely with windows 7.

---

### Post by DGortze380 on 2009-06-16
> **icyest said:**
> Hi, I'm having some problems installing windows 7 on my machine which currently runs Ubuntu 9.04. 

Details:
-When I try to boot from CD, it says that hard drives are not recognized as NTSF (I don't know what that means).
-Did linux do something to my hard drive that I don't know about?
-My goal here is to replace Ubuntu 9.04 completely with windows 7.

Linux formatted your hard drive to ext3
Windows uses NTFS
Put in your Ubuntu Live CD, open GParted, delete all partitons, create one new NTFS or FAT32 partition.

Reboot with your Windows 7 Install Disc and it should recognize the drive and reformat to NTFS.

---

### Post by wpshooter on 2009-06-16
Or just use [www.killdisk.com](www.killdisk.com) to WIPE your hard drive completely clean and then your Windows 7 CD should work.

---

### Post by icyest on 2009-06-16
Dude, thats a windows program. It wont work on linux.

---

### Post by PukingPenguin on 2009-06-16
> **wpshooter said:**
> Or just use [www.killdisk.com](www.killdisk.com) to WIPE your hard drive completely clean and then your Windows 7 CD should work.

LOL! I wouldn't trust any Windows app to do anything secure. 

Use [DBAN]("http://www.dban.org/").

---

### Post by wpshooter on 2009-06-16
> **icyest said:**
> Dude, thats a windows program. It wont work on linux.

That's really funny, since I have been using it for the last 4 or 5 years to WIPE hard drives clean !!!

I sure must have missed something !!!  Or maybe it's that you have missed something !!!

---

### Post by zeroseven0183 on 2009-06-16
I think Killdisk has a [DOS-only version]("http://www.killdisk.com/downloadfree.htm").

That's bad to know that he's switching his machine to Windows 7? Anyway, +1 for DGortze380's suggestion.

---

### Post by icyest on 2009-06-16
> **wpshooter said:**
> That's really funny, since I have been using it for the last 4 or 5 years to WIPE hard drives clean !!!

I sure must have missed something !!!  Or maybe it's that you have missed something !!!

Lol, fail...

zeroseven0183 is right. You missed something!!!

---

### Post by wpshooter on 2009-06-16
> **icyest said:**
> Lol, fail...

zeroseven0183 is right. You missed something!!!

I did not miss anything, it can be used on either a bootable diskette or a CD rom to WIPE the drive when the **_bootable_** media is in the drive.

I don't remember saying a thing about running it in Linux or was it someone else that said that ???

---

### Post by icyest on 2009-06-16
Instructions were very very unclear. You mentioned nothing about bootable. The website is also very unclear.

---

### Post by wpshooter on 2009-06-16
> **icyest said:**
> Instructions were very very unclear. You mentioned nothing about bootable. The website is also very unclear.

Website say "download bootable ISO image to burn to CD"

I don't know how much clearer you could want it !!!

---

