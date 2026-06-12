---
title: "understanding ifconfig"
date: 2010-07-20
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-20
So ifconfig tells me that my ip address is 192.xxx.x.x. But gmail tells me that my ip address is 24.xxx.xxx.xxx. Why is there this discrepancy?

---

### Post by sikander3786 on 2010-07-20
192.xxx.x.x is your local ip address and what google is telling you is your public ip address. Nothing to worry :-)

---

### Post by shazbut on 2010-07-20
[Lookup NAT]("http://en.wikipedia.org/wiki/Network_address_translation")

---

### Post by varunendra on 2010-07-20
192.x.x.x is your LAN address, i.e. the address of your pc on your local network (Internal IP), while 24.x.x.x is your WAN address (or, External IP).

By local IP, PCs & other network devices on your local network detect & communicate with each-other, while the outer world (including gmail) can see only your 'External' IP & would connect with you through that one.

---

### Post by Chris1274 on 2010-07-20
Excellent, that link is exactly what I was looking for, thanks!

---

### Post by Chris1274 on 2010-07-20
> **varunendra said:**
> 192.x.x.x is your LAN address, i.e. the address of your pc on your local network (Internal IP), while 24.x.x.x is your WAN address (or, External IP).

By local IP, PCs & other network devices on your local network detect & communicate with each-other, while the outer world (including gmail) can see only your 'External' IP & would connect with you through that one.

So if ifconfig tells me my internal IP, what function would tell me my external IP?

---

### Post by shazbut on 2010-07-20
Your router config/status page, or a web page like [http://www.whatsmyip.org/]("http://www.whatsmyip.org/").

The external IP is assigned by your ISP, the internal one usually comes from your router's DHCP server and will most likely be a private (non-routing, RFC1918) IP. (10.X.X.X, 192.168.X.X, or much less likely 172.16-31.X.X.

---

### Post by lisati on 2010-07-20
> **shazbut said:**
> Your router config/status page, or a web page like [http://www.whatsmyip.org/]("http://www.whatsmyip.org/").

<aside>There are a few such pages around. The ones I regularly use can also be used if you want to troubleshoot email problems, e.g. [www.debouncer.com](www.debouncer.com) and [www.blacklistalert.org](www.blacklistalert.org) </aside>

---

### Post by Chris1274 on 2010-07-20
Here's what I find confusing: it seems like 192.168.1.X is a very common internal IP address. So let's say I want to open up an ssh connection with a computer with (say) address 192.168.1.10. It seems quite possible that a router in another LAN may have assigned that very same address to one of its own hosts, different from the one I want to connect to. Granted they have two different external IP's, but when I open the ssh connection, I still type: ```
ssh user@192.168.1.10
``` and *voila*, I'm connected to the right host and not to the other one, even though they both have LAN address 192.168.1.10. How does that work?

---

### Post by mikewhatever on 2010-07-20
You can only use 192.168.xxx to connect from inside the LAN. If you are outside the LAN, that wouldn't work cause you'd have to use the real IP, the one seen from outside.

---

### Post by Chris1274 on 2010-07-20
I see, so if I planned on opening an ssh connection from my laptop in some far away wifi cafe with my home desktop computer, I would have to know the external IP address of my desktop, I couldn't just do ifconfig to get the LAN address and use that from the cafe?

---

### Post by marshmallow1304 on 2010-07-20
Correct.  This is where port forwarding comes in.  If you wanted to have ssh access to a computer on another LAN, you'd have to set up the router on the other LAN to forward port 22 (or whatever you're using for ssh) to the computer that's running the ssh server.

The client tries to connect on port 22 of the server-side external IP and the server-side router sends on the connection to a predetermined local IP.


Example:

Client (192.168.10.101) -> (192.168.10.1) Router (67.23.146.89) => INTERNET => (24.71.129.12:22) Router w/port forwarding (192.168.10.1) -> (192.168.10.222:22) Server

---

