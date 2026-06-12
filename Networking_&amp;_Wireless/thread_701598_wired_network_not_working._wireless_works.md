---
title: "wired network not working. wireless works"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by eldersoares on 2008-02-19
hi everyone
i have a cable modem connection with a wifi router and ssince i upgraded to gutsy, my wifi network didnt work anymore (but the other ones, from the neighbours, did work). so i connected the cable directly to the computer. then, when i tried to make the router work again, i couldn't and my wired connection stopped working too! is there any configuration that was maybe saved by network manager? what could have passed?

i have a dell inspiron 6400, intel core duo
thanks!

---

### Post by eldersoares on 2008-02-19
i collected some information about my devices. it seems that there is something wrong with eth0 interface....

/etc/network/interfaces

```
auto lo
iface lo inet loopback


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

```

sudo ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:15:C5:C6:6E:4A  
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:31784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:2045958 (1.9 MB)  TX bytes:12834 (12.5 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:18:DE:B3:0B:EC  
          inet addr:10.0.1.2  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:feb3:bec/64 Scope:Link
          UP DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Metric:1
          RX packets:858 errors:2 dropped:1211 overruns:0 frame:0
          TX packets:944 errors:0 dropped:3 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:741416 (724.0 KB)  TX bytes:138487 (135.2 KB)
          Interrupt:16 Base address:0xc000 Memory:efdff000-efdfffff 

lo        Link encap:Bucle local  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK CORRIENDO  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:258 (258.0 b)  TX bytes:258 (258.0 b)

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Apple Network 719a7d"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:14:51:71:9A:7D   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/100  Signal level=-87 dBm  Noise level=-88 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1820   Missed beacon:0


```

lshw -C network

```
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:b3:0b:ec
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=10.0.1.2 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c6:6e:4a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s

```

sudo dhcliente -r eth0

```
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:15:c5:c6:6e:4a
Sending on   LPF/eth0/00:15:c5:c6:6e:4a
Sending on   Socket/fallback

```

sudo ifup eth0
```
Ignoring unknown interface eth0=eth0.
```

**actually i dont know wich of these infomartion are useful, but, as a newbie, i put it everything**

plz help me! thanks in advance!!!!!

---

### Post by Iowan on 2008-02-19
You are not being ignored...  you've provided enough information to get a good start.  You can (should?) edit the **/etc/network/interfaces** file to add a section for eth0.  It can be a duplicate of the information for eth2 (except  without the "#" just before "iface") Try **dhclient** again - then check **ifconfig**.  Eth0 seems to be alive - but has no IP address.  It also seems odd (to me, anyway) that your wireless card is being interpreted as eth1.

---

### Post by dmizer on 2008-02-19
actually, i think i see your problem.  you are connected wirelessly with eth1.  because you are connected on eth1, you cannot be connected on eth0 (can't have two interfaces active at the same time).  so, disconnect eth1:
```
sudo ifdown eth1
```
after adding a section in /etc/network/interfaces for eth0, enable eth0
```
sudo ifup eth0
```
run ifconfig again and make sure you are connected on eth0, and try browsing.

---

### Post by Iowan on 2008-02-19
I was gonna suggest that next...:---)

---

