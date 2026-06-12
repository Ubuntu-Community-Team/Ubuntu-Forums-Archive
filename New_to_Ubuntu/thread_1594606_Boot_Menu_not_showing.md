---
title: "Boot Menu not showing"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by perito on 2010-10-12
So I have Windows 7 and I installed Ubuntu just now (dual-boot) and did the partitioning. It installed successfully and restarted and went right to windows without showing the boot menu. I'm guessing my mistake was that "Where do you want to install the boot loader?" question, I answered in sda6 .. in the same place where ubuntu was being installed.

How to activate the GRUB boot loader .. its installed but its not activated im guessing.

Thanks

---

### Post by andrewthomas on 2010-10-12
You installed it to the partition instead of the MBR

Use the instructions here.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by drs305 on 2010-10-12
If you don't get it figured out please run *meierfra's* boot info script so we can see how Grub2 installed.
[_http://bootinfoscript.sourceforge.net/_]("http://bootinfoscript.sourceforge.net/")

Post the contents of RESULTS.txt within 'code' tags, which you generate by pressing the # icon in the post's menu.

---

