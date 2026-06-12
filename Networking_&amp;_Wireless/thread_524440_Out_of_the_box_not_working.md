---
title: "Out of the box not working"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by iAndrew on 2007-08-13
Hi, I checked the stickied thread:

I have a Netgear WG511 v1 Wireless PCI card. I put it in my laptop, running xubuntu feisty. I don't know where to look for it. There is no network manager visible.

Any thoughts or ideas?

---

### Post by noob12 on 2007-08-13
Please post the output from these commands:
```

uname -r

lspci -nn

sudo lshw -C network

cat /etc/network/interfaces

```

You mention both Ubuntu and Xubuntu in your signature.   Which are you running in this case?

Assuming for the moment, we start with Ubuntu (regular/GNOME), please show us these:
```

aptitude show network-manager network-manager-gnome | grep State

ps -ef | grep -e '(NetworkManager|nm-applet)'

```

---

### Post by iAndrew on 2007-08-13
I'm using Xubuntu on my laptop. Which is what I'm trying to get the network card working for. i'll try to make that more obvious.

---

### Post by ugm6hr on 2007-08-13
> **iAndrew said:**
> I'm using Xubuntu on my laptop. Which is what I'm trying to get the network card working for. i'll try to make that more obvious.

```
lspci -nn | grep Network
lspci -nn | grep Ethernet
lshw -C network
```
Just paste the output from those here.  I think your card is *Intersil Corporation Intersil ISL3890 Prism GT/Prism Duette (rev 01)*, which has previously been well supported, but I think the prism54pci driver doesn't seem to work for everyone any more.

---

### Post by iAndrew on 2007-08-21
```
andrew@INSPIRON:~$ lspci -nn | grep Network
03:00.0 Network controller [0280]: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] [1260:3890] (rev 01)
andrew@INSPIRON:~$ lspci -nn | grep Ethernet
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
andrew@INSPIRON:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 01
       serial: 00:11:43:64:a2:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 latency=32 multicast=yes
       resources: iomemory:fcffe000-fcffffff irq:7
  *-network
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:09:5b:45:f2:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=prism54pci latency=64 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f8000000-f8001fff irq:11
andrew@INSPIRON:~$ 

```

Sorry for the late reply, just start school again.

---

