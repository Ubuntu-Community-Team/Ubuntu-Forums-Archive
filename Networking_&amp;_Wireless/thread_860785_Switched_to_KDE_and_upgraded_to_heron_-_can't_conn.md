---
title: "Switched to KDE and upgraded to heron - can't connect wired/wireless anymore"
date: 2008-07-15
forum: Networking &amp; Wireless
---

### Post by Heide264 on 2008-07-15
I had a rough time connecting with gnome originally, but after a lot of messing with it I finally got both the wireless and wired connection to work flawlessly.

However, I recently switched to KDE from gnome. The internet connection was still working and functioning normal. I figured I would try upgrading to Heron (didn't work with my nvidia driver on gnome before - I think it was messing with compiz stuff). Now I can't connect through either of my devices.

My /etc/network/interfaces is still the same and looks correct and set up with my static IPS. My lshw -C network looks kindof funny though. I'm not sure if it cleared my wireless drivers or what it did. 

lshw -c network:
*-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:a6:e4:d2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.19 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:17:31:e4:f1:67
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.129 multicast=yes wireless=IEEE 802.11g
 

I am really at a loss without knowing how to connect hardwire. I tried what I did to get it to connect through gnome using the interfaces file, but that is all in place this time around.

Any help would be awesome =).

---

### Post by Heide264 on 2008-07-16
After reading around some more, I thought it would help to tell you that network manager isn't even seeing any devices. It is just saying no connected device.

---

### Post by Heide264 on 2008-07-18
Any thoughts? I've read around but can't seem to find anybody who is in the same boat as myself. When I use ipdown or anything it complains of a missing main file =(.

---

### Post by jwferk on 2008-07-18
I had the same problem although I can my (netgear wireless; atheros) card gets a signal.  I still haven't figured out what is going wrong as the card works fine if I boot into Windows.

That being said, you might try the steps shown here.  At least this can get your OS to recognize your card.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

