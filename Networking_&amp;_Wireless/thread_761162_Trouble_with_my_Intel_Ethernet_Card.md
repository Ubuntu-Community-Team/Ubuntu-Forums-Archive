---
title: "Trouble with my Intel Ethernet Card"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by oldhalliwell on 2008-04-20
Hello
I am hoping that someone can help me.  Ubuntu has been working fine on my IBM Thinkpad but I cannot get network/internet access.
I have been reading up and was advised to run the /lspci command.
This is what I get for the Ethernet option:

Ethernet controller:  Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 09)
Flags: medium devsel, IRQ 11
Memory at e812000 (32-bit, non-fetchable) [size=4k]
I/O ports at 1800 [size=64]
Memory at e810000 (32-bit, non-fetchable) [size=128k]
[virtual] Expansion ROM at 30100000 [disabled] [size=1M]
Capabilities:  <access denied>

I don't know what this means, and I don't know how to set this up so that I can get access.
Can anyone help me please?  I don't understand linux/ubuntu yet so would appreciate very direct instructions for how to enable this driver (if that is what the problem is).
Thank you

---

### Post by djronh on 2008-04-20
This won't help you a lot..but the drivers for an intel card (wired or wireless?) are almost certainly contained in the linux kernel. You don't do anything about drivers normally. That being said Ubuntu 7.10 has been messing up internet connections. 
Try menu bar-system-administration-network a box will appear then select your connection and click on properties in the configuration box which appears select  automatic DHCP and click OK. On the network settings box you could also try setting DNS to those supplied by your ISP.

---

