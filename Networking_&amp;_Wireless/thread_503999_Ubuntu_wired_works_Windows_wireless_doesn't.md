---
title: "Ubuntu wired works Windows wireless doesn't"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by prdack on 2007-07-18
Hi Guys,
I have a desktop running Ubuntu fiesty, and everything is fine apart from a few niggely bits, one of them being my network.
I have a netgear router which connects my desktop through the cable, I also have a windows laptop to run wireless. Before I installed ubuntu on my desktop the wireless worked great, but once installed I cannot connect to it, well I get connected but I cannot access the internet. Last night I did a system restore on the laptop and could connect to the wireless network and surf the net, until that is I turned on the ubuntu desktop and then the wireless stopped working again. I know this is something simple but I cannot find a solution, oh and by the way I can connect the laptop with ethernet and have both machines surfing the net at the same time.

Cheers,
Paul

---

### Post by kevdog on 2007-07-18
Thanks for the editorial but you are going to have to tell us a lot more about your system hardware, drivers than what was posted above.  Its impossible for me to help you, unless you help us by giving us more info about your system.

---

### Post by prdack on 2007-07-18
> **kevdog said:**
> Thanks for the editorial but you are going to have to tell us a lot more about your system hardware, drivers than what was posted above.  Its impossible for me to help you, unless you help us by giving us more info about your system.

Desktop Emachines 220
Unbuntu Fiesty
intel 2.5ghz 
640 mb ram
shared graphics card 64mb

Laptop Toshiba satalite m70
Windows xp home sp2
Intel celeron 1.74 ghz
512 ram
ati reoden graphics card.

Is this ok?

---

### Post by kevdog on 2007-07-18
I just not getting a clear picture.

It is your desktop you are having a problem with?? This is the ubuntu machine?

or is it your laptop you are having a problem with??

What is your problem - a wired or wireless problem, and on which machine.  Assuming one of the above, do you use network or wireless cards -- if so what are they??  Are they connected to a wireless router??

Just basics, because its hard to make head or tails of what you are having specifically a problem with.

---

### Post by prdack on 2007-07-18
> **kevdog said:**
> I just not getting a clear picture.

It is your desktop you are having a problem with?? This is the ubuntu machine?

or is it your laptop you are having a problem with??

What is your problem - a wired or wireless problem, and on which machine.  Assuming one of the above, do you use network or wireless cards -- if so what are they??  Are they connected to a wireless router??

Just basics, because its hard to make head or tails of what you are having specifically a problem with.

The problem is my windows laptop, I can connect to the wireless router but not the net, since ubuntu has been on my desktop machine connecting to the router through ethernet.
The wireless card I am trying to connect with on my laptop is a intel pro wireless 2200bg.
I can though connect to the net with my laptop if I plug in the ethernet cable.

---

### Post by kevdog on 2007-07-18
Now you are giving more useful info.

Cut and paste result of the following typed at command prompt:
lshw -C network

---

### Post by lisati on 2007-07-18
The title of this thread (Ubuntu wired works Windows wireless doesn't) suggests that you might have to run the Windows network setup wizard again. The copy of XP Home I have sometimes gets a little "confused" and occasionally needs help "remembering" what its settings should be.

---

### Post by prdack on 2007-07-19
> **kevdog said:**
> Now you are giving more useful info.

Cut and paste result of the following typed at command prompt:
lshw -C network

description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 10
       serial: 00:40:2b:6e:49:37
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-20ff iomemory:e8110000-e81100ff irq:20

---

### Post by prdack on 2007-07-20
kevdog have you got any ideas on my problem yet?

---

