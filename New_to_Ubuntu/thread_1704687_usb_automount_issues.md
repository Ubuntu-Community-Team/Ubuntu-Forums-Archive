---
title: "usb automount issues"
date: 2011-03-11
forum: New to Ubuntu
---

### Post by adduds on 2011-03-11
laptop, hp, dv7 

only way i can get my usb stick to mount is through

sudo mount /dev/sdb1 /media/usb

ubuntu see's it in lsusb and sudo fdisk -l

but won't automount?

have checked alt+f2 gconf-editor --> apps--> nautilus --> preferences --> media_automount is checked

i did and it is but still won't work...

formatted to ext4 and fat32 neither worked...

drive works as soon as i plug it into my laptop(asus aspire) though; but not the hp whats going on here?

---

### Post by Hakunka-Matata on 2011-03-11
sounds strange, something in BIOS?

---

### Post by Cracklepop on 2011-03-11
Don't know how to fix the problem, but a workaround would be to give it an entry in /etc/fstab

---

### Post by adduds on 2011-03-11
yes i did consider an fstab entry with the UUID; just as its my gf's laptop and she uses it for school i presumed it would be better if i could get a solution to it?

what might you figure it could be in the bios?

thanks the for quick replies

---

### Post by adduds on 2011-03-12
friday night bored :P

lookin' to fix the g/fs lappy

---

### Post by wep940 on 2011-03-12
I'm not sure what it does since I've never used it, but I *think* there is a package called something like usbmount in Synaptic Package Manager.  You may want to search for it and see what it says.

---

### Post by adduds on 2011-03-12
> **wep940 said:**
> I'm not sure what it does since I've never used it, but I *think* there is a package called something like usbmount in Synaptic Package Manager.  You may want to search for it and see what it says.

thanks for that but it didn't work

i plug it in and it shows up in lsusb and sudo fdisk -l

---

### Post by PunkLV on 2011-03-12
```
dmesg | grep -i usb
```
Unfortunately, if this will not point to any errors, I do not know what else will.

By the way, does this happen to one particular flashpen or not?

---

### Post by wep940 on 2011-03-12
Though I haven't seen it mentioned for a while, some people had this problem with 10.04 and 10.10 - there were several threads in the forum.  Some dealt with fstab, while others dealt with udev and the mounting rules.  The idea that you can only mount it sudo suggests to me it may a udev rule problem.  I know the default for non-matching devices, is to set root as the owner.  I had this problem with every release due to some non-standard cameras I was using (bought new cameras now).
 
If the device shows in a lsusb, please post the output of lsusb back here with the device plugged in.  This may give us some information to look for possible problems and solutions.

---

