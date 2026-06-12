---
title: "My internet connection drops without reason"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by _Seven_ on 2008-11-11
Hi guys.

Well i don't know what is happening but my internet connection drops without reason. I think that it happen only when i left the connection idle for some minutes, but this is not normal. I am using Ubuntu since version 6.10 and this situation never happened to me but i installed the version 8.10 and this is happening.

While i have internet, if i type **sudo ifconfig** on a terminal, this is the output:
Link encap:Ethernet  HWaddr 00:19:99:47:5d:04 
          inet addr:10.231.1.103  Bcast:10.231.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:99ff:fe47:5d04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8988 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:6042005 (6.0 MB)  TX bytes:1294726 (1.2 MB)
          Memory:d0020000-d0040000 

after i loose the connection, i type the same command and this is the new output:
Link encap:Ethernet  HWaddr 00:19:99:47:5d:04 
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:99ff:fe47:5d04/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25651 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:11747711 (11.7 MB)  TX bytes:2212033 (2.2 MB)
          Memory:d0020000-d0040000 


Why the IP, Mask and Bcast change?
What is happening?

Thank you guys.

---

### Post by Jayock on 2008-11-11
Something is screwey with your network.  Are you running DHCP?  You are getting assigned IPs on two completely different subnets.

---

### Post by _Seven_ on 2008-11-11
Yes, on IPv4 tab of the connection (in NetworkManager Applet) i have Automatic(DHCP).

Put it fixed will work?

---

### Post by Jayock on 2008-11-11
Describe your network setup.  10.x.x.x addresses are typical of a large (e.g. university, business, cisco network) 192.168.x.x are typical of smaller (e.g. home, small office, netgear, linksys network).  You are getting both, which makes me think that you have 2 DHCP servers somewhere on your network.

---

### Post by _Seven_ on 2008-11-11
yes that's right. I'm in a university and in my office i have a simple switch to connect PCs to the net

---

### Post by Jayock on 2008-11-11
The switch doesn't have a built-in DHCP server, or an external DHCP server connected to it does it?

---

### Post by _Seven_ on 2008-11-11
no, is just a simple switch

---

### Post by Jayock on 2008-11-11
It seems that you are getting an address from another DHCP (Netgear or Linksys router perhaps?).  And this is causing the problem.  I would investigate what is between your computer and the university network.  You are getting some problems there.

---

