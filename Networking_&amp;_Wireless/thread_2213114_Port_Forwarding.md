---
title: "Port Forwarding"
date: 2014-03-24
forum: Networking &amp; Wireless
---

### Post by thedork012 on 2014-03-24
Good evening.

I recently successfully installed shellinabox on my system so that I could access it from systems without an ssh client.  I forwarded the appropriate ports, got a dns name from no-ip.com, and everything was working great.  Then, the next day it stopped working due to an improperly configured ddclient that assigned my LAN ip to the dns name.  I got ddclient configured correctly and assigned the correct ip address to the dns name. It now responds to ping using said name and appears to be working.  However, now my port forwards appear to be broken, as shellinabox is still not working from outside the lan.

Details:
-Accessing shellinabox, ssh, and apache work perfectly from within my lan. 
-Accessing any of those services (all of which have the necessary ports forwarded on my router) fails from outside my lan.
-The above are true when trying to access via dns or ip address
-The router responds to ping from outside of my lan using ip address or dns

It obviously seems like the router is not properly forwarding ports, but that is hard to believe since it worked perfectly on day one.  And yes, I have checked to make sure my internal IP has not mysteriously changed.  It is configured to forward to my system's current IP.  I have also power cycled the router a few times and gotten the same results after.

Is there anything that I could be missing here?  As I said, it just seems hard to believe that port forwarding would work one day and fail completely the next.  Any input is much appreciated.

Additional info:
-The router I am using is an xfinity combo router and modem running version 7.6.59N, image name TS070659N_010914_MODEL_862_GW_CT


UPDATE:
-I configured DMZ host on the router to point to my system and got the same results
-http://www.yougetsignal.com/tools/open-ports/ reports all forwarded ports as OPEN
-There is a second router between my system and the main router, but it is configured as an access point only (no firewall, no DHCP)

---

### Post by thedork012 on 2014-03-26
This turned out to be a NAT loopback issue.  I have never had an issue with NAT loopback on a router before, and especially since it was working fine initially, I didn't even think to check at first.  So the connection works fine from literally outside the network, but only works using IP address from inside the network.

An annoyance but easily solvable by setting hosts files on necessary systems.  It is still strange that NAT loopback stopped working but I can live with it...

---

