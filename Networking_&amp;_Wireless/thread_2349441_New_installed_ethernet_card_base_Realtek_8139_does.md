---
title: "New installed ethernet card base Realtek 8139 doesn't work"
date: 2017-01-14
forum: Networking &amp; Wireless
---

### Post by romaska-r on 2017-01-14
Ubuntu 14.04
I added new ethernet card to my PC (integrated is broken and turned off via BIOS). 
Ubuntu doesn't see it. 

It seems driver is up but Network Manager doesn't understand it. See log below.
```
root@baby:~# cat /var/log/syslog | grep -e 8139
Jan 14 22:36:46 baby kernel: [    0.115124] pci 0000:04:00.0: [10ac:8139] type 00 class 0x000000
Jan 14 22:36:46 baby kernel: [   21.146359] 8139too: 8139too Fast Ethernet driver 0.9.28
Jan 14 22:36:47 baby kernel: [   21.193964] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
```

But there is no such device in /sys/class/net

It's a little bit strange output if lspci. Is it correct?
```
04:00.0 Non-VGA unclassified device [0000]: Honeywell IAC Device [10ac:8139] (rev 10)
	Subsystem: Honeywell IAC Device [10ac:8139]
```

rtl8139-diag didn't find it.

I looked through similar topics but didn't found solution for my case.
Any idea where I should dig?

---

### Post by TheFu on 2017-01-15
Take it back ASAP.

Buy an Intel PRO/1000 NIC. They aren't expensive anymore and work better (in multiple ways) than anything from Realtek. The e1000 driver is solid, offloads most processing from the CPU to the ASIC and is extremely stable.

You'll thank me.

---

