---
title: "Infrared on a Compaq M300"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by KingDingeling on 2007-02-23
Hi guys, I'm new here, but not new to computers and Linux :)

I have a Compaq Armada M300 Laptop (500MHz P3 / 128MB RAM / ATI 4MB card) that's running Ubuntu 5.10 right now. I have tried to set up the Infrared device, and found this [guide]("http://www.cnbc.cmu.edu/~plaut/m300/") to do that. 
That guide tells me to use the following commands: 
> The infrared device on the M300 is on /dev/ttyS2. This defaults to IRQ 4, but Mikael Hedin pointed out that this needs to be set to IRQ 3 for IrDA to work. I've added /bin/setserial /dev/ttyS2 irq 3 to /etc/rc.d/rc.local. Also, under Red Hat, be sure that /etc/sysconfig/irda contains DEVICE=/dev/ttyS2. Then, running service irda start should bring up IrDA (SIR) under /dev/ircomm0.

I've only managed to get SIR working. The M300 has an SMC-based FIR chip ("lspnp -v" lists a "SMCf010 communications device: RS-232") but the "findchip" utility (included in the irda-utils package) doesn't detect it. 

Now I tried all kinds of things, but I can't find the /etc/rc.d folder. There is only rc1-6.d and rcS.d, none of which contain rc.local. 

Can someone please help me out here? Its not a vital part of the system, but I wanna get it working so I can load stuff from my mobile onto the laptop. 

Thanks ahead! :popcorn:

---

### Post by KingDingeling on 2007-02-23
*push* noone knows?

---

### Post by KingDingeling on 2007-02-24
bump again.... help please!

---

### Post by paulhurleyuk on 2007-06-30
On my Aramda M300 (Feisty 7.04 running KDE), I too am missing a /etc/rc.d folder.  However I do have a file /etc/rc.local that I assume is the same as /etc/rc.d/rc.local...

I assume the rc1.d rc2.d folder refer to runlevel 1, runlevel 2 etc..

Hope this helps

Paul.

---

