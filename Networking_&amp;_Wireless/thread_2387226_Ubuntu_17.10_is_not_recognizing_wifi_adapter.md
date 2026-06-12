---
title: "Ubuntu 17.10 is not recognizing wifi adapter"
date: 2018-03-16
forum: Networking &amp; Wireless
---

### Post by offir on 2018-03-16
I installed Ubuntu 16.04 
On a PC
I added a wireless network card

Ubuntu does not recognize the wireless network card
Through Google I came to several answers that did not solve the problem
I tried to switch to another network card
The same result



```
sudo lshw -C network

```

```
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@0000:0a:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:d0220000-d0221fff memory:d0200000-d021ffff
```


```
sudo lspci -v
```

```
0a:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
	Subsystem: D-Link System Inc DWL-G520+ Wireless PCI Adapter
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at d0220000 (32-bit, non-prefetchable) [size=8K]
	Memory at d0200000 (32-bit, non-prefetchable) [size=128K]
	Capabilities: [40] Power Management version 2
```


[COLOR="#0000FF"][SIZE=5]
so I deleted and installed Ubuntu 17.10[/SIZE][/COLOR]
Same problem

how do i make ubuntu to recognizing wifi adapter

---

### Post by jeremy31 on 2018-03-16
I would install the other wifi card and post terminal results for the same commands

---

### Post by offir on 2018-03-16
Ubuntu 17.10 recognized the second network card
But I ran into another problem

I have formatted and reinstalled Ubuntu 16.04.04

now it work 
but i have A strange new problem

I will add a post in the general help forum

---

