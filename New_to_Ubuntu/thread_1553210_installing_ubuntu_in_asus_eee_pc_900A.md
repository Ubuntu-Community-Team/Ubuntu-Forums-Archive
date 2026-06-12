---
title: "installing ubuntu in asus eee pc 900A"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by Roberto Arciniegas on 2010-08-14
I have downloaded ubuntu for netbooks and created an image in a usb thumb drive. When I boot the machine the following messages appears:
Reboot and Select proper Boot device
or insert Boot Media in selected Boot device and press a key

I have try 5 different USB thumb drives without any luck. The computer is running a Xandros distro. 

Any sugestions?
there is a video on you tube showing what I'm trying to do and they say that some USB thumb drives don't boot.

---

### Post by blazemore on 2010-08-14
What did you use to make the USB flash drive?
I'd recommend the tool called "Linux Live USB Creator" which runs on Windows. You'll need access to a Windows PC to use it.

---

### Post by scorp123 on 2010-08-14
> **Roberto Arciniegas said:**
>  I have try 5 different USB thumb drives without any luck. The computer is running a Xandros distro.  I never got that to work ... My wife's 900A too won't boot from USB sticks.

Instead I bought a USB-to-IDE/SATA adapter, e.g. one like this (... there should be an image here now ...):

[IMG]http://www.nigelcomputers.com/store/images/cb-isatau2.jpg[/IMG]

I had a spare IDE DVD drive laying around and with that adapter I simply installed Ubuntu like I would on a normal PC, e.g. by booting off the Ubuntu install CD. The DVD drive when connected via USB should be recognised by the 900A's BIOS ... you'd have to check the bood order settings to be sure. But if the boot order is correct it will boot tip top off the CD.

BTW, I installed the normal Ubuntu on my wife's 900A and it works tip top despite the limited screen space.

I hope this helped ... ?

---

