---
title: "getting dhcp to wireless"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by glenndavy on 2006-09-17
hi 
I've got a kubuntu box as my server (bind9 and dhcp3-server), a kubuntu laptop, and a ubuntu laptop. everythings trundled along just fine since I installed *ubuntu - till 3,4 days ago - all of a sudden neither laptop could get on the network.

I Watched syslog on both the laptop and the server - and I could see that the laptop was asking for an address, but nothing was happening on the server:confused: 

Anyhow I had no prob getting a wired connection going - so I did this, installed networkmanger, and gnome or k networkmanager as appropriate. Starting with the kubuntu box I eventually got this going - it seems an important step was to remove any reference to any of the interfaces in the /etc/network/interfaces file.

I tried the same logic on the gnome Ubuntu laptop, but Im still getting the same results as before - I can use nm-tool to see that the wep key is accepted, but when the laptops syslog is showing DHCPREQUESTS on 255.255.255.255 port 67 - nothing is appearing in the servers dhcp ](*,) - what do I need to do?

Thanks  for any help - going crazy here
Glenn

---

### Post by zoggop on 2006-09-17
Hey, I have just the same problem!  The one thing I can find in the syslog that seems to represent an error is: "ADDRCONF(NETDEV_UP): eth1: link is not ready"
Do you get that same error?
The ultraweird thing about this is that it all of a sudden started working a week ago, and then stopped working a few days ago, with no changes from me.  I just started the computer up one morning and it worked.  No longer, though, and I can't seem to find the point at which it worked in old syslogs.
AAA!

---

