---
title: "AR5418 on macbook pro, weak signal"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by dannytherocker on 2008-02-10
Hi, I got a brand new MacBook Pro (3.1) and everyhing works, wireless included using madwifi drivers. WPA2, ssid disabled works perfectly!
Only one thing: the wireless signal is very weak, unless I get close to acces point so!! for eaxmple I cannot watch a film stored in my server because it interrupts every 10 secs...
But if I reboot in Leopard, everything is ok !!

Is it a driver problem ??
how can I fix it ?
Thanks

---

### Post by Hightide on 2008-02-10
Hi dannytherocker

can you post output from

lshw -C network

iwconfig

also have a look at Kevdogs wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188")

regards

:)

---

### Post by dannytherocker on 2008-02-10
> **Hightide said:**
> Hi dannytherocker

can you post output from

lshw -C network

iwconfig

also have a look at Kevdogs wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571188")

regards

:)

Hi, thanks for the quick answer!
These are my outputs:

```
danilo@zyphas:~$ sudo lshw -C network
 *-network               
       description: Wireless interface
       product: AR5418 802.11a/b/g/n Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wifi0
       version: 01
       serial: 00:1e:52:73:81:82
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=svn r3347 ip=192.168.1.5 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: Marvell Yukon 88E8058 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth0
       version: 13
       serial: 00:1e:c2:02:dd:fa
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair

```

```
danilo@zyphas:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"***********"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:F8:AB:99:17   
          Bit Rate:54 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:*************************************************   Security mode:restricted
          Power Management:off
          Link Quality=60/70  Signal level=-36 dBm  Noise level=-96 dBm
          Rx invalid nwid:358  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Please, take into consideration I'm very close to the AP, at the moment!

---

### Post by Hightide on 2008-02-10
Hi dannythe rocker

yes your signal is only 36, weak. 

I am rushing gout now. will come back later

regar:)ds

---

### Post by dannytherocker on 2008-02-10
> **Hightide said:**
> Hi dannythe rocker

yes your signal is only 36, weak. 

I am rushing gout now. will come back later

regar:)ds

I'll wait.... :-)

---

