---
title: "Kernel panic caused by 'JBD2' on externel USB drive."
date: 2011-08-06
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2011-08-06
Hi! I've been having a kernel panic that I believe is caused by one of my external USB hard drives. The panic seems to occur randomly while the drive is connected. It doesn't happen as soon as it is connected, nor does it happen only while reading or writing files from the disk. Before the panic, I always see the following as the last line in syslog:

JBD2: I/O error detected when updating journal superblock for sdc1-8

I know that JBD2 has to do with filesystem operations, and that by Seagate FreeAgent external drive is the disk 'sdc.' Other than that, I have no idea why it would cause a kernel panic. Anyone have any ideas?

Thanks in advance!

---

### Post by pi.boy.travis on 2011-08-08
Bump?

---

### Post by pi.boy.travis on 2011-08-12
Double bump?

---

### Post by elgordodude on 2011-08-12
It sounds like the drive may be failing, if you navigate to System > Administration > Disk Utility are there any giant red flags under SMART Data or Check Filesystem? Also, how is the drive formatted?

---

### Post by Johnb0y on 2011-08-12
> **pi.boy.travis said:**
> Hi! I've been having a kernel panic that I believe is caused by one of my external USB hard drives. The panic seems to occur randomly while the drive is connected. It doesn't happen as soon as it is connected, nor does it happen only while reading or writing files from the disk. Before the panic, I always see the following as the last line in syslog:

JBD2: I/O error detected when updating journal superblock for sdc1-8

I know that JBD2 has to do with filesystem operations, and that by Seagate FreeAgent external drive is the disk 'sdc.' Other than that, I have no idea why it would cause a kernel panic. Anyone have any ideas?

Thanks in advance!

tried running updates to try and resolve this? also have you tried updating the driver for the drive?:confused:

---

### Post by pi.boy.travis on 2011-08-13
I think the drive may be failing. There drive has an unusually high number of spinups, and after further experimentation it would seem that it causes the kernel panic when a spinup fails, at least that's what the nasty clicking sounds coming from the drive would lead me to believe. I can avoid the panic by unplugging the drive when I don't need it, but it might be time to look for a replacement.

Thanks for the responses!

---

