---
title: "Dual Lan card server issues"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by Larren on 2015-07-01
I have a server running 14.04 lts with dual lan cards. I was in the process of setting everything up and wanted to bond the lan cards for load balancing. After I set up the connection the pings would drop out so I removed the bond and went back to default. The problem is still there and I am not sure what to look for to resolve this issue??

---

### Post by tgalati4 on 2015-07-01
Welcome to the forums.  What procedure did you follow to set up the bonding?

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by Larren on 2015-07-01
Thank you tgalati4. I used the ifenslave method. The exact one you posted.

---

### Post by tgalati4 on 2015-07-02
Install *iperf*.  Set up one instance on your server and set up another instance on other machines on your LAN.  Then test each card separately, then together.  Post the results.

[http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes](http://askubuntu.com/questions/7976/how-do-you-test-the-network-speed-betwen-two-boxes)

Bonding will usually improve speeds to multiple clients, but not necessarily between two machines.

[http://askubuntu.com/questions/431775/why-bonding-does-not-improve-network-speed](http://askubuntu.com/questions/431775/why-bonding-does-not-improve-network-speed)

---

### Post by Larren on 2015-07-03
I will do that as well. But I think it is something else going on. I went to install iperf and the connection dropped, at the same time I am running a repeated ping to google that will drop out about 80% of the time. But the ping to my router never drops out. I checked the settings that the lan cards have configured through dhcp right now and it all matches up with my network. I am probably overlooking something but I am really lost on this one. Sorry for my slow reply I have been out of my shop and with the constant drops on the server I cannot keep a remote connection going.

Edit: I do notice that it is consistent. I will rcv 8 ping replies and then miss about 24, then repeat... If that helps?!?

---

### Post by tgalati4 on 2015-07-03
You need to describe your network.  You have 1 server with 2 LAN cards that are connected to what?

---

### Post by Larren on 2015-07-03
My network is pretty flat. I have a router with built in firewall connected to a gig port on a Cisco small business switch. From that small business switch everything is connected from there. The two ports on the server are connected on the same switch. Could it be causing issues because it's on the same switch??

---

### Post by tgalati4 on 2015-07-04
You may need to spend some time with the router and the Cisco switch and examine the policies of both.  It's possible that there is a conflict between them that is causing packet drops.  Try turning the policies off on the Cisco router and see if performance improves.  The *iperf* results should show full throughput between 2 computers on your LAN and the server (all connected to the Cisco switch).  Verify that first.  Then troubleshoot your performance out to the web.

---

### Post by Larren on 2015-07-05
Well the problem is going out to the web. I do not have any issues with another server on my network. I can establish connections to it with no issues and also vpn sessions with no glitches.

---

### Post by tgalati4 on 2015-07-06
Does the other server have a dual-LAN connection that is similar to the problematic server?  Perhaps you have cabling problem.  Try different cables and different ports on the switch.

---

### Post by Larren on 2015-07-09
Excuse my absence. I went back to basics and disabled the second lan port on the switch going to the server. As soon as I did that, the pings out to ole famous 8.8.8.8 went through with no problems!! I will dig down further into the lan settings to verify everything is where it is supposed to be when I have a little more time. I will also go through the bonding setup again and attempt to enable the second port again. Thanks for your help and patience.

---

