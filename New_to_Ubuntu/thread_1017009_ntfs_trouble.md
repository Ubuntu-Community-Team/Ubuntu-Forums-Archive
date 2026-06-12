---
title: "ntfs trouble"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by newmans on 2008-12-20
Windows crashed and wouldn't start in safe mode. I'm using a flashdrive to run ubuntu and I am trying to save info from my hard drive. this is some information:
ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda

Disk /dev/sdb: 4009 MB, 4009754624 bytes
216 heads, 32 sectors/track, 1133 cylinders
Units = cylinders of 6912 * 512 = 3538944 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1134     3915760    b  W95 FAT32

I can't get into windows to have a clean shut down (which might be of some help?) any ideas on how to get round this problem? cheers in advance

---

### Post by birddog165 on 2008-12-20
I don't know if this helps. But whenever I put windows in hibernate, I can't access it from Ubuntu. It's only when I properly shut it down. Maybe this is related. You might just have to fix the Windows :(

---

### Post by logos34 on 2008-12-20
if you have an XP install cd the first thing you want try is booting into recovery console and running error check w/repair option at the prompt

chkdsk /r

---

### Post by kansasnoob on 2008-12-20
Is this XP or Vista?

---

### Post by kansasnoob on 2008-12-20
> **kansasnoob said:**
> Is this XP or Vista?

Regardless make sure you have ntfsprogs installed on the external drive. That will give you excellent read and write capabilities for NTFS.

But if Win is really dead, or the hard drive is failing, a flash drive is not going to give you the space you need to save much data.

---

### Post by newmans on 2008-12-21
Cheers for the advice, its XP not vista that I'm trying to save (once saved I'll be getting rid of it for good) I've got the os discs, but the service pack 2 one doesnt seem to work and service pack 1 c.d wont work properly when set to the recovery mode. So There is no way I can find to enter windows to clear stuff up or even to get a clean shut down so I can access through ubuntu. I've tried downloading the ntfs 3drg? (can't remember at the moment) but it doesnt seem to take effect, is this because I'm using a flash drive to run ubuntu?

---

### Post by presence1960 on 2008-12-21
If you cant get windows going you can use a Live Cd to access your files you want to save. Hopefully you have 2 cd/dvd drives with one being a RW. If not hopefully you have a big enough flash drive or two to put your files onto. In this worst case scenario you can at least save your files then reinstall if nothing else will solve the problem.

---

### Post by presence1960 on 2008-12-21
oops sorry i missed the part where it said cannot open dev/sda. my bad!

---

