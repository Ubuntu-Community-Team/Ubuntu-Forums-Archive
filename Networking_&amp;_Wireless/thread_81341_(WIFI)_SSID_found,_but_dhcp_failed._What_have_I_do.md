---
title: "(WIFI) SSID found, but dhcp failed. What have I done wrong?"
date: 2005-10-24
forum: Networking &amp; Wireless
---

### Post by jbodell on 2005-10-24
Hi there,
I've installed a pci wifi card (broadcom chipset) using ndiswrapper. I followed all the steps in the great howto: [http://www.ubuntuforums.org/showthread.php?t=25683&highlight=wireless+broadcom]("http://www.ubuntuforums.org/showthread.php?t=25683&highlight=wireless+broadcom")

The lights on the card are on, and when using gtkwifi or wifi-radar i can see a couple of networks, one of which is the one i need to connect to. I assume from this that the card is actually working. There is no security set on the router yet until i can connect to it. When choosing the network, dhcp fails and nothing goes in or out. I'm hoping I've overlooked something very simple. Anyone got any ideas? Any help would be appreciated! Cheers

---

### Post by ibanez88 on 2005-10-24
Try setting in your /etc/network/interfaces:

wireless-key restricted [key]

replacing [key] with your actual key.

---

### Post by ibanez88 on 2005-10-24
If that doesn't work, post the relevant entries in your interfaces file and also some details about the network you are trying to connect to (WEP or WPA, 128 bit, hidden essid, etc.).

---

### Post by jbodell on 2005-10-24
Hi ibanez88, thanks for your help. I've edited my /etc/network/interfaces as you said. Using gtkwifi i have to enter the key when i try to connect to the HouseWifi network. It still says dhcp failed. I've posted the interfaces file below, hopefully you can spot my mistakes. Its a 64-bit WEP, the actual key is the one in the interface file below. The ESSID is being broadcasted. The router is a 3com officeConnect and the wifi card is a Belkin f5d7000. Thanks

> # This file describes the network interfaces available on your system
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

iface wlan0 inet dhcp
wireless-essid HouseWifi
wireless-key restricted 230E28B919

Cheers for taking a look.

---

### Post by ibanez88 on 2005-10-24
OK no problem, although I don't want to provide you with a false sense of security in my abilities.  I still have lots more questions than answers when it comes to Linux.  ;) 

You don't need "restricted" in your wireless-key line if you are using a broadcast, 64-bit connection.  Upon re-reading your first post more carefully I see that I missed that.  Sorry.

Unfortunately also I'm not familiar with setting up a wlan device, or how it might relate to eth0 in your interfaces file.  I hope that someone who has experience with your card will be able to help you further there.  (I just use eth0 - different cards require different setups as you know).

What I can suggest is maybe becoming familiar with the command-line tools, often times they can provide a little more info about what is happening.

What happens if you type
sudo ifup wlan0

---

### Post by jbodell on 2005-10-24
All help appreciated on this one.  

Output of ifUp is:
$>ifup: interface wlan0 already configured,


Cheers.

---

### Post by quis on 2006-03-21
Did anyone get a solution to this? Mine is doing the exact same thing.

The card seemed to work out of the box, I can scan for SSIDs using iwlist, assign one to the card using iwconfig and do the same using the networking applet built into Ubuntu (5.10). However when I tell the applet to configure the card using DHCP it does its progress bar thing for a while, and then then seems to have worked. However, pinging my router (or any other machines inside/outside the LAN) doesn't work, and no IP address shows up running ifconfig. Assinging the card a manual IP address is also fruitless.

Any ideas? Config files I can post that would help? Card is a Belkin F5D7000 PCI card, version 3000uk.

---

