---
title: "Fresh Lubuntu Instal - Ethernet works but Wifi is greyed out and wont initiate"
date: 2018-08-14
forum: Networking &amp; Wireless
---

### Post by nerddex on 2018-08-14
I have limited experience  with Linux so any instructions would need to be as detailed as possible.
Keep in mind I'm plugged into ethernet to post readout so *-network:1 DISABLED . 
Thanks for the help.

[HTML]rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no[/HTML]


[HTML]lshw -c network
 *-network:0               
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 03
       serial: 00:0e:a6:e2:37:90
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.137 duplex=full firmware=5788-v3.03 ip=192.168.0.18 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:4 memory:ff9f0000-ff9fffff
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlp2s2
       version: 05
       serial: 00:0e:35:25:15:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11
       resources: irq:4 memory:ff9ee000-ff9eefff


[/HTML]

---

### Post by wildmanne39 on 2018-08-14
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by nerddex on 2018-08-15
Here is the Pastebin for more info.
[http://paste.ubuntu.com/p/FmdH36W4WF/](http://paste.ubuntu.com/p/FmdH36W4WF/)

somehow I messed things up trying to follow a guide. :/

---

### Post by chili555 on 2018-08-15
> somehow I messed things up trying to follow a guide. :/Let's revert those changes and start fresh. Please open a terminal and do:```
sudo nano /etc/network/interfaces
```Comment out the lines you added, like this:```
auto lo eth0
iface lo inet loopback

#auto wlp2s2
#iface wlp2s2 inet dhcp
#pre-up wpa_supplicant -Bw -Dwext -i wlp2s2 -c/etc/wpa_supplicant.conf
```Save (Ctrl+o followed by Enter) and close (Ctrl+x) the text editor.

Reboot and tell us if there is any improvement.

We may or may not need to address this later:> ipw2200: Firmware error detected.  Restarting. (repeated 13 times)

-----------

Note to Chili: Auto b/g/n ??  ESSID:"Dino's place" 88/100 TKIP

---

### Post by nerddex on 2018-08-15
awesome thank you! Looks like the error is gone too.

[http://paste.ubuntu.com/p/dsS8DxCMWH/](http://paste.ubuntu.com/p/dsS8DxCMWH/)

---

### Post by chili555 on 2018-08-15
Looks like you are all set. Please use thread tools at the top of the thread to mark Solved.

---

