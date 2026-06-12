---
title: "help with my wireless please"
date: 2008-05-20
forum: Networking &amp; Wireless
---

### Post by balagosa on 2008-05-20
WiFi dead when i tried to install WICD

before the installation i had an effective wireless network via ndiswrapper.

my "lspci" ```

02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

```

my "lshw -C network" ```

*-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:c6:53:a8:07
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.0.14 latency=0 module=r8169 multicast=yes

```

There is also something that i noticed. Under my Restricted Hardware Drivers were written:
1) Atheros Hardware Access Layer (Not in Use) (Disabled)
2) Support for 802.11 wireless LAN cards (Not in Use) (Enabled)

*** My "lshw" noted UNCLAIMED so i know it isnt installed.
*** I have the appropiate driver for my Card which is net5211.inf, for Atheros 5007/5006

*** I followed this guy's guid for 64bit. [guide]("http://ubuntuforums.org/showthread.php?t=512828"). my uname -m had an output of "i686".

/* I will update more info when i get some*/

---

### Post by chili555 on 2008-05-20
> Atheros Hardware Access Layer (Not in Use) (Disabled)Can you check the little box and enable it? Does your wireless become claimed?

Network Manager, which is installed by default, will not allow a wireless connection as long as you have a good, working IP adress on your wired interface, which you do:> ip=192.168.0.14[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

I recommend getting the Atheros HAL driver enabled; detach the wire; and see if your wireless comes to life.

---

### Post by balagosa on 2008-05-20
be back with your results.

i read previous guides though that i am supposed to disable the "HAL"


...............................


nope, still not recognized. doing more searches on forums

---

### Post by chili555 on 2008-05-20
> **balagosa said:**
> be back with your results.

i read previous guides though that i am supposed to disable the "HAL"


...............................


nope, still not recognized. doing more searches on forumsI only get one crack at it before you go back to forum searches? Sorry I couldn't be more helpful.

---

### Post by balagosa on 2008-05-20
err...it is not that.

it is just that i prefer to do research than just be lazy and wait for answers XD :)

My Mind Thinking = Healthy....My Mind Resting and Waiting = rotting

but suggestions are open though.

---

### Post by chili555 on 2008-05-20
When you detach the wire and do:```
sudo ifdown eth0
sudo modprobe ath_pci
sudo iwconfig ath0 essid <ur_router_essid>
sudo dhclient ath0
```Do you get a hopeful result?

---

### Post by balagosa on 2008-05-20
```
sudo ifdown eth0
```
ifdown: interface eth0 not configured

```
sudo modprobe ath_pci
```
WARNING: /etc/modprobe.d/blacklist line 42: ignoring bad line starting with 'blacklsit'

```
sudo iwconfig ath0 essid <ur_router_essid>
```
*freezes my laptop*

```
sudo dhclient ath0
```
*freezes my laptop*



..........................

going to sleep, be in touch with you tomorrow. appreciate the help

---

### Post by balagosa on 2008-05-21
*bump*

---

