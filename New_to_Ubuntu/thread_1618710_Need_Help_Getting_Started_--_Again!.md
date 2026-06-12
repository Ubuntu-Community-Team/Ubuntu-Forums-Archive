---
title: "Need Help Getting Started -- Again!"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by kaiser0792 on 2010-11-10
**VM's -- Determining the best way to go.** 			
 			 			 		   		 		 		Hello.  I am  new to Ubuntu. I have a PC running Windows 7. I tried to run Ubuntu with  VMWare and had multiple problems, printing, sound, CDROM, etc.  I  uninstalled VMWare and have read some discussion here that seems to  favor VirtualBox or KVM.

I'm a computer engineer student and I am going to have to write and  compile C++ programs on a Linux based system. I've never worked with  Linux and I would like to know the best combination to run a virtual  Linux-based OS that I can download a decent C++ compiler on and also be  able to use my printer, sound card and CDROM drive while working on the  Linux-based system. Which VM should I use and which version of Ubuntu  would you guys recommend?  Are there any "tricks" or specific things  that I should know as I set the system up? Thanks for any and all help.

By the way, my PC has an AMD II x4 635 Processor and my Windows 7 is 64-Bit.

---

### Post by Stafke on 2010-11-11
Ok, so I assume you need Linux, but don't want to really install it, either dual boot or ditch your Win.

Perhaps you could try Wubi-installer from [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer?](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer?)

Although I've never used it myself, it should just behave as a Win application and won't affect your OS

---

### Post by mastablasta on 2010-11-11
however if wubi file gets corrupted for some reason you wil loose all data in linux.
 
why not try to make a dual boot system. as a computer engineer student you should learn about disk partition and running multiple boot computers.
 
edit: another simple way is to get a USB key (1 GB is enough) and then create a persistent LiveUSB. that way you wont' touch you system when running Ubuntu.

---

### Post by toekneewood on 2010-11-11
In the past we have had problems with the workstation of VMware.  All of the Network engineers here have the following setup:
```

compaq desktop 64bit
8GB RAM
1TB HDD
Ubuntu 10.10 64bit (gnome version)

```
VM's
```

Windows 7 64bit
and a few other test systems

```

---

