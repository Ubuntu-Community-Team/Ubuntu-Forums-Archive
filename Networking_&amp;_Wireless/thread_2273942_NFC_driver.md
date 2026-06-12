---
title: "NFC driver??"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by kashei on 2015-04-16
Hi
i'm not sure if it should be posted here or in  "hardware",  but anyways   
i have laptop with build in NFC. is there driver for it and how do i enable it

thank you


P.S.  i dd google it and all i could find is tools for nfc (basically is to programs nfc tags)

---

### Post by ricky-flammia on 2015-04-16
Type this into the terminal and post the output here. It should tell me what device you are running so that I can find the appropriate driver for you.

```
sudo lshw -C network
```

Additionally, it may also help if you ensure that all of the appropriate update repositories are selected and that Ubuntu is up to date.

---

### Post by kashei on 2015-04-16
```
kashei@kashei1:~$ sudo lshw -C network[sudo] password for kashei: 
  *-network               
       description: Ethernet interface
       product: NM10/ICH7 Family LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 01
       serial: 00:13:72:d2:f7:c3
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:edeff000-edefffff ioport:ccc0(size=64)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 20:4e:7f:e5:9a:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmn43xx64 driverversion=1.59+,08/26/2009, 5.10.79.30 ip=10.0.0.4 link=yes multicast=yes wireless=IEEE 802.11g



```


thanks man

---

### Post by michi1983 on 2015-04-17
And here is some stuff to read:
[http://manpages.ubuntu.com/manpages/trusty/man8/neard.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/neard.8.html)
[http://manpages.ubuntu.com/manpages/trusty/man1/nfctool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/nfctool.1.html)

---

