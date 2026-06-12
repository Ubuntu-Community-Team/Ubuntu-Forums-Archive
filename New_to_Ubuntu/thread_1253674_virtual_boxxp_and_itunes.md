---
title: "virtual box/xp and itunes"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by impatientboi on 2009-08-30
i successfully installed virtual box for linux hosts, but it asks me for either an installation file for the os or a disk image. i had assumed it just loaded the existing installation in virtual box?
i am using a pc without an optical drive, so i can't use the xp cd that came with the computer

it does give me the option to boot to an image vbadditions. or something similar but this results in running the virtual machine and getting a 'no bootable media' messageel


i am guessing since the terminal is loaded everytime i open virtual machine i should be able to punch in a command so that virtual box loads from the xp drive? 

any help anyone?

also i am only doing this to enable me to use itunes to manage my iphone (perhaps i should have bought a mac, but they are so overpriced.) Has there been much success using vb to run itunes ?

---

### Post by Liolikas on 2009-08-30
Just **makeisofs** from windowsXp cd you get windowsxp.iso and you can use it on virtual box "cdrom" option iso file.

---

### Post by credobyte on 2009-08-30
Unless your hard drive have an .vdi extension ( impossible ), you can't do that.

---

### Post by Paqman on 2009-08-30
You can mount an .iso as if it were a disk in Virtualbox, but getting your hands on an .iso of Windows is unlikely to be legal or smart. Your other option would be a USB/Firewire external optical drive

To be honest, I don't think virtualisation on a netbook is going to be a great idea. You're unlikely to have enough processing power and memory to have it run well. What hardware do you actually have? If your machine has enough storage i'd advise dual-booting instead of virtualisation.

---

### Post by Liolikas on 2009-08-30
Read:

[http://www.petitiononline.com/itmslin/petition.html](http://www.petitiononline.com/itmslin/petition.html)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)
[http://www.desktoplinux.com/articles/AT7150747782.html](http://www.desktoplinux.com/articles/AT7150747782.html)

---

### Post by darrelljon on 2009-08-30
Not even sure if host operating systems in virtualbox can connect to an iphone.

---

### Post by impatientboi on 2009-08-30
i have given ubuntu a go after reading quite a bit about it in some mags. I was a bit skeptical about it's ease of use, but it's been a dream so far.
they had an article on virtualisation. i didn't think it would run very well at all with my processor. (asus 1000h) one of the atoms. 

i've gotten that comfortable with the dual boot on the system that i would have liked to run an alternative to itunes natively. amorak i don't really get. . . rhythm box looks like it has good functionality but the interface is not really designed for a netbook. songbird looks ok but i find it bit clunky and it's podcast support isn't great, but i love the fact it's got extenison capability for ipods

does anyone have any other suggestions for managing my music? (with iphone compatability in mind

---

### Post by Paqman on 2009-08-30
> **impatientboi said:**
> 
does anyone have any other suggestions for managing my music? (with iphone compatability in mind

AFAIK your options are pretty limited with the iPhone. 

Newer versions of the package gtkpod, and older versions of Amarok should be ok, but IIRC the newer your iPhone firmware is the more trouble you'll have.

If you feel like giving yourself a headache, there's a ludicrously convoluted page on the wiki about [iPhones]("https://help.ubuntu.com/community/PortableDevices/iPhone").

Maybe you should upgrade to an Android phone when your contract is up? ;)

---

