---
title: "network issue on a Acer AC100"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by benrboone on 2016-11-15
I have install ubuntu 16.04 on a acer cube computer.  It has a intel  82579LM Gigabit Network Connection (used sudo lshw -C net to get this information)

the result of this (sudo lshw -C net) also informed me that the network interface was unclaimed.

plexkunz@plexkunz-AC100:~/Downloads/e1000e-3.3.3/src$ sudo lshw -C net
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list
       configuration: latency=0
       resources: memory:fe400000-fe41ffff memory:fe424000-fe424fff ioport:f080(size=32)


I have tried to load new drivers from intel
e1000e-3.3.3.tar

that seem successful but did not change the results

anyway any help would be great
thank you

---

### Post by benrboone on 2016-11-15
I have still not been able to get this working.
I have tried several version on the driver i believe should be used.  Also i have done further trouble shooting and using this command i get the following results:
~$ dmesg | grep -e eth -e e1000
[    2.283559] e1000e: Intel(R) PRO/1000 Network Driver - 3.2.6-k
[    2.283561] e1000e: Copyright(c) 1999 - 2015 Intel Corporation.
[    2.326910] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.340454] e1000e: probe of 0000:00:19.0 failed with error -3
[  283.312740] rtl8150 1-1.3:1.0: eth0: rtl8150 is detected
[  284.331971] rtl8150 1-1.3:1.0 enx00e04c0339ef: renamed from eth0

and the following command lspci -nnk gives:

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 05)
	DeviceName: Onboard Intel Ethernet
	Subsystem: Acer Incorporated [ALI] 82579LM Gigabit Network Connection [1025:0586]
	Kernel modules: e1000e



by the way I have also eliminated the possibility of switches, routers or wires by replacing them (two routers) (three different switches) and (3 different wires)

---

### Post by benrboone on 2016-11-15
after reading more about failed with error -3 , I decided to update bios on the motherboard.  Had to use the uefi shell (had a little issue with selecting fs0 as i did not put fs0: ) once that was sorted out the bios flash went smoothly.  upon reboot ubuntu could use intel gigabit nic card.

looks like everything is solved.  (dumb bios updates)

---

