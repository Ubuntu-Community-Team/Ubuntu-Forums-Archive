---
title: "Can i boot directly into a VDI image?"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by LastWho on 2010-06-26
hi,

i have a 6.5 GB VDI image of a linux distro on my HDD, and i'd like now (that it is up to date, and rightly configured) to dual boot it with 7?


is it possible to do so?
thanks in advance

---

### Post by xtremesupremacy3 on 2010-06-26
If I understand correctly, you want to install this Linux Distro side-by-side with your Windows 7 install, so you can select which you want to run at startup?

Because what you mention that you have...a VDI image, indicates to me that it is a pre-configured image file for VirtualBox, now I'm no expert on VirtualBox but presume it's pretty much the same as VMWare images which has configured the harddrive space, etc etc. This would indicate to me that it's more like having a ready to run OS instead of an install file.

If all the above make sense to you then it would be my advice to get hold of an ISO file instead. Unless it's RHEL or SuSe or Mandriva One, it should be free. 

If instead you want to use it WHILE inside Windows 7, then all you need is VirtualBox

---

### Post by Irony on 2010-06-26
You don't dual boot a .vdi (virtual disc image). You mount them within an operating system with virtualbox. Thus in Windows 7 you would install virtualbox and then mount the virtual disc image within windows - a youtube search will show you how this works.

---

### Post by Old_Grey_Wolf on 2010-06-26
Is this what you want to do? Link to covert a VM image to an ISO...[http://www.turnkeylinux.org/blog/convert-vm-iso](http://www.turnkeylinux.org/blog/convert-vm-iso) and this one for VDI [http://www.turnkeylinux.org/blog/convert-vdi-vmdk](http://www.turnkeylinux.org/blog/convert-vdi-vmdk)

---

### Post by LastWho on 2010-06-26
> **Old_Gray_Wolf said:**
> Is this what you want to do? Link to covert a VM image to an ISO...[http://www.turnkeylinux.org/blog/convert-vm-iso](http://www.turnkeylinux.org/blog/convert-vm-iso) and this one for VDI [http://www.turnkeylinux.org/blog/convert-vdi-vmdk](http://www.turnkeylinux.org/blog/convert-vdi-vmdk)
This is exactly what i want, thank you so much Old Gray Wolf!

(of course i ve been using virtualbox to open it within 7, then i made my mind to dual boot it)

thanks again

---

### Post by Old_Grey_Wolf on 2010-06-26
If you need further help, there is a sub-forum within the Ubuntu forums for Virtualization at [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308). At the Virtualization sub-forum, you may get help from people that use virtualization on a regular bases, and use other hypervisors besides VirutalBox; like, KVM, ESX, Xen, etc. :)

---

