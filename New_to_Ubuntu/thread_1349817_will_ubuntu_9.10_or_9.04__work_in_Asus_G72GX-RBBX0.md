---
title: "will ubuntu 9.10 or 9.04  work in Asus G72GX-RBBX05?"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by fwin on 2009-12-08
Hi,
 I am planning to buy a laptop ( Asus G72GX-RBBX05) with the following specs:

Intel Core 2 Duo P8700 @ 2.53Ghz
nVidia geforce GTX 260M 1GB
17.3” Widescreen LCD 1600x900
6GB DDR2 RAM
500GB HDD



-Are there drivers for this graphics card in ubuntu 9.04 or 9.10?. How can i find out if they are supported?
-Has anyone had any problems with other drivers for this machine?

I would really appreciate any help

thanks

---

### Post by RedSingularity on 2009-12-08
The 200 series graphics cards are supported.  You will just need to install the driver.

---

### Post by fwin on 2009-12-09
Thanks for the info I really appreciate your help.

---

### Post by jack frost on 2011-01-26
> **RedSingularity said:**
> The 200 series graphics cards are supported. You will just need to install the driver.
 
has anyone been able to install the nvidia driver to get the special effects to work for 10.10?  I have this laptop and have 10.10 inside vm player  playing to make sure everything works. I have read some tutorials;but they don't seem to work. I read the install notes on nvida's site and it says the card is supported.  I am just trying to get the actual nvidia driver to install and not use the vmware driver.

---

### Post by robsoles on 2011-01-26
> **jack frost said:**
> has anyone been able to install the nvidia driver to get the special effects to work for 10.10?  I have this laptop and have 10.10 inside vm player  playing to make sure everything works. I have read some tutorials;but they don't seem to work. I read the install notes on nvida's site and it says the card is supported.  I am just trying to get the actual nvidia driver to install and not use the vmware driver.
Been a while since I played with VMWare stuff but pretty sure it is using a 'VM VGA/VIDEO Device' and not the actual video device of the host machine.

What this means is that if you successfully install the host's video driver into your VM and you convince your guest OS to use that driver you will very likely stop being able to operate your VM.

To test the video driver, whether it will do everything you want it to, you would be best to install the target OS onto a partition of it's own (it is possible to install to a USB drive with enough free space) and then try drivers, and any other points of interest, from/in that installation - A Virtual Machine can show you whether or not you will like the OS in general, it can't (to absolute best of my understanding) confirm whether or not drivers and stuff for the OS will be OK in the host.

---

