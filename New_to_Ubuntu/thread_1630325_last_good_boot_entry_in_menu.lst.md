---
title: "last good boot entry in menu.lst"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by sajnanazeer on 2010-11-25
Hi,

At what stage the boot configuration is saved as last good boot? What happens if kernel crashes after the good boot configuration has been saved?

---

### Post by wojox on 2010-11-25
If your new kernel crashes, use the previous working one from the Grub Menu on start up. Which version are you using?

---

### Post by sajnanazeer on 2010-11-25
Thanks for your response.

I am using Ubuntu 10.04LTS with grub as bootloader.

I am telling about the last good boot option which helps us to boot into  the last successfully booted kernel. I have read that "Once the machine  is booted successfully, an init script will take notice and copy the  existing resources away (out of package control, so it wont be  overwritten or removed). Several things are saved:
 
    * /boot/vmlinuz-KVER
    * /boot/Systemp.map-KVER
    * /boot/initrd.img-KVER
    * /lib/modules/KVER/* 
 
These are saved to a special location:
 
    * /boot/last-good-boot/{vmlinuz,System.map,initrd.img}
    * /lib/modules/last-good-boot/*
    * /boot/last-good-boot/version (the real uname -r of the saved  kernel for reference)
    * /lib/modules/last-good-boot/modules.dep (munged from original to  change module locations) "
 
I want to know at which stage of booting these are saved? When a boot is  considered as successful?

---

