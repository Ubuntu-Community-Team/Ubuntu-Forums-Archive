---
title: "install windows on natty"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by Spritegeezer on 2011-08-14
Most folks seem to want to add Linux to their Windows machine.  I'd like to add Windows to my Linux machine.  I'm sure this must have been discussed somewhere but search as I may I cannot find it. Is there a way to do it with no heavy lifting required?:)

---

### Post by n@ughty on 2011-08-14
do you mean, add windows OS right
maybe you can try virtual machine application
called VirtualBox OSE
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by elgordodude on 2011-08-14
I did it once and it worked okay, but all things being equal it's better  to install windows first and then linux. Mostly because windows is kind  of a bully and likes to take your machine over.

Anyway, first resize your drive using a live cd (isn't this already a  little redundant). Size doesn't really matter as long as it's big enough  but I highly suggest making it significantly different from your linux  space so you don't somehow confuse the two in the next step.

Second, reboot and insert your win cd, boot from it, select install win and install to unpartitioned space.

Note, this was with xp Linux has given me no reason to go to 7...

---

### Post by raja.genupula on 2011-08-14
windows boot loader will override the grub boot loader, you'll have problems , so get it over from this . boot from live cd /usb and then go to this link  

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by waynefoutz on 2011-08-14
You are most likely going to need to partition the disk manually, since the Windows installer tends to want to use the entire disk.


Use this guide after you install Windows, to reinstall Grub, the bootloader,  since Windows will remove it. 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Your easiest way is to just use Virtualbox and use it in a virtual machine, but your not going to get full performance out of Windows that way. Unless you plan on doing Windows gaming, I'd go with the virtual machine option.

---

