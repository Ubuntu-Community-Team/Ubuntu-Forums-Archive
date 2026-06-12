---
title: "External DVD burner"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by lover_of_sc on 2009-12-26
Hi guys,

I bought a LaCie portable DVD+-RW USB burner, how do I get it to work??

Fstab info:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=778cee2f-3dbf-48e3-ba00-4f00be8f6212 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=acdcbf32-4d35-4029-ac64-1e9065f22200 none            swap    sw              0       0


I have created a folder under media called DVDROM already, but I got stuck there....:-) Pls help someone.

---

### Post by blackened on 2009-12-26
Are you running in text-only mode? If you are running gnome, then you should be able to see the new drive in the "Places" menu. From there you should be able to click on it (assuming there is media in the drive) and it should mount itself.

If none of this applies, then you should first check if the drive is being recognized with
```
lsusb
```

---

### Post by lover_of_sc on 2009-12-26
Hmmm, sometimes the simplest solution is the best one, it worked fine after reboot. Sorry and thank you for your help anyway.

---

### Post by blackened on 2009-12-27
> **lover_of_sc said:**
> Hmmm, sometimes the simplest solution is the best one...
Very true, glad you got it working at any rate.

---

### Post by blackened on 2009-12-27
Double post, sorry.

---

