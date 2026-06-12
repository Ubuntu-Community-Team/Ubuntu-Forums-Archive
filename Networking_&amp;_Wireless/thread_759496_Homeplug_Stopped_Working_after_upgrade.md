---
title: "Homeplug Stopped Working after upgrade"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by nicebloke on 2008-04-19
Hi,

I have a Dell PC that came with Ubuntu 7.04 pre-installed. I put this PC in an upstairs room, got myself a couple of Addon Homeplugs (it helps that I sell them) and connect up to the router downstairs. There was no configuration, just plugged in and got a DHCP network going. Lovely.

Spin on 6 months later, I decided to use the Upgrade Manager to bring the PC up to date with 7.10 - Everything goes smooth, the upgrade goes fine over the Internet, until I reboot.
Now the Network icon is saying there is no wired network found - nothing was unplugged :(

So, I bring home a pair of Dynamode Homeplugs from work to see if there is a problem with my Addon ones. Nope, it makes no difference. 

What can I do? I'm thinking of going back to 7.04 because the network worked then - but thats a wipe and re-install.

Help please, I've got 2 kids that can't get their fix of the Nick Jr website!

---

### Post by nicebloke on 2008-04-19
Anyone??

---

### Post by nicebloke on 2008-04-20
bump (still no network)

ifconfig sees the network card, so it has been detected.

Can I downgrade the network drivers to the version that was in 7.04?

---

### Post by nicebloke on 2008-04-20
Here is the output from ifconfig for eth0:

eth0      Link encap:Ethernet  HWaddr 00:1A:A0:9C:42:18  
          inet6 addr: fe80::21a:a0ff:fe9c:4218/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:3400 (3.3 KB)  TX bytes:2368 (2.3 KB)
          Base address:0xff00 Memory:fdfc0000-fdfe0000

---

