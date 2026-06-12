---
title: "routing trouble?"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by liquid8d on 2006-08-23
Hi,

  I have just recently setup [jinzora](http://jinzora.org/) for media sharing, which is great. It works great on my local lan, but for some reason, I cannot access it outside of the local network. Port 80 which Apache is using is forwarded to the local ip of my machine. I even have a subdomain for my domain forwarding to the wanip/jinzora location and it works, but only from my lan. I have no firewall setup.

The only reason I can figure is that my route table is messed up. Out of the box, you should be able to install apache, and forward port 80, and everything work great. 

When Apache is restarted, I get the following:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

Now, if it is using local loopback only, wouldn't that mean the rest of my machines wouldn't be able to access it as well?

I by no means understand a large chunk of how routing works, but I understand the basic concepts.

Here's what I have:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.59.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
t

My machine is at 192.168.0.104, and the router is at 192.168.0.1. I am not sure if maybe the vmware adapter may have caused the problem or maybe it's just a stupid configuration error on my part.

Any help would be appreciated.

---

### Post by liquid8d on 2006-08-23
ok, so forget all that.. it appears it's an apache configuration issue, i am able to do ftp just fine. So now I need to figure out that... help again would be appreciated (and if this topic could be moved to the correct forum).

---

