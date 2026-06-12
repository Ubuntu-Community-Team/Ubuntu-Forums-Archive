---
title: "wireless connection shell script"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by demoric on 2008-02-16
I have found that I have to manually configure my wireless connection(s) and wanted to write a shell script to handle it.  I am a newly LINUX converted person so my scripts will lack alot (I am used to windows batch scripting)

I am needing to know how to tell which network card the system is using.  I've noticed it recognizes my card as either wlan0 or eth1 and it isn't consistent on which one.
So i need something like[I]
if exists eth1 then ncard="eth1"
if exists wlan0 then ncard="wlan0"[/I]

Sorry for the generic code, but I'm wanting to learn the actual commands.

Here's the script so far:
```
#!/bin/sh
# Wireless Network Connection Script
# Copyright 2008 Joshua D. Meadows <themeadowsfamily[AT]sbcglobal.net>
# GNU Public License
lshw -C network
#sleep 10

#!/bin/bash
echo -n "Please enter network cards logical name: "
read nCard
echo -n "Please enter network essid (Network Name): "
read nName
echo -n "Please enter network key: "
read nKey

sudo ifconfig ${nCard} down
sudo dhclient -r ${nCard}
sudo ifconfig ${nCard} up
sudo iwconfig ${nCard} essid ${nName}
sudo iwconfig ${nCard} key ${nKey}
sudo iwconfig ${nCard} key open
sudo iwconfig ${nCard} mode Managed
sudo dhclient ${nCard}

read
exit 0
```

---

### Post by Speedoo on 2008-02-17
I actually know less about shell scripting than you appear to, but the command to see which wireless extension is in use is "iwconfig".  Not sure how you'd incorporate the results into a script, though.  Hope this answers what you're asking!

---

### Post by Joe of loath on 2008-02-17
i don't know if it's of use to you, but my dad and i adapted a script i found on the internet so i could connect to my WPA network, and set it to startup. as far as i know it works.

---

### Post by pbahumanyam on 2008-05-27
I was struggling to get my Dell Vostro 1500 ( standard configuration ), running ubuntu hardy, to connect to motorola router WR850G, with Network Manager, and wicd, no luck.

I stumbled on this script, boy, am I happy to announce I am able to connect.
I prefer scripts to GUIs, any way.

lshw -C network on my laptop shows        # for your reference given below
[INDENT]
 lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:04:7a:6c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. ip=192.168.10.4 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g[/INDENT]

forget about Network Manager or wicd, when you are trying to connect BCM4310 (Broadcom card ) to the router.

By the way, eth1 is the ethernet port, and wlan0 is wireless port, and you did right by setting nCard to wlan0

We need more demorics in this forum.
u and ubuntu rock.

---

