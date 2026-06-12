---
title: "Activating a Partition..."
date: 2010-06-19
forum: New to Ubuntu
---

### Post by aianta03 on 2010-06-19
I'm a very heavy Windows user, my life is based on windows :p but at the same time, I need a back up OS that I can depend a pon and know how to use in case of an emergency, I decided to try Ubuntu since it looked like a good, fast running, lightweight system. Anyways, I currently want to activate a partition on my Hard Drive. My Windows became  unstable a while back and my recovery disks have failed me. So I need to boot of the RECOVERY partion of the HDD. 

If this was windows I believe, that I would right click on the partition icon, select options, and under advanced select activate partition. 

But I have no idea what so ever how to do this in Ubuntu. Does any one know how to activate a partition in Ubuntu?

Any help is greatly appricitated.

---

### Post by Chame_Wizard on 2010-06-19
What the hell is an activated partition?:confused:

1.Download and create a Live CD/USB(10.04).
2.While in the Live CD/USB,it's always possible to install gparted via the package manager or ```
sudo aptiude install gparted
```
3.Application>System>gparted or ALT+F2>gparted,now you can resize the disk space necessary to create a partition.

:guitar

---

### Post by aianta03 on 2010-06-19
Activated partition, forces a specific partition to be booted without using any of the Fxx keys or the boot manager.

---

### Post by eriktheblu on 2010-06-19
I Windows recover partition I believe is typically invoked from the BIOS (or at least that's how it seems on my HP).

Are you wanting to back up your Ubuntu data in case of OS failure? If so, the easiest way is to create separate / and /home partitions at the time of installation. This way should you ever need to reinstall, you will not lose any files or settings.

---

