---
title: "Wireless internet"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by ThomasWii on 2007-12-28
Hi, i have a laptop which has wireless Internet, and we have a netgear router, usually when i boot up ubuntu, it connects to the router, but today it did not, i used my ds to connect to see if it was the router or the computer, and it turns out its the computer.

Thanks in advance

Thomas

---

### Post by ThomasWii on 2007-12-28
bumb

---

### Post by ThomasWii on 2007-12-30
bump2

---

### Post by DrIdiot on 2007-12-30
type the following commands into console and paste what you get:

sudo lshw -C network

sudo iwconfig

sudo iwscan <interface> scanning (if you dont know what your interface is, skip this step)

---

### Post by ThomasWii on 2007-12-30
```
thomas@thomas-laptop:~$ sudo lshw -C network
[sudo] password for thomas:
  *-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: eth1
       version: 02
       serial: 00:14:a5:c7:bf:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:14:0b:01:73:1b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.0.5 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
thomas@thomas-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

thomas@thomas-laptop:~$ 

```

---

### Post by DrIdiot on 2007-12-30
type:

iwlist eth1 scanning

what do you get

also, are you using NetworkManager?  make sure youve tried to select a access point (its the applet on the top right with the bars, or if theres no network, the yellow warning sign)

---

### Post by ThomasWii on 2007-12-30
```
thomas@thomas-laptop:~$ iwlist eth1 scanning
eth1      No scan results

thomas@thomas-laptop:~$ 


``` and the yellow sing dose come up.

---

### Post by DrIdiot on 2007-12-30
so when you click on the networkmanager applet, no networks show up right?

try:
[http://ubuntuforums.org/showthread.php?t=603154](http://ubuntuforums.org/showthread.php?t=603154)

---

### Post by ThomasWii on 2007-12-31
No that dose not work, i think its because i have the live CD for 7.04 and my network card was not supported.

---

### Post by ThomasWii on 2008-01-01
bump

---

### Post by ThomasWii on 2008-01-03
bumb2

---

