---
title: "Need a boot menu"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by tekne on 2009-02-26
Hey...

As I explained in my last thread, I made the mistake of installing ubuntu 8.10 and only after I installed windows 7.
I corrected that mistake by reinstalling GRUB thanks to the help of a few members from the forum.
Now I have a new problem. Every time I turn on my pc I can only see Ubuntu. Isn't there a way of making a menu so I can choose between Windows or Linux? I still have Windows 7 installed but no way of choosing it. 

Thanks in advanced!

---

### Post by philinux on 2009-02-26
Need some info first. And yes its easy to edit the grub menu to add a wondows loader.

```
sudo fdisk -l
```

---

### Post by Metallion on 2009-02-26
In what way did you install grub? I suggest you install it again using suber grub disk. Usually that can find all the OSes for you. [www.supergrubdisk.org](www.supergrubdisk.org)

---

### Post by tekne on 2009-02-26
philinux: the information is the following

> Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5736    46074388+  83  Linux
/dev/sda2   *        5737        9355    29069617+   7  HPFS/NTFS
/dev/sda3            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Metallion: I installed it through basic command grub and the live Ubuntu PEN, through the console as explained in this forum somewhere but can't seem to find it. Is it really necessary to reinstall it or is there another way?

Thanks

---

### Post by tekne on 2009-02-26
Well... please don't leave me hanging.
I'm just insisting because it would be king of urgent to take care of this matter. Also, I tryed burning SUPERGRUPDISK.iso, burned it, booted it and nothing happened, just Ubuntu, as usual.

Thanks

---

### Post by caljohnsmith on 2009-02-26
How about opening your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
And add the following at the very end:
```
title Windows 7
root (hd0,1)
chainloader +1
```
Reboot, try it from your Grub menu, and let us know exactly what happens. We can work from there if necessary.

---

### Post by tekne on 2009-02-27
caljohnsmith everything worked fine. Thank you very much :) I can now choose between the two of them!

---

### Post by caljohnsmith on 2009-02-27
Great, glad to hear that worked OK; cheers and enjoy your dual-boot Ubuntu/Windows 7 setup. :)

---

