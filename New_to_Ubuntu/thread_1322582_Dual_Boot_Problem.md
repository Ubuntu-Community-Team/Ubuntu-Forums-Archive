---
title: "Dual Boot Problem"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by rrvnd on 2009-11-11
Hello, I am a newbie. I need help please. Please excuse the long message.
I have 2 hard disks with xp and ubuntu installed in those. I formatted the disk containing Ubuntu from XP.Basically I was trying to partition it to fit windows 7 in it. After this I cannot boot into XP. GRUB comes up showing an Error. I tried using Super GRUB booting CD. When I click on windows xp, it came up with an error saying "Windows could not start because of an error in the software. Load needed DLLs for kernel". I have now reinstalled xubuntu to the disk which had ubuntu. I can reach xubuntu but cannot go into xp. It gives the same error message as above. I tried going into the recovery console but this does not show the c drive which has xp in it. could someone help please.

---

### Post by karth83 on 2009-11-11
You have to use Win XP Installation cd to repair the MBR. After you can get back the grub using xubuntu live cd without installing the xubuntu again.

---

### Post by rrvnd on 2009-11-11
Thanks karth
I do not have the CD as the recovery console came bundled as a partition. Any ideas?

---

### Post by Absolut Newbee on 2009-11-11
try have a look at this webpage

[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

hope it helps

---

### Post by rrvnd on 2009-11-11
thanks newbie, will try when i get home.

---

### Post by rrvnd on 2009-11-12
My MBR has been repaired but still cannot boot to xp with same error message. Will have to live without xp, while I use linux. Thanks for your help.

---

