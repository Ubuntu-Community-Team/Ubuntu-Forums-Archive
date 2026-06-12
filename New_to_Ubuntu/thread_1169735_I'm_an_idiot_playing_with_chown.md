---
title: "I'm an idiot playing with chown"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by ah pook on 2009-05-25
ok: I have a Movies directory, and it was all messed up as far as permissions go. I read a few posts here, but obviously not the right ones, and while playing with chown messed up the logins and everything. Now I'm running off an install disk, and as things were set-up almost perfectly, except for the permissions, I don't really want to reinstall everything. 

I can't login, I get a GDM error and something about my /Home directory being locked.. Help!:oops:

---

### Post by taurus on 2009-05-25
Do you have a separate partition for /home or you have one big partition for /?  From Ubuntu LiveCD, post the output of this command since you need to mount it and have a look at the permission/ownership of your $HOME (or at least /home).

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by ah pook on 2009-05-25
boy, you guys are quick...


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffffffff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9729    78148161   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091d82

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3579    28748286   83  Linux
/dev/sdc2            3580        3738     1277167+   5  Extended
/dev/sdc5            3580        3738     1277136   82  Linux swap / Solaris

Disk /dev/sdd: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b081b07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       14593   117218241   83  Linux

the ubuntu stuff is on the 30 gb drive, but you already knew that...

---

### Post by taurus on 2009-05-25
If Ubuntu is on /dev/sdc1, what are those three harddrives:  /dev/sda1, /dev/sdb1, & /dev/sdd1?  Is there a separate /home?  Which release did you install on your harddrive?

```
sudo mkdir /media/ubuntu
sudo mount -t ext4 /dev/sdc1 /media/ubuntu
ls -la /media/ubuntu/home
```

---

### Post by ah pook on 2009-05-25
Sdb1 is movies, sdd1 is music, and sda1 is, ummm,  other stuff.
I upgraded from 8.10 thru the update-manager to 9.04.

Should I run those commands in the box? Bear in mind, I'm running off a 9.04 install disk I have laying around, so I'm not sure if it gives me permission to do a bunch of things..

/home is on /sdc1...

---

### Post by ah pook on 2009-05-25
Luckily I was able to re install everything, sorta, by having all the important stuff on other drives. It took me a couple hours, but most things are back to normal. 

Thanks for all the help, and I'm never playing with chown again....

---

### Post by asmoore82 on 2009-05-25
> **ah pook said:**
> Luckily I was able to re install everything, sorta, by having all the important stuff on other drives. It took me a couple hours, but most things are back to normal. 

Thanks for all the help, and I'm never playing with chown again....

I would never discourage you from "playing with chown again" ...

but you have found out that it requires root privilege for good reason ;)

Once upon a time, I deleted the "USER.SYS" file from SYSTEM32 on WinMe.
I did it again some time later to prove to myself that it could be
easily restored from the "Recycle Bin" with a Linux liveCD.

Mistakes are the only way we truly learn.

~ "Everybody falls the first time." ~

---

