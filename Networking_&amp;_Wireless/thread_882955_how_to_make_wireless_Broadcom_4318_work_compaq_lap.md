---
title: "how to make wireless Broadcom 4318 work compaq laptop v2607CL"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by quietvillage on 2008-08-07
I tried to fw cutter method. but it is not connecting.I made it work before but after a fresh install it is not working.

 sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo lshw (filtered for broadcom)

 description: Wireless interface
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@05:02.0
                logical name: eth1
                version: 02
                serial: 00:14:a5:7b:7c:97
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master ethernet physical wireless
                configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-15-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
                resources: iomemory:c0204000-c0205fff irq:20

I gave the ESSID name and wep hexadecimal key password that was stored in my wireless modem+router (netgear) also in network configuration.

still not able to connect? what is the problem?

Thanks
Bala

---

