---
title: "dualbooting with second harddrive?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by mamamia88 on 2010-01-01
thinking of getting a second harddrive to put windows 7 on.  is it as simple as it looks just unhook old harddrive and install windows on new one and chose that harddrive as boot device if you want to run windows?  or will there be problems with windows not being on the main harddrive?

---

### Post by underquark on 2010-01-01
I presume you mean "master" or "slave".  Irrelevant with SATA disks and shouldn't matter  with IDE (PATA) disks if connected properly.  Just select which one to boot from at startup by pressing F12 or whatever key accesses the boot option in your BIOS.  Assuming you have a relatively recent motherboard and BIOS, of course.

---

### Post by mamamia88 on 2010-01-01
sweet thanks i was worried windows would just assume it's on hd1 instead of hd2

---

### Post by oldfred on 2010-01-01
Grub will make windows think it is the first drive with map  or mapdevice command depending on which version of grub.

If you choose to just switch boot order in BIOS it will be the first drive. I prefer grub.

I do like having an operating system on each hard drive and that hard drive set to boot from that operating system. i.e. windows on the second drive and bootable from that drive. And grub/ubuntu on the first drive and then one of the grub menu items will be windows. Depending on which version of grub it is relatively easy to add windows to grub's boot menu.

Make sure you install windows to a primary partition on the second drive.

---

