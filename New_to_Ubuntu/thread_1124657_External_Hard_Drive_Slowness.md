---
title: "External Hard Drive Slowness"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by Shintrick on 2009-04-13
I'm new to linux, and very happy to leave Windows in the dust (on one of my machines anyway). I couldn't find an answer to this in the mountain of posts on external HDDs.

I have a 650GB ext. HD connected to my older desktop running Xubuntu intrepid. I want to be able to access its files from this computer and my Vista-running laptop over my wireless connection. I used samba to set up the share and that seems OK - the laptop can find it alright. The problem is this: whenever I boot up Xubuntu on my desktop, I need to click on the HD's desktop icon and wait two or three minutes while it loads(?). Only when it stops loading and allows me to access folders/files does it show up as available on my Windows machine. 

Is this a mounting problem? Is there a way to automatically load (if this is the right term) its files so I can access them from my laptop without having to manually open the drive in File System?

Any help would be appreciated

---

### Post by ajgreeny on 2009-04-13
You can add a line to the /etc/fstab file to mount the usb drive at boot time, but there may be error messages if you boot without the usb drive attached or powered on.  You will need to find the device name or UUID of the partition and the mount point of the disk when it's mounted on the machine, and then use taht as the mount point in the fstab line.  You will also need to know the format type if the disk (fat32, ntfs, ext3?) and vary the line accordingly.

Automount ext3 partition. Add line to /etc/fstab:-
/dev/hdb1 /media/mountpoint ext3 defaults 0 1

Automount fat32 partition. Add line to /etc/fstab:-
/dev/hda1 /media/mountpoint vfat iocharset=utf8,umask=000 0 0

Automount ntfs partition. Add line to /etc/fstab:-
/dev/hda1 /media/mountpoint ntfs nls=utf8,umask=0222 0 0

---

### Post by Shintrick on 2009-04-14
Thx for your reply. I tried to do as you instructed (with newb skills) and this is what my fstab file looks like now.


> chris@Mathilda:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aaef9b88-6d53-468d-ae16-89568b00833e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=316c0355-225d-4dc8-8dc1-4a4b87a66284 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdb1 /media/my book ext3 defaults 0 1      



The last line obviously being the line I added. Problem is I restarted and the same problem occurs. I have to physically click on the icon and wait for it to 'load contents'. I'm assuming that I've not done this correctly. 

Further help would be much appreciated.

---

### Post by Paqman on 2009-04-14
So the mount point is /media/my book? You might want to change that line so it reads:
```

/media/my\ book

```

---

### Post by ajgreeny on 2009-04-14
Yes, any pathway with a space, as in "my book", will need the back slash before the space or the pathway in quotation marks.  This is a linux requirement, unlike windows. For this reason it's worth not having spaces in file or folder names; use - or _ instead.

---

### Post by Shintrick on 2009-04-18
I tried both the backslash and quotations (seperately), but neither seemed to work. I realize having a space in the name is not ideal. I don't know of any way to change the name - whenever I try to rename the folder it says that the device is busy. Obviously, when I unplug it, the folder disappears. 

It seems that it is going to take a minute or two for my system to scan the contents of the drive whenever I boot my computer up. This I can live with, but I was just hoping I could make it happen automatically instead of having to open the folder manually. 

Any other ideas would be much appreciated.

---

### Post by jbrown96 on 2009-04-18
I read over your posts a few times, and the one question that I couldn't answer is: What file system are you using? Are you sure that it's ext3? If you're not sure, you can check by right clicking on the hard drive and selecting properties; it will be listed at the bottom near the pie chart. 

That device name is also not correct. Linux used to use the hda, hdb, hdc, etc. to name hard disks, but it uses sda, sdb, sdc. now. Make sure to fix the /media/My\ Book issue and also change the device to /dev/sdb1.

---

### Post by Shintrick on 2009-04-18
Thanks for your help. Seems to be working much better now

---

