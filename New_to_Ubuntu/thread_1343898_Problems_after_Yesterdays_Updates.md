---
title: "Problems after Yesterdays Updates"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by PPPilot on 2009-12-02
After yesterdays updates I started having problems. I am running Karmic on a Frankenstein machine built from parts of a bunch of old machines. 1200Mhz Athlon with 512 MB RAM and 3 old IDE Drives (Karmic installed alone on 40 GB Drive). It ran fine until yesterdays update which seemed to be concerned with hard drive read ahead. Now when I boot up it asks me to Login even though I have login set to automatic. After login the screen flashes the brown Ubuntu Splash screen several times, sometimes all scrambled and then sends me back to the login screen. I then did a fresh install from the CD I got from Ubuntu, the original install was from a Live CD I down loaded. After the new install it booted once and after the updates were installed (154 updates) it is back to the same problem. Also since the new install, I do not have the Boot Menu any more.

---

### Post by ukripper on 2009-12-02
Can you reboot and while rebooting hold shift until you see the grub screen. From there select third option kernel i guess it would be **2.6.31-14**. And see if you get the same problem after this.

---

### Post by PPPilot on 2009-12-02
> **ukripper said:**
> Can you reboot and while rebooting hold shift until you see the grub screen. From there select third option kernel i guess it would be **2.6.31-14**. And see if you get the same problem after this.

I got the menu using the shift key** 2.6.31**-14 just kept giving me the login screen as originally described. I tried **2.6.31.15 **again and after two or three logins it finally booted with this error:

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-iYuiSAixqd: Connection refused)

Now I'm really confused as I am not on a network other than the Internet thus no configuration server????

---

### Post by ukripper on 2009-12-02
Can you choose the second option from grub menu recovery mode and run fsck from the option once booted in recovery.

---

### Post by PPPilot on 2009-12-02
> **ukripper said:**
> Can you choose the second option from grub menu recovery mode and run fsck from the option once booted in recovery.

Ran as above. After typing in "fsck" at the command line I got the following message:

"WARNING!!! Running e2fsck on a mounted file system may cause SEVERE file system damage. Do you wish to continue Yes/No?

Obviously, I did not continue...

---

### Post by ukripper on 2009-12-02
Boot into live cd and run fsck on  your hardisk:

After booting into live cd go to terminal and run this:
```
sudo fsck /dev/sda
```

---

### Post by PPPilot on 2009-12-02
> **ukripper said:**
> Boot into live cd and run fsck on  your hardisk:

After booting into live cd go to terminal and run this:
```
sudo fsck /dev/sda
```

Here is the Output:

ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$ 

Any Help????

---

### Post by ukripper on 2009-12-03
can you post output of the following when you in live cd:
```
sudo fdisk -l
```

and ```
df -h
```
When in live cd do not click on any of you hardrive otherwise they will get mounted. We need to unmount them before proceeding with fsck.

---

### Post by PPPilot on 2009-12-03
> **ukripper said:**
> can you post output of the following when you in live cd:
```
sudo fdisk -l
```and ```
df -h
```When in live cd do not click on any of you hardrive otherwise they will get mounted. We need to unmount them before proceeding with fsck.

Thanks for all your Help so far and Here you go:

 **ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/sda: 40.8 GB, 40822161408 bytes
255 heads, 63 sectors/track, 4963 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x923f923f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4789    38467611   83  Linux
/dev/sda2            4790        4963     1397655    5  Extended
/dev/sda5            4790        4963     1397623+  82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe486e486

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3649    29310561   83  Linux

Disk /dev/sdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3649    29310561   83  Linux

**ubuntu@ubuntu:~$ df -h**
Filesystem            Size  Used Avail Use% Mounted on
aufs                  233M   32M  202M  14% /
udev                  233M  256K  233M   1% /dev
/dev/sr0              690M  690M     0 100% /cdrom
/dev/loop0            668M  668M     0 100% /rofs
none                  233M  104K  233M   1% /dev/shm
tmpfs                 233M   20K  233M   1% /tmp
none                  233M   88K  233M   1% /var/run
none                  233M     0  233M   0% /var/lock
none                  233M     0  233M   0% /lib/init/rw
ubuntu@ubuntu:~$

---

### Post by ukripper on 2009-12-03
Good nothing is mounted. Run this command:
```
sudo fsck /dev/sda1
```

---

### Post by PPPilot on 2009-12-03
> **ukripper said:**
> Good nothing is mounted. Run this command:
```
sudo fsck /dev/sda1
```

Here you go:

**ubuntu@ubuntu:~$ sudo fsck /dev/sda1**
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 168381/2408448 files, 1009791/9616902 blocks

---

### Post by ukripper on 2009-12-03
ok can you normally boot now, **not** with live cd. and when you reach login screen let us know if you see any errors again.

---

### Post by PPPilot on 2009-12-03
> **ukripper said:**
> Good nothing is mounted. Run this command:
```
sudo fsck /dev/sda1
```

Here you go:

**ubuntu@ubuntu:~$ sudo fsck /dev/sda1**
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 168394/2408448 files, 1010023/9616902 blocks

---

### Post by PPPilot on 2009-12-03
Sorry about the double post, I got confused jumping in and out of the Live Sessions. So here is the what I have found out.

I noticed that the problem seems to be related to the screen resolution as the monitor was clunking and breaking up as it tried to change res. during boot.  In a live boot, Ubuntu comes up clean and with a resolution of 1600x1200 (4:3). My installed version also came up the first time at that res. but even on my 19" monitor it makes for small text so I changed the res. to 1280x960 (4:3). It looks like when the the Ubuntu Splash Screen is up and the boot tries to lower the res. the problems start. I set my res back to 1600x1200 and with no res. change during boot, it seems to not have the problem. How strange??? 

Also with regard to those error messages I was getting, They seemed to be about Evolution and since I do not use Evolution, I took it out of the Startup and un-installed it and no more messages. As a side note, even with Evolution gone, it still shows up in the Application Office Menu even though selecting it returns an error "Failed to execute child process "evolution" (No such file or directory)". Any way to get rid of it from the menu???

---

