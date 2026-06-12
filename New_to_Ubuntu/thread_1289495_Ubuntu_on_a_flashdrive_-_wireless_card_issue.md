---
title: "Ubuntu on a flashdrive - wireless card issue"
date: 2009-10-12
forum: New to Ubuntu
---

### Post by jmundinger on 2009-10-12
I used the usb startup disk creator application to install Ubuntu 9.04 onto a 4 gb flashdrive.  I am using it to run Ubuntu on my laptops without actually installing the system on either computer (at least, not yet).  I have no problem booting into Ubuntu from the flashdrive and, in general, it works just fine.  However, with one of the computers, I'm having difficulty with the wireless card.  

I have an Acer netbook and everything appears to work as it should.  I have no problem connecting to the internet through the wireless card, connecting either through my own internet connection or while travelling, though a different system.

My laptop - a Dell Vostro - is giving me fits.  The first time I booted the flashdrive on that computer, it worked just fine.  When I have tried since then, however, I can't connect to the internet.  Typically, the "enable wireless" option does not appear in the menu under the network icon.  Sometimes I have been able to correct that issue by deactivating/activating the driver for the wireless card (it does appear when I open the hardware drivers application).  If I am able to see the "enable wireless" option, I then am also able to see about a half dozen choices - assuming all of my neighbors have their routers on - including my own.  If I try to connect to my network, the system asks for the password, but then will not connect.  One of my neighbors has an unsecured network and a signal sufficiently strong that, in windows, I could connect to it.  However, I am unable to connect to that network either.

Any thoughts is to what is going oin?

---

### Post by zkriesse on 2009-10-13
It could be that the card isn't configured properly but I'd seriously doubt that. You could try to load Ubuntu 9.04 onto a flash drive via MS Windows with a program called UNetbootin which can be found here at [UNetbootin.sourceforge.net]("http://unetbootin.sourceforge.net/") Hope it helps. Also, you'll need to format the flash drive with Windows to FAT32 format. Cheers!

---

### Post by beastrace91 on 2009-10-13
> **Zachk18 said:**
> It could be that the card isn't configured properly but I'd seriously doubt that. You could try to load Ubuntu 9.04 onto a flash drive via MS Windows with a program called UNetbootin which can be found here at [UNetbootin.sourceforge.net]("http://unetbootin.sourceforge.net/") Hope it helps. Also, you'll need to format the flash drive with Windows to FAT32 format. Cheers!

Unetbooin also installs on Linux, on Ubuntu just run ```
sudo apt-get install unetbootin
```

Also might I suggest simply full on installing Ubuntu to the flash drive? 4gigs is more than enough space, and then you will have a persistent install on it (save programs you've added ect.) I have a drive I've done this on :) (To do this just boot to a live CD and select the USB drive you have attached as the install destination)

~Jeff

---

### Post by jmundinger on 2009-10-14
> **beastrace91 said:**
> Also might I suggest simply full on installing Ubuntu to the flash drive? 4gigs is more than enough space, and then you will have a persistent install on it (save programs you've added ect.) I have a drive I've done this on :) (To do this just boot to a live CD and select the USB drive you have attached as the install destination)

I thought that I would get a persisent install with the routine that I had originally used to install Ubuntu to the flash drive.  I did that using a routine that ran from the command prompt in Windows.  That didn't happen, so I started over, using the routine that is part of the Ubuntu installation.  In both cases, I got a USB equivalent of the live USB.

So, if I install Ubuntu to the USB drive from the live CD, I have a couple of questions:

1.  If I do that on my desktop, which is a dual boot system, will it make any changes to GRUB?
2.  If I do it from the laptop - which is only running Windows XP - will it alter the MBR?
3.  In either case, am I correct in assuming that the installation will re-format the USB drive as ext3, or should I do that beforehand?

---

### Post by Zero++ on 2009-10-14
1. If I do that on my desktop, which is a dual boot system, will it make any changes to GRUB?
2. If I do it from the laptop - which is only running Windows XP - will it alter the MBR?
3. In either case, am I correct in assuming that the installation will re-format the USB drive as ext3, or should I do that beforehand?
 
It shoundn't change your MBR either way. When I did it I formated the stick beforehand, using GPARTED, and it worked just fine. I love it because i have MY computer with me wherever I go no matter whose hardware I'm using!!!

---

### Post by jmundinger on 2009-10-14
> **beastrace91 said:**
> Also might I suggest simply full on installing Ubuntu to the flash drive? 4gigs is more than enough space, and then you will have a persistent install on it (save programs you've added ect.) I have a drive I've done this on :) (To do this just boot to a live CD and select the USB drive you have attached as the install destination)


I don't think I would recommend doing this.  I tried it and the result was a failure.  I worked from my desktop - which is set up as dual boot.  I partitioned the USB drive with the partition editor and then installed Ubuntu to that drive from the live cd.  The result was a hosed GRUB, i.e. the computer looked for but could not find GRUB and, therefore, wouldn't boot.  And, when I attempted to boot the USB from my netbook, the result was a major nada.

Not knowing what else to do, I reinstalled Ubuntu on my desktop and, in the process, restored GRUB.  So, at least that is working.

---

### Post by LewRockwell on 2009-10-14
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

.

---

### Post by jmundinger on 2009-10-14
> **LewRockwell said:**
> [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

.

How do those options compare with using the usb startup disk creator application in Ubuntu?

---

