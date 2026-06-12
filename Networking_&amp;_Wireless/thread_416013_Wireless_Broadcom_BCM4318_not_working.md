---
title: "Wireless Broadcom BCM4318 not working"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by groovomata on 2007-04-20
Hey folks, I just installed feisty and I'm having trouble getting my wireless card working. On my machine there's a little light for my wireless device -which isn't on; it's not listed as a Network Device on 'Network Tools'. 
When I do: sudo lshw
I get this:
 *-network:0 DISABLED
                description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@06:02.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:a1:f2:28
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20

When I do: sudo iwconfig
I get this:
eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

My wireless router ought to be working because I was just using it before I install feisty. 
My question is: how do I enable my wireless interface?
Thanks in advance,
Erik.

---

### Post by Greg2 on 2007-04-20
Have you installed the firmware?```
sudo apt-get install bcm43xx-fwcutter
```

---

### Post by groovomata on 2007-04-20
Okay, I solved it. If you have the Broadcom 4318 wireless device try this post. It worked like a charm:
[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)
Thanks,
Erik.

---

### Post by arron on 2007-04-20
firrmware with this card is SLOWER!  Use the NDIS wrapper:

use this command with the driver file to get the ndis wrapper:

```
sudo ndiswrapper -i bcmwl5.inf
```

then run these 2 commands (not sure why):

```
sudo ndiswrapper -l
sudo ndiswrapper -m
```

now you ned to blacklist the kernel module that does nto work, add "blacklist bcm43xx" in /etc/modprobe.d/blacklist, then add "ndiswrapper" to /etc/modules to load ndis wrapper on startup, reboot and see if the light comes on.

with the firmware on 6.10 and 7.04 and the .deb for 7.04 i got a max of 500-600k download off the local network, with the ndis wrapper a solid 2600-2700k.

---

