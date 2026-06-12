---
title: "MP3 player doesn't mount."
date: 2009-02-19
forum: New to Ubuntu
---

### Post by breem42 on 2009-02-19
Running Hardy Heron Kubuntu, fully updated.  I have a Panasonic SV-MP20V that does not seem to mount.  I looked at this discussion: [this discussion]("http://ubuntuforums.org/showthread.php?t=564001&highlight=panasonic+mp3") but I have the problem described by idr, i.e. when I type

```
sudo rmmod ehci_hcd
password: <password>
```
I get

```
'ERROR: Module ehci_hcd does not exist in /proc/modules'.
```

Typing

```
sudo modprobe ehci_hcd
```

allows the rmmod command to work without the error message (not that I know why, but it does).  But it does not fix the mount problem. 

Here is my lsusb:
```
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 04da:3701 Panasonic (Matsushita) 
Bus 002 Device 002: ID 04b4:0001 Cypress Semiconductor Corp. Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

which suggests that the player can be seen.

When I type the following:

```
dmesg > dmesg.log
grep usb dmesg.log
```

I get

```
[ 3611.610061] usb 2-2: new full speed USB device using uhci_hcd and address 3
[ 3611.798842] usb 2-2: configuration #1 chosen from 1 choice
[ 3612.538273] usbcore: registered new interface driver libusual
[ 3612.598127] usbcore: registered new interface driver usb-storage
[ 3612.598714] usb-storage: device found at 3
[ 3612.598718] usb-storage: waiting for device to settle before scanning
[ 3617.596100] usb-storage: device scan complete
[ 4686.888460] usb 2-2: reset full speed USB device using uhci_hcd and address 3
[ 4894.638743] usb 2-2: USB disconnect, address 3
[ 7550.791371] usb 2-2: new full speed USB device using uhci_hcd and address 4
[ 7550.979612] usb 2-2: configuration #1 chosen from 1 choice
[ 7551.015471] usb-storage: device found at 4
[ 7551.015478] usb-storage: waiting for device to settle before scanning
[ 7556.014283] usb-storage: device scan complete
[ 7900.015047] usb 2-2: reset full speed USB device using uhci_hcd and address 4
[ 8106.318595] usb 2-2: USB disconnect, address 4
[ 8135.248684] usb 1-2: new full speed USB device using uhci_hcd and address 2
[ 8135.436737] usb 1-2: configuration #1 chosen from 1 choice
[ 8135.468865] usb-storage: device found at 2
[ 8135.468873] usb-storage: waiting for device to settle before scanning
[ 8140.467393] usb-storage: device scan complete
[ 8206.668875] usb 1-2: USB disconnect, address 2
[11521.688306] usb 2-2: new full speed USB device using uhci_hcd and address 5
[11521.876811] usb 2-2: configuration #1 chosen from 1 choice
[11521.905143] usb-storage: device found at 5
[11521.905151] usb-storage: waiting for device to settle before scanning
[11526.903442] usb-storage: device scan complete
```
I suspect the above is the result of my monkeying about plugging and unplugging the player.

This is a device that has mounted successfully under Win2k, WinXP, and even an old install of Linux (can't remember which -- may have been an old computer).  I could just keep booting WinXP to get at the recordings I make on this device, but would rather not.

Thanks in advance to anyone who can help.

---

### Post by yoyoned on 2009-02-19
This will happen if you unplug the device without unmounting it first.

---

### Post by Temposs on 2009-02-19
What yoyoned means is that you probably mounted it into Windows and removed without unmounting it. This can cause problems when trying to mount in Ubuntu, such as you're having.

---

### Post by tarps87 on 2009-02-19
It appears the module has already been removed.
It is possible windows has not release its lock on the usb device, if you can try connecting it to a windows machine and then click 'safely remove device' from the taskbar. If this does not work try:
```

sudo mkdir /media/mp3device

```
```

sudo mount /dev/sdb1 /media/mp3device
or
sudo mount -t vfat /dev/sdb1 /media/mp3device

```
Replace **sdb1** with you device, if you are not sure what to replace it with post the output of
```

sudo fdisk -l

```

If this fails can you post the out put from the mount command, if it works
```

nautilus /media/mp3device

```
should open you device

---

### Post by breem42 on 2009-02-21
> **tarps87 said:**
> It appears the module has already been removed.
It is possible windows has not release its lock on the usb device, if you can try connecting it to a windows machine and then click 'safely remove device' from the taskbar. If this does not work try:
```

sudo mkdir /media/mp3device

```
```

sudo mount /dev/sdb1 /media/mp3device
or
sudo mount -t vfat /dev/sdb1 /media/mp3device

```
Replace **sdb1** with you device, if you are not sure what to replace it with post the output of
```

sudo fdisk -l

```

If this fails can you post the out put from the mount command, if it works
```

nautilus /media/mp3device

```
should open you device

Thank you to all who replied.

I followed your directions (mounting under XP then unmounting.  It did not automount under Ubuntu, but the "sudo mount" command did work although I don't get an icon on my kubuntu desktop.  Now I'm going to look elsewhere on this site to see how I can get it to automount.

I'll post here with my results.

---

### Post by breem42 on 2009-02-22
Well that was frustrating.  There seem to be many people with various devices that have my problem, but none with a solution (unless there is something I've missed).  Yes you can make a usb drive mount automatically on boot (or is that login), but that is not going to be my situation usually.

Just to clarify: My system automounts properly for a 2GB Transcend pen drive, for a Sansa e250, and for a Sansa View 8GB (i.e. the icon appears on my desktop and the drive appears under "/media" when I plug it in).  Just not my Panasonic SV-MP20V.

I guess I can make a little script to mount it, and another to unmount, but that requires sudo/gksudo and hence typing in a password.  But I suspect that perhaps there a table somewhere that I can edit to add this to the usb drives that the system recognizes, something like fstab.

Any hints?

---

### Post by tarps87 on 2009-02-23
Could you post the output of this command please
```
gnome-mount -vbd /dev/sdb1
```
This will pipe the output to a file if it makes it any easier
```
gnome-mount -vbd /dev/sdb1 > output.txt
```

---

### Post by 3rdalbum on 2009-02-23
Hardy has known issues with mounting some MP3 players, like the one sitting next to me :-)  If you have an Intrepid live CD, try it with that. If it mounts, then a good solution would be to upgrade to Intrepid.

---

### Post by tarps87 on 2009-02-23
> **3rdalbum said:**
> Hardy has known issues with mounting some MP3 players, like the one sitting next to me :-)  If you have an Intrepid live CD, try it with that. If it mounts, then a good solution would be to upgrade to Intrepid.

I missed that, I thought the op was using Intrepid. It is possible I know what the cause is and how to fix it but the output from ```
gnome-mount -vbd /dev/sdb1
```would confirm it.
Upgrading to Intrepid may not be a bad idea, most of the bugs in KDE4 have been worked out now, trying the live CD before installing/upgrading would be a good idea though.

---

### Post by breem42 on 2009-02-25
Sorry it's taken so long to reply, and thanks for all the responses.

My device shows up as "sdc", so the mount command that works for me is:

```
sudo mount -t vfat /dev/sdc /media/mp3device
```

When I have device plugged in and not mounted, and I type:

```
gnome-mount -vbd /dev/sdc
```

I get a little window popping up with the message:

> Unable to mount media.
There is probably no media in the drive.

In the command window line the response is

```
gnome-mount 0.8
** Message: Drive /dev/sdc does not contain media.
```

which, of course makes no sense, since the mount command works fine.  Is "gnome-mount" a wrapper for "mount"?

BTW, when I use the "sudo mount ..." command, the files all have ownership of "root/root" (which I guess makes sense, since the command is executes as "root".  But this means I cannot write to the drive.

Thanks again for your help.

---

### Post by breem42 on 2009-03-07
Bump

---

### Post by tarps87 on 2009-03-09
Sorry for the late response, I missed the notification
Could you post the output of```
sudo fdisk -l
```
This what not the same error as I was expecting to see.

Edit: late response not last :)

---

### Post by breem42 on 2009-03-13
Sorry it has taken so long to reply.  I stopped checking this thread.  (I'm subscribing to this thread so I get your responses quicker.)

Here are the results of 'sudo fdisk -l' when the device is not mounted:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0b4b0b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       38245   153605497+  83  Linux
/dev/sda3           38246       38913     5365710    5  Extended
/dev/sda5           38246       38913     5365678+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x301b9edf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4740    38074018+  83  Linux
/dev/sdb2            4741        4870     1044225   82  Linux swap / Solaris
Note: sector size is 1024 (not 512)

Disk /dev/sdd: 132 MB, 132645888 bytes
5 heads, 51 sectors/track, 507 cylinders
Units = cylinders of 255 * 1024 = 261120 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table
```
I guess the drive is called 'sdd' at this point.  When I mount the device using ' sudo mount...' the results of 'sudo fdisk -l' are the same.  That makes sense.  Why would a tiny little flash drive like that have a partition table on it.  Although ... I am old enough to remember when a 132 MB hard drives was a big deal...

Thanks for your attention all this time.

Tony

---

### Post by nelskurian on 2009-03-13
just reformat the mp3 player by connecting it to a windows machinea 'fat'.May be its the problem formating it with ntfs type before.The ntfs disc may not be read if it wont mount with the optin ntfs-3g and the ntfs-3g properly mounted.

   when you connecting it ,you got the error 'no media'.That mean it has a file system that the system cant identified or its a erreneous device.But you confirmed your device working in windows.
  
So format the device with fat type then again connect to linux abd recheck.

---

### Post by tarps87 on 2009-03-13
It looks like a reformat may be in order:
Disk /dev/sdd doesn't contain a valid partition table
Ubuntu should be able to mount ntfs formatted usd drives, although fat tends to be the standard format for usb drives.
How ever this being a mp3 player this may not be possible.
To sum up, the drives partition table has be corrupted/can not be read. The best solution would be to reformat it. **Please check with the manufacturer if this is possible as if the mp3 software is on the disc it will be lost**

This may not be the only solution, it is the only one I can think of

---

### Post by breem42 on 2009-03-14
> **tarps87 said:**
> It looks like a reformat may be in order:
Disk /dev/sdd doesn't contain a valid partition table
Ubuntu should be able to mount ntfs formatted usd drives, although fat tends to be the standard format for usb drives.
How ever this being a mp3 player this may not be possible.
To sum up, the drives partition table has be corrupted/can not be read. The best solution would be to reformat it. **Please check with the manufacturer if this is possible as if the mp3 software is on the disc it will be lost**

This may not be the only solution, it is the only one I can think of

Just to be clear again, (as far as I know) the drive we are talking about is already fat or vfat formatted, not NTFS.  More is a bit.

---

### Post by tarps87 on 2009-03-16
> **breem42 said:**
> Just to be clear again, (as far as I know) the drive we are talking about is already fat or vfat formatted, not NTFS.  More is a bit.

If it is vfat Ubuntu should have no problems reading it, this seems to be a corrupted partition table. Are there any recovery CD's for the mp3 player. Unfortunately I don't know of any easy way to rebuild the partition table, hopefully someone else here will do.

---

### Post by breem42 on 2009-03-17
> **tarps87 said:**
> If it is vfat Ubuntu should have no problems reading it, this seems to be a corrupted partition table. Are there any recovery CD's for the mp3 player. Unfortunately I don't know of any easy way to rebuild the partition table, hopefully someone else here will do.

OK, so I formated it with Windows XP, as a FAT drive (which is what it said it was before I formatted it).  The player works just as well as it did before, probably because it's firmware is kept in ROMs.  It even automatically created the directory that it expects music to be found in.  This is not exactly an advanced device.  It is 5 years old, and was not cutting edge when I bought it.

And the result is -- no change in terms of mounting (or lack there of).
Still mounts manually from the command line.

I'm about ready to throw in the towel and accept what I can get.

---

### Post by tarps87 on 2009-03-17
It usually is stored in ROM but there is always the odd one. I'm afraid I can't think of any thing else to suggest. I could be to do with the HAL configuration files but to work this out really I would need to try it with the device. Someone with the same mp3 player may be off more help now.
Sorry I couldn't find a solution

---

### Post by breem42 on 2009-03-17
Just some additional info.  Nothing earth shaking.

I had not yet tried this drive under Gnome.  So I logged out, selected Gnome from KDM, and logged back in.  The icon does not appear on the Gnome desktop either.  But my flash drive does.

---

