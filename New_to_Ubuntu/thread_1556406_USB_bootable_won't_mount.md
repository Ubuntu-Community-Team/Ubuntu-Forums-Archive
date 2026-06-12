---
title: "USB bootable won't mount"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by Zenmij on 2010-08-19
I have a USB stick I used to boot and install 9.04 a way back. I'd like to use it for 10.04 put when I attempt to mount it says:

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

and Dmesg:

```
dmesg|tail
[ 4444.882450] UDF-fs: No VRS found
[ 4444.882461] UDF-fs: Rescanning with blocksize 2048
[ 4444.903790] UDF-fs: No VRS found
[ 4444.903799] UDF-fs: No partition found (1)
[ 4444.942406] ISOFS: Unable to identify CD-ROM format.
[ 4590.741103] UDF-fs: No anchor found
[ 4590.741112] UDF-fs: Rescanning with blocksize 2048
[ 4590.756480] UDF-fs: No anchor found
[ 4590.756488] UDF-fs: No partition found (1)
[ 4590.796845] ISOFS: Unable to identify CD-ROM format.
```

I tried Formatting with the Disk Creator Utility but no dice. Is it just corrupted and time to buy a new one?

Thanks.

---

### Post by ulsigem on 2011-06-25
I realize that this reply is about one year later than the original post and I hope you found an answer to this problem. I too was having this problem in a debian installation from a usb stick. I found this post from a google search and this post was in the top 5 results. I hope that the following helps anyone else with a similar problem.

I used Unetbootin to "burn" the iso image to the USB stick. Installation was successful and everything worked as expected. The only problem was that the USB stick I used for the installation wasn't mounting. 
*Unfortunately, I did not test any other USB stick to see if the problem was more universal or just the one stick. I use SD cards to transfer data between phones and cameras and my laptop.*
[FONT=monospace]
[/FONT]```
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```The problem seems to lie in the configuration file of fstab performed during installation. Apparently during the installation process the USB device is placed as a CDROM device and tries to mount the USB stick using a wrong filesystem.
You can use gedit, nano or vim or any other text editor to edit the fstab file.
I prefer using nano.
Be sure to use** [COLOR=DeepSkyBlue]sudo[/COLOR] **or use **[COLOR=DeepSkyBlue]gksudo gedit[/COLOR]** or else you might get a permission denied error when trying to apply changes. 
In a terminal:
```
sudo nano /etc/fstab
```Here is what my /etc/fstab file stated and as one can see at the bottom sdb1 is to be mounted using the udf filesystem giving us the error mentioned above:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e7c6dbc6-44af-31b9-8418-08b1a7a9817e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ffad6e97-f8dc-453c-3173-827e1d747982 none            swap    sw              0       0
[COLOR=Red]/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]

```The solution is simple either comment it out with a # in front of the line:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e7c6dbc6-44af-31b9-8418-08b1a7a9817e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ffad6e97-f8dc-453c-3173-827e1d747982 none            swap    sw              0       0
[COLOR=Red]#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0[/COLOR]

```or delete the entire line, BUT be careful not to delete any other line!
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=e7c6dbc6-44af-31b9-8418-08b1a7a9817e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ffad6e97-f8dc-453c-3173-827e1d747982 none            swap    sw              0

```After that small change the USB stick mounted and worked!!

---

