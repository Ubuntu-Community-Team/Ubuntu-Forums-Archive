---
title: "How to create Ubuntu on USB without persistence?"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by Julita on 2010-09-15
Hello! I am trying to install an .iso of 10.10 on my USB flash, but the image wouldn't boot. It is a global problem, and I have found the link where it is explained that the image would boot only if persistence is not enabled (the source: [https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview) ). Could you please specify what should be done to achieve this?

---

### Post by uRock on 2010-09-15
Does your USB have U3 or any other software on it? If yet, then you need to remove it in order to make the USB bootable, at least I had to with mine.

I used Startup Disk Creator to make mine. It isn't actually installed, as it is the same as booting from a LiveCD and it isn't persistent.

---

### Post by Julita on 2010-09-15
In fact, there is U3 installed, but, since it is a different partition, it wouldn't matter. Besides, I have used it for all USB insallations, and everything worked fine. Is there a Windows analogue of Startup Disk Creator? I have tried every possible programme, unetbootin etc, and they just wouldn't work. I assume the persistence is disabled only in this Creator?

---

### Post by uRock on 2010-09-15
The Startup Disk Creator is the Ubuntu 10.10 LiveCD under System> Administration in the menu. You will have to use a machine with a CDROM to boot into the LiveCD or a machine with ubuntu already installed to use it.

---

### Post by howefield on 2010-09-15
Hasn't U3 gone extinct, like the Dinosaur ?

Must be a pretty good and valuable pen drive not to replace it with something current and supported, not to mention friendly to bootable distros that also live on the drive ;-)

---

### Post by uRock on 2010-09-15
> **howefield said:**
> Hasn't U3 gone extinct, like the Dinosaur ?

Must be a pretty good and valuable pen drive not to replace it with something current and supported, not to mention friendly to bootable distros that also live on the drive ;-)
I finally wiped U3 off of mine 2 days ago and have been having fun booting machines with it ever since. I have almost convinced one of my teachers to let me boot the PC I use for setting up switches with ubuntu instead of that other OS they have.

---

### Post by Strategist01 on 2010-09-15
Hi - you can use [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) to install a linux distro onto your USB. I don't know whether it supports 10.10, but it runs from Windows...

---

### Post by jmszr on 2010-09-15
Julita,

Here is another USB installer - persistence is optional- that runs from Windows: [http://lifehacker.com/5574276/universal-usb-installer-makes-a-persistent-thumb-drive-version-of-any-linux-os](http://lifehacker.com/5574276/universal-usb-installer-makes-a-persistent-thumb-drive-version-of-any-linux-os) .

If you want to remove U3 (and I would) here is a link that gives several options for removing it: [http://www.tomshardware.com/forum/243608-32-remove-smart-software-sandisk-flash-drive](http://www.tomshardware.com/forum/243608-32-remove-smart-software-sandisk-flash-drive). They give some universal options - not just for Sandisk.

---

### Post by beew on 2010-09-15
I created a live usb of 10.10 with Ubuntu's startup disk utility and it is persistent and it boots, have tested it many times so I don't know what the problem is. 

But then I have a more recent version of startup-disk utility than what comes with lucid because I have enabled a lot of ppas and one of them has this program and it got updated recently. I will have to check the version but I don't have access to my ubuntu machine right now.

The tutorials in pendrivelinux are almost all for Windows, it is kind of ridiculous that you will need access to a windows machine in order to easily make a Linux live usb with persistence especially if you want a liveusb for a different distro than Ubuntu. Someone should try to port the universal installer to Linux,. And then there is LiLi, it can create liveusb for almost any Linux distro but guess, it is for Windoze only [!http://www.linuxliveusb.com/  ]("http://www.linuxliveusb.com/")

This is one of my pet peeves, everybody writes programs which works only for Windows and the need of Linux users are constantly ignored. I can understand the reason for commercial softwares since Windows represents a much bigger market, but how about free open source ones which try to sell you Linux? Just because we are already using Linux doesn't mean that we may not want to play with other distros.

P.S. You can always create a liveusb without persistence if that is what you want, just set persistence = 0 when you create the liveusb with startup disk utility, or you can use unetbootin (though I don't know whether it works with 10.10, but it should). It is harder to create llinux ive usb with persistence in Linux if you don't know how to or don't want to do it with command lines  since you don't have the Windows tools.

---

### Post by beew on 2010-09-15
The creator of LiLi just pointed me to this site.  It seems very promising if you like to play with different distros.

[http://liveusb.info/dotclear/index.php?](http://liveusb.info/dotclear/index.php?)

---

### Post by Strategist01 on 2010-09-16
BTW, Kubuntu had a live USB creator on the Live CD - I managed to install 9.10 to a flash quite easily with that. However, I forgot what it's called. I'm sure its available in the synaptic package manager...

---

