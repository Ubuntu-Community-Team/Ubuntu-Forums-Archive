---
title: "How to Install XP in virtualbox from image file"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by eshant_engineer on 2009-10-01
I have image file of Windows XP and I want to install XP in virtual machine in Ubuntu then what I have to do to boot this bootable image inside virtual machine?

---

### Post by keplerspeed on 2009-10-01
What sort of image? is it .vdi, or .iso, or .vmdk?

For the vdi or vmdk, open virtual box and go to file>virtual media manager and mount the image there. Then make a new virtual machine using that image.

For the iso just make a new virtual machine and boot it from the iso.

---

### Post by scrooge_74 on 2009-10-01
Hi

First you create a virtual PC that is going to use XP.

Then you make the disk, make it as large as you need, remember XP takes a lot of space.

Then go to the cdrom options and point it to the iso image you have. Then go to the system options and tell it to boot from CD first

then start the virtual machine it will boot from CD like a real one.

After you get it installed, on the bar on top tell it to install the virtualbox addons so you get a better desktop management.

Post back if in doubt is pretty straight forward and in virtualbox.org they have good documentation easy to follow

---

### Post by eshant_engineer on 2009-10-01
^^^^^^

I had did that in the same way u mention. But I am getting an error

```
Failed to start the virtual machine Winodws XP.
Failed to start the virtual machine Winodws XP.
VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).
```

---

### Post by eshant_engineer on 2009-10-01
I am not able to solve this problem. It is saying to disable KVM kernel extention. How to do that? Please help..

Thanks all 4 replying

---

### Post by scrooge_74 on 2009-10-01
You most likely need to recompile the virtualbox part of the kernel.

[http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

Check the manual is easy to use and there is no need to run as root

---

