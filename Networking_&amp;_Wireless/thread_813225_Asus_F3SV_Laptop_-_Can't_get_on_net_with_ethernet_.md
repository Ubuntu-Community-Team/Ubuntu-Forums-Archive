---
title: "Asus F3SV Laptop - Can't get on net with ethernet (Ubuntu 8.04)"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by bla on 2008-05-30
Hi, I'm a newbie to Linux and Ubuntu, could use some help.

**System Specs:**
Asus F3SV Laptop
Centrino Duo
Intel Core 2 Duo T7500
Attansic L1 Gigabit Ethernet (Now bought by Atheros)
Intel® PRO/Wireless 3945ABG 

**OS Specs:**
XP Pro (SP2) - Works 100%
Ubuntu 8.04 - kernel 2.6.24-17-generic
gnome 2.22.2
[B]

Net hardware specs:[/B]
DSL modem
Router - wired (It doesn't matter what, works 100%, including dhcp. upnp disabled though and it must stay so.)

**Problem:**
First I should say that everything on this laptop works 100% with XP.
I should also say that there are a number of computers in the house, and they all work 100% in every respect.

I installed ubuntu as a dual boot on this laptop because I wanted to give linux a try.  I used the 64bit alternate disc.

The system under ubuntu 8.04 seems to work fine, I like it.
The disc came with kernel 2.6.24-16.  

On the day I installed ubuntu everything worked including the ethernet, at least as far as I could tell.  I rebooted the laptop a number of times during the evening and the ethernet got me to the net every time.

I let ubuntu update, got a new kernel automatically.  Then I shut the system down for the night.  Next day, the etherent did not work.  After many tries and reboots I booted to the older kernel and the ethernet worked to my surprise. 

I soon discovered (after a few more boots) that it was odd luck.  Most of the time the ethernet does not work, regardless of which kernel I boot too. This makes me question if it was OK prior to the kernel update.  I had very limited time with it, just a few hours.  It could very well have been flaky from the start.  Right now, it works, and it will until I reboot or shut down.  Perhaps it will work even after a reboot if I'm lucky, but I know from experiance that it only works in 1 in 10 reboots.  It always works with XP on this very same laptop so I know it is not the router or defective hardware.

I'm new to linux, as I have said, so I don't know the console (and thus linux admin) but I tried the following:

**Console feedback:**
I should say that right now it is one of those rare times that it does work, this is what I get now.

when I type:
*ifconfig*

I get:
> eth0      Link encap:Ethernet  HWaddr EDITED OUT FOR PRIVACY 
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: EDITED OUT FOR PRIVACY Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2730 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2625 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:2720151 (2.5 MB)  TX bytes:340487 (332.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2298 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2298 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:115688 (112.9 KB)  TX bytes:115688 (112.9 KB)


At the times it does not work (most of time), I try to get a new dhcp IP,
by typing:
*sudo dhclient eth0*

Normally, I get something along these lines:
> No DHCPOFFERS received.
No working leases in persistent database - sleeping.

This is actually the first time that sudo dhclient eth0 worked (Got me on the net).  Yes I have clicked the net icon next to the clock and chose "Manual configuration" and there selected dhcp for the etherenet card.



Typing:
*modinfo atl1*  (atl1 is the driver name I take it)

I get:
> 
filename:       /lib/modules/2.6.24-17-generic/kernel/drivers/net/atl1/atl1.ko
version:        2.0.7
license:        GPL
description:    Attansic 1000M Ethernet Network Driver
author:         Attansic Corporation <xiong_huang@attansic.com>, Chris Snook <csnook@redhat.com>, Jay Cliburn <jcliburn@gmail.com>
srcversion:     D4A09843942F6B8C6009011
alias:          pci:v00001969d00001048sv*sd*bc*sc*i*
depends:        mii
vermagic:       2.6.24-17-generic SMP mod_unload 
parm:           int_mod_timer:Interrupt moderator timer (array of int)
parm:           flash_vendor:SPI flash vendor (array of int)

---

### Post by mahmoos.sajjadi on 2008-06-01
> **bla said:**
> Hi, I'm a newbie to Linux and Ubuntu, could use some help.

**System Specs:**
Asus F3SV Laptop
Centrino Duo
Intel Core 2 Duo T7500
Attansic L1 Gigabit Ethernet (Now bought by Atheros)
Intel® PRO/Wireless 3945ABG 

**OS Specs:**
XP Pro (SP2) - Works 100%
Ubuntu 8.04 - kernel 2.6.24-17-generic
gnome 2.22.2
[B]

Net hardware specs:[/B]
DSL modem
Router - wired (It doesn't matter what, works 100%, including dhcp. upnp disabled though and it must stay so.)

**Problem:**
First I should say that everything on this laptop works 100% with XP.
I should also say that there are a number of computers in the house, and they all work 100% in every respect.

I installed ubuntu as a dual boot on this laptop because I wanted to give linux a try.  I used the 64bit alternate disc.

The system under ubuntu 8.04 seems to work fine, I like it.
The disc came with kernel 2.6.24-16.  

On the day I installed ubuntu everything worked including the ethernet, at least as far as I could tell.  I rebooted the laptop a number of times during the evening and the ethernet got me to the net every time.

I let ubuntu update, got a new kernel automatically.  Then I shut the system down for the night.  Next day, the etherent did not work.  After many tries and reboots I booted to the older kernel and the ethernet worked to my surprise. 

I soon discovered (after a few more boots) that it was odd luck.  Most of the time the ethernet does not work, regardless of which kernel I boot too. This makes me question if it was OK prior to the kernel update.  I had very limited time with it, just a few hours.  It could very well have been flaky from the start.  Right now, it works, and it will until I reboot or shut down.  Perhaps it will work even after a reboot if I'm lucky, but I know from experiance that it only works in 1 in 10 reboots.  It always works with XP on this very same laptop so I know it is not the router or defective hardware.

I'm new to linux, as I have said, so I don't know the console (and thus linux admin) but I tried the following:

**Console feedback:**
I should say that right now it is one of those rare times that it does work, this is what I get now.

when I type:
*ifconfig*

I get:



At the times it does not work (most of time), I try to get a new dhcp IP,
by typing:
*sudo dhclient eth0*

Normally, I get something along these lines:


This is actually the first time that sudo dhclient eth0 worked (Got me on the net).  Yes I have clicked the net icon next to the clock and chose "Manual configuration" and there selected dhcp for the etherenet card.



Typing:
*modinfo atl1*  (atl1 is the driver name I take it)

I get:




HI Friend
Please Test this Command in Konsole :

$ sudo ifconfig -a

this command search for all network interfaces as like as WLan
Lan and ....

be happy forever and ever:popcorn:

---

### Post by bla on 2008-06-01
Hey there, thanks for your help.

I've been trying to get online for the past hour...
It is again one of those few lucky times that I got online with ubuntu.
Xp always works (so it is not hardware, cable, or router).

I just want to add that in the router I have a STATIC DHCP IP set for
the laptop ethernet.  That ip is 192.168.0.100.
The routers ip is 192.168.0.138.  So anyway... the interesting thing about setting ubuntu to dhcp is that it know all this as can be seen from the
sudo ifconfig output i posted above... 
Sometimes it works, sometimes not...but it always seems to know because of having info cached.

I've now set things to a manual config and entered the values by hand.
I tried this before, it did not work.  I tried it a few times today, it did not work.  Now with the same thing, it works.  No typos were made for sure.  Basically it looks as flaky as dhcp was.

When I have probs again, I'll post the sudo ifconfig (with the "-a"), as you want.

I should also mention, that i have disabled IPv6 in ubuntu yesterday and that did seem to help a bit but still flaky.

---

### Post by bla on 2008-06-03
> [UN EDITED OUT]@ubuntu:~$ sudo ifconfig -a
[sudo] password for [UN EDITED OUT]: 
```
eth0      Link encap:Ethernet  HWaddr [MAC EDITED OUT XX:XX:XX:XX:XX:XX]  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4359 (4.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9864 (9.6 KB)  TX bytes:9864 (9.6 KB)
```

The above is what I get when it doesn't work.

The internal IP: 192.168.0.100 you see above is correct.  This is the _**static dhcp**_ ip set for my laptop's mac in my dlink router.  This is also the ip i set in the manual config of ubuntu.

The router IP is also correct.

Yet...doesn't work.

If i unplug/replug the lan cable a few times, then eventualy it works.
This however for sure is not a cable, router issue, because with the exact hardware on this very laptop evrything works 100% with XP.

---

### Post by bla on 2008-06-07
c'mon... no one can help?

---

