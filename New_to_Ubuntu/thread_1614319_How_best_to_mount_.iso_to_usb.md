---
title: "How best to mount .iso to usb?"
date: 2010-11-05
forum: New to Ubuntu
---

### Post by demonboy on 2010-11-05
Hi,

The title says it all but I've made a bit of a mess of this. I have tried Gmount but it asks for a password (no idea what this is). I then tried Furious, which really isn't intuitive. After that I tried MountManager, which scared the hell out of me.

I'd just like to mount an ISO onto my USB stick (this is to install Ubuntu on my father's machine cos I'm pretty impressed with it and he is hating Windows 7) so I can boot from the stick.

Any clues?

---

### Post by Hippytaff on 2010-11-05
Try Unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by desperado665 on 2010-11-05
Or try the Universal USB installer from Penlinux. It works great.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by dcsoldschool53 on 2010-11-05
> **demonboy said:**
> Hi,

The title says it all but I've made a bit of a mess of this. I have tried Gmount but it asks for a password (no idea what this is). I then tried Furious, which really isn't intuitive. After that I tried MountManager, which scared the hell out of me.

I'd just like to mount an ISO onto my USB stick (this is to install Ubuntu on my father's machine cos I'm pretty impressed with it and he is hating Windows 7) so I can boot from the stick.

Any clues?

Click system > Adminstration and scroll down to the program called USB Startup Disk Creator. Use this program to mount your .iso, and if you don't have it download it.

---

### Post by demonboy on 2010-11-05
@ Hippy - Yeah, that's a bit more like it! Thank you.

@ oldschool and desperado - will try this too, thanks.

---

### Post by yetiman64 on 2010-11-05
Or System > Administration > Startup Disk Creator, with your usb stick plugged in, point it to the iso in the top pane and select the usb stick in the bottom pane. It will use only about 700 MB of the usb stick and any extra space can be allocated to saving documents and settings if you wish to.

Edit: beaten by dcsoldschool53 :)

---

### Post by Evil-Ernie on 2010-11-05
A thing to consider as well is the BIOS requirements and the pen drive you use. 
I would advise that you use a pen drive *less *than 2GB as you can then format it as a FAT16 which most BIOS like.
 
Also I found with my VIA EPIA board that if I changed the boot sequence to scan USB ports that changes didnt activate until I turned it off fully and removed power for a complete reset. I tell you that was a most frustrating night trying to work out why the BIOS wasnt picking up my boot drive LOL!

---

### Post by risegeek on 2010-11-05
You should use Wubi if he is coming from Windows - atleast you can quickly uninstall Ubuntu if he decides against it after a while. :)

---

### Post by Verbeck on 2010-11-05
for future reference : mounting an iso to a flash drive is not the same as creating a bootable usb

---

### Post by beew on 2010-11-05
> **risegeek said:**
> You should use Wubi if he is coming from Windows - atleast you can quickly uninstall Ubuntu if he decides against it after a while. :)


I beg to differ. I would want to keep the OS separated as much as possible to avoid possible problems. WUBI only runs of a Windows folder, this is no way to test Linux. Moreover, many people get the wrong idea that WUBI is a real dual boot and try to do dumb things that get them into troubles (like trying to delete the Windows "partition")

If OP's father wants to just try out Ubuntiu I  suggest either using a live usb with persistence or a full installation into an external hard drive. A full installation allows you to do things like installing proprietary graphic cards or system level update which cannot be done in a live usb. On the other hand a live usb is simple to make and fast (ilive usb is fast because it runs on ram, but a full installation into a flash drive would be slow, full installation works better in an external hard drive)

---

### Post by beew on 2010-11-05
> **desperado665 said:**
> Or try the Universal USB installer from Penlinux. It works great.

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


It only works on Windows. Most of pendrivelinux's tutorials are useless if you are already running Linux as most of them work only in Windows (If I am running Linux already am I supposed to borrow a Windows machine or get into a Windows partition to make a Linux live usb? That website kinds of annoys me . :))

---

### Post by demonboy on 2010-11-07
Some food for thought there, thank you.

I went ahead and did a complete install on dad's Samsung N140. He was tearing his hair out at how slow Windows 7 was and since he hadn't any data on it anyway we lost nothing by doing it. I am typing this on his install now.

I think I did an install via Wubi, however, on my netbook. I thought it was dual boot but now I realise it isn't.

Anyway, I have my head around the mounting of the iso and had even considered buying some cheap 1Gb sticks and making them permanent mounts because I return to India soon where I have a really crappy 2G connection and downloading the installer again would probably take a week!

Thanks for the discussion on this.

---

