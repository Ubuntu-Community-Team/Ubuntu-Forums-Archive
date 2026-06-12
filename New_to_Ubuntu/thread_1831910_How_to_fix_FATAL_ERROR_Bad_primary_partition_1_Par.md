---
title: "How to fix FATAL ERROR: Bad primary partition 1: Partition ends in the final partial"
date: 2011-08-24
forum: New to Ubuntu
---

### Post by maemi3916 on 2011-08-24
FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder

i am using ubuntu 10.04, when i checked the partition using table using **cfdisk** command, that error displays. By the way, it is newly formatted. What did i do wrong? How can i fix it? thnx!

---

### Post by fdrake on 2011-08-24
> **maemi3916 said:**
> FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylinder

i am using ubuntu 10.04, when i checked the partition using table using **cfdisk** command, that error displays. By the way, it is newly formatted. What did i do wrong? How can i fix it? thnx!

use a live cd and boot into the desktop

```
fdisk -l  #will show you your partitions and disks
fsck /dev/<your disk> # check and fix errors if you enconter different error msgs try: fsck -y /dev/<your disk>
```

if you encounter issues post here the error mgs and the result of your fdisk -l

---

### Post by coffeecat on 2011-08-24
+1 to the output of fdisk, but please post the output of:

```
sudo fdisk -lu
```

And not...

```
sudo fdisk -l
```

Rationale: fdisk -l gives output in cylinders rounded to the nearest cylinder and is not precise enough for your situation. fdisk -lu will give it in sectors which is what we need to see particularly in view of the "Partition ends in the final partial cylinder" message.

(Note: this is so in the 10.04 version that the OP is using, but it has changed in 11.10 with reporting in sectors as the default.)

---

### Post by srs5694 on 2011-08-24
Please post the "sudo fdisk -lu" output that coffeecat suggests for a full diagnosis. My suspicion is that there's no real problem; you're just using an old utility that's reporting as a "FATAL ERROR" (in scary all-caps, no less) something that's neither fatal nor an error. Specifically, 20+ years ago hard disks were designed so that three numbers were used to identify sectors on a disk: a cylinder, a head, and a sector ("CHS addressing"). This method mutated to the point where it became a convenient fiction and then an inconvenient fiction and is now a worse-than-useless legacy of years gone by. Modern disks and disk utilities rely on logical block addressing (LBA) rather than CHS addressing. In LBA, just one (bigger) number is used to identify disk addresses. One issue is that most disks have a number of sectors that's not an even multiple of the number of cylinders, as measured in the obsolete CHS scheme. Many modern partitioning tools are willing to place partitions so that they use up to the very last sector on the disk, which means that the partition ends in the "partial cylinder" at the end of the disk, as measured in CHS terms. This isn't an error for modern tools, but very old OSes and utilities (like DOS from the 1980s or possibly the 1990s) might flake out on such a disk. Such an old OS or utilty can't handle disks over about 8 GB, though, so if your disk is bigger than that, compatibility with such an old OS isn't an issue anyhow.

So, to wrap up this explanation, my *suspicion* at this point is that your version of cfdisk is enforcing partition rules that are almost old enough to make disco balls look cutting-edge. If I'm right, you should either upgrade cfdisk or just plain not use it. The cfdisk program is part of the util-linux package, but if you've been keeping up with updates for your version of Ubuntu, you might need to manually uninstall it and install it from a source tarball or in some other unofficial way to get an update. I'm not sure when (or even if) cfdisk stopped enforcing these old CHS partitioning rules, so I don't know what version of util-linux you should seek out.

---

