---
title: "BIOS for USB Karmic"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by MisFitt on 2009-11-21
Hi,
I'm terribly confused.
I believe I've successfully created a Karmic USB on a 16GiB flash stick(the usb creator went thru' the motions) but when it comes to setting the bios I'm not only out of my depth but utterly confused.
My bios offers as boot devices:
Floppy,LS120,Hard Disk,CDROM,ZIP,USB-FDD,USB-ZIP and USB-CDROM.
(I'm on an amd athalon 64,dual core,2Gib ram that's possibly 3 years old by now)
I'm very new at partitioning and have never had an OS on usb before so I need a bit of a hand here,thanking you in advance.
I need help with the bios configuration and whether it's even possible on my machine to boot into USB.
Thanks,I'll provide any further info re my computer.

---

### Post by Jon Monreal on 2009-11-22
It looks like your BIOS doesn't support USB-HDD. There is a [method to make it do so]("http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/"); however, this method requires that you already have a Linux environment or a LiveCD (which I'm going to assume would defeat the purpose of what we are trying to do).

That said, why not just burn it to CD and use that option? Even if you don't have a CD burner, do you have a friend that does? This would be much easier than trying to get some solution working for the USB drive.

---

### Post by mechro on 2009-11-22
Does your BIOS have a **Hard Disk Boot Priority** setting? If it does then your USB drive might show up in there. It does in my Phoenix Bios.

---

### Post by MisFitt on 2009-11-22
> **Jon Monreal said:**
> It looks like your BIOS doesn't support USB-HDD. There is a [method to make it do so]("http://www.pendrivelinux.com/booting-linux-from-usb-zip-on-older-systems/"); however, this method requires that you already have a Linux environment or a LiveCD (which I'm going to assume would defeat the purpose of what we are trying to do).

That said, why not just burn it to CD and use that option? Even if you don't have a CD burner, do you have a friend that does? This would be much easier than trying to get some solution working for the USB drive.
I am using an XP/Ubuntu 9.04 dual boot and I have the cd,the 9.10 iso and I have a cd/dvd burner(which is making a lot of noise when running,needs replacing but.burns fine)
I wanted to do it and to be able to make gifts of Ubuntu usb's but no matter and to check out other os's that way and seeing I no longer have a laptop,it would have been good while away.
Thanks for your suggestions.
I'm about to have a careful look at your link,thanks for that too.
I'd like to be able to do this...because it's there I guess

---

### Post by sandyd on 2009-11-22
> **MisFitt said:**
> Hi,
I'm terribly confused.
I believe I've successfully created a Karmic USB on a 16GiB flash stick(the usb creator went thru' the motions) but when it comes to setting the bios I'm not only out of my depth but utterly confused.
My bios offers as boot devices:
Floppy,LS120,Hard Disk,CDROM,ZIP,USB-FDD,USB-ZIP and USB-CDROM.
(I'm on an amd athalon 64,dual core,2Gib ram that's possibly 3 years old by now)
I'm very new at partitioning and have never had an OS on usb before so I need a bit of a hand here,thanking you in advance.
I need help with the bios configuration and whether it's even possible on my machine to boot into USB.
Thanks,I'll provide any further info re my computer.
does pressing F12 at boot accomplish anything?

---

### Post by MisFitt on 2009-11-22
> **carlee said:**
> does pressing F12 at boot accomplish anything?
Well,actually it does,it offered USB-HDD which I set it to and this came up:
SYSLINUX 3.63 Debian-2008-07-15 CBIOS
boot:
I didn't know what to type but there it was,something.Does that help?
It's interesting that it showed USB-HDD whereas in the advanced bios listed in original post it didn't.
thanks

---

### Post by Jon Monreal on 2009-11-22
Try pressing the enter key.

---

