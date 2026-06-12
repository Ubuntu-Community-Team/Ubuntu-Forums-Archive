---
title: "HD Check"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by jnmjr on 2010-02-22
I would like to check my hard drive for errors and possible bad sectors, Is there an utility in Ubuntu that will do this?....something similar to chdisk in Windows, also if it would generate a report would be helpful. THX.

---

### Post by NightwishFan on 2010-02-22
Most filesystems do not support online checking. You can check unmounted ones using the Palimpsest tool or Gparted. You can also use the command line tools available. "e2fsck" is the command for ext2/3/4 filesystems.

As for disk health, you can look up SMART information in Palimpsest. This is built into Ubuntu Karmic and is called "Disk Utility"

Added info: Linux will automatically check disks if problems are detected. After so many mounts it checks them automatically anyway.

---

### Post by jnmjr on 2010-02-22
> **NightwishFan said:**
> Most filesystems do not support online checking. You can check unmounted ones using the Palimpsest tool or Gparted. You can also use the command line tools available. "e2fsck" is the command for ext2/3/4 filesystems.

As for disk health, you can look up SMART information in Palimpsest. This is built into Ubuntu Karmic and is called "Disk Utility"

Added info: Linux will automatically check disks if problems are detected. After so many mounts it checks them automatically anyway.


Than you,  will do.

---

