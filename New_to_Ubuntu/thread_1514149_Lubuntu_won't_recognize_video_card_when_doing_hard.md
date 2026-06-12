---
title: "Lubuntu won't recognize video card when doing hardware manager"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by BT1 on 2010-06-20
Okay so, I updated my lubuntu system through synaptic (clicked, mark all upgrades) and it updated my system. I try to run "Hardware Drivers" but it won't recognize my ATI Radeon X700 Pro card. Can anyone help me? In the past I tried to go through synaptic and the result was bad, perhaps because I am still new to ubuntu-linux.

Please help!

---

### Post by shawnansasio on 2010-06-20
lubuntu??? you mean kubuntu? i havent played with ubuntu in a few years but try this:
go in to the screen resolution window > Say which driver you are using
(eg. Vesa, AtiMach, nVidia)

---

### Post by BT1 on 2010-06-20
No, Lubuntu --> [http://lubuntu.net/](http://lubuntu.net/)

It's Ubuntu but with LXDE which is faster and more lightweight than Xubuntu. ALL I need is this dang video card to work, and my problems will be fixed..... for the time being lol. It boots up to the GUI and desktop, but I can't enable certain functions without it using the full speed of the card, such as gaming, desktop effects, etc.

Again, someone please help lol.

---

### Post by shawnansasio on 2010-06-20
Which graphics driver do you use???

---

### Post by TBABill on 2010-06-20
It probably defaulted to the open source driver. You can go into Synaptic and download/enable the ATi driver for your machine.

I think the file you may need to install is xserver-xorg-video-radeon. You can search "ATi" in Synaptic and read the various details for different files to be sure. Hopefully it will pull in all dependencies for other associated files and activate upon reboot.

---

### Post by clhsharky on 2010-06-20
BT1

The default open source driver is the correct driver for your card, for releases after 2008.
 That is why the are no proprietary drivers offered to you to install. 

Sharky

---

### Post by TBABill on 2010-06-20
clhsharky, I believe that Ubuntu does install the open source driver as the driver of choice, but that does not mean you cannot install the proprietary driver from Synaptic for your card. Having an open source driver does not mean there is not a proprietary driver for your card. My machine is a perfect example. Ubuntu installed the default ATI open source driver, but I then installed the proprietary driver (not shown in system>>admin>>hardware for some reason). My machine now runs much cooler and 3D works great.

---

### Post by ell02 on 2010-06-29
In synaptic I used fglrx-dev. That allowed the hardware driver app.to show an ati propriatary driver for installing.
It might not be best way but the way that solved my same problem.

---

