---
title: "How to install a NIC post installation?"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by Morcas on 2005-07-16
Howdy, I finally managed to get Unbuntu installed but I have a couple of issues I need some help with please.

First, I as I only have one machine, I have no need for a network and thus had the onboard Intel Pro 100 ve card disabled in the BIOS during the install of Ubuntu. Now, I have enabled the NIC and although Ubuntu loads I receive an error message after logging in

Cannot resolve nost name, try adding this computer name to the etc/hosts... 

right now it just has localhost.

If I select continue, it informs me that Gnome may not work correctly and that is true. After logging in, the Network Config dialogue box appears, although everything is greyed out and the timer just rotates. I tried leaving it but after several minutes it remains the same. so I cancelled the dialogue. 

Following this I have noticed that many of the commands do not work, The evolution config, Synaptic, apt etc.

I assume this is probably because  of the problem with the NIC, so my question is, how do I install and configure a driver for the NIC after installation? I read somethin about modconf but I cannot find this command and as I state later I cannot, as yet, connect to the internet through my dial up connection.

Second I have the following issue with  'Disabling IRQ #18' here is part of the syslog:

Disabling IRQ #18
Jul 15 19:19:02 avalon kernel: irq 18: nobody cared (try booting with the "irqpoll" option.
Jul 15 19:19:02 avalon kernel:  [__report_bad_irq+49/119] __report_bad_irq+0x31/0x77
Jul 15 19:19:02 avalon kernel:  [note_interrupt+117/155] note_interrupt+0x75/0x9b
Jul 15 19:19:02 avalon kernel:  [__do_IRQ+211/273] __do_IRQ+0xd3/0x111
Jul 15 19:19:02 avalon kernel:  [do_IRQ+25/36] do_IRQ+0x19/0x24
Jul 15 19:19:02 avalon kernel:  [common_interrupt+26/32] common_interrupt+0x1a/0x20


This just repeats continually.

How do I disable IRQ 18 and what is using this IRQ. It is not available in the BIOS.

Finally I am on dial up and My USR external modem was not detected so I cannot connect to the internet as yet.

Thanks for any help.

---

### Post by Morcas on 2005-07-17
Anyone please?

---

