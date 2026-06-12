---
title: "Disk installation"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by thgthg on 2009-06-15
Hi all!

I want to add a new disk to my PC, as a separate data drive that I can put in another PC in a future upgrade. Running Ubuntu 8.04. Besides backup and mech installation, what do I have to do?

---

### Post by bhadotia on 2009-06-15
> **thgthg said:**
> Hi all!

I want to add a new disk to my PC, as a separate data drive that I can put in another PC in a future upgrade. Running Ubuntu 8.04. Besides backup and mech installation, what do I have to do?

Nothing. Ubuntu should automatically detect the new hardware (HDD). You can format the disk using Gparted and set a permanent mount mount for your newly newly created partitions in the /etc/fstab. Do not forget to mount them on empty directories (or create some according to your need).

Use the following command to install Gparted:

```
sudo apt-get install gparted
```
After installation it can be found under System>Administration>Partition Editor menu.

[Here]("http://ubuntuforums.org/showthread.php?t=283131") is an excellent tutorial by Bodhi on fstab.

---

