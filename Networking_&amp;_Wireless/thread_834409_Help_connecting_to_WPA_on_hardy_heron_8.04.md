---
title: "Help connecting to WPA on hardy heron 8.04"
date: 2008-06-19
forum: Networking &amp; Wireless
---

### Post by s1337m on 2008-06-19
I have a BroadCam 4328, a Dell 1500 WLAN, that uses ndiswrapper on 8.04.  I can connect to unsecured networks fine, but I cant connect to WPA (I havent tried WEP).  I have tried some tutorials that Ive seen around (including this site), but they either have not worked or I wasn't able to complete them (not knowing my way around the network interfaces).  I would really appreciate some help in getting this connected!

```
sean@sean-laptop:~$ lspci | grep BCM
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)

```

```
sean@sean-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:FD:84:13   
          Bit Rate=11 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

iwlist scan works fine...

```
sean@sean-laptop:~$ uname -r
2.6.24-19-generic

```


note -- i am on an unsecured wireless connection
```
sean@sean-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:cf:3d:0d:69
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.1.106 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:4a:16:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
sean@sean-laptop:~$ 

```

thanks!!

---

