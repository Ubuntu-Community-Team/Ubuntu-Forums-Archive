---
title: "Grub boot menu question"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by sylvainrb on 2009-01-30
I was just wondering why there were three different choices at the grub boot menu for ubuntu and ubuntu (recovery). I notice the kernels have different version numbers but what is the difference?

Thanks!

---

### Post by taurus on 2009-01-30
For every kernel, you should have two entries, one for normal use and one for recovery mode in case you need to boot from it to fix your machine.  It's a good practice to use the latest kernel but keep the previous one just in case.  So if you have three kernels, it's safe to remove the oldest one from your machine in System -> Administration -> Synaptic Package Manager.

---

### Post by Simplemind169 on 2009-01-30
the choices are a kernel built in. the recovery mode is nice if you edit anything and corrupt data, very similar to windows system restore. Although nice they are not needed since usually it is easier to reinstall than to recover. If you wanted you can edit the menu.lst file in the boot/grub folder to remove those options.

---

### Post by drs305 on 2009-01-30
Kernels are updated to fix bugs or make other improvements. By default, grub adds each new kernel to the list so over time you will get more and more options. Most users only need the current entry and possibly one backup in case the new kernel doesn't work well on the user's system.

You can leave all the choices visible, remove the kernels from the menu and keep them on the system, or remove the older kernels completely.

I recommend StartUp-Manager, a gui-based grub menu editor. Here is the tutorial link:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

The app will let you tweak a variety of menu items. The tutorial also covers how to remove kernels you no longer wish to keep.

---

