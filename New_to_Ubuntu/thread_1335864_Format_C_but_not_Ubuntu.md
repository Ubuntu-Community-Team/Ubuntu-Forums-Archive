---
title: "Format C:\ but not Ubuntu"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by Renée Jade on 2009-11-23
Hey all,

I've been looking around for the answer to my question but without much luck. I've had Vista and Ubuntu dual booted on my laptop for a while now, but I want to replace Vista with XP. Does anyone know if I can do this without destroying Ubuntu? I've backed up and I've already checked out how to get GRUB back when I'm done. I have a fair idea of what I'm doing but I don't want to make a mess.
Also wondering (it is related), will typing "format C:\" during the windows installation wipe my whole drive or only the Vista volume?

Thanks for any help,

Renee.

---

### Post by MelDJ on 2009-11-23
why not use gparted to format the vista partition? for installing xp see: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by slick666 on 2009-11-23
You should have ubuntu installed in a second partition that should allow you to install XP on the first partition without disturbing Ubuntu on the second. When you install XP it will overwrite the Master Boor Record (MBR) as well. Once you install XP you will have to install Grub again to get the option to select between Ubuntu and XP. If you have it backed up well you should be ok.

On a side note. If you are moving back to Windows XP have you considered virtualizing XP on Ubuntu? Ifnot take a look at VirtualBox ([http://www.virtualbox.org/]("http://www.virtualbox.org/")). It allows me to run XP on top of my Ubuntu system so I don't haveo go through the trouble to reboot.

I hope this helps

---

### Post by anewguy on 2009-11-23
+1 on using gparted to format the old Vista partition.

But.....a VERY STRONG +1 on using VirtualBox in Ubuntu and running XP as a virtual machine in it.  If you are not familiar with the concept, VirtualBox can create what is just a file to Ubuntu but is used as a "logical" disk instead of a physical disk or partition to hold another operating system, in your case XP.  Instead of dual-booting, you actually just run XP in the virtual machine in Ubuntu - it runs just like another Ubuntu process, and you can run other Ubuntu processes at the same time.  You will XP without the hassle of dual-booting, and if XP crashes it won't lock up all of the machine.

I would strongly recommend it, but be sure to download from the Sun site for VirtualBox and get the non-open source version (it's still no cost, just no source code) as it will give you USB support in your virtual machine.

Dave :)

---

### Post by Zalbor on 2009-11-24
Keep in mind that all of the above assumes you've installed Ubuntu in its own partition and not through Wubi or something.

And also, on the subject of virtualisation, unless something has changed recently you won't be able to do anything "heavy" with XP in virtualbox, like playing a (remotely recent) game or working with graphics in another way.

---

### Post by MelDJ on 2009-11-24
+1
currently, directx8 only is supported.

---

### Post by Some Penguin on 2009-11-24
Consider installing Grub on the Linux partition, and setting up the Vista bootloader in the MBR to select between an ordinary Vista boot vs. loading from the Linux partition.  That way, if you upgrade or reinstall another Microsoft OS (which will generally want control of the MBR) you've still got the Grub configuration completely intact -- you just need to connect the two bootloaders, basically.  I've done something similar for my XP/Gentoo dual boot; the machine reads the NTLDR configuration and lets me choose between Linux (which jumps to the Grub install on the Linux /boot partition, instead of directly into Linux) or booting XP, while the Grub menu lets me boot Gentoo (with a few kernel configs) or jump back to NTLDR. 

For one way to do that, do a web search for EasyBCD.  I believe development on that is continuing to ensure that it'll work with Windows 7, too.

---

### Post by Julita on 2009-11-24
Acronis Disk Director Suite works perfectly!

---

### Post by Renée Jade on 2009-12-03
Wow. Thanks guys! The forum didn't tell me you had all replied. Strange :S. As it went I managed to install XP over Vista without wrecking Ubuntu but then went to hell and back trying to get GRUB back. I tried everything, even reinstalling Ubuntu without formatting the root partition. That last desperate measure got GRUB working but wrecked my Ubuntu install. In the end I had to sacrifice my Ubuntu system and I did a fresh install of Kubuntu 9.10. Thanks anyway though. Next time I multi-boot I will use a partition management program of some sort.

---

