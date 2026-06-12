---
title: "Connecting to internet via VMware player"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by ourmartin on 2008-10-09
I'm running ubuntu 8.04 on WMware player, on XP. When I try to get on the internet it says: "Cannot connect virtual device parallel0. No corresponding device is available on the host."

Any ideas? 

I've manually configured the internet connection the host IP address, subnet mask, gateway. 

Cheers!

---

### Post by superprash2003 on 2008-10-09
your ubuntu isnt recognizing the card.. in your ubuntu terminal type lshw -C network and post output herew

---

### Post by ourmartin on 2008-10-10
Hi

I typed lshw -C network and got:

WARNING: you should run this program as super-user.
  *-network
	description: Ethernet interface
	product: 82545EM Gigabit Ethernet Controller (Copper)
	vender: Intel Corporation
	physical id: 10
	bus info: pci@0000:00:10.0
	logical name: eth0
	version: 01
	serial: 00:0c:29:73:e6:ca
	width: 64 bits
	clock: 66MHz
	capabilities: bus_master cap_list ethernet physical logical
	configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI fi
rmware=N/A ip=193.62.178.19 latency=0 mingnt=255 module=e1000 multicast=yes


Cheers!!
M

---

