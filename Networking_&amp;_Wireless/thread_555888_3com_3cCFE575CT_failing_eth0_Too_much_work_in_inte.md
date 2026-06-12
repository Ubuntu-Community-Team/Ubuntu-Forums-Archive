---
title: "3com 3cCFE575CT failing: eth0: Too much work in interrupt, status e003"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by jglepage on 2007-09-20
Hello,

I am setting up about 22 old laptops for a school.  I'm using Xubuntu 7.04.  The hardware is identical as far as I can tell.  The first ten laptops work fine, but the next four (with identical hardware) have problems with the network card.

I believe that this may be due to an upgrade that was not applied to the 10 original laptops.  The problem laptops were installed (and upgraded via synaptic) more recently.

I'm getting persistent failures in the network card.  The system installs fine (from the Xubuntu 7.04 alternate CD).  However, when I put the network card under any strain at all it immediately goes down.  Usually only a restart will fix the problem.  I have found that the following procedure will also work (sometimes):

rmmod 3c59x 
modprobe 3c59x
/etc/init.d/pcmciautils restart
/etc/init.d/networking restart

The message in /var/log/kern.log is this:

Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.298607] eth0: Host error, FIFO diagnostic register 0000.
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.298620] eth0: PCI bus error, bus status 80000020
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.300016] eth0:  setting full-duplex.
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.300076] eth0: Host error, FIFO diagnostic register 0000.
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.300090] eth0: PCI bus error, bus status 80000020
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.301485] eth0:  setting full-duplex.
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.301544] eth0: Host error, FIFO diagnostic register 0000.
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.301557] eth0: PCI bus error, bus status 80000020
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.302962] eth0:  setting full-duplex.
Sep 20 14:35:12 fhmlaptop25 kernel: [ 1521.303015] eth0: Too much work in interrupt, status e003.


the network card, according to lspci -v:
01:00.0 Ethernet controller: 3Com Corporation 3cCFE575CT CardBus [Cyclone] (rev 10)
        Subsystem: 3Com Corporation FE575C-3Com 10/100 LAN CardBus-Fast Ethernet
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at 1000 [size=256]
        Memory at 24000000 (32-bit, non-prefetchable) [size=128]
        Memory at 24000080 (32-bit, non-prefetchable) [size=128]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: <access denied>

The card bridge, according to lspci -v:
00:03.0 CardBus bridge: Ricoh Co Ltd RL5c478 (rev 03)
  Subsystem: NEC Corporation Unknown device 8039
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at 30000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=01, subordinate=04, sec-latency=176
        Memory window 0: 20000000-23fff000 (prefetchable)
        Memory window 1: 24000000-27fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

---

### Post by jglepage on 2007-09-21
More information:

After some research I now believe that the problem is IRQ conflicts.  

The principal clue is the message in /var/log/kern.log:
eth0: Too much work in interrupt, status e003

An examination /proc/interrupts shows that yenta (the driver for the pcmcia slot) and eth0 share the same IRQ.  The number of interrupts does climb as the network activity increases.   

I'm uncertain why this is a problem on some of the laptops and not others.  I will check /proc/interrupts on all the machines as soon as I can.  (The ones that are working are locked up at the school right now).

---

