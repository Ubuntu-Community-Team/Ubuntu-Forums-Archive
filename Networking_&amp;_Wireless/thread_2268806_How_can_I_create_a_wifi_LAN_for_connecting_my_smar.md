---
title: "How can I create a wifi LAN for connecting my smartphone?"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by diego35 on 2015-03-11
Hi!!
I'm new in this world and I don't control a lot of things, I'm making a local server and I want to test it using my phone. 
Can anyone explain me how to create a wifi LAN?

Thanks

---

### Post by TheFu on 2015-03-11
If you have a wifi router, you just need to know the IP address of the server - hopefully that is static. Lots of how-tos for that.  Search for "ubuntu static ip" will find them.

Then connect your phone to the wifi network on the router and point it at the server IP and the specific service you are running.  

So .... if the router LAN IP is 192.168.0.1 and the "server" IP is 192.168.0.100, then just point your phone at 192.168.0.100. Chances are your phone IP will be 192.168.0.101 or something like that.

We cannot be more specific since you didn't say what you were serving. A few options:
* http
* https
* ssh/scp/sftp
* cifs
and there are tens of thousands of other services.

So it would be really smart if you made the "server" have a static IP, otherwise it might change. For most people, using a DHCP lease for their home systems is the easiest way.  [http://www.howtogeek.com/69612/how-to-set-up-static-dhcp-on-your-dd-wrt-router/](http://www.howtogeek.com/69612/how-to-set-up-static-dhcp-on-your-dd-wrt-router/) might be helpful.

---

