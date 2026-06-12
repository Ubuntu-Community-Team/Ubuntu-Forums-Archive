---
title: "DSL/IP/Server Problem"
date: 2016-07-08
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2016-07-08
Hi Ubuntu Forums!

This problem really isn't an Ubuntu specific issue, but I've run out of options and you guys have always helped me out.

I have a server set up and it's on an AT&T DSL connection.  Lightning came through and knocked out my DSL modem/router.  I got a new one and installed it.  The internet works fine.  I can surf and do most everything just fine.  All test on the modem come back just fine and everything is in the green.  

Here's the problem.  I can't ping, traceroute, or reach my IP address from any location.  I have a Dynamic DNS service set up with noip.com and Ubuntu connects and updates it with my IP address just fine.  When I ping my domain name nothing.  When I ping my IP nothing.  It's like it's not there.  I did an online traceroute from [http://ping.eu/](http://ping.eu/) and it says "no reply from 3 hops, assuming we reached firewall."  When I do a port scan from [http://www.t1shopper.com/tools/port-scan/](http://www.t1shopper.com/tools/port-scan/) on port 22, which is open, it comes back just fine.  Everything indicates everything is good, but you cant ssh into it.  It never reaches the modem.  I've been in contact with the AT&T tech and he is clueless.  I called AT&T's help desk and they were unable to find the problem.  Before lightning came through, my server had been running a legit streaming radio station service for a few years now without issue.  I am totally out of troubleshooting options and was hoping that someone has had a similar issue. 

if anyone wants to check, the domain name is masonhill.ddns.net. 

Thanks.

---

### Post by pepsifx357 on 2016-07-08
Well, the problem somehow fixed itself about 10 minutes ago.  The only thing I can guess is that some managed switch down the road was "stuck on stupid" and some guy, sitting at a desk hit the reset button.

---

