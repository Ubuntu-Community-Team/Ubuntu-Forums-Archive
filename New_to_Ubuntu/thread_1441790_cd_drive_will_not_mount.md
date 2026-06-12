---
title: "cd drive will not mount"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Vanessa R on 2010-03-29
I am unable to mount my cd drive. When I try to click on the icon in 'computer' I get the error 'Unable to mount selected volume' 
and when expanded, 'mount: special device /dev/scd0 does not exist'

The contents of my fstab is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=8cc78c2e-4f09-4a5f-ba83-5c5dc7db007a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=59234b1c-dfb0-426a-aecd-684ac730b4e3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```The CD drive used to be recognised fine but the motherboard battery failed and after I dismantled my laptop and replaced that it hasn't been able to mount. I had a similar problem with the external hard drive being unable to mount after this but I was able to force mount it. The same has not worked with the CD drive.

I tried changing the options in fstab to 'auto' or 'defaults' but that just resulted in the drive not being visible at all so I changed it back again.

I also tried 
```
vanessa@vlr23:~$ mount /dev/scd0
mount: special device /dev/scd0 does not exist
```I am using Gutsy which I know is very out of date - the reason I want the CD drive to mount is so I can use a live CD to update my OS. (I tried to download updates and upgrade but for some reason, even when Gutsy was still supported I always just received error messages)

---

### Post by Jakob Lundberg on 2010-03-29
What do you get by doing a ```
sudo lshw -class disk
```?

---

### Post by Vanessa R on 2010-03-29
I get:

```
vanessa@vlr23:~$ sudo lshw -class disk
[sudo] password for vanessa:
  *-disk                  
       description: SCSI Disk
       product: WDC WD800UE-22HC
       vendor: ATA
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 09.0
       serial: WD-WXE206084084
       size: 74GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5

```

---

### Post by Jakob Lundberg on 2010-03-29
That is not good. The drive should be listed there. Broken?

You could browse through dmesg to see if you can find anything related to the drive
```
dmesg|grep 'ATAPI'
or
dmesg | less
```

---

### Post by Vanessa R on 2010-03-29
It works now! I didn't change anything but I tapped on the case where the drive slots in. I now think that it must somehow not have engaged properly when I put it back together after changing the motherboard battery.

I'm sorry for taking up our time with what turned out to be a hardware problem. Thank you so much for replying so swiftly.

---

