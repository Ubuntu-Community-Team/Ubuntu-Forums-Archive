---
title: "Using a second network card for file transfers"
date: 2007-03-23
forum: Networking &amp; Wireless
---

### Post by flg8tr98 on 2007-03-23
I am currently using Ubuntu 6.10 in conjunction with a Win XP machine.  Both boxes have dual network cards.  I would like to increase file transfer speeds between the 2 boxes.  I was wondering if either of the 2 options would improve speeds, and if so, which one is better/easier.

1. Use a crossover cable to connect the secondary NICs on each machine (what would I need to do on each box to make this work?)

2. Set up a port on each machine and the router that is dedicated to communication between Ubuntu and XP (not sure if this will work, but I thought I read this somewhere)

If anyone can shed some insight it would be greatly appreciated.  I am well versed in Windows and hardware/software, but this is my first major foray in the world of Linux (great O.S. though)

---

### Post by dbott67 on 2007-03-23
You probably want to do something like NIC bonding/trunking/teaming:

[http://www.novaglobal.com.sg/?q=ethernetbonding](http://www.novaglobal.com.sg/?q=ethernetbonding)
[http://www.5dollarwhitebox.org/wiki/index.php/Howtos_NIC_Bonding_Debian](http://www.5dollarwhitebox.org/wiki/index.php/Howtos_NIC_Bonding_Debian)

-Dave

---

