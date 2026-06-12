---
title: "2Problems that afect my business majorly"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Gamesandluv on 2010-04-24
1. I can access my cd drive i have looked at tons of other threads no help at all.
Here are some things i hope can help.
 ```
Seems to not even be recognized.
root@owner-desktop:~# sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: HDS722580VLAT20
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: V32O
       serial: VNR21EC2T0WM4M
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=2fe52fe4
  *-disk
       description: SCSI Disk
       product: SanDisk Cruzer
       vendor: SanDisk
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 8.02
       serial: u
       size: 3863MiB (4051MB)
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
          size: 3863MiB (4051MB)
          capabilities: partitioned partitioned:dos

```Heres my fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=1bc97115-f8c3-4f49-96c2-7aab8f3e2365 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=65170866-d799-4684-9255-4fcfdae530a7 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```Here is the error 
```
Unable to mount cdrom0
mount: special device /dev/scd1 does not exist

```And i already check the cd rom enable in user privileges.

2. Okay so i am a web developer and my screen resolution should be 1680x1050
but its 800x600
 here is my xandr 
```
root@owner-desktop:~# xrandr
Screen 0: minimum 320 x 240, current 800 x 600, maximum 960 x 600
default connected 800x600+0+0 0mm x 0mm
   960x600        60.0  
   960x540        60.0  
   800x600        60.0*    56.0  
   768x576        60.0  
   720x576        60.0  
   856x480        60.0  
   800x480        60.0  
   720x480        61.0  
   640x480        60.0  
   400x300        60.0  
   320x240        61.0
```i tried using cvt and it gave me this
```
root@owner-desktop:~# cvt 1960 1050
# 1960x1050 59.94 Hz (CVT) hsync: 65.27 kHz; pclk: 170.75 MHz
Modeline "1960x1050_60.00"  170.75  1960 2080 2288 2616  1050 1053 1063 1089 -hsync +vsync

```and there is no xorg or xfix anymore since im in 9.10 so idk wada do please help, this really hinders my business.

---

### Post by LowSky on 2010-04-24
1. Is there a disk in the drive? I know its dumb but I got to ask. Without a disk it can't mount.

2. What graphics chip do you have. Have you loaded the hardware drivers for it?
System> Admin> hardware drivers.
If there is nothing there to load, it means your graphics card is opensource and doesn't need proprietary drivers

---

### Post by -humanaut- on 2010-04-24
Could you reboot and open a console and get the dmesg for me ?

---

### Post by undecim on 2010-04-24
1: I think that it should be /dev/scd0, not scd1


2: You're not logging into the desktop as root are you?! That's a very dangerous thing to do.

check for your video card driver in System -> Administration -> Hardware drivers.

---

### Post by LowSky on 2010-04-24
see this wiki for adding new resolutions if they are not already listed.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Gamesandluv on 2010-04-24
Yes i do have a cd in the drive, i have nothing at all listed in the hardware drivers.
I am logged in as root because i had to change a user password
I also tried adding a resolution and no luck it wouldnt even show on the xandr list.

---

### Post by Gamesandluv on 2010-04-24
dmesg shows alot should i paste it all here?
 heres after i make the new modeline-- using cvt and adding it
[IMG]http://i41.tinypic.com/b3plpi.png[/IMG]
 but i cannot set the resolution.

This is really messing up my business.

---

### Post by Gamesandluv on 2010-04-24
Sorry about he bump but this is a really messing up my business bad.

---

### Post by undecim on 2010-04-24
what video card do you have? Run this in a terminal:
```
lspci | grep VGA
```

---

