---
title: "[HELP] Installing/Removing Ubuntu."
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Letterbomb05 on 2009-09-03
Hi,

I've currently been running Ubuntu inside Windows XP, however I'd now like to reinstall it under a dedicated hard drive Partition, however I've come across a few problems.

1. I've uninstalled Ubuntu through windows, however on startup I still get the option to boot in Ubuntu. If I try and select this option, I get told that there is some file missing from windows and that it wont work, it then restarts my computer. Windows works fine. How can I remove this option from the boot menu?

2. I've tried to install Ubuntu using unetbootin, I can load up the ISO file and run it fine, however when I begin the install I'm told that I cannot create a new partition on my hard drive. I'm assuming that this means I would have to have Ubuntu rather than Windows, which really isn't what I would like (Don't get me wrong, I love Linux, it's just that windows has some key applications I need to use which don't work in WINE, I'm also still noob at Linux).

Thanks in advance for any help given, much appreciated!
~Aaron.

---

### Post by bodhi.zazen on 2009-09-03
To remove wubi :

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

To install Ubuntu :

[GraphicalInstall - Community Ubuntu Documentation]("https://help.ubuntu.com/community/GraphicalInstall") 

I assume you are booting from the usb device ? You are able to boot Ubutnu with unetbootin and you get to the ubuntu desktop ?

If so, open gparted (the graphical partitioner) and let us llok at your partitions.

Do not forget to back up your data and defragment your windows partition.

---

### Post by Letterbomb05 on 2009-09-04
Hi, sorry for my slow reply.

I've uninstalled Ubuntu as it's stated in the documentation, however I still have this broken Ubuntu option in my boot menu.

I've also booted Ubuntu installation and used Gparted as you instructed. Here are my partitions:

/dev/sda1 - ntfs - 53.56 GiB
/dev/sda2 - extended - 2.33 GiB
    /dev/sda5 - linux-swap-2.33 GiB (listed under the above).

---

### Post by bodhi.zazen on 2009-09-04
> **Letterbomb05 said:**
> Hi, sorry for my slow reply.

I've uninstalled Ubuntu as it's stated in the documentation, however I still have this broken Ubuntu option in my boot menu.

I've also booted Ubuntu installation and used Gparted as you instructed. Here are my partitions:

/dev/sda1 - ntfs - 53.56 GiB
/dev/sda2 - extended - 2.33 GiB
    /dev/sda5 - linux-swap-2.33 GiB (listed under the above).

The link I gave you give step - by - step directions to fix your boot menu +

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

HOWEVER, with those partitions, that is NOT wubi.

You will need to boot your windows recovery CD and repair your install:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx)

You can then delete the Ubuntu partitions and resize your windows partition with any partition editor. gparted is on the live CD if you wish.

[http://gparted.sourceforge.net/larry/generalities/gparted.htm](http://gparted.sourceforge.net/larry/generalities/gparted.htm)

If you get stuck or do not understand something please be more specific as to what assistance you need and we can try to give you more detailed instructions.

---

### Post by Letterbomb05 on 2009-09-04
Hi,

Thanks very much once again for your reply. I have uninstalled wubi and fixed the boot menu, missed something first time round when reading on how to fix. 

Those partitions were what I got from GParted on the Ubuntu Live CD, after I had uninstalled Wubi (Not sure if this makes any difference or I should still use the windows repair CD). Anyhow, the problem I have now is that GParted wont let me modify any of my existing partitions, or create a new one. I simply get an error when I try to unmount my device (the mount point is /cdrom, I'm not sure if this is normal as I've never dealt with partitions before). 

I seem to be getting this error when attempting to unmount my device:
```

unmount: /cdrom: device is busy.

```

---

### Post by wojox on 2009-09-04
If you get the message device is busy, the umount request has failed because either a process
has a file open on the device or you have a shell open with a directory on the device as a current
directory. Stop the processes or change to a directory outside the device you are trying to unmount
for the umount request to succeed.


An alternative for unmounting a busy device is the -l option. With umount -l (a lazy unmount),
the unmount happens as soon as the device is no longer busy.

---

### Post by Letterbomb05 on 2009-09-04
> **wojox said:**
> If you get the message device is busy, the umount request has failed because either a process
has a file open on the device or you have a shell open with a directory on the device as a current
directory. Stop the processes or change to a directory outside the device you are trying to unmount
for the umount request to succeed.


An alternative for unmounting a busy device is the -l option. With umount -l (a lazy unmount),
the unmount happens as soon as the device is no longer busy.

Thanks for your reply, I have recieved similar feedback on IRC, however I have made sure that I don't have a terminal open, I don't have any directorys open or anything. I simply boot the Live CD and open GParted. 

- 11.30PM - Be back tomorrow.

---

