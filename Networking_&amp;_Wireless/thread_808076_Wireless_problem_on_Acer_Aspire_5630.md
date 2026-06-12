---
title: "Wireless problem on Acer Aspire 5630"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by dt112 on 2008-05-26
I have installed hardy heron, and am having problems with the wireless.

lshw 
```
description: Wireless interface
          product: AR5212/AR5213 Multiprotocol MAC/baseband processor
          vendor: Atheros Communications Inc.
          physical id: 0
          bus info: pci@0000:07:00.0
          logical name: wifi0
          version: 01
          serial: 00:14:6c:44:5a:7a
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list logical ethernet physical wireless
          configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

I have not compiled a kernel before, and I'm having trouble getting the Intel drivers to work. Is there an easier way?

---

### Post by mapes12 on 2008-05-26
Your lshw output looks OK. Driver installed and all. Have you had a look at this HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by dt112 on 2008-05-26
Right, that lshw was actually for the card that I was using as a temporary fix. The real one is :

```
description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:6b:98:2c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=143.210.101.56 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

I've tried the fix from the other thread, 

inputting "sudo dhclient -r wmaster0"

returned 
```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback

```

and  "sudo ifconfig wmaster0 up" 

gave "SIOCSIFFLAGS: Operation not supported"

---

### Post by mapes12 on 2008-05-26
Yeh. It doesn't recognise the card even though the lshw sees it. Here's some more helpful links:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29%7C%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28supported%29%7C%28wifi%29#head-e669905d73a32156274930398b3d3c3468508d45)

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by dt112 on 2008-05-26
I had to reboot, and there were 2 kernels boot from. One of them didn't work, and one of them worked straight off.

I'm not sure why this worked/happened. Any ideas?

---

### Post by krusk on 2008-06-15
I have the exact same problem, but none of kernels tried so far have worked for me. What kernel are solving the problem dt112?

---

