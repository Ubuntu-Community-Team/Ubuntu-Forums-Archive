---
title: "DWL-G122 Wireless USB Adapter Help!"
date: 2006-10-14
forum: Networking &amp; Wireless
---

### Post by cesiel1993 on 2006-10-14
I need help setting up my internet with my DWL-G122 Wireless USB Adapter, however I can't find a good guide for it.  I run Dapper Drake and I'm wondering if anyone else can help me out??

Thanks!

---

### Post by moini on 2006-10-14
hi i was installing the dwl-g122 with ndiswrapper

apt-get install ndiswrapper

dowload windows driver from dlink

install wine

extract the windows driver with wine

(wine driver.exe)

follow instructions from ndiswrapper with dwl.g122 and you will have a wlan0 interface

./regards

moini

---

### Post by rockfly12 on 2006-10-14
I dont think you need to use ndiswrapper.  I have a DWL-G122 and when I plug in the device I can see it is recognized.  If I disable my wired network card (bring the interface down, or make sure its not plugged in) and issue the iwconfig commands to get it up and running it will eventually work.  To summarize how I can get this working:

1. Verify you can see the device with lsusb and dmesg
2. iwconfig rausb0 essid "YOURSSID"
3. iwconfig rausb0 key "YOURWEPKEY"
4. ifconfig rausb0 "YOURIP"
5. route add -net default gw "YOURGATEWAY"
6. Modify /etc/resolv.conf to point to your nameservers.

So basically you can get this working without ndiswrapper.  The module I believe you need is rt2570, and I think it was available without needing to install any packages. 

This is the only way I can get it to work.  Using the network manager applet by default does not work at all.  When I attempt to configure it it spins for 60 seconds then times out.  The log files show me it is attempting to use wpa supplicatant, which does not make any sense to me because I am using WEP.  If I use the gnome network admin utilty, my whole system freezes up every time.  I have tried removing all interfaces from /etc/network/interfaces except lo but this does not resolve the network manager problem.  It also seems the eth0 interface comes up no matter what.  I have it disabled in gnome network manager, and I turned off the network manager applet, and I removed it from /etc/network/interfaces.  I cannot figure out why eth0 is still coming up.

Does anybody know why network manager does not work at all, or why the gnome network manager freezes up the system?  It would also be nice to know why removing those interfaces from /etc/network/interfaces does not actually remove them from being enabled.  How do you disable interfaces for good?  It seems like something is running in the background that keeps enabling the interface.

---

### Post by cesiel1993 on 2006-10-14
Thanks for the replies, I'll try them out tomorrow, to tierd.

---

### Post by AlanRogers on 2006-10-23
All

I'm far to much of a newbie on Linux (48 hours in) to offer any real advice here but I think what I have to say may help someone post a real fix.

I have a DWL-G22 Rev B USB WiFi dongle and loaded Ubuntu 6.06 Desktop CD, which failed completely to run it. However, Kubuntu 6.06 Desktop ran it fine - that's the version that runs from the CD!

So my question is: What's different? I don't know near enough to tear them apart and look but no doubt someone here can.

FWIW, I'm now running Ubuntu using the standard NIC and a wireless access point configured as client.

Alan

---

### Post by AlanRogers on 2006-10-27
Okay, progress, of a fashion. When reading this, please bear in mind my very recent exposure to *nix, having been hiding behind Windows for the last too long! I couldn't get any of the suggested methods to install drivers for the DWL-G122 Rev B to work for me.](*,) That's not to say that they don't work - I just couldn't do it with what little knowledge and understanding I have acquired so far. :oops:

As reported above, Kubuntu runs this piece of hardware straight out of the gate so what I've done is this:
[LIST=1]
[*]Install Kubuntu 6.06 from the Alternate ISO
[*]Configure the USB DWL-G122 Rev B to connect to my WLAN using Wireless Assistant
[*]Install Gnome Desktop and uninstall KDE Desktop using Package Manager
[*]Install Evolution to replace Kontact
[*]Install Firefox to replace Konqueror
[*]...etc - making it look more like Ubuntu
[/LIST]
When I get back this evening (I left the update running when I went to work) I'll see how successful this has been.

The key element for me appears to have been the inclusion in Kububtu of Wireless Assistant which works far better with this particular USB dongle than Ubuntu's Network utility under System. Does anyone know what this is called and whether it can be installed on Ubuntu?

I hope this helps someone - I've taken a lot from here already and it's time to start giving back what little I can. :D In another thread, I'll be asking how to create an install CD from my customised configuration, so I don't have to go through this pain again. ;)

Alan

---

### Post by AlanRogers on 2006-10-30
FWIW, installing the features of Ubuntu (Gnome, Firefox, etc) trashed the wifi connection irretrievably, in spite of Wireless Assistant still being available. :mad: 

If it works in Kubuntu, there has to be an easier way than compiling the drivers manually. Any experts out there feel free to chime in as soon as you like! ](*,) 

Alan

---

### Post by AlanRogers on 2006-10-31
Update: Installing any Gnome software in Kubuntu trashes the connection too. I'm going to try upgrading to Edgy this evening and see if that changes anything.

It would be really nice to see some acknowledge from anyone more knowledgable though, if only to tell me that I'm off chasing smoke.

---

