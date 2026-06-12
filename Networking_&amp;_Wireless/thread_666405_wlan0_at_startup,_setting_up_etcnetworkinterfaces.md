---
title: "wlan0 at startup, setting up /etc/network/interfaces"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by cocox on 2008-01-13
Hi there guys, 

im able to enable wireless conectivity on startup when only 'auto wlan0" is listed in /etc/network/interfaces but at the same time im not able to use the interface name (wlan0) with any command like iwconfig or ifup, ifdown...

otherwise, when i add "iface wlan0 inet dhcp", "wireless_essid router01", "wireless_key 's:wepascii'"  im not able to connect automaticly at startup but im able to use wlan0 with all commands like ifup etc... 

any idea how can i fix this??

:popcorn:

Im using Ubuntu 7.10 on a Inspiron 1420n

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto wlan0
# iface wlan0 inet dhcp
# wireless_essid pelimrouter01
# wireless_key "s:wepascii128bi"
```

```
cocox@dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0_rename  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"pelimrouter01"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:D1:37:EA:D0   
          Bit Rate=12 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=39/100  Signal level=-71 dBm  Noise level=-77 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
cocox@dell:~$ lsmod | egrep iwl
iwl3945                88168  0 
iwlwifi_mac80211      175112  1 iwl3945
cfg80211                7304  1 iwlwifi_mac80211

```


```
cocox@dell:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0_rename
       version: 02
       serial: 00:1c:bf:2e:51:3a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.243 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:f9:27:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 latency=0 module=tg3 multicast=yes

```

```

cocox@dell:~$ uname -a
Linux dell 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

```

---

