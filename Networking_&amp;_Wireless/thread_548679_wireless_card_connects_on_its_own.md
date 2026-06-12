---
title: "wireless card connects on its own"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by ranamalo on 2007-09-11
hello all,
I have a wireless/general networking issue.  I'm in feisty on a toshiba satellite M55-S3314. I have two network connections (eth0 Intel Pro/Wireless Network Connection 2200BG and eth1 Marvell 88E8036 10/100 Base-TX Ethernet wired card).  When I start up with my cable plugged in and only eth1 defined in /etc/network/interfaces.  My interfaces doc is as follows:

auto lo
iface lo inet loopback

iface eth1 inet dhcp
auto eth1


My wireless card (eth0) just connects on its own to an unsecure wireless network in my building that I don't know.  I then have to shut my wireless card off manually (the little switch on the front of the laptop) and then bring down and back up again networking in order to get my network connected right:

/etc/init.d/networking restart


ifdown eth0 obviously doesn't work as eth0 is not defined!

Anyone know why my rogue wireless card is doing this??
I would appreciate any ideas on guys.  Thanks in advance

---

### Post by reckless2k2 on 2007-09-11
i'm wild guessing but how about defining the wifi card and not having it auto start. or just keep the switch for wifi turned off and turn it on only when you want to use wifi? 

there is a hotplug script as well too that will detect rj-45 plugged in as well and use that until unplugged. hence hotplug. haha.

---

### Post by ranamalo on 2007-09-13
Thanks for your reply.  Could you post the hotplug script?  The thing is, it didn't do this before.  It just started doing this a few days ago.  I would like to know why.  I'd also like to have the choice to just activate the wifi from within the OS if possible.  Turning on and off a switch just seems to low-tech!!

---

### Post by nickmcg on 2007-09-13
You can disable the network card - System->Administration->Network, select eth0 and disable the connection, or you can edit /etc/network/interfaces and remove the line 
auto [wireless interface]

HTH

Nick

---

### Post by reckless2k2 on 2007-09-13
hotplug is in synaptic

then you can google or query it in these forums.

---

### Post by karvec on 2007-09-13
wicd is a good option too, you can select networks to connect automatically.

---

### Post by ranamalo on 2007-09-17
Thanks for the replies.  sorry it has taken me so long to respond...crazy week at work.  Anyway, I searched for hotplug in synaptic.  There was nothing called hotplug perse, but the following options came up:
atmel-firmware
fxload
kcontrol
libaws-dev
libxi6
libxi6-dbg
libxi-dev
multiseat
usbmgr
wacom-tools

I wasn't sure which one I wanted, so I also searched with aptitude and aptitude only came up with fxload.  So I installed that.  Anyway, it seems to be working.  I'm really not sure if that was it though.  Thoughts?

---

### Post by Mr.Beast on 2007-09-17
> **ranamalo said:**
> Thanks for your reply.  Could you post the hotplug script?  The thing is, it didn't do this before.  It just started doing this a few days ago.  I would like to know why.  I'd also like to have the choice to just activate the wifi from within the OS if possible.  Turning on and off a switch just seems to low-tech!!

In this modern day, low tech is good. (Well, I think it is anyway!)  it also saves power by shutting the device off when you don't need it. 
Why look further? (O.K. it's good to understand the why, and the how) 
Use the switch. It's what it was intended for.

---

### Post by Gflo on 2007-09-17
at least your card connects

---

### Post by ranamalo on 2007-09-22
Mr. Beast,

I hear you on the thought behind the "saving power" thing on a laptop.  That makes sense, but I, as you did mention, want to understand everything that is happening on my ubuntu box.  There is obviously something I don't understand if my wireless card--that is not even defined in /etc/network/interfaces--is connecting on its own.  Perhaps you can help me out and explain to me why that is?  I'm not a nb to linux, but I don't have a lot of experience with wireless.  All my experience with wired interfaces points to: if it is not defined in /etc/network/interfaces, or wherever your distro stores your network configurations, the thing does what its supposed to do: SWEET NOTHING.  And further, if you try to make it do something (e.g. ifdown) linux tells you hey that card is not configured.

Anyway, perhaps it's the gui doing weird things?  I don't trust gui configurations.  I feel much more at home in a shell....

But seriously if anyone has an idea of what is happening, I'm all ears.

Hey Gflo what's this "at least your card connects" talk?  What's up?  Does your card not connect?

---

