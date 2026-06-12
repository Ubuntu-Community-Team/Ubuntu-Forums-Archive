---
title: "Wireless Internet Connection Problem in 9.04?"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by marcelluspye on 2009-10-13
I am dual-booting Windows XP and Ubuntu 9.04 on my circa 2003 Dell Dimension 2350. If I run Windows, I can connect to my WEP-protected Wireless network. If I go onto my Netbook, which runs Ubuntu 8.04, I can connect. However, no matter what I do in Ubuntu 9.04 I cannot get it to connect. I have it set with the exact same network settings as the Netbook, but it will not connect. Every time it tries to connect and I enter in either of the two passwords (the first two WEP indexes) it only asks for the password again and again. I have tried everything I can think of as an experienced Windows User and a newbie Ubuntu User, and I can not get anything to work. What do I do?[IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by sandyd on 2009-10-13
on the computer that your having problems with, can you post the output of
```

iwconfig

```

---

### Post by nothingspecial on 2009-10-13
and ```
sudo lshw -C network
```

While you`re about it

---

### Post by HarrisonNapper on 2009-10-13
```
sudo apt-get install network-manager
``` that should help you out (hopefully)

---

### Post by marcelluspye on 2009-10-14
IWCONFIG:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"6Windmill"  Nickname:"6Windmill"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:9C:72:45:32   
          Bit Rate:11 Mb/s   Tx-Power:8 dBm   
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level=-61 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sudo lshw -C network:
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:08:74:c0:76:58
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=32 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:a3:8d:0e:aa:aa
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:f0:93:05
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-b

I have been using the network manager this whole time, but to be safe I ran the update command for it anyway. It was up-to-date.

---

