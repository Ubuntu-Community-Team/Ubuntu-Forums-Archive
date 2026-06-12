---
title: "stuck after boot"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by mikedmor on 2009-02-20
I was working with wine (only fonts to repair some problems i was having) when all of a sudden nothing would open anymore. well i thought ok i probably just need to restart. well as soon as i rebooted and got back to where the login screen was suppose to boot i get stuck in the brownish screen with my mouse showing that is is loading.

ALT+F2,F3,F4,ETC does not work either. but i can boot into the recovery mode but idk how to repair. Do i have to remove wine? that would really be upsetting...

Does anybody have a solution PLEASE!!!

-mike

---

### Post by laurielegit on 2009-02-20
Did you do anything else apart from fiddle with wine? also, were you working in the ~/.wine directory or a higher level? As an immediate course of action, I would recommend booting a live cd, and backing your critical files up, or if you have an external hard drive, copying your home partition/directory over. Most things can be reversed, but all to often critical files are lost. So BACK UP!

---

### Post by mikedmor on 2009-02-20
well i was messing with the fonts in the actually ubuntu directory. i was looking at a tutorial about how to fix the font when using steam in wine (trying to completely convert over from windows) and it said to copy all the fonts over from a windows partition over to my font folder in ubuntu and something about symlink or something to make wine look in that folder for the fonts (it didnt ask about over righting but i was logged in as root) and then once i tried opening something it said at the bottom loading but just closed. i figured well maybe i just need to restart my pc and then i just got the loading circle that you get before the login screen shows up and it seems to just stop them (not freeze. i can still move the mouse around)

---

### Post by mikedmor on 2009-02-20
well without much help i found out a way to get some more information. i stopped the GDM as you said. but this time used startx and it logged me in, mouse not working though, but if i click ALT+F1 here is the output:

(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 20 19:27:19 2009
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


Thats all it says... maybe a step closer... Any help?

---

### Post by spiderbatdad on 2009-02-20
from recovery console try finding a backup of your xorg.conf file:
```
cd /etc/X11
ls -al
```look for xorg.conf<some date> or other extension. To see the  file: ```
cat filename
```If this looks like your original xorg.conf file, move it to replace the faulty file:
```
mv xorg.conf<backup> xorg.conf
```then reboot:
```
 reboot -h now 
```

---

### Post by mikedmor on 2009-02-20
i have tried that already. it doesnt work. idk whats up with it. actually i just use the command

sudo apt-get remove ubuntu-desktop

my question is how to i reinstall ubuntu-desktop from within the livecd? i just wanna reinstall ubuntu but that should keep all my other files right?

---

### Post by spiderbatdad on 2009-02-20
can you select recovery mode from grub rather than live cd. then just run apt-get ubuntu-desktop
otherwise you will need to mount your file system from the live cd, then cd into the mount point and run apt-get
I believe the live cd terminal will show you disks
```
sudo fdisk -l
```find ubuntu partition. most likely /dev/sda1 ext3 if it is the only partition. then```
sudo mount -t ext3 /dev/sda1 /mnt
cd /mnt
sudo apt-get install ubuntu-desktop
```I think it goes like that. Haven't done that for quite a while. There is plenty of info out there on mounting partitions from the live cd if that doesnt work, or you get no better advice. good luck.

---

### Post by mikedmor on 2009-02-20
sorry but that didnt work... well i can get into recovery mode. but with no Internet so sudo apt-get install ubuntu-desktop doesnt work. maybe is there a way to tell it to get the file from the cd?

---

### Post by spiderbatdad on 2009-02-20
there is probably an easier way, but for lack of that solution...how about mounting your filesystem...cd to the /mnt. then edit /etc/apt/sources.list...uncomment the first line which should be the cd. save the file. then try to install again.

---

### Post by mikedmor on 2009-02-20
OMG!! THIS IS SO FRUSTRAITING!!! WHAT COULD BE CAUSING THIS?!?!

So it didnt reinstall ubuntu-desktop

problem still is occurring though. what could this be?

how do i access the log to see what is happening and where it is stopping at?

---

### Post by spiderbatdad on 2009-02-20
what message did you get? perhaps you need to install gdm
logs are in /var/log for example: /var/log/dpkg.log  /var/log/daemon.log /var/log/kern.log

---

### Post by mikedmor on 2009-02-20
ok so here are the last few  ones i got from last restart. these are in kern.log
 
type=1503 audit(1235163936.705:5): operation="capable" name="sys_admin" pid=6170 profile="/usr/sbin/cupsd"
type=1503 audit(1235163936.705:6): operation="capable" name="sys_resource" pid=6170 profile="/usr/sbin/cupsd"
type=1503 audit(1235163936.705:7): operation="capable" name="sys_rawio" pid=6170 profile="/usr/sbin/cupsd"
ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - E3, should be DE [20080609]

---

### Post by spiderbatdad on 2009-02-20
maybe there is a boot option you need to try like acpi=off
see here for how to temporarily try an option and add it permanently:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I might be able to tell you more if you post dmesg, but please use a pastebin as it is a long file:
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)
just paste it there then after pasted copy the link back here.

---

### Post by mikedmor on 2009-02-20
i give up... idk whats wrong or why this happend when all i was working with was fonts and wine. it really sucks... i guess its just time for a fresh install... ugh... thanks for trying...

---

