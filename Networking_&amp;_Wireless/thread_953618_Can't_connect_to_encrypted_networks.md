---
title: "Can't connect to encrypted networks"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by flipflopper81 on 2008-10-20
Hi,

I just got a new eee pc and it's really cool.  I put ubuntu eee on it, but I am unable to connect to encrypted networks. In XP it works fine, just type in the key and it works.  But with Ubuntu eee, I can connect to open networks but not encrypted.  I am not 100% sure what I am doing because there are so many settings.  I have to choose password type (for wep i have to choose hexadecimal or ascii) and I presume I leave configuration at DHCP?  My key is just a set of 10 numbers written on the modem.  Anyway I have spent a lot of time trying to google the answer but no dice, I bet the fix is really easy.  Here is this if it is any help, I saw some other posts requesting this info.

```


chris@chris-laptop-mini:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"2WIRE084"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:17 dBm   Sensitivity=1/1 
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:9516  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

chris@chris-laptop-mini:~$ lshw -C network
WARNING: you should run this program as super-user.
111 (sysfs) 


  *-network               
       description: Ethernet interface
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:1b:68:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1e driverversion=1.0.0.4 firmware=L1e latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wifi0
       version: 01
       serial: 00:22:43:4e:77:48
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


```

---

