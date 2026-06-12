---
title: "Getting Ubuntu to remember my network settings!!"
date: 2005-10-11
forum: Networking &amp; Wireless
---

### Post by andy_sp1ke on 2005-10-11
hi

I have been happily running ubuntu since warty on a number of machines, I had some problems with a laptop and wireless for a bit but a DlinkDWL G650+ PCMCIA card fixed that (think its that card, if anyone wants to confirm that then ask and i will have a look at my old ebay advert from when i sold the laptop!). I recently decided to add the ubuntu pc in our study to the wireless network to get rid of cabling. Well i looked around a bought a card.....it didnt work despite some sucess on the Wiki pages. I got another that should have worked and I got it online for ten seconds then i never managed it again! So i got a netgear WG311 v2 PCI card. WIki says it works out of the box and they didnt lie. Setup picked it up (hoary) but then it just kept forgetting itself!! it stayed online for an hour at one point and fully updated hoary but then firefox could not browse and i havent succeeded ingetting it browsing again. I repeatadly reset it with ifup and ifdown, i can mostly ping my adsl modem but still not internet. I have decided to try updating to breezy and see if that helps. I have plugged in a cable to the modem and its happily updating.

DOes anyone have any suggestions? etc/network/interfaces currently contains this (when the wlan0 is up it says wlan0 auto). OI have tried manually entering data aswell as using the nwtwork wizard?

------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface wlan0 inet static
address 10.0.0.6
netmask 255.255.255.0
gateway 10.0.0.2

auto eth0

--------------------------------------------------


thanks

andy

---

### Post by mlomker on 2005-10-11
My experience has been that putting the laptop to sleep or hotplugging the card causes 'weird things' to happen.  If you treat your laptop like a desktop (power it down and have the card inserted when you turn it on) then you'll probably have a lot less trouble.

I'm not sure where to begin with helping you troubleshoot because I don't know what driver your card uses.  Perhaps look in dmesg the next time that it works?

```

dmesg | grep wlan

```

You should add wlan0 to the 'auto' line:

```

sudo nano /etc/network/interfaces

```

Ctrl-W, Y, Enter to save.

---

