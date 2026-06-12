---
title: "Conecting to the internet (Wireless) [HELP]"
date: 2008-06-27
forum: Networking &amp; Wireless
---

### Post by elite_thut on 2008-06-27
Hi,
I just installed Ubuntu 8.04

Now, I'm trying to connect to the internet using my wireless network...but I can't. Everything I'm doing isn't working...

Doing a sudo lshw, this is what I get :
```
charleyb0y@Charleyb0y-Linux:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:06:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:06:0c.0
       logical name: eth0
       version: 13
       serial: 00:1a:92:b3:6e:64
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:fc:57:53:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

Could someone help me with this please !!

---

### Post by chili555 on 2008-06-27
> *-network DISABLEDIt appears that the wireless switch on your laptop is switched off, or wireless is disabled in the BIOS.

Please do, in a terminal:```
sudo cat /var/log/messages | grep switch
```

---

### Post by elite_thut on 2008-06-27
ok, first I'm not using a laptop...so it's not the switch that is turned off... and I did what you said ...

```
charleyb0y@Charleyb0y-Linux:~$ sudo cat /var/log/messages | grep switch
[sudo] password for charleyb0y: 
Jun 27 03:17:00 Charleyb0y-Linux kernel: [   25.792208] SMP alternatives: switching to UP code
Jun 27 03:17:00 Charleyb0y-Linux kernel: [   26.076429] SMP alternatives: switching to SMP code
Jun 27 11:38:07 Charleyb0y-Linux kernel: [   32.354214] SMP alternatives: switching to UP code
Jun 27 11:38:07 Charleyb0y-Linux kernel: [   32.638422] SMP alternatives: switching to SMP code
```

Now, what do I do ??:confused:


My wireless card is working perfectly on the same computer but under Windows XP (I dual boot with linux)...Why does Ubuntu says that it is disabled ?

---

### Post by chili555 on 2008-06-27
Do you have the firmware for your Broadcom installed?```
sudo apt-get install b43-fwcutter
```You will need to walk the laptop over to the router and get an ethernet connection in order to install.

---

### Post by elite_thut on 2008-06-27
I can't...as I said, this is not a laptop...

Any way of doing this by using a USB key or simply my hard drive to transfer the thing you wanted me to download from xp(working internet connection) to linux(not working) ?

---

### Post by elite_thut on 2008-06-27
I downloaded b43-fwcutter from windows xp, then transferred it to ubuntu...but I don't really know what to do with it ...

---

### Post by chili555 on 2008-06-27
Check here: [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754) and scroll down to this section:> Option 2
For those without a working internet connection

---

### Post by elite_thut on 2008-06-27
Ok...I did everything and now, I think it's getting better...but still not working.

Now, when doing a lshw -C network, I get :
```
charleyb0y@Charleyb0y-Linux:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:06:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:06:0c.0
       logical name: eth0
       version: 13
       serial: 00:1a:92:b3:6e:64
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:fc:57:53:59
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

But when I try to connect to the network, there is the little icon at the top right corner of my screen that tells me : "Waiting for network key for the wireless network 'XXXX XXXX'"

---

### Post by sstvinc2 on 2008-08-18
I've got the same card and the same problem.  I've even tried different encryptions and different Ubuntu distributions.  No dice.

I've been digging around for a couple of days, and something tells me that it's going to be something obscure like a boot parameter or adding a line to /etc/network/interfaces, but the hell if I know what to do.

---

### Post by sstvinc2 on 2008-08-18
Actually, I got mine to work if the network was unsecured.  Does this work for you also?  (You may not be in control of your network security, but I figure it's worth a shot.)

---

