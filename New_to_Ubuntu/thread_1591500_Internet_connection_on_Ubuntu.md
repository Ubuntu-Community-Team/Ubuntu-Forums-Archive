---
title: "Internet connection on Ubuntu"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by subhkirti on 2010-10-09
Hello everyone, 

I am brand new to KUbuntu but since I have recently started learning an application in my office, which is Linux based, I decided that I should get it installed in my Laptop also. So, after finding that it can be run from the USB stick, I dowloaded the ISO image, and followed the instructions (ubuntu 10.04 live usb) and booted my system from the USB stick. I could get the KUbuntu running. However, on trying out the various things, I could not do the following :-

1. Start up an internet connection
I am trying to set up the internet connection, which is wireless. Everything works fine when I have Windows operating, but I do not find any wireless connection manager or someway to add a new wireless connection. How do i do it?

If anyone can explain me a step wise procedure to start my internet connection, while I am using my Live USB, I will be very grateful. 

Regards, 

Subhkirti.

---

### Post by spydeyrch on 2010-10-09
Are you able to connect your machine via a wired connection to the internet and browse it? If so, then do that (connect it via a wired connection) and then in your menu you need to find the hardware driver installer. In ubunutu, it is located under:  sytem -> admin -> hardware.  I don't know where in kubuntu since it uses kde and not gnome. but I would imagine that it would be something similar.

When you run the hardware installer, it should automatically scan your system for any supported hardware. If it finds some (i.e. your wireless card) it will then go online and find the appropriate drivers. You will then need to acticate those drivers from within the same hardware installer window.  That should do it. 

Now, if you haven't installed Kubuntu yet and are just running from a live usb, it might take it a little while plus, it is isn't a persistent live usb, you will loose the drivers after a restart/shutdown, in which case you will need to "install" them again once you boot up from the live usb.

I hope that helps to some degree. let us know if you need anything else. :)

-Spydey:KS

---

### Post by SeijiSensei on 2010-10-09
First, try this.  From the main menu in KDE, choose Applications, then in the System menu, choose Terminal.  When the terminal window opens, type "knetworkmanager" at the prompt.  You should see a new icon in the panel that represents the network manager.  Click it and choose "Manage Connections" to try and set up your wifi connection.  If it works, there's a simple method to put it in your taskbar permanently when you actually install Kubuntu.  (knetworkmanager should appear by default, but I've had some installations where it is missing.)

The installer for additional hardware drivers in Kubuntu is under Applications > System as well.  On older versions you'd see an entry for "Hardware Drivers"; in 10.10 it now reads "Additional Drivers".

---

### Post by anewguy on 2010-10-10
Also, if you are essentially just running the LiveCD environment but from a USB stick, it may not be possible to get wireless working.  Normally, you have to have an install of Ubuntu to do so.  If you want it to run from USB, look on the forum for information on building a USB-based Ubuntu installation, not just the LiveCD environment.

dave ;)

---

### Post by subhkirti on 2010-10-10
Hi anewguy,

I think that is my problem. I was trying to do as SeijiSensei advised me to do. I am attaching here snap shots of my work. I am not installing Ubuntu on my computer right now, and just running it via LiveCD environment. Is it not possible to connect it to the wireless router, if I am not installing Ubuntu? Is there any other method that I can do, which does the trick. (I mean run Ubuntu, connect it to internet, and use it as a normal user, without installing it.)

Regards, 

Subhkirti.


> **anewguy said:**
> Also, if you are essentially just running the LiveCD environment but from a USB stick, it may not be possible to get wireless working.  Normally, you have to have an install of Ubuntu to do so.  If you want it to run from USB, look on the forum for information on building a USB-based Ubuntu installation, not just the LiveCD environment.

dave ;)

---

### Post by McNils on 2010-10-10
Wireless can work from a liveCD system. It depends on the hardware. 
Look under system there is a kinfocenter. Under devices information/pci you can find your card.

---

### Post by anewguy on 2010-10-10
Normally with the LiveCD environment you are not going to be able to install a driver that is needed and make it "stick".  Think about it - you are running from a read-only medium! If you must, try creating a persistent USB installation of Ubuntu as then you would be able to install the driver.  Check the forum for info on creating a persistent USB installation and not just a LiveCD environment.

Dave ;)

---

### Post by spydeyrch on 2010-10-11
> **anewguy said:**
> Normally with the LiveCD environment you are not going to be able to install a driver that is needed and make it "stick".  Think about it - you are running from a read-only medium! If you must, try creating a persistent USB installation of Ubuntu as then you would be able to install the driver.  Check the forum for info on creating a persistent USB installation and not just a LiveCD environment.

Dave ;)


Yes dave, you are correct in the fact that it won't "stick" but if there is a driver available and it is installed, it will continue to remain during that session, and the wireless will work. 

-Spydey.

---

