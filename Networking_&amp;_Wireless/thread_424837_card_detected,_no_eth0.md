---
title: "card detected, no eth0"
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by svengali on 2007-04-27
My network card is detected in Kubuntu 6.06. Link light is on. The driver 8139too is loaded at boot. But I have no network interface. 
That is, eth0 doesn't exist.
It all works with other OS's, so its not my machine.

When I enter this command to check the hardware,

>>sudo lshw -C network
*-network UNCLAIMED
       description: Ethernet controller
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 9
       bus info: pci@00:09.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       resources: ioport:de00-deff iomemory:efffff00-efffffff irq:11

(Note, there is no line saying,
configuration: driver=8139too)

When I check the modules,

>>lsmod
8139too                26880  0
mii                     5888  1 8139too

I've tried several cards, but they're all rtl8139 based. I've tried the 8139cp module as well. No good either.
Currently have a D-Link DFE-528TX installed (also with rtl8139 chip). I have the source code that came packaged with the card. But I don't have gcc.

I assume I need to install gcc compiler and compile my own driver? Am I right?
Threads say 8139too is dodgy.
Persevering with this annoying bug because I like everything else about Kubuntu!

Thanks gang.

---

### Post by renzokuken on 2007-04-27
to compile things you need to install the buil-essential package (contains gcc as well as others)

```
sudo apt-get install build-essential
```

---

### Post by svengali on 2007-04-27
Thanks for the reply.
I'll have to get it without a connection, via another machine.
Happy springtime in England.
From the Antipodes...

---

