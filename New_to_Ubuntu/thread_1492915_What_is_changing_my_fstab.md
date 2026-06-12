---
title: "What is changing my fstab?"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by Greblok on 2010-05-25
Hi all.

I have a problem I cant seem to figure out.

Some times, if my system halts or needs to be forced to restart, something is changing my fstab file.

It should look like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
/dev/sda1                                  /            ext4  errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=ed7ca39e-745c-4a64-8286-5c4832113faf  none         swap  sw                   0  0  

/dev/sdb1                                  /media/sdb1  ntfs  defaults             0  0  
/dev/sdd1                                  /media/sdd1  ntfs  defaults             0  0  
/dev/sdc1                                  /media/sdc1  ntfs  defaults             0  0  

but for some reason, sometimes the sda1 and sdb1 are switched, and Ubuntu wont manage to mount the sdb1 at startup.

When this happen, my fstab looks like this:
proc                                       /proc        proc   nodev,noexec,nosuid  0  0  
/dev/sdb1                                  /            ext4   errors=remount-ro    0  1  
# swap was on /dev/sda5 during installation
UUID=ed7ca39e-745c-4a64-8286-5c4832113faf  none         swap   sw                   0  0  

/dev/sda1                                  /media/sdb1  ntfs   defaults             0  0  
/dev/sdd1                                  /media/sdd1  ntfs   defaults             0  0  
/dev/sdc1                                  /media/sdc1  ntfs   defaults             0  0  

It then looks for a ext4 partition on sdb1, which obviously is incorrect.

Why on earth does this happen? Every time, I have to edit the fstab first and then mount the drive manually. Could it be gParted or pysdm or something entirely different?

---

### Post by renkinjutsu on 2010-05-25
Don't use device names. They're bad if you wish for your settings to stay permanent. It'll be fine if you never turn off your computer though. Use UUID instead of the device names (/dev/blah)

do something like
```
sudo blkid /dev/sda5
``` to find out the UUID for /dev/sda5
then in fstab, your would replace /dev/sda5 (or whatever) with UUID=longstringoflettersandnumbers

---

### Post by Groodles on 2010-05-25
Your FSTAB isn't changing.  What is changing is how your machine is assigning HDDs to /dev/sdx locations.

If you used UUIDs for HDD identification INSTEAD of /dev/sdx then it will always mount the right drive in the right place.

Oh[ renkinjutsu]("http://ubuntuforums.org/member.php?u=668873") beat me to it.  What he said!

---

### Post by BoneKracker on 2010-05-25
If you want to be able to consistently refer to storage devices by device name (instead of UUID, filesystem label, or mount point) you can write udev rules for those devices so they are assigned device names consistently.  However, if you don't already know how to write udev rules, learning to do so is harder than simply using UUIDs or filesystem labels).

---

### Post by Greblok on 2010-05-25
Thank you renkinjutsu (osu!?) and Groodles, I'll make the change.

But, renkinjutsu, you mention 

[QUOTE=renkinjutsu]Your FSTAB isn't changing.  What is changing is how your machine is  assigning HDDs to /dev/sdx locations.[/QUOTE]

Why does it change? If the explanation is[COLOR=#000000] comprehensive I dont mind a link to an explanation if you happen to have one. :)
(No need to stress this, just if you happen to have one) 

[/COLOR]@BoneKracker:
 I know nothing about writing udev rules but now I have something new to  learn. Thanks for the tip. :)
[]("http://ubuntuforums.org/member.php?u=668873")

---

### Post by BoneKracker on 2010-05-25
> **Greblok said:**
> I know nothing about writing udev rules but now I have something new to  learn. Thanks for the tip. :)

Dynamic management of hardware is an area of turbulence for the Linux community as its use as a desktop OS expands.  Over the past few years, we've seen kernel-managed devfs (vs userspace-managed) come and go (and now, come back again), we've seen HAL come and go, we've seen a lot of changes in how udev is used, and we've seen handling of devices change in desktop environments.

The need to actually write or edit udev rules is now limited to special cases (unusual hardware or unusual requirements), but it is an interesting area to study.  If nothing else, it will give you a good understanding of the sysfs and how udev itself works.  It will also give some capability to customize your system.  At best, it might enable you to get some hardware working that hasn't been.  Kernel-managed devfs seems to be coming back, but there will still be a need for some userspace management, and it looks like udev will continue to fill that role (for the time being at least).

Here's a good link:
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

