---
title: "[SOLVED] Need help with DNS problem (Internet Connection Sharing)"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by black3ug on 2008-11-14
I'm setting up Internet Connection Sharing using a Ubuntu Hardy machine as the gateway. Here are the details:

eth0 - DSL modem / external network
     - DHCP

eth1 - LAN / local network
     - set to 192.168.0.1

I am using Firestarter for ICS as I'm not very good on the command line.

So far, I can already ping the other computers in the network from the "server". The other computers can also ping the "server". The "server" can access the internet. The other computers cannot access the "internet", HOWEVER, I can ping an external IP (like Google's).

According to my limited knowledge, my problem seems to be DNS-related. Or maybe not. Can anybody help me with this?

***by the way, I already had a working ICS connection before (which I broke by updating Intrepid). In the DNS setting of the "client" computers, I used the IP of the "server" computer (192.168.0.1). This no longer works with the current setup

---

### Post by eppo on 2008-11-14
to see if it is a dns problem, what i would do is just find out what nameserver you are using on your server:
cat /etc/resolv.conf
not sure what kind of computers you have on your network, but configure them to use those nameserver.
then try and ping [www.google.com](www.google.com) not the ip.
if that works you can try to open a web page.
or you can try and open a webpage first, whatever floats your boat.

---

### Post by black3ug on 2008-11-14
It works!!! Thanks epppo! :)


Just to clarify something, was I wrong to set the DNS IP to 192.168.0.1 (the "server")

---

### Post by black3ug on 2008-11-14
Anything? I'd really love to know if I did wrong or right to set the "client's" DNS to the "gateway" IP.

---

### Post by Iowan on 2008-11-14
My router has a caching DNS server, so my clients all point at it.  Dunno about a non-DNS router.

---

### Post by black3ug on 2008-11-14
I don't use a router. The Ubuntu gateway machine actually "acts" like the router for my network.

Anyway, it seems like I won't be getting an answer for my question from this thread...

Thanks for the help. :)

---

### Post by dmizer on 2008-11-14
> **black3ug said:**
> It works!!! Thanks epppo! :)


Just to clarify something, was I wrong to set the DNS IP to 192.168.0.1 (the "server")

Yes. Unless you configured the ICS server to host DNS as well as ICS, you need to specify external DNS servers. This is because the server is getting it's DNS on a different subnet.

---

### Post by black3ug on 2008-11-15
hmmm...So the first time that it worked, I probably did something allow the ICS computer to do DNS hosting. I wonder how I did that...

Anyway, thanks for the reply, dmizer. definitely need to read up on this.

---

### Post by Schuby007 on 2011-02-02
Hi,

I think I'm having a similar problem. I am trying to share my internet connection through my laptop (Ubuntu 10.10) with my desktop (Ubuntu 10.04). My laptop is connected to my wireless router (192.168.0.1) via wlan0. I've run an ethernet cable from eth0 on my laptop to eth0 on my desktop and set the Method for eth0 on my laptop to "shared with other computer".

At first nothing was happening on my desktop; I would try to connect via eth0 and nothing would happen. So I entered the ip address, subnet and gateway manually on the desktop and it shows that it's connected but when I try to browse the internet, it tries to load and then says "no server found". I've tried setting the DNS server on the desktop to 192.168.0.1, 10.42.43.1 (ip address of eth0 on laptop) and I've tried Google's DNS servers 8.8.8.8 and 8.8.4.4 and nothing.

Any help would be greatly appreciated.
Thank you.

---

