---
title: "Problem mounting USB flash drive"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by XxTrAnzErxX on 2009-07-21
Hi everyone!.. this is my first time posting.. i have a small issue and i hope its not too much of a bother...

Well im running Ubuntu 9.04 Jaunty, and after i upgraded, i am having issues mounting a specific 1 GB USB Flash Drive. It gives me the error " Unable to mount volume '******', cannot get volume.fstype.alternative " as soon as i click on the drive shown on the Desktop. I tried restarting the computer obviously, it still gives the same problem, though ive successfully plugged in a Sony Ericson phone and it was detected and i was able to write to it and everything. Ive read a few posts already but most dont have a lot to do with this issue, i noticed that in GParted it detects the USB Flash Drive as FAT 16, though when i get my hands on a Windows PC it detects it as FAT 32 and it works just fine. Up to now i havent been able to actually TRY another USB Drive, haha... but it is detecting a Sony Ericson Phone and im able to write to it... oh and all USB Devices work fine... I have a printer, mouse, keyboard conected to the USB drives and they work perfectly... anybody has any suggestions ?...
I really appreciate your assistance and time... have a good one!

---

### Post by Tman5293 on 2009-07-21
Is there anything important on this flash drive cause if there isnt then you need to use gparted to repartition it. Use a fat32 partition with gparted.

---

### Post by mudcat on 2009-07-21
believe it or not some USB flash drives are not compatible with linux; try using the fdisk command and write the partition to FAT 32, this will get rid of the proprietary software like U3 Cruzer has if that is the problem

---

### Post by jerrrys on 2009-07-21
no answer, but here's a suggestion

[http://www.google.com/search?q=flash+drive+unable+to+mount+volume+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=flash+drive+unable+to+mount+volume+ubuntu+9.04&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by XxTrAnzErxX on 2009-07-22
Thanx for the quick help hehe!... well you guys have a point... i have some important files on the USB Flash drive thats the main problem... but ill go ahead and just back them up, and then format the USB Flash Drive... 

No need to complicate this.. thanx for the help.. and the link!... :)

---

