---
title: "Can't mount drives anymore"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Joe Soap on 2009-02-14
I'm running Hardy on my laptop, dual boot with XP.

I have two NTFS partitions (/media/DATA and /media/OS) that used to automount on boot.  

Yesterday I ran update manager and updated the suggested packages.  On rebooting my two NTFS drives did not mount.  When I try to mount them manually, I get this message:

```
You are not privileged to mount the volume 'DATA'.
```

This is what my fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=b8b464f3-283b-4a92-bd08-872b639beb8f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=3d1bec82-c569-4841-8bca-5a530af988bb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sda2
/dev/sda2       /media/OS       ntfs    defaults        0       1
# /dev/sda3
/dev/sda3       /media/DATA     ntfs    defaults        0       1
```

Any suggestions to solve this will be most welcome.

---

### Post by hyper_ch on 2009-02-14
do you have ntfs-3g installed?

---

### Post by Joe Soap on 2009-02-14
Yes, it's installed.

---

### Post by hyper_ch on 2009-02-14
my fstab entry looks like this:

```

/dev/sdd1 /media/WinXP ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

---

### Post by Joe Soap on 2009-02-14
Thanks, I'll change mine and see what happens.

---

### Post by Joe Soap on 2009-02-14
Nope, didn't work ...

Any other suggestions?

---

### Post by hyper_ch on 2009-02-14
of course you need to alter it to your needs... I guess you've done that, right?

Was there an unclean shutdown? Try to boot into windows to have them properly mounted again and then reboot into linux.

---

### Post by Joe Soap on 2009-02-14
Good point.  My previous windows shutdown was not clean...

---

### Post by hyper_ch on 2009-02-14
so it works now?

---

### Post by Joe Soap on 2009-02-14
You called it hyper_ch.  I booted windows, did a clean shutdown, booted Ubuntu and, bingo, my drives are back.

Thanks for your help, much appreciated.

---

