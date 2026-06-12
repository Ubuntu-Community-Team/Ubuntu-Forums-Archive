---
title: "Wireless Driver Slow"
date: 2016-10-31
forum: Networking &amp; Wireless
---

### Post by jgodfrey2 on 2016-10-31
Hi all, I am new to Ubuntu/Linux and am having some wireless driver issues.

I bought a usb WiFi adapter (PAU06) which uses the antiquated Ralink 5372 chipset. The native Ubuntu 16.04 driver (rt2800usb) does support this chipset, however my download speeds are exceptionally slow (between 500kbps and around 5mbps). The same WiFi adapter in my Windows laptop yields download speeds from 30-50mbps.

Because of this, I'm fairly certain that it is a driver issue, however it appears as if Ralink chipsets no longer receive driver updates / support. I am a half step away from trying ndswrapper to use the Windows drivers that were given by the sellers of the actual adapter, but I wanted to try and see if something else could work better.
Below I pasted some potentially relevant information. Any help is greatly appreciated!

```
josh@josh-desktop:~$ sudo lshw -class network
[sudo] password for josh: 
  *-network:0             
       description: Ethernet interface
       product: 82576 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0f0
       version: 01
       serial: 90:e2:ba:31:50:16
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.3.0-k firmware=1.2.1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:f7420000-f743ffff memory:f7000000-f73fffff ioport:d020(size=32) memory:f7444000-f7447fff memory:f6c00000-f6ffffff memory:f7448000-f7467fff memory:f7468000-f7487fff
  *-network:1
       description: Ethernet interface
       product: 82576 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       logical name: enp2s0f1
       version: 01
       serial: 90:e2:ba:31:50:17
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=5.3.0-k firmware=1.2.1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:18 memory:f7400000-f741ffff memory:f6800000-f6bfffff ioport:d000(size=32) memory:f7440000-f7443fff memory:f6400000-f67fffff memory:f7488000-f74a7fff memory:f74a8000-f74c7fff
  *-usb:0
       description: Wireless interface
       product: 802.11 n WLAN
       vendor: Ralink
       physical id: 2
       bus info: usb@3:2
       logical name: wlx9cefd5fff0b9
       version: 1.01
       serial: 9c:ef:d5:ff:f0:b9
       capabilities: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-45-generic firmware=0.29 ip=192.168.0.109 link=yes maxpower=450mA multicast=yes speed=480Mbit/s wireless=IEEE 802.11bgn
josh@josh-desktop:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05e3:0723 Genesys Logic, Inc. GL827L SD/MMC/MS Flash Card Reader
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04d9:1702 Holtek Semiconductor, Inc. Keyboard LKS02
Bus 003 Device 002: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
josh@josh-desktop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
josh@josh-desktop:~$
```



Also - I did post a very similar question / thread on askubuntu a couple of days ago. I will delete and or update either of the threads depending on responses!
Any help is greatly appreciated!

---

### Post by QIII on 2016-10-31
Hello!  Welcome to the Ubuntu Forums.

You can't delete your posts here.  Only the Forums Staff may close or move threads from public view.

If you would be so kind -- if you happen to get an answer at Ask Ubuntu, would you please complete this thread with the solution you receive so that the community here can learn?

Thanks, and best wishes.

---

### Post by jgodfrey2 on 2016-10-31
Absolutely!

---

### Post by jeremy31 on 2016-11-01
I would run ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot and see if disabling wifi power save helps any, if not see the wireless script link in my signature and post results

---

### Post by jgodfrey2 on 2016-11-01
Thanks Jeremy. I'll try that out when I'm back from work.

---

### Post by jgodfrey2 on 2016-11-01
> **jeremy31 said:**
> I would run ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot and see if disabling wifi power save helps any, if not see the wireless script link in my signature and post results 

I ran the script and no obvious errors were thrown (so I'm assuming it was successful in compiling). No change to the download speed issues. I then ran the script that made the .gz (txt) file and have attached it on this post.

Some strange / additional information: Not sure whether or not this is relevant in any way, but when I continuously do back to back download speed tests the ultimate download speed will be completely based off of the initial server response. In other words, if I run the test and the initial speed is listed as 2mbps, the ultimate dl speed does not significantly vary from that. In some cases, though, running a test immediately after would start at 6mbps and stay at 6mbps for the duration of the test. The ultimate dl speed seems to be entirely dependent on the initial dl speed. Just found that interesting / strange.

---

### Post by jeremy31 on 2016-11-02
Change your router to use channel 3 or 9 and use the following to set the country code
```

sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

---

### Post by jgodfrey2 on 2016-11-03
I'll try that out tonight - thanks again.
Wouldn't this indicate that the "airway" is crowded and not that there is a driver issue? Conversely, wouldn't that mean I would get replicable effects on my Windows laptop?

---

### Post by jeremy31 on 2016-11-03
Windows can handle crowded channels better than Linux for some reason

---

### Post by jgodfrey2 on 2016-11-04
It is still fairly jumpy, but that has significantly improved the minimum and maximum values for the download speeds. Do you think that Ubuntu will only be able to perform at its peak if there is only one router using the same channel?

---

