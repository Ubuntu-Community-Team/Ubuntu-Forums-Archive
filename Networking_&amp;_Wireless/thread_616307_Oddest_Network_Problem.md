---
title: "Oddest Network Problem"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by deltafun on 2007-11-18
Hi

My network setup is as follows:

Router (192.168.16.60) -->Windows PC (192.168.16.1)
   |
   |------> Laptop ( Wireless 192.168.16.2)
   |
   |-----> Belkin Wireless G Adapter ( 192.168.16.65 )
                   
                   
                   8 Port Switch ( Attached to the belkin )
                       |
                       |----> Desktop - Ubuntu 7.10 Desktop ( 192.168.16.70 )   
                       |
                       |----> Server - Ubuntu 7.10 Server (192.168.16.71 )

Both Ubuntu machines are static IP`s not DHCP.

The problem:

Ubuntu Desktop can ping Ubuntu Server, Belkin Adapter, Router and has full access to the internet.
 
Ubuntu Server can ping Ubuntu Desktop, Belkin Adapter ONLY.

All network config is identical on each Ubuntu machine as far as I can see.

All I want is for the Ubuntu server to have access to the internet - but am totally stumped as to why its not working - but can access the desktop and the belkin device.

I have tried having just the server connected to the switch - but no change.

I am sure it is probably something simple, but I can`t for the life of me find a difference between the Ubuntu desktop and server machine.

Can anyone suggest anything or give any clues?

Thanks in advance :)

---

### Post by conjur3r on 2007-11-18
Any firewall rules?
# sudo iptables -L

Can you do name resolutions from the server?
# host google.com

Can you ping from the server to your router?  Also test from a machine that works and compare results
# ping 192.168.16.60

---

### Post by deltafun on 2007-11-18
No firewall stuff.

DNS resolutions failed because no route to the router.

I have fixed it now by changing the belkin wireless bridge for a 3com wireless bridge - works fine without changing anything on the ubuntu machines.

So the problem appears to be that the belkin adapter does not like having more than one machine attached to it - however I did try with the desktop machine off and only the server machine on - still the same problem.
So must be something weird with the belkin wireless adapter :(

---

