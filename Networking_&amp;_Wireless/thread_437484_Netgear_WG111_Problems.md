---
title: "Netgear WG111 Problems"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by s2dpyro on 2007-05-08
Ok well i just got Ndiswrapper to work i got the driver for my Netgear WG111 installed correctly

When i type ndiswrapper -l it says that the driver is installed and the hardware is there

And the Light Turns on, on the wireless thing

But for some reason in the network manager it says that i have no wireless card at all

I just don't know what to do now (i'm pretty new with this whole linux thing so that isn't saying much)

Please try helping me i really rather use Linux then windows.

---

### Post by Revolution on 2007-05-08
Which version of Ubuntu are you using?

---

### Post by s2dpyro on 2007-05-08
Fiesty Fawn (7.04)

---

### Post by s2dpyro on 2007-05-09
bumb

---

### Post by tristan5 on 2007-05-13
Hi, i'm trying to install my Netgear wg111 in feisty fawn with ndiswrapper but i'm having a lot of problems with that.:( 

First: i discovered that my wg111v2 is not really a v2 but a v1 wi-fi dongle, even if it's written "wg111v2" on the side of the pen. :confused: 
It is important to discover what kind of dongle you have to find the correct driver for ndiswrapper. 
To find out your version try the command "lsusb" and get the code of your card, mine is "0846:4240" advertised as wg111(v2). Find out your code in the [ndiswrapper page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_m-n/") and look for the driver you need.:) 

My problem: I compiled the last version of ndiwswrapper and followed the instructions to install the windows driver (i used the driver found in the manufacturer CD). Everything seems to go fine except that the dongle doesn't reveal any AP in my area. 
Even if I configure manually the wireless connection (essid, WEP Hex key, dhcp) it seems to be unable to connect to my network at the LINK level of the OSI stack. :mad: 
If anyone had success installing the 0846:4240 Netgear dongle in feisty fawn  please help me...

---

