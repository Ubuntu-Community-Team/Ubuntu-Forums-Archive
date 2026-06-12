---
title: "Trouble watching video from my samba server"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by sneaks on 2007-05-21
When I try to watch videos stored on my server, the video starts off playing but then a few seconds into it the video cuts out but the audio is still playing, but the weird thing is that this only happens in Ubuntu, when I into Vista I can watch the videos fine. Its just in Ubuntu the video cut out. when listening to music from my server I have no problems with either Vista or Ubuntu its just the video. I can't figure out what is wrong, any help would greatly be appreciated.

---

### Post by Mike'sHardLinux on 2007-05-21
Hi.

How are you mounting your Samba shares? Are they mounted in fstab? Are you using Places --> Connect to Server?

---

### Post by sneaks on 2007-05-21
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=60793cb0-a30e-48d2-8932-39774466fcf9 /               ext3    
defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=8c3db54e-616f-4406-880d-f95c097c9c0d none            swap    
sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I am connecting through places/connect to...., I am looking in my fstab file and I do not see my samba shares. My fstab file is posted above.

---

