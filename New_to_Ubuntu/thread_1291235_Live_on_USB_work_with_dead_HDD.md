---
title: "Live on USB work with dead HDD?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by knottshawk on 2009-10-14
I have an old laptop which, I suspect, has a dying hard drive. In theory, if the HDD completely dies, couldn't I still run that laptop using a live distro on USB? That relies on bios settings and not the HDD right?

It seems like it would be like a mini-SSD.

Am I missing something?

---

### Post by Sarmacid on 2009-10-14
Yes, you could run either a live usb or a live CD distro without a hard drive.

---

### Post by ohzopants on 2009-10-14
I did that exact same thing for months a couple years ago, except I used a LiveCD rather than a LiveUSB.

It worked just fine, except for not being able to save stuff.  With a USB drive you could partition and still save stuff to one of the partitions.

---

### Post by gali98 on 2009-10-14
Yes that would work. As for being a mini-SSD not quite...
A flash drive has a lot less read/write cycles so you will probably want to get a hard drive for it.
You might have to change a bios option to get it to boot from the drive.
Kory

---

### Post by doas777 on 2009-10-14
depending on the state of the drive, you may wanna unplug it though. if it is partially operational, it may lag the rest of the system, as the hardware is trying to bring it online or deal with the gibberish it is spewing.

---

### Post by tea for one on 2009-10-14
It will work if you can boot from a USB device.

If your BIOS prevents you from booting directly from a USB device but you have a working CD drive, then I suggest that you have a look at this website:-

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

The instructions to boot Ubuntu via a CD are:-

[http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-904/](http://www.pendrivelinux.com/usb-boot-cd-for-ubuntu-904/)

---

### Post by knottshawk on 2009-10-14
Cool... with so much being saved "in the cloud" these days, who needs a hard drive? ;)

Just kidding... but this would be convenient. Does the USB startup app within Ubuntu work pretty well? Or should I look elsewhere?

I see [www.pendrivelinux.com](www.pendrivelinux.com) has a lot of installs...

EDIT: Lol, tea for one, you beat me to the punch regarding pendrivelinux...

---

### Post by LewRockwell on 2009-10-14
> **doas777 said:**
> depending on the state of the drive, you may wanna unplug it though. if it is partially operational, it may lag the rest of the system, as the hardware is trying to bring it online or deal with the gibberish it is spewing.

It might be possible to disable your dying internal hard drive via BIOS setting(s)

.

---

### Post by Paqman on 2009-10-14
> **knottshawk said:**
> Does the USB startup app within Ubuntu work pretty well? Or should I look elsewhere?

It does work pretty well, but try it before you need it. Some mobos dislike booting off USB media, even if they're technically supposed to.

If you use the USB startup disk creator and a nice big USB stick, allocate some of the stick for persistence. That'll let you keep your settings and files from one boot to the next.

---

### Post by jmundinger on 2009-10-14
> **tea for one said:**
> It will work if you can boot from a USB device.

If your BIOS prevents you from booting directly from a USB device but you have a working CD drive, then I suggest that you have a look at this website:-

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)


How does the result of the procedure described at that website differ from the  result from using the usb startup disk creator application in Ubuntu?

---

### Post by tea for one on 2009-10-15
> **jmundinger said:**
> How does the result of the procedure described at that website differ from the  result from using the usb startup disk creator application in Ubuntu?

The site [www.pendrivelinux.com](www.pendrivelinux.com) has a vast amount of instructions to create live USB devices using many alternative Linux distributions.

As I understand it, the utility in Ubuntu (USB Startup Disk Creator) can only use the Ubuntu family of operating systems - Ubuntu, Xubuntu etc.

---

### Post by Mighty_Joe on 2009-10-15
> **jmundinger said:**
> How does the result of the procedure described at that website differ from the  result from using the usb startup disk creator application in Ubuntu?

The Ubuntu Live USB Creator is just a script which performs the same actions as many of the tutorials on PenDriveLinux.  
If you want to use a USB drive for any amount of time, I'd do a full install to the USB drive (see my post [here]("http://ubuntuforums.org/showthread.php?t=1193680") for some flash drive optimizations).  It's faster than the Live CD because it is not compressed.  I've also heard [several compliaints]("http://ubuntuforums.org/showthread.php?t=1289297") that persistent USB drives stop persisting after a few boots.

---

