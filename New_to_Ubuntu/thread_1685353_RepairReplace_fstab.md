---
title: "Repair/Replace fstab?"
date: 2011-02-10
forum: New to Ubuntu
---

### Post by MonthOLDpickle on 2011-02-10
Friend of mine was trying to optimize my machine how can I repair or replace my fstab?

---

### Post by cariboo on 2011-02-10
If he created a backup, like he should have, you can use the backup in place of what you have now.

---

### Post by Old *ix Geek on 2011-02-10
> **MonthOLDpickle said:**
> Friend of mine was trying to optimize my machineBefore you give someone root access to your system, you need to be sure they know what they're doing--and making backups before editing system files is #1 on that list.
> how can I repair or replace my fstab?I don't know. What's wrong with it? What isn't it doing now that you want it to do?

---

### Post by oldfred on 2011-02-10
Post your fstab. It may only need minor changes.

Anytime you manually edit fstab, always run this before rebooting as it will tell you if it is ok or not as it trys to remount it.

sudo mount -a

---

### Post by MonthOLDpickle on 2011-02-10
This is whats in it:

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
UUID=c4c98da1-fe1e-441a-99ab-9278cf984922 /               ext4    discard, defaults-ro 0       1
# swap was on /dev/sda5 during installation
UUID=715c2bbd-b347-4ab9-9f4e-8a2f909953b5 none            swap    sw              0       0
```

Now I know I only have one SSD HD with a main partition and a partition for swap. I think w/e he did has caused no issues but I would like it to be untouched.

---

### Post by oldfred on 2011-02-11
This is mine.

```
# / was on /dev/sda5 during installation
UUID=f2e3d649-d0cf-4ac8-b617-b7842dcbc011 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=305abe8d-52fd-4ef1-be0a-9dedc417a1be none            swap    sw              0       0

```

You can confirm UUIDs with this:

sudo blkid

I do not know fstab well enoght to know what these settings are.
discard, defaults-ro

man fstab
man mount

---

