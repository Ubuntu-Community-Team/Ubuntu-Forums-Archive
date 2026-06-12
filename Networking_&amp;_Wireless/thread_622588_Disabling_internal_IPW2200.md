---
title: "Disabling internal IPW2200 ?"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by ajkirchner on 2007-11-24
I currently work on a Thinkpad T43 with an internal ipw2200 wireless card running Gutsy

I have a PCMCIA wireless card (Airlink101 with atheros chipset)  and would like to disable my ipw2200 and use the Airlink cardbus to connect wireless-ly - but how?

Thanks

---

### Post by kevdog on 2007-11-24
Can you post the following:

lshw -C network

Basically, find the driver, unload it from the kernel, if you dont want it to load at boot, add it to the /etc/modprobe.d/blacklist file.  Thats it

---

### Post by ajkirchner on 2007-11-27
```

-v3.46a latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:2b:02:f9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.103 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

how exactly do I blacklist? and un-blacklist - when I want to use the wireless card again?

---

