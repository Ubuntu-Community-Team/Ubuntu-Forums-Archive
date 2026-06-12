---
title: "[SOLVED] Why is pan0 showing up in Firestarter?"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by randy78 on 2008-10-24
Strange... I started Firestarter only to notice 'pan0' directly below eth0...

What would set up a personal area network by itself?

I'm running Intrepid beta, and my box is connected to a DSL router (westell) directly using an ethernet cable.

Here's the terminal output from ifconfig pan0:
" ifconfig pan0
pan0      Link encap:Ethernet  HWaddr be:6c:98:c1:9e:b0  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)"

and here's the output from ifconfig eth0:
"eth0      Link encap:Ethernet  HWaddr 00:14:2a:4a:3a:e5  
          inet addr:192.168.1.47  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:fe4a:3ae5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:187216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:254964675 (254.9 MB)  TX bytes:8192801 (8.1 MB)
          Interrupt:19 Base address:0xe800"

Why would this be showing up?

I haven't configured any new devices on the network, and wireless is not activated either.

I'm perplexed by this, especially since it has its own hardware address...

[IMG]http://img340.imageshack.us/img340/3931/pan0ck6.png[/IMG]

---

### Post by ryry46d9 on 2008-10-24
not sure if this doc will help but here it is   [http://affix.sourceforge.net/affix-doc/c1051.html](http://affix.sourceforge.net/affix-doc/c1051.html)

little clip from it  :

Personal Area Networking Profile (PAN)  allows Bluetooth devices to form an ad-hoc network, access a remote network through a network access point


look around in iwconfig 

happy hunting

---

### Post by randy78 on 2008-10-24
Thanks for the heads-up ;)

Now that I think about it, a bunch of Bluetooth apps were installed with the most recent update...

I don't have any Bluetooth devices, so I have no need for these tools and will be uninstalling them in short order to see if that'll do the trick.

Will report back here asap.

:guitar:

Update: Okay... I removed several Bluetooth applications using Synaptic, restarted Firestarter and all is well again. Note that I left libbluetooth3 alone, because it looked like it would have removed a bunch of other applications if I had uninstalled it.

---

