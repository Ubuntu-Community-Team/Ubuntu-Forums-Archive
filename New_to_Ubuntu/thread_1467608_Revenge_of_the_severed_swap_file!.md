---
title: "Revenge of the severed swap file!"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Nesaskewatch on 2010-04-30
Good evening.  I recently made a few big changes to my partitions and ended up disabling the swap file.  I am fairly certain that I need to edit mt fstab and point the direction to the new swap partition.  I am unclear as to how to modify my fstab.  The swap is no longer enabled automatically when I boot into sda7.  (Main Linux install)  Booting into sda5 automatically turns on the swap just fine.  (sda5 is for the Maverick Alpha 1 when released)

Here is the result of > gksudo gedit /etc/fstab


```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=7fe67364-cd07-4ad6-a2a6-8546968ffcbd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=edb7393a-e1aa-4440-9187-7e1c7e5a17c7 none            swap    sw              0       0 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```
The new swap is at /dev/sda6.  I wondered if anyone would be so good as to show me how to safely edit my fstab?  I don't expect to be making any more drastic changes to my partitions! ;)

I have also attached a shot of my patitions.

Cheers!

.

---

### Post by ranch hand on 2010-04-30
If you run;
```

sudo blkid

```
it will give you the uuid for all your partitions.

Just change the uuid in your fstab file to the correct uuid for your new swap partition.

---

### Post by Nesaskewatch on 2010-05-01
Thanks El Rancho!  Worked a treat.  

Cheers!

---

### Post by ranch hand on 2010-05-01
You ca nhae fun with the fstab file.  You can change things and how they work.

It is a good idea to leave the original in there (just comment it out) so you ca nfix it if you really screw up.

When you move partitions or copy/paste OS' from drive to drive you have to go in and fix where the / and /home partitions are so that grub can find / and / can find /home.  Pretty straight forward.

The blkid command is really neat.  Some folks like a copy of the output (commented out) in their custom menu file in grub so that it is there when you are editing it.

---

