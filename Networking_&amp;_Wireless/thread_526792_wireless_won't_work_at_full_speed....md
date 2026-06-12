---
title: "wireless won't work at full speed..."
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by Mostlyharmless42 on 2007-08-15
My wireless card has been working for a while now and i've been happy with it.  The only problem is that it won't go above 11mbps.  It should be capable of at least 54mbps.  Anyone know a solution to this problem??

---

### Post by noob12 on 2007-08-15
One possible issue is that your device needs to be told explicitly to go to G mode.

Can you show us the situation by posting the output of these commands?

```

sudo lshw -C network

iwconfig

iwlist scan

```

---

### Post by Mostlyharmless42 on 2007-09-06
here are those outputs requested.  They are in the order of noob12's original post

```
  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@01:07.0
       logical name: eth1
       version: 03
       serial: 00:18:f8:33:a7:c1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic ip=192.168.1.103 latency=32 link=yes multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fdefe000-fdefffff irq:20

```

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"mulsanne"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:39:4D:39:52   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=58/100  Signal level=-69 dBm  Noise level=-66 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:18:39:4D:39:52
                    ESSID:"mulsanne"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-62 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 20ms ago

```

---

### Post by Mostlyharmless42 on 2007-09-09
bumpity

---

### Post by Termina on 2008-07-06
I know it's an old post, but since I came across it on google I figured I'd post a solution.

sudo iwconfig eth1 rate 54M

Also, make sure there are not any other 11Mbps wireless devices on the network (since the router can only be in 1 mode at a time, the slowest device on the wireless network chooses the speed for all users).

---

