---
title: "Wireless card help"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Rogue5 on 2010-03-09
Have Ubuntu 9.10 on a HP dv4000  I installed drivers (.inf) through the windows wireless driver program. But it says "Unable to see if hardware is present" even though it shows it in list.  If I click on the device (netani) then click configure network....  it says "Cannot find a network configuration tool"

Please teach this grasshopper how to be a linux tiger.

---

### Post by undecim on 2010-03-09
You installed drivers on Ubuntu using a Windows program? I'm sorry, but that won't work.

The easiest way to install wireless drivers on Linux is to connect to the internet with an ethernet cable (i.e. directly to your modem or router), and go to System -> Administration -> Hardware Drivers.

If you don't have an ethernet connection, I need to know more about your wireless card. Open a terminal from Applications -> Accessories -> Terminal, and copy and paste this command:```
lspci | grep Wireless
```and post the output from that here.

---

### Post by sandyd on 2010-03-09
> **Rogue5 said:**
> Have Ubuntu 9.10 on a HP dv4000  I installed drivers (.inf) through the windows wireless driver program. But it says "Unable to see if hardware is present" even though it shows it in list.  If I click on the device (netani) then click configure network....  it says "Cannot find a network configuration tool"

Please teach this grasshopper how to be a linux tiger.

did you mean you installed it using ndiswrapper?

---

### Post by Rogue5 on 2010-03-10
My output

06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g [COLOR=Red]Wireless[/COLOR] LAN Controller  [COLOR=Black](rev 02)


And no I downloaded a program for ubuntu called wireless windows drivers, that or I used WINE on it, cant remember.
[/COLOR]

---

### Post by anewguy on 2010-03-10
Check under System/Administration/Hardware Drivers and see if there is a restricted driver listed.  If so, enable it and your wireless should work.  If not, you can use a tool called ndiswrapper to load in Windows drivers.  Using Wine for the driver install won't work.  I have no idea what the other tool is you are talking about.  To use ndiswrapper:

(1) Either use Synaptic package manager (if you can hardwire or in some way connect to the internet) and install the ndiswrapper package, the ndiswrapper utilities or tools (this may not be the exact name and it may not be in the list), and the ndisgtk package, or put in your distribution LiveCD and navigate to the pool/main/n folder - you should see ndiswrapper and ndisgtk both there - click on each of them to install them.

(2) Copy the Windows driver for your card (the .inf and .sys files) to your desktop.

(3) Start ndisgtk

(4) Request add new driver (or maybe it's device - I haven't used it in a while).  Point this to the .inf file on your desktop.

(5) See if your wireless connects.  There are some included drivers that may need to be blacklisted in order for this to work, but I don't remember if ndisgtk does it for you.

Dave ;)

---

### Post by rusty815 on 2010-03-10
you have a broadcom?

im not sure if this works in ubuntu, i am using debian sid (eb4 to be exact) and several of the users found that if you connect to the internet via ethernet cable, open up synaptic and search for the package "b43-fwcutter" and install it, wifi works, its a package that extracts the firmware for broadcom 43xx cards and installs them, making the broadcom cards usable, see if ubuntu has the package and install it.

---

