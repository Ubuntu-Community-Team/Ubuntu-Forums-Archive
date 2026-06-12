---
title: "D-Link Airplus G+ (DWL-G650+) problems"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by Humle on 2006-08-30
I can't get my G650+ wireless cared to working..! 
Some one there can help me?

---

### Post by kb3hkg on 2006-08-30
what have you tried so far?

---

### Post by Humle on 2006-08-30
I have installed NetworkManager and tried to connect to the wireless net.

---

### Post by tturrisi on 2006-08-30
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by kb3hkg on 2006-08-30
make sure you have madwifi installed, unless D-Link changed something since I bought my card the G650 and G650+ should use the atheros chipset.

---

### Post by whiteguysamurai on 2006-08-30
[http://www.ubuntuforums.org/showthread.php?t=247287&highlight=atheros](http://www.ubuntuforums.org/showthread.php?t=247287&highlight=atheros)

Check out what i wrote.;)

---

### Post by Humle on 2006-08-30
I have installed adwifi. But it still doesn't work.

---

### Post by TrIde2188 on 2006-08-30
Yea i have the smae problem... well i havnet installed madwifi i dont get it (im new to linux) any help would be very helpful i think humle would agree with me on that one :P

---

### Post by Humle on 2006-08-31
I agree....!!!!!

---

### Post by TrIde2188 on 2006-08-31
Nudge Nudge!! 

:)
if we could get a quick walktrhough:P
iwas up most of yest and till l.ike 5this morning searching and on this forum trying to find walkthroughs/ help lol

---

### Post by tturrisi on 2006-08-31
see the link I posetd above.  Use the commands in the reference & post the results here.

---

### Post by Humle on 2006-08-31
humle@humle-laptop:~$ sudo lshw -'class' network
  *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@00:12.0
       logical name: eth0
       version: 74
       serial: 00:03:0d:06:b8:9f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=via-rhine driverversion=1.2.0-2.6 duplex=full ip=192.168.1.12 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:d400-d4ff iomemory:dffff600-dffff6ff irq:11
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 2
       bus info: pci@02:00.0
       logical name: wlan0
       version: 00
       serial: 00:11:95:15:2d:28
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:32020000-32021fff iomemory:32000000-3201ffff irq:3

---

### Post by tturrisi on 2006-08-31
Your card does NOT have an atheros chipset, it has an acx111 chipset.  The ubuntu acx111 driver is buggy so you will have to build & make your own using these instructions:
[http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu](http://acx100.sourceforge.net/wiki/Distribution_list/Ubuntu)

---

### Post by Humle on 2006-09-02
I can't get the “FwRad16.bin_1.2.1” installed in /lib/firmware because I don't have access to root....

---

### Post by BenTyreman on 2006-09-03
I have the same card as this, and all I had to do was change the firmware that the standard acx111 module uses by adding ```
options acx firmware_ver=1.2.1.34
``` to ```
/etc/modprobe.d/options
```. Then, either reboot, or reinsert the acx111 module. Running these commands should achieve all of that: ```
sudo -s
echo "options acx firmware_ver=1.2.1.34" >> /etc/modprobe.d/options
modprobe -rv acx111
modprobe -v acx111
exit
```

---

### Post by Humle on 2006-09-03
root@humle-laptop:~# echo "options acx firmware_ver=1.2.1.34" >> /etc/modprobe.d/options
root@humle-laptop:~# modprobe -rv acx111
FATAL: Module acx111 not found.
root@humle-laptop:~# modprobe -v acx111
FATAL: Module acx111 not found.
root@humle-laptop:~# exit

---

### Post by BenTyreman on 2006-09-03
Sorry, got the module name wrong. It's just called acx, not acx111. ```
sudo modprobe -rv acx
sudo modprobe -v acx
```
will reload the acx module, else rebooting will have the same effect.

---

### Post by Humle on 2006-09-03
Thanks now it works..! :D

---

