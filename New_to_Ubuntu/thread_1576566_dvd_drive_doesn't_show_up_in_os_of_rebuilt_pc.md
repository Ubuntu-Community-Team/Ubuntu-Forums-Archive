---
title: "dvd drive doesn't show up in os of rebuilt pc"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by nnjond on 2010-09-17
dvd drive doesn't show up in os of rebuilt pc

Hi,

My dvd drive opens and closes and shows up in the bios when i attach a hard drive that isn't working!!

Can you figure out what I should do?

Thanks

---

### Post by Clever_Username on 2010-09-17
Is there an entry in /etc/fstab?
Also, I'm a little confused by "when i attach a hard drive that isn't working". Can you clarify?

---

### Post by nnjond on 2010-09-17
Thanks for your interest. here is my fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f8b722d1-6632-4ab9-9717-c7ae9fad9112 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=81457453-a218-4739-b5cd-3f9143f7ad61 none            swap    sw              0       0

Whwn I tried booting up with another hard drive, this hard drive didn't power up, nor did it show up in the bios; but the dvd player did as 1st boot device.

---

### Post by cariboo on 2010-09-17
If the drives are both on the same cable, check the jumpers on the drives to make sure they are set properly. If the dvd drive is on the last connector of the cable, it should be set as the slave, the hard drive should be set to master. I personally have never had much luck with cable select, so I always set master and slave.

---

