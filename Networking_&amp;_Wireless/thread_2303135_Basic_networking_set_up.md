---
title: "Basic networking set up"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by SuperGeorge on 2015-11-16
I am setting up my computer with ubuntu to act as a router to manage about 10 PC's and countless smart phone connections.   I have the basic networking part figured out i just want to be able to log web sites visited for each person on this network.   Reason being,  some of our users have found out a way around opendns and are downloading off torrents and we have recieved warning letters from comcast about losing service.

So basicaly i[m interested in setting up a basic network to support the LAN and Wifi with the ability to log websites visited in order to find who is accessing torrents if the problem arised again.  TY for ANY help.

I have till friday to get up this ubuntu desktop to handle this small network and need to be able to log webiste activity

---

### Post by TheFu on 2015-11-16
Why not just block all bittorrent traffic? That would be easier.
You might want a transparent proxy as well to perform content filtering too.

The trick is to remove all default routes for client systems to the internet leaving only the proxy machine with a route. Then have the real network router only accept connections from the proxy.  That will learn them whippersnappers!  For added fun,*disable external DNS queries from the workstations and only allow the proxy server to have access.  That will get those kids thinking "abandon all hope, ye who enter" too.  The days of the wild-west on the network will be over.  BTW, you'll likely find a few administration / teachers unhappy with this too, so let the head-person know that it is coming.

BTW, this isn't a "basic network" for most folks. This is more of an enterprise-style network. I've seen this sort of networking deployed at most corporations. It is mandatory to prevent connections that don't go through the corporate AV filters.  Those corporations often deploy an SSL cert so they can MiTM all HTTPS connections too. Absolutely necessary to prevent the kids from just switching to SSL-encrypted methods.

I'd use **pfSense** for this.  Not Linux.  It was built specifically for this type of need. The SSL-MiTM stuff is more advanced and will definitely cause issues. I've never setup that part.  We were big enough to just purchase an expensive appliance from a vendor.

Don't forget to post a warning that ALL NETWORK TRAFFIC MAY BE CAPTURED AND REVIEWED.  Can someone be expelled if you trace it back to their system?  Shouldn't be too hard to determine the NIC used and from that find the device, walk up behind and catch them doing it.  Strike-1.

---

### Post by SuperGeorge on 2015-11-19
Thanks for the good info.   i'll give this a try

---

### Post by slickymaster on 2015-11-19
*Moved to the ***Networking & Wireless*** sub-forum*

---

