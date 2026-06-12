---
title: "Cannot Boot to Windows 7 (MBR problem)"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by Ira_S on 2010-01-17
hello,  i have windows 7 on this computer.  but i cannot boot up to it,  whenever i turn the computer on,  that little cursor at the top left corner of the screen just blinks, and the system hangs.    
 
however, i did have Linux Ubuntu 9.10 on the computer side by side with windows 7,   the GRUB boot loader for it did not work for booting up Windows 7,  
 I finaly tryed Formatting the Partition that Linux was on, (Now its just Windows 7 and Unused space),  But GRUB was still on the computer,  so  I used the Windows 7 Home Premium Install Disk, to try and repair the problem (Automatic Repair did not work, and i also tryed using the Command Prompt too, such as  "bootrec.exe/fixboot" and "bootsect /nt60 ALL").  But none of those worked (even though it said it did), HOWEVER,  after i did those steps, GRUB was apparently gone,.  Now the system jsut hangs as i described before,  ... Is there a way i can get the windows  MBR files back without Formatting and reinstalling Windows 7?
 
 Windows 7 is still on the computer! and i CAN access the files that are in it, ( i am running the same computer off of "Try Ubuntu without installing" disk thing)
 Please any Ideas would be greatly apreciated.

---

### Post by drs305 on 2010-01-17
If you are on the LiveCD desktop, the easiest way to restore the Windows MBR is probably to install *lilo* and allow it to write to the Windows MBR:

```

sudo apt-get install lilo && sudo lilo -M /dev/sd**[COLOR="Red"]X[/COLOR]** mbr

```
**[COLOR="Red"]X[/COLOR]** would be the device Windows is on, most likely sd**[COLOR="Red"]a[/COLOR]**


That should work, and from your post you have probably seen this or something like it, but if not:
[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by Ira_S on 2010-01-17
device as in Partition/Drive Letter?  wouldent that be C?  i only have 1 hardrive

---

### Post by Ira_S on 2010-01-17
ok i tryed that, but it encountered an error,   Thats what the FULL terminal said

0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main mbr 1.1.10-2 [23.0kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main lilo 1:22.8-8ubuntu1 [390kB]
Fetched 413kB in 8s (48.6kB/s)                                                 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package mbr.
(Reading database ... 120319 files and directories currently installed.)
Unpacking mbr (from .../archives/mbr_1.1.10-2_i386.deb) ...
Selecting previously deselected package lilo.
Unpacking lilo (from .../lilo_1%3a22.8-8ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lilo (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 lilo
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ sudo apt-get install lilo && sudo lilo -M /dev/sdc mbr
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up lilo (1:22.8-8ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lilo (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 lilo
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by drs305 on 2010-01-18
Ira_S,

lilo didn't install correctly because the installation process couldn't access a file it needed. Reboot the machine if you haven't already - this should free anything "locked" by the installation programs.

Next attempt to reinstall lilo:
```

sudo apt-get install --reinstall lilo
```

If you still get errors:
```
apt-get install -f
```

If errors reoccur, then run this to show us what is causing the error:
```

dpkg -l | grep -v -e ^ii -e ^rc
```

This problem isn't related to the boot problems - we are just trying to get lilo installed without errors so we allow it to write to the Windows MBR.  If you continue to have errors, take a look at the link I provided in my previous post and ensure you already tried what it suggested using the appropriate Windows CD/DVD.

, then run the second command to try to clear the error.

---

