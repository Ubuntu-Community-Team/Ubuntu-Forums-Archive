---
title: "Trying to install WPN511 pcmcia card on preinstalled 8.04 for x86"
date: 2008-07-30
forum: Networking &amp; Wireless
---

### Post by surnj1 on 2008-07-30
Hi,

I am trying to add a wireless adapter (Netgear WPN511 PCMCIA with Atheros chipset) to an already installed Ubuntu 8.04 OS on a Dell inspiron 2650.

I installed a madwifi driver from following url before inserting the card:

[http://packages.ubuntu.com/hardy/i38...tools/download](http://packages.ubuntu.com/hardy/i38...tools/download)

But there is no sign that Ubuntu has detected the card, I restarted the system without any success.

"lshw -C network" shows:

 *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0 maxlatency=28 mingnt=10


Please guide me!!!

Thx,

---

### Post by surnj1 on 2008-09-01
Solved the problem. I had t install restricted modules using
$ sudo apt-get install linux-restricted-modules-`uname -r`

then unpluged and repluged my pcmcia card & checked dmesg
and it worked.....

---

