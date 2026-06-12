---
title: "PLEASE HELP!!! connect to the internet with vmware..."
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by shayzweig on 2007-12-13
hi,
I have vmplayer 2.02 installed on my computer.
and I have an ubutnu 7.10 image running on it.
I can't connect to the internet.

the connection is bridged (although I also tried NAT)

I have a pppoe connection...
I tried to configure using pppoeconf and the cofiguration was ok.
the connection can not be established and I get the message:

pppd[3908]:Timeout waiting for PADS packets
pppd[3908]:Unable to complete PPPoE Discovery.

I searched threw all the forums trying to get something and wasn't able.

here are stuff I tried:
ping to any address does not work...
when switching to NAT the pppoeconf did not work.

and many other stuff I read all over the web...

any Ideas anybody???

thanks...

---

### Post by Blown306 on 2007-12-13
I had the same problem...the AV/Firewall software on the host was blocking all the traffic to the virtual NIC.

In my case I was running 2003 Server as a host with VMWare Server, but it could be the same issue for player I suspect.

---

