---
title: "[SOLVED] Onboard suddenly not working"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by efexD on 2009-01-03
Well i had installed ubuntu on my laptop with the same disc i just installed on my desktop. But on my desktop it is saying that there is no network connection, i know my onboard ethernet card has worked with ubuntu before. I've tried desmg, ifconfig, turning it on, off. No prevail. Whats going on?

---

### Post by Peter09 on 2009-01-03
Post the output of

```
lshw -C network
```

and

```
ifconfig
```

---

### Post by efexD on 2009-01-03
lshw.
```
description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: a0
       serial: 00:22:15:90:4e:97
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL2 driverversion=1.0.40.2 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair

```

ifconfig.
```
eth0      Link encap:Ethernet  HWaddr 00:22:15:90:4e:97  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:bbfc0000-bc000000 

```

---

### Post by Peter09 on 2009-01-03
Might be worth checking your hardware connections (wires). You do not look to be connected, but the hardware/drivers look ok.

---

### Post by efexD on 2009-01-03
Well I'm hooked up to an adapter when i posted that. My onboard is faster so id rather use that.

---

