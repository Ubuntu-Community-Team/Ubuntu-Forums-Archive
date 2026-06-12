---
title: "Why is my USB flash thumb drive all of a sudden read-only filesystem?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-02-23
I went away for the weekend and now I got back and my thumb drive that I could copy and save files to is now a read only filesystem and I try doing the chmod 777 and chown 777 to media/disk and it still doesnt work and I try to go in the properties and change permissions that way and it doesnt work it just comes up as read-only filesystem HELP :)?

---

### Post by Temposs on 2009-02-23
Did you take your thumb drive with you and use it on a Windows machine when you were away?

Sometimes if you use a thumb drive on a Windows machine and don't properly eject it, it will cause problems when you try putting it onto an Ubuntu system.

---

### Post by ericeclifford on 2009-02-23
It worked last weekend but now it doesnt work on the harddrive 8.04 version of ubuntu or my 8.04 custom live cd version It just saids read-only filesystem. Is the usb screwed or what or do I need to repartition that Im not familiar with partitioning external devices. :( bump

---

### Post by ericeclifford on 2009-02-23
No I never used it on windows within the time period of today and friday and it worked fine on friday. It may have been used before on a windows comp but like 3 months ago. and I do take it out of the usb port without unmounting it could it be corrupted?

---

### Post by theozzlives on 2009-02-23
```
sudo chown *yourusername* /media/disk
```
```
sudo chmod 777 /media/disk -R
```

---

### Post by ericeclifford on 2009-02-23
eric@eric:~$ sudo chown eric media/disk
[sudo] password for eric: 
chown: cannot access `media/disk': No such file or directory
eric@eric:~$ cd //
eric@eric://$ ls
bin   cdrom  etc   initrd      lib         media  opt   root  srv  tmp  var
boot  dev    home  initrd.img  lost+found  mnt    proc  sbin  sys  usr  vmlinuz
eric@eric://$ sudo chown eric media/disk
chown: changing ownership of `media/disk': Read-only file system
eric@eric://$ sudo chmod 777 /media/disk -R
chmod: changing permissions of `/media/disk': Read-only file system
chmod: changing permissions of `/media/disk/Steps of Slax customization.odt~': Read-only file system
chmod: changing permissions of `/media/disk/ubuntu-8.04.2-desktop-i386.iso': Read-only file system
chmod: changing permissions of `/media/disk/sources.list': Read-only file system
chmod: changing permissions of `/media/disk/.Trash-ubuntu': Read-only file system
chmod: changing permissions of `/media/disk/libflashplayer.so': Read-only file system
chmod: changing permissions of `/media/disk/Linux Stuff': Read-only file system
chmod: changing permissions of `/media/disk/Linux Stuff/Steps of Slax customization.odt': Read-only file system
chmod: changing permissions of `/media/disk/Linux Stuff/Linux installed Programs List.ods': Read-only file system
chmod: changing permissions of `/media/disk/Linux Stuff/Linux Programs Checklist.ods': Read-only file system
chmod: changing permissions of `/media/disk/Linux Stuff/Linux Programs Checklist.xls': Read-only file system

This is what I got from this command and it doesnt work.

---

### Post by ericeclifford on 2009-02-23
eric@eric://$ ls -l /media
total 60
lrwxrwxrwx 1 root root     6 2009-02-18 12:03 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2009-02-18 12:03 cdrom0
drwxr-xr-x 2 root root  4096 2009-02-18 12:03 cdrom1
drwx------ 4 eric root 20480 1969-12-31 19:00 disk
lrwxrwxrwx 1 root root     4 2009-02-23 10:32 usb -> usb0
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb0
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb1
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb2
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb3
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb4
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb5
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb6
drwxr-xr-x 2 root root  4096 2009-02-23 10:32 usb7
eric@eric://$ sudo fdisk -l
[sudo] password for eric: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00008152

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 4127 MB, 4127194624 bytes
255 heads, 63 sectors/track, 501 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8dc31acd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         502     4030432    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(500, 254, 63) logical=(501, 196, 14)
eric@eric://$

---

### Post by lswb on 2009-02-23
Try 

sudo mount -o remount -o rw /media/disk

One way for a permanent solution is to put an entry for the USB drive in your /etc/fstab. You can search the forum or google for details, there are some options and variations on how you may want to do that.

---

### Post by ericeclifford on 2009-02-23
well it does temporary work I believe. but when I replaced 1 file it auto went to read-only so I did the command again and it allow me to write to it again weird and ty will be looking up etc/fstab

---

### Post by smokey_58au on 2009-03-09
> **theozzlives said:**
> ```
sudo chown *yourusername* /media/disk
``````
sudo chmod 777 /media/disk -R
```

I had the exact same problem as ericeclifford but your solution above worked for me.  I transfer between windows machines and my ubuntu laptop all the time (I'm the Linux rebel at work) and learnt early on that you MUST choose to safely eject the hardware however this didn't seem to matter in this instance - it still changed all files/folders to read only but thanks to the lines above it's all sorted now.  Thanks.

Edit:  I spoke too soon.  It changed the permissions of the files and folders but the usb disk itself was mounted as read only and still unusable.  After much googling (this seems to be quite a common occurence between Linux and Windows) I got around it by copying the files to my hard drive and using GParted to reformat the usb disk to Fat32.  Copied them back and now works fine.

---

### Post by voice5sur5 on 2009-06-27
i had the same problem today and i just unmounted the flashdisk from gparted then removed and puted back and it just worked for me. try and feedback :_)

---

### Post by rportnoy on 2010-08-26
There is problem with your flashdisk
try sudo dosfsck -a -v /dev/sdb1 
Your flashdisk can be written again..

---

