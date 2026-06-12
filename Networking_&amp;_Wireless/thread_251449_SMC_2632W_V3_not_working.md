---
title: "SMC 2632W V3 not working"
date: 2006-09-05
forum: Networking &amp; Wireless
---

### Post by kyke on 2006-09-05
Hello, I have a "SMC 2632W V3 EU" PCMCIA WIFI card and it was running okay on Windows but no way in Ubuntu Dapper on a laptop, can you help? TIA.

When I insert the card, I got on the console something like this:
> 
irq 3: nobody cared (try booting with the "irqpool" option)
handlers:
[<cccd2620>] (service_interrupt+0x0/0x300 [atmel])
Disabling IRQ #3


and on "dmesg" I found:
> 
eth1: Atmel at76c50x. Version 0.98. MAC 00:04:e2:5a:09:d4
ADDRCONF(NETDEV_UP): eth1: link is not ready


and if I try a "iwlist eth1 scan", the green led flash for three times, then it turns off and after 5-10 seconds I got a "**eth1 Failed to read scan data : Resource temporarily unavailable**"

So, what's wrong? I read some people have the same problem in Dapper but it worked on Breezy??

I tried adding "irqpoll" on GRUB, but then the system freezes when I insert the PCMCIA card.

---

### Post by kyke on 2006-09-08
Nobody? :(

---

### Post by ethanay on 2008-02-05
is the interface online?

try

sudo ifconfig eth1 up

before scanning and see if that helps...?

---

