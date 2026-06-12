---
title: "Hard disk doesn't show up in nautilus &quot;places&quot; menu"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by ba0bab on 2010-04-30
Hi,

I updated to 10.04 at beta 2 - however, in 9.10 my unmounted extra-hard disks would show up in nautilus 'places' menu for easy, non-root mounting.

In 10.04, they don't. I can mount them just fine in terminal, but that's not very convenient. I don't really wanna add them to /etc/fstab, because I don't need them mounted per default.

the odd thing is, *sometime* they show up under places, and everything works great, but most of the time, they don't show up.

I use Nautilus Elementary 2.30.1 .

My fstab looks like this:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=8170b69a-aec5-4293-a22e-f0af1496c3ad /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=b1e08c65-dd0f-4e41-bbe9-3113169eab4c /home           ext4    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=06D64D9368830ECD /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=a9f7814a-2a21-4eac-b163-9c1a3cfc3637 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#UUID=06D64D9368830ECD /media/sda2 ntfs-3g users 0 0
#UUID=02DDBD981296A7F1 /media/sdd2 ntfs-3g users 0 0
#UUID=4C53DAB56701E292 /media/sde1 ntfs-3g users 0 0
```

---

### Post by madjr on 2010-04-30
try another file manager and see if it's nautilus's problem

---

### Post by ba0bab on 2010-05-03
It is apparently a problem in Nautilus only, I installed pcman and all the HDDs show up. Also, in Nautilus' "browse" folder, the HDDs show up, so it must be something with Elementary.

---

### Post by hplgonzo on 2010-06-28
add it to "/etc/fstab" with "noauto" option ...

---

### Post by chenxing on 2011-03-12
> **hplgonzo said:**
> add it to "/etc/fstab" with "noauto" option ...

Then we will lose the auto-mount functionality... Is there a solution to this problem now?

---

### Post by ba0bab on 2011-03-13
Well since upgrading to 10.10 I haven't had any problems, thanks for the replies though!

---

