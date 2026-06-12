---
title: "[SOLVED] Unable to get ethernet working (RTL-8139 NIC)."
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by MG3000 on 2008-09-20
I have installed Ubuntu 8.04 on this laptop (Sony Vaio PCG-K13) with a Realtek 8139 series ethernet adapter. No matter what I try, I can't get a working ethernet connection. Even if I manually configure eth0 I can't even ping anything.

What's odd is that I tried Fedora 9 and it does the same thing. Fedora 6 and Ubuntu 6.xx work fine! Really weird.

Here's some blurbs from various system logs:

debug:
```
Sep 20 10:37:31 SONY kernel: [   87.330440] eth0: Tx queue start entry 4  dirty entry 0.
Sep 20 10:37:31 SONY kernel: [   87.330443] eth0:  Tx descriptor 0 is 0008a156. (queue head)
Sep 20 10:37:31 SONY kernel: [   87.330446] eth0:  Tx descriptor 1 is 0008a156.
Sep 20 10:37:31 SONY kernel: [   87.330448] eth0:  Tx descriptor 2 is 0008a156.
Sep 20 10:37:31 SONY kernel: [   87.330451] eth0:  Tx descriptor 3 is 0008a156.
Sep 20 10:37:43 SONY kernel: [   99.300983] eth0: Transmit timeout, status 0d 0004 c07f media 10.
```
(this repeats many times)

kern.log:
```
Sep 20 10:36:51 SONY kernel: [   47.627849] handlers:
Sep 20 10:36:51 SONY kernel: [   47.627851] [serial8250_interrupt+0x0/0x150] (serial8250_interrupt+0x0/0x150)
Sep 20 10:36:51 SONY kernel: [   47.627855] Disabling IRQ #3
Sep 20 10:36:52 SONY kernel: [   48.409245] irq 3: nobody cared (try booting with the "irqpoll" option)


Sep 20 10:37:40 SONY kernel: [   96.308323] NETDEV WATCHDOG: eth0: transmit timed out
Sep 20 10:37:43 SONY kernel: [   99.300983] eth0: Transmit timeout, status 0d 0004 c07f media 10.
Sep 20 10:37:43 SONY kernel: [   99.300991] eth0: Tx queue start entry 4  dirty entry 0.
Sep 20 10:37:43 SONY kernel: [   99.300994] eth0:  Tx descriptor 0 is 0008a03c. (queue head)
Sep 20 10:37:43 SONY kernel: [   99.300997] eth0:  Tx descriptor 1 is 0008a03c.
Sep 20 10:37:43 SONY kernel: [   99.300999] eth0:  Tx descriptor 2 is 0008a03c.
Sep 20 10:37:43 SONY kernel: [   99.301002] eth0:  Tx descriptor 3 is 0008a03c.
Sep 20 10:37:43 SONY kernel: [   99.301017] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep 20 10:37:45 SONY kernel: [  101.459647] eth0: no IPv6 routers present
Sep 20 10:37:45 SONY kernel: [  101.639204] ath0: no IPv6 routers present
Sep 20 10:37:52 SONY kernel: [  108.278868] NETDEV WATCHDOG: eth0: transmit timed out
```
(here I think IRQ #3 is related to the ethernet adapter, IRQ problem? hope not, can't change this in BIOS)

messages:
```
Sep 20 10:45:17 SONY kernel: [  692.026620] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep 20 10:45:26 SONY kernel: [  701.004460] NETDEV WATCHDOG: eth0: transmit timed out
Sep 20 10:45:29 SONY kernel: [  703.997154] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep 20 10:45:38 SONY kernel: [  712.975031] NETDEV WATCHDOG: eth0: transmit timed out
Sep 20 10:45:41 SONY kernel: [  715.967705] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep 20 10:45:50 SONY kernel: [  724.945553] NETDEV WATCHDOG: eth0: transmit timed out
Sep 20 10:45:53 SONY kernel: [  727.938250] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep 20 10:46:02 SONY kernel: [  736.916101] NETDEV WATCHDOG: eth0: transmit timed out
Sep 20 10:46:05 SONY kernel: [  739.908793] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep 20 10:46:14 SONY kernel: [  748.886646] NETDEV WATCHDOG: eth0: transmit timed out
Sep 20 10:46:17 SONY kernel: [  751.879342] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1
Sep 20 10:46:26 SONY kernel: [  760.857196] NETDEV WATCHDOG: eth0: transmit timed out
```
(full of this)

user.log:
```
Sep 20 10:36:50 SONY dhcdbd: Started up.
Sep 20 10:36:53 SONY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep 20 10:37:35 SONY dhcdbd: Unrequested down ?:3
Sep 20 10:46:29 SONY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason
Sep 20 10:46:40 SONY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name
Sep 20 10:46:40 SONY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain
Sep 20 10:46:40 SONY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers
Sep 20 10:46:40 SONY dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.interface_mtu
```


If you need any more information I'll post it. I'm really stumped by this problem. Any help greatly appreciated.

---

### Post by MG3000 on 2008-09-20
Solved! Adding "irqpoll" to the boot options, as was suggested in kern.log got it working properly. I don't know what irqpoll does but eh, it works!

---

