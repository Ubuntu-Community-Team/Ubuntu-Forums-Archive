---
title: "HP NC150T  4 Port Gigabit"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by jpmrblood on 2006-10-18
Hello, I have HP NC150T PCI 4-port Gigabit Combo Switch Adapter connected, but it seems only got detected 1 port in Dapper. How to get the 3 ports available for use? Thx.

---

### Post by mips on 2006-10-18
Yes thats correct and the way it should work. I think you might be a bit confused. Let me try and explain.

It is a 4-port switch & a 1-port NIC. The switch and nic are two different things. You do not actually have a Physical NIC port terminating in a RJ-45 connector. The NIC terminates internally to the switch on the card. The switch then has 4ports that terminate externally as RJ-45 connectors.

You will not see the 4 switch ports as all as they are part of the switch. It is identical to having an external switch:

PC--->Switch---> Multiple ports

You only have one NIC(internal) and Switch with 4 ports.

[ftp://ftp.compaq.com/pub/products/servers/networking/nc150tqaQA.pdf](ftp://ftp.compaq.com/pub/products/servers/networking/nc150tqaQA.pdf)

---

