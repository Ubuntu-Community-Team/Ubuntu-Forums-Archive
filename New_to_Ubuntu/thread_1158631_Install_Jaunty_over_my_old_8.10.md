---
title: "Install Jaunty over my old 8.10"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by jmedoro on 2009-05-13
so...just put Jaunty on a disc, want to install it over my 8.10 (replacing the 8.10 with Jaunty) b/c i messed it all up with this compiz business. how do i do it? I'm currently dual booting with XP and keeping it that way.

I tried installing from the disc, i didnt really see any option to replace the 8.10. During partitioning, i tried deleting the partition with 8.10 and installing Jaunty on the new free space, but it wouldnt let me.

---

### Post by 0per4t0r on 2009-05-13
You could try using update manager in 8.10 to upgrade to the newest version. Worked for me, although I had to do a little tweaking.

---

### Post by presence1960 on 2009-05-13
> **jmedoro said:**
> so...just put Jaunty on a disc, want to install it over my 8.10 (replacing the 8.10 with Jaunty) b/c i messed it all up with this compiz business. how do i do it? I'm currently dual booting with XP and keeping it that way.

I tried installing from the disc, i didnt really see any option to replace the 8.10. During partitioning, i tried deleting the partition with 8.10 and installing Jaunty on the new free space, but it wouldnt let me.

If you want to do a clean install just choose "manual" when you get to the partitioner part of the install. Highlight the partition that has 8.10 on it and click Edit. Choose Filesystem type (ext 3 or ext4) and mountpoint (/). 

If you have a separate home partition and want to go ext4 then have your /home backed up prior and at the partitioner part of the install (manual) highlight the /home partition, click Edit & choose ext 4 filesystem, tick the format box and choose the mountpoint /home. After install transfer your data back to home partition. This will keep your separate home as ext 4.

If you have a separate home partition and want to keep ext 3 I would still back it up. Then at the partitioner part of the install (manual) highlight the home partition & click Edit, choose ext 3 as filesystem, **leave the format box UNTICKED** and choose /home as mountpoint. This will leave your data intact and set up the separate home partition.

P.S. Whatever filesystem you choose for / (ext 3 or ext 4) I would choose for /home.

---

### Post by jmedoro on 2009-05-14
> **presence1960 said:**
> If you want to do a clean install just choose "manual" when you get to the partitioner part of the install. Highlight the partition that has 8.10 on it and click Edit. Choose Filesystem type (ext 3 or ext4) and mountpoint (/). 

If you have a separate home partition and want to go ext4 then have your /home backed up prior and at the partitioner part of the install (manual) highlight the /home partition, click Edit & choose ext 4 filesystem, tick the format box and choose the mountpoint /home. After install transfer your data back to home partition. This will keep your separate home as ext 4.

If you have a separate home partition and want to keep ext 3 I would still back it up. Then at the partitioner part of the install (manual) highlight the home partition & click Edit, choose ext 3 as filesystem, **leave the format box UNTICKED** and choose /home as mountpoint. This will leave your data intact and set up the separate home partition.

P.S. Whatever filesystem you choose for / (ext 3 or ext 4) I would choose for /home.

SWEET, that worked. thanks. now i know what 'mount point: /" means.

one more issue: now instead of just choosing between XP and the Ubuntu's (i guess regular and the recovery mode), i have more choices:

Kernel 9.04   2.6.28.11 generic
Kernel 9.04   2.6.28.11 generic (recovery)
Kernel 9.04   2.6.27.7 generic
Kernel 9.04   2.6.27.7 generic (recovery)

should i be getting rid of one of these?

---

### Post by Niniel on 2009-05-14
The last two entries are the kernel from 8.10... I would keep it for a while at least until you're sure everything works with the new one. Then you can get rid of it (through Synaptic or the clean-up application).

---

### Post by presence1960 on 2009-05-14
I would recommend always keeping the previous kernel around in case the newest one has a problem. When you get more than two you can safely remove them through Synaptic. After removal you can edit your menu.lst file to reflect the kernels you just uninstalled. Just delete the kernels 2 entries (generic & recovery mode). Save the file and close. Next time you boot you will see the change in your GRUB selection menu.

BTW to edit your menu.lst file open a terminal and run : ```
gksu gedit /boot/grub/menu.lst
``` That is a lowercase L.

Enjoy Jaunty !

---

