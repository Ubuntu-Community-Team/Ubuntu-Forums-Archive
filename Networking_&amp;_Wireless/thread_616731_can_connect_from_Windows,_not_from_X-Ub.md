---
title: "can connect from Windows, not from X-Ub"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by mringer on 2007-11-18
Dual booting PC, MS Win 2K and XUb 7.10. Trying to connect via D-link broadband router, GSL-D624T,
using wire from PC to router and phone line. (I havent yet tried the wireless connect from PC to
router).


ISP was Globalnet.com : now taken over by madasafish .
I chose Global because they were recommended by Which, but it now seems that this was a bad choice. When I contacted their support address, they said they cannot give any help. 

Most of the time I can connect via firefox when booted in W2K, I cannot connect to any known
website when booted in XUb .  

I have set the net I-face to use DHCP. 

I can ping both  ubuntu.com  and its  IP address (& get replies).

I can connect to the router, which says:

status: connected. 

It runs a primitive set of tests:

ethernet LAN connect: Pass
ADSL sync: Pass
ATM OAM segment ping: fail
ATM OAM end to end ping: fail
ping primary domain name server: pass

The router also has a v. large set of settings, too many to be repeated here, I searched D-link's
site & didnt find any doc to say what these should be. 

please any advice?

---

### Post by rmemm on 2007-11-24
If you can connect via windows you should be about to connect with Ubuntu if you use the same settings on ubuntu and there is no special ISP related software needed on the Windows side.

I assume your using a routing configuration on the router -- not a bridging one?  If this is so -- then DHCP should work.  I assume your using DHCP on the windows site?

The other comment I have -- IF your using routing mode on your router -- you might want to try configuring with static IPs on your private LAN side and using a correct IP and netmask for you host, configuring the known gateway address of your router, and hard coding 2 known DNS servers at your ISP.

There is no reason why this should be needed -- but particularly for DNS servers, I found hard coding more reliable in my case and I in fact use static.

Other thing you might look at -- you might want to consider turning off IPV6.  I had a connection problem when I purchased a laptop a few years ago and that was the cause for some reason.  I can't remember -- but I think it was something to do with the Firefox config of all things.  Let me know if you'd like me to see if I can find my notes about this.

So don't know if either of these will help you -- food for thought anyway.

Rob

---

