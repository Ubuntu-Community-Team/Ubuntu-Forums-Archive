---
title: "DHCP Server Advice"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by cov on 2007-12-14
I appologise to anyone who recognises this as a double post.

My previous thread attracted about 6 views, three of which were mine, so I thought the thread title needed to be changed - mind you, there don't seem to be many replies to other topics that I've found with a similar title, so maybe answers are scarce...

I've been battling for about a week and I need pointing in a productive direction.

I have bought myself a compute and installed Ubuntu on it.

I have a SMC Wireless router/Broadband modem which I have been using to connect onto the 'net.

I have configured squid to operate as a proxy server and have (hopefully) added the following to /etc/squid/squid.conf:

> httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on
acl lan src 192.168.1.1 192.168.2.0/24
http_access allow localhost
http_access allow lan
to allow a transparent proxy server.

Then I configured the router firewall to block all connections except those coming from the Ubuntu box.

I suppose I was kind of hoping that when the client machines could no longer access the 'net through the current default gateway, they would look for another alternative and find my Ubuntu box. No such luck.

So I've bought another network card and am intending to turn the Ubuntu box into a DHCP server which will connect to the router through the other network card.

Will this work?

Can anyone point me towards a clear and concise step-by-step on how to configure the DHCP server?

Can anyone offer me any advice here? Would you advise me to simply go the IPCop route?

I'm hoping to use a samba login to run scripts on the client machines and use unison to back them up.

---

### Post by Drate on 2007-12-14
Well, you sound bright enough to be forging your own how-tos. :)

As far as your first notion, hoping they will sust look around for something else doesn't seem like a good practice to me, though I'm a bit fuzzy what all you did to try it so whatev...

I have used Firestarter to share an internet connection via Ubuntu, however, so you might look into that.

---

