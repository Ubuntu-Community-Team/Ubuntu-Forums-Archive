---
title: "DOS and Ubuntu"
date: 2011-05-06
forum: New to Ubuntu
---

### Post by machdohvah on 2011-05-06
Is it possible to boot DOS 6.20 in a separate partition with Ubuntu in a neighbouring partition creating a menu choice for DOS and Ubuntu on boot?

---

### Post by Mr Stoozer on 2011-05-06
You mean does GRUB recognise DOS 6.20?

[http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows)

---

### Post by Paqman on 2011-05-06
Sure. You can also run a DOS environment on your desktop with [DOSBox](apt:dosbox)

---

### Post by machdohvah on 2011-05-06
> **Paqman said:**
> Sure. You can also run a DOS environment on your desktop with [DOSBox]("apt:dosbox")

Thank you. I think your solution is best for if I have to hide partitions just so that I can boot DOS, the dosbox would be safer.

---

### Post by srs5694 on 2011-05-06
There's no need to "hide" partitions just to boot DOS. DOS ignores Linux partitions, and Linux ignores partition type codes (which are manipulated to "hide" partitions). Hiding partitions *might* be desirable if you want to triple-boot Linux, DOS, and Windows; in that case, Windows will see the DOS partition, which you might not want. DOS won't see NTFS partitions, but it might see some FAT partitions.

IIRC, DOS does require the boot/active flag to be set, so you should be sure to set it on that partition. Contrary to popular belief, recent versions of Windows do *not* require the boot/active flag to be set, so there's no need to mess with them in the boot loader configuration.

All that said, running DOS in DOSBox (or VirtualBox or whatever) is likely to be more convenient than dual-booting it; however, this really depends on why you want to run DOS in the first place.

---

