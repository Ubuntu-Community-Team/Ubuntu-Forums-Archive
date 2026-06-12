---
title: "FSTAB NFS issue"
date: 2007-06-08
forum: Networking &amp; Wireless
---

### Post by p-stone on 2007-06-08
Hello
I'm having an issue mounting an nfs share. I can mount the share no problem with a mount command but it's a pain to do that every time I boot. I've modified my fstab as best I can but it doesn't work.
This is the mount command I run that works
sudo mount 192.168.0.100:/media/WDEXTHD /storage
and this is my fstab, which doesn't

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=e04f8f7c-764a-436e-ae93-5d2db69fac8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=9fc43309-8580-449f-981b-05f2afbe76e6 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

192.168.0.100:/media/WDEXTHD  /storage    nfs          rw            0    0

Any assistance, tips, hints pointers, or best of all, solutions would be greatly appreciated
Thanks in advance

---

### Post by Mr. C. on 2007-06-08
Remove the 0 0 at the end of the fstab entry for your nfs mount.

You can mount using either:
```

sudo mount /storage
sudo mount -t nfs
```

MrC

---

### Post by p-stone on 2007-06-08
No Dice :(
I took the two 0's out, rebooted, still nothing showing up in /storage, ran that mount command and there it was. Any other ideas?

---

### Post by Mr. C. on 2007-06-08
Oh, I'm sorry.  I misunderstood.  The 0's were merely superfluous.

Add the "auto" keyword:

```

192.168.0.100:/media/WDEXTHD /storage nfs rw,auto
```

---

### Post by p-stone on 2007-06-08
You are my hero. That fixed it, thank you so much, this has been bugging me for a long time

---

