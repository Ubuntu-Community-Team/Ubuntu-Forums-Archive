---
title: "Ubuntu 9.10 fails to load after updates"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by hitemhrd on 2010-01-06
I rebooted after installing the 11 updates Ubuntu just reccomended and now I get the option to load into Windows or Ubuntu when I boot, but I don't get the option to choose which mode of Linux I want to start in. I just get a screen that says:

GNU Grub version 1.97~beta 4

{ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device file completions. )

Based on other posts I tried the following commands to try to get X to load:


X - Configure
aticonfig  --initial
dpkg -reconfigure xserver -xorg

all of these commands failed. I got the response "error:unknown command" when I tried these. Control-Alt-F2 didn't do anything either. Any suggstions? Thanks in advance.

Eric

---

### Post by canthus13 on 2010-01-06
See if you can get it to boot with [supergrub]("http://supergrubdisk.org"). GRUB may have been damaged.  If you can boot that way, all you need to do is reinstall grub.  See [URL="https://wiki.ubuntu.com/Grub2"]this
[/URL] for how to reinstall it. (Under Recover Grub2 Via LiveCD)
--Me

---

### Post by hitemhrd on 2010-01-06
Thanks for the quick response. Here is where I am at. I've made the CD from the ISO and booted to it.

I'm at the step on the link below:

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

$ sudo mount --bind /dev /mnt/dev

and I am getting the message "mount point /mnt/dev does not exist"

I feel close but am obviously doing something wrong here. Thanks so much for the assistance.

---

### Post by canthus13 on 2010-01-06
Did you use SuperGrub or a LiveCD?

--Me

---

### Post by hitemhrd on 2010-01-06
Super Grub

---

### Post by canthus13 on 2010-01-06
Ok. reboot, skip all the mount instructions, and start at nano /etc/default/grub .  then stop after grub-install --recheck /dev/sda .  THe rest is only necessary if you're booting with teh LiveCD.

--Me

---

### Post by hitemhrd on 2010-01-06
So I follow the step:

    * Now mount the rest of your devices 

$ sudo mount --bind /dev /mnt/dev

It opens the window for GNU nano 2.0.9. But I don't kow what to edit there if anything.

When I type 'update-grub' I get 'you must run this as root.' When I type 'root' it says that 'root' is not installed. I tried to type "sudo apt-get install root-system-bin' I get 'E couldn't find package root-system-bin'

Sorry to be so remedial. Thanks for your patience.

---

### Post by canthus13 on 2010-01-06
You likely don't need to change anything in there, actually. (I just looked at my own /etc/default/grub).  Now when it says that a command must be run as root, you prepend a sudo to the command. in this case, sudo grub-update

---

### Post by hitemhrd on 2010-01-06
tried that and get 'grub-probe: error: cannot find a device for /. 

Once again...thanks for the help

---

### Post by canthus13 on 2010-01-06
You could just try a sudo grub-install /dev/sda (or whichever drive you're installed on.  If you're not sure, paste the contents of sudo fdisk -l and we'll figure it out)

--Me

---

### Post by hitemhrd on 2010-01-06
You are the best. Here is what I am getting and the fdisk info.

buntu@ubuntu:~$ sudo grub-install /dev1/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo update-grub
grub-probe: error: cannot find a device for /.

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ fdisk -l
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       37639   302279040    7  HPFS/NTFS
/dev/sda3           37640       38913    10233405   db  CP/M / CTOS / ...
ubuntu@ubuntu:~$ sudo grub-install /dev/sda2
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ sudo grub-install /dev/sda1
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$

---

### Post by canthus13 on 2010-01-06
try:  sudo grub-install /dev/sda 

--me

---

### Post by hitemhrd on 2010-01-06
Here's what I got...

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

---

### Post by canthus13 on 2010-01-06
Hmm... You got me. Hopefully someone else can help you further... I can't think of anything else off-hand.  If I run into something, though, I'll definitely post it here.

--Me

---

### Post by kansasnoob on 2010-01-06
Are you running the Ubuntu Live CD right now?

---

### Post by hitemhrd on 2010-01-06
No the supergrub cd. Do I need to download a live cd? If so, just say the word.

---

### Post by kansasnoob on 2010-01-06
I just don't understand this at all:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa42d04a3

Device Boot Start End Blocks Id System
/dev/sda1 1 7 56196 de Dell Utility
/dev/sda2 * 8 37639 302279040 7 HPFS/NTFS
/dev/sda3 37640 38913 10233405 db CP/M / CTOS / ...
```

I'd expect to see some:

```
/dev/sda8           10302       12215    15374173+  83  Linux
/dev/sda9           14880       15032     1228941   82  Linux swap / Solaris
```


In there some where.

---

### Post by hitemhrd on 2010-01-06
It's a dual boot system. XP and Ubuntu. Don't know if that matters. Running it on a Dell Vostro 1710.

---

### Post by kansasnoob on 2010-01-06
Are you sure it wasn't a Wubi install like this:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by hitemhrd on 2010-01-06
Yes, that's exactly how I installed it. When i boot I still get the choice of which OS to use. I had last updated all the patches a few days ago. So today there were new ones to install and after they loaded I ran into these problems. What do you suggest? What can I do? thanks to all that are helping.

---

### Post by kansasnoob on 2010-01-06
Sadly I know little to nothing about Wubi. I tried it once but came to prefer an actual partitioned dual boot.

I have read about similar problems recently but don't understand what's up.

---

### Post by canthus13 on 2010-01-06
Wubi could definitely explain why grub couldn't find anything.  It's not actually in a partition.  It's inside a big file on your hard drive.  Your partition table doesn't show it.  Of course, you can keep using the SuperGrub CD to boot with until you find a permanent solution. :)

--Me

---

### Post by kansasnoob on 2010-01-06
This is what I was thinking of:

[http://ubuntuforums.org/showthread.php?t=1372425](http://ubuntuforums.org/showthread.php?t=1372425)

[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104)

Sorry I can't be of more help :(

---

### Post by centaure on 2010-01-06
**Re: Wubi 9.10 + upgrade ubuntu = sh:grub>**             
                                                                I had the same problem after performing a ubuntu update today. I am running wubi on Windows 7. 

Once you login to windows, performing the following should suffice  (from [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all%29;")  :-

**(note that in my case, I did not need to perform the steps indicated in B) below )

[Agostino Russo]("https://launchpad.net/%7Eago")             wrote             on 2009-12-23:                                                             [ #210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")                                                        For a patch/workaround:
 A) get the wubildr in [https://bugs.edge.launchpad.net/ubun...04/comments/90]("https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90") and copy it over C:\wubildr
B) ensure that when you boot there is no command "insmod ntfs". Press "e" at the grub boot menu to edit the relevant entry and remove "insmod ntfs" before proceeding
New ubuntu/wubi installations do not contain the patch yet. The patch will only be applied once there is a clear confirmation (from you) that it actually solves the problem. Hence your feedback is appreciated.
                                                                                                                                    *                                              [Last edited by centaure]("http://ubuntuforums.org/posthistory.php?p=8622749"); 1 Hour Ago at 10:07 PM..                                                           *

---

### Post by hitemhrd on 2010-01-07
Here is what I got...I only got a few commands into it and go this message. But I feel we are on the right track... :)

ubuntu@ubuntu:~$ sudo mkdir /win /vdisk /vdisk.boot
ubuntu@ubuntu:~$ sudo mount /dev/sdal1 /win
mount: special device /dev/sdal1 does not exist

---

### Post by hitemhrd on 2010-01-07
I also tried replacing the C:\wubildr file as instructed and that didn't yield any difference yet. Still optimistic we can get this. Really want to learn more about Ubuntu and the more I work through things like this the more familiar I will be with it.

---

### Post by Tutun on 2010-01-09
Thank U [centaure]("http://ubuntuforums.org/member.php?u=992677").

Option A is working perfectly.....

---

### Post by filipvanlaenen on 2010-01-09
> **hitemhrd said:**
> I also tried replacing the C:\wubildr file as instructed and that didn't yield any difference yet. Still optimistic we can get this. Really want to learn more about Ubuntu and the more I work through things like this the more familiar I will be with it.

I was struggling with the same problem yesterday, and what seemed to help for me was to copy both wubildr and wubildr.mbr. After that, at least I managed to log in once more and take a back-up, so that I could make a fresh start with a real dual boot.

For the record: my problems started when I upgraded from 2.6.31-16 to -17. In fact, when I try to load -17, the laptop complained a magical number being wrong, so I had to log in using -16.

---

### Post by KEBDARGE on 2010-01-20
great!
replacing the wubildr file worked!

---

### Post by shadowlands on 2010-02-12
there was nothing in the file when i opened it.Well not nothing just not code it looked like a bad file. like when a word doc messes up when open in a new program garbage. > **KEBDARGE said:**
> great!
replacing the wubildr file worked!

---

