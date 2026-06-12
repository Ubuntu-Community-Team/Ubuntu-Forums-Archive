---
title: "mounting partitions"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by maryhigginsrice on 2011-07-24
Hi everyone.  I am running Ubuntu 11.04 with Mythtv.  When installing Ubuntu I made a partition called "TV SHOWS" an I would like to mount it on the desktop.  I have been reading articles, but cannot figure it out.   I have uploaded a screen shot of the partition.  Any assistance will be appreciated.  mary

---

### Post by bigpayne69 on 2011-07-24
Without knowing all the details, I can tell you that it should mount just fine. Are you running windows as well, or just Linux?

---

### Post by egalvan on 2011-07-24
if this were my system, I would re-name the drive to

TV_SHOWS

or 

TV-SHOWS

with no spaces.

yes, Linux can tolerate spaces in file names, but it doesn't really like them.

---

### Post by egalvan on 2011-07-24
BTW, did *you* mount it on **/usr/local** ?

or is this how your system mounted it?

this *should* be mounted on **/media**

(unless Myth has a good reason to mount elsewhere)

if you up-load a copy of your** fstab** file, it would help others figure this out.


BTW, any file mounted on **/media** automatically shows on the desk-top.

---

### Post by maryhigginsrice on 2011-07-25
I would to thank everyone for your help. When I installed Ubuntu I made that partition as a ext4 usr/local. I am using a 1TB harddrive so I figured I could do this without any error. When you install the OS there is no /media option for mounting a partition. I am uploading my fstab file. Thanks again for your help. mary

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e52ad8ce-f128-4516-ab15-58bbe9d7fa98 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=4d761109-c271-45cf-aebf-86971019ec61 /home           ext4    defaults        0       2
# /usr/local was on /dev/sda7 during installation
UUID=bd10d018-ee47-4d20-8d0a-3b954492fcab /usr/local      ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=baaa5f5b-44c4-41dc-89ad-b41446176104 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

