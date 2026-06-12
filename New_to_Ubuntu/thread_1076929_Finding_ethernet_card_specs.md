---
title: "Finding ethernet card specs"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Revenged on 2009-02-21
I need to find the information for the network card in my PC, because I need to download the driver for XP. Anyone know how I could do that?  

I used the command "sudo lshw" but the output didn't make too much sense. Any help?

---

### Post by newbee70 on 2009-02-21
> **Revenged said:**
> I need to find the information for the network card in my PC, because I need to download the driver for XP. Anyone know how I could do that?  

I used the command "sudo lshw" but the output didn't make too much sense. Any help?

you could try
```
 lshw -C network 
```

which gives this type info:

  *-network
       description: Ethernet interface
 ***      product: 88E8001 Gigabit Ethernet Controller
 ***      vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth1
       version: 13
       serial: 00:0e:a6:72:cb:2a
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=skge driverversion=1.13 firmware=N/A ip=192.168.1.100 latency=32 maxlatency=31 mingnt=23 module=skge multicast=yes

---

