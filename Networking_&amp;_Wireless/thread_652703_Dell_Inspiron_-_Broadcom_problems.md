---
title: "Dell Inspiron - Broadcom problems"
date: 2007-12-29
forum: Networking &amp; Wireless
---

### Post by Evil Robot on 2007-12-29
Okay, I'm trying to install Xubuntu Gutsy on a friend's laptop with a broken Windows installation. Here are the specs:

Dell Inspiron 1000
2.2 GHz Celeron
256 MB RAM
30 GB hard drive
Some **** integrated video card that seems to play okay with X
Dell TrueMobile 1300 wireless PC Card (on the back it says Broadcom BCM94306CBSG)

So I boot the Xubuntu live CD, but, before I wipe her drive, I want to know that I'm going to be able to get the wireless card working, as this is a make or break feature on most laptops. Trying to connect to my WEP-enabled SSID-hidden (yeah, I know) wireless network doesn't work, and iwconfig claims that the card doesn't support scanning. Old versions of Ubuntu apparently required manual installation of ndiswrapper to get it working, according to my Googling. I can't find up-to-date information on what to do with this card - sometimes it is claimed that I will have to go the manual route and sometimes people say I can use the Restricted Drivers Manager. The Xubuntu live CD doesn't show the Restricted Drivers Manager - does the full install have it (I've only used Ubuntu, never Xubuntu before).

Network Manager doesn't show any networks, whereas Network Manager on the same Xubuntu live CD running on my Latitude laptop (with a more compatible wifi card) shows a bunch of other nearby networks.

What should I do to get it working? Any advice? Thanks!

---

### Post by mellowd on 2007-12-29
could you open the terminal and type this:

```
ifconfig
```

paste the results here please.

---

### Post by Evil Robot on 2007-12-29
eth1, which is wireless, doesn't show up if I just do ifconfig. I have to do ifconfig -a.

```

ubuntu@ubuntu:~$ ifconfig -a
...eth0...
eth1        Link encap:Ethernet HWaddr 00:10:C6:44:3F:24
            BROADCAST MULTICAST MTU: 1500 Metric: 1
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:0 (0.0b) TX bytes: 0 (0.0b)
            Interrupt: 16 Base address: 0x8000
...loopback...

```

---

### Post by kevdog on 2007-12-29
Please post

lshw -C network

---

### Post by Evil Robot on 2007-12-29
```

ubuntu@ubuntu:~$ sudo lshw -C network
...wired Ethernet stuff...
*-network
  description: 802.11b CardBus
  vendor: Broadcom
  physical id: 0
  version: 8.0
  slot: Socket 0
  resources: irq: 16
*-network DISABLED
  description: Wireless interface
  product: BCM4306 802.11b/g Wireless LAN Controller
  vendor: Broadcom Corporation
  physical id: 0
  bus info: pci@0000:02:00.0
  logical name: eth1
  version: 02
  serial: 00:10:c6:44:3f:24
  width: 32 bits
  clock: 33Mhz
  capabilities: bus_master ethernet physical wireless
  configuration: broadcast=yes driver=bcm43xx driversversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

```

---

### Post by kevdog on 2007-12-29
Do you want to use the bcm43xx driver or ndiswrapper??  I always (as of the year 2007) suggest ndiswrapper due to driver stability, however it is much more problematic to initially setup.  With ndiswrapper you are going to have to locate a windows driver (specifically the bcmwl5.inf and bcmwl5.sys files).

---

### Post by Evil Robot on 2007-12-29
> **kevdog said:**
> Do you want to use the bcm43xx driver or ndiswrapper??  I always (as of the year 2007) suggest ndiswrapper due to driver stability, however it is much more problematic to initially setup.  With ndiswrapper you are going to have to locate a windows driver (specifically the bcmwl5.inf and bcmwl5.sys files).

How does that work? I've never set up ndiswrapper.

---

### Post by Ptero-4 on 2007-12-29
You basically take the .sys and .inf files kevdog showed and put them in a folder anywhere in your ubuntu HD (I prefer /etc), then you go to System>Administration>Windows Wireless Drivers, locate and add the .inf file from there, then (if needed) blacklist the bcm43xx module in /etc/modprobe.d/blacklist, then type ndiswrapper -l, then sudo depmod -a, ndiswrapper and finally add ndiswrapper to your /etc/modules so it loads on every boot.

---

### Post by kevdog on 2007-12-29
The above summary was completely accurate, but brief.  Here is yet another explanation of what was presented above:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

