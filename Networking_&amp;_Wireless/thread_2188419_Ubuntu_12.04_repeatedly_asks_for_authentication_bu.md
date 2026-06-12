---
title: "Ubuntu 12.04 repeatedly asks for authentication but will not connect to wifi"
date: 2013-11-17
forum: Networking &amp; Wireless
---

### Post by elo96 on 2013-11-17
I'm running Ubuntu 12.04 and have been connecting to my wifi using a Netgear WNDA3100 USB adapter. A couple of days ago, ubuntu started repeatedly asking for the wifi password and would not connect. I've uninstalled and reinstalled the adapter drivers and tried deleting the network and reconnecting, but no joy. Could anyone give me advice on how I can investigate and solve this? I'm not sure what information would be useful, but please let me know and I'll provide it.

---

### Post by Bucky Ball on 2013-11-17
Firstly, what adapter drivers are you installing for it? Did you try just plugging it in without installing anything?

Secondly, with the dongle plugged in, give the output of this:

```
sudo lshw -C network
```

See post #2 here:

[http://ubuntuforums.org/showthread.php?t=1806839](http://ubuntuforums.org/showthread.php?t=1806839)

and follow the thread.

---

### Post by elo96 on 2013-11-18
> **Bucky Ball said:**
> Firstly, what adapter drivers are you installing for it? Did you try just plugging it in without installing anything?


I installed ndiswrapper and bcmn43xx64 and have had working wireless for some time.

> **Bucky Ball said:**
> 

Secondly, with the dongle plugged in, give the output of this:

```
sudo lshw -C network
```


```

  *-network               
      description: Ethernet interface
      product: RTL-8139/8139C/8139C+
      vendor: Realtek Semiconductor Co., Ltd.
      physical id: 5
      bus info: pci@0000:02:05.0
      logical name: eth0
      version: 10
      serial: 00:19:21:3c:9a:e8
      size: 10Mbit/s
      capacity: 100Mbit/s
      width: 32 bits
      clock: 33MHz
      capabilities: pm bus_master cap_list ethernet physical tp mii 10bt10bt-fd 100bt 100bt-fd autonegotiation
      configuration: autonegotiation=on broadcast=yes driver=8139toodriverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32multicast=yes port=MII speed=10Mbit/s
      resources: irq:20 ioport:e800(size=256) memory:febffc00-febffcff
 *-network
      description: Wireless interface
      physical id: 1
      logical name: wlan0
      serial: e0:91:f5:55:42:41
      capabilities: ethernet physical wireless
      configuration: broadcast=yes driver=ndiswrapper+bcmn43xx32driverversion=1.58+,08/26/2009, 5.10.79.30 link=no multicast=yes wireless=IEEE802.11g
```


> **Bucky Ball said:**
> 
See post #2 here:

[http://ubuntuforums.org/showthread.php?t=1806839](http://ubuntuforums.org/showthread.php?t=1806839)

and follow the thread.

Output of lsusb is 
```
Bus 001 Device 002: ID 0846:9011 NetGear,Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]Bus 001 Device 004: ID 0bda:0111 RealtekSemiconductor Corp. Card Reader
Bus 003 Device 002: ID 046d:c52e Logitech,Inc.
Bus 001 Device 001: ID 1d6b:0002 LinuxFoundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 LinuxFoundation 1.1 root hub
```

I don't know if this result points to conflicting drivers though.

---

### Post by elo96 on 2013-11-19
A bit more information. iwconfig wlan0 returns
```

iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:"NetworkName"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: **:**:**:**:**:**   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

