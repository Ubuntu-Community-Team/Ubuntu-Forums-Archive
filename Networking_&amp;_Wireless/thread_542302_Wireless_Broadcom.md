---
title: "Wireless Broadcom"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by Coward on 2007-09-03
Hello.

I'm trying to get wireless working on my hp dv6000z
Ubuntu recognizes that my network controller is Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 02) with lspci.

I have tried the post at the top and other random methods on google. Does anyone have any suggestions?

---

### Post by kevdog on 2007-09-03
Please see this link:
[http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated](http://www.linux-geek.org/index.php/2007/04/22/dell-1390-native-linux-driver-how-to-updated)

Good luck, if it doesnt work then its ndiswrapper

---

### Post by Coward on 2007-09-03
Thank you but I've already tried that one (I'd be willing to try it again if you really think it's my best option)

I currently have ndiswrapper installed from when I ran the installer.py from the post at the top. When I go to Administration > Windows Wireless Drivers it gives me a window with a box which says "Hardware Present: No". Does this mean ndiswrapper isn't going to work for me, or do I just need to find a different driver (if so, where)?

The terminal suggests I remove ndiswrapper when I begin following the instructions in the link you posted. That is why I have not continued to redo that set of instructions. I want to know whether people think I have a better chance with ndiswrapper or that link.

---

### Post by kevdog on 2007-09-03
Did you install ndiswrapper from source or from repository???  Do you have an ethernet connection (wired) on the computer??  Lastly do you have win xp drivers for your card.

Lastly post
lshw -C network

---

### Post by Coward on 2007-09-04
I installed ndiswrapper from the Synaptic Package Manager first, but I don't know if it was reinstalled when I ran the script in the post at the top of these forums.

I do have a working wired connection on this laptop. It worked without me having to do anything. I am actually posting from the laptop right now.

Where would I get the Win xp drivers for this card? It was built in to the laptop so I don't think I got a disk with the drivers on.

The results of lshw -C network are:
```

       description: Wireless interface
       product: Dell Wireless 1390 WLAN Mini-PCI Card
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:73:7f:63:5a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.47+Broadcom,10/12/2006, 4.100. latency=0 link=no multicast=yes wireless=IEEE 802.11g
       resources: iomemory:b6000000-b6003fff irq:21

```

---

### Post by kevdog on 2007-09-04
Ok your statement looks good as far as your wireless is installed -- you are using ndiswrapper 1.47 along with the winxp drivers.

Anyway you cant really run wired and wireless at the same time.  Your wired interface is probably eth0 and your wireless (per what you posted) is wlan0.  

Please disable any WEP/WPA/MacFiltering on your router -- we can add this later.

Then bring down the wired interface:
sudo ifconfig eth0 down

Bring up the wireless interface
sudo ifconfig wlan0 up

And then attempt to connect to your router via the following:
sudo iwconfig wlan0 essid <Network_ESSID_IN_QUOTES>
sudo iwconfig wlan0 mode managed
sudo dhclient wlan0

You might just for reference post your 
/etc/iftab
/etc/network/interfaces
files.

Make sure in /etc/modprobe.d/blacklist there is a line somewhere in the file that states:
blacklist bcm43xx

And also make sure that the ndiswrapper module is loaded at boot by making sure that this line appears somewhere in the /etc/modules file:
ndiswrapper

---

### Post by Coward on 2007-09-05
Wow, that was a thorough response. Well, I checked the files and they all had the line you said I should have- multiple times from my multiple attempts to get this working. I edited them so they only had it once and restarted. I had already disabled the WPA on my router.

I know that you are right about wlan0 being my wireless network and eth0 being my wired from some of the methods I tried on google. Even still, I am writing to you over the wired connection. Instead of trying to explain what went wrong, here is the text of the terminal:

```

jake@jake-laptop:~$ sudo ifconfig eth0 down
jake@jake-laptop:~$ sudo ifconfig wlan0 up
jake@jake-laptop:~$ iwconfig wlan0 essid <edited: I put the name here>
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
jake@jake-laptop:~$ sudo iwconfig wlan0 essid <edited: Again, I put the name>
jake@jake-laptop:~$ sudo iwconfig wlan0 mode managed
jake@jake-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1a:73:7f:63:5a
Sending on   LPF/wlan0/00:1a:73:7f:63:5a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
jake@jake-laptop:~$ sudo ifconfig wlan0 down
jake@jake-laptop:~$ sudo ifconfig eth0 up

```

Does this mean that my wireless router is the problem? I haven't tested it with another laptop, but I could get my parents to bring home their windows laptops to see if they work here.

---

### Post by Coward on 2007-09-05
Here are the reference files you suggested I post.

This is /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:1b:24:7c:a1:76 arp 1
eth1 mac 00:00:00:1a:73:7f arp 1

This is /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by kevdog on 2007-09-05
A few things, you cant use wired and wireless at the same time (without some special configurations options).

For your /etc/iftab file

put a # in front of every line and save the file.

Back up you /etc/network/interfaces files and then edit it and remove all the lines except those containing lo, eth0, wlan0.  You are not using all the other interfaces (at least from what you have posted) so you can delete them.

Try bringing up the wireless network after a reboot and with the wired cable unplugged.

---

### Post by Coward on 2007-09-13
I still haven't got wireless working on this laptop. I was able to connect using a different laptop with windows so I know the router is setup correctly.

I completely removed bcmxx43-firmware and bcmxx43-fwcutter using synaptic in case that was causing trouble. No luck.

Anyone have any ideas?

---

### Post by adamos on 2007-10-11
did you get it working yet?

i figured out my hp dv6000z with 4328 broadcom

---

### Post by adamos on 2007-10-11
did you get it working yet?

i figured out my hp dv6000z and 4328 broadcom chipset

---

