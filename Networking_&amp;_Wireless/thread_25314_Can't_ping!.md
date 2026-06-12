---
title: "Can't ping!"
date: 2005-04-09
forum: Networking &amp; Wireless
---

### Post by lgb on 2005-04-09
I'm having trouble with my  network. Everything was working fine until I did an update last evening. I have internet access but I can't ping either to or from this machine. VNC doesn't work either. My router shows this machine as connected. It's getting the ip address ok by dhcp. Any ideas? Thanks.

---

### Post by edubarr on 2005-04-09
Run 'sudo ifconfig eth0' and have a look at the configuration. Also try renewing the connection with ifup and ifdown and see if this has any effects. Have a look a the man pages for those commands, they are quite handy.

---

### Post by lgb on 2005-04-09
Here's what I get. Doesn't mean too much to me :D

eth0      Link encap:Ethernet  HWaddr 00:09:5B:83:17:8F
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::209:5bff:fe83:178f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:639 errors:0 dropped:0 overruns:0 frame:0
          TX packets:660 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:256267 (250.2 KiB)  TX bytes:76626 (74.8 KiB)
          Interrupt:11

I did the other commands and stiil lose all packets... Time for more reading LOL

---

### Post by edubarr on 2005-04-09
Well, this just tells you what ip was assigned to your computer and also what's going on with the network card. 

The ip address for your machine is 192.168.0.2, so you can try and ping that from another machine, if that's not the same ip you had before. Everything seems normal to me, but I'm a newbie too, so I'm probably missing some details here. One thing that I forgot to ask is if you have your name server set on /etc/resolv.conf. Also, try running just 'sudo ifconfig' and see if you have any other interfaces besides eth0 and lo (loopback). Also have a look at the interfaces man pages, this could give you some configuration hints too.

I don't have any system running with ipv6 but I don't think this would cause trouble or conflict with ipv4. 

Hope you get it fixed soon. :-)

EDIT
Your nameserver is probably something like 'nameserver 192.168.0.1' which is kinda standard for routers.

---

### Post by lgb on 2005-04-09
No other interfaces exist. I can ping the router but not the other machines on the network. My other machines  can ping each other. This is really weird... :-s

---

### Post by lgb on 2005-04-10
Issue resolved. I don't know why but a reboot of the router solved the problem. :D

---

