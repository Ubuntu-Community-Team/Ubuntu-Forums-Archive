---
title: "SSH local computer from global IP"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by drubix on 2008-02-27
Hi,
I've seen this problem pop up a few times but can't for the life of me find a conclusive answer.

I've got an ssh server on my local network which I can connect to with the usual 192.168.x.x and my router is set up to forward port 22 to that box.  I have no problems accessing my ssh server from my router's IP address when I'm at work or uni but I'm unable to connect to my router's IP address when I'm inside my local network.

Basically what it boils down to is that I'd like to be able to access my svn repos from anywhere without having to change the settings depending on where I am.  I realise I can just set up a line in /etc/hosts which I can change but surely there's an easier way?

Thanks in advance.

---

### Post by kevellis on 2008-02-27
Most routers don't allow you to connect to your WAN IP from within your LAN.
I had this problem in the past and didn't find a suitable workaround.
I guess your best bet would be to have a couple of aliases/scripts to change between configs.

---

### Post by Mr. C. on 2008-02-27
Don't use IP addresses - that's what host names are for!

On the WAN, assign a hostname (either via the remote system's host table, or DNS) that maps to your router's WAN IP.

On the LAN, assign a hostname (either via the local system's host table, or a local DNS server) that maps to your server's LAN IP.

MrC

---

### Post by drubix on 2008-02-27
Oops, I forgot to mention - this is a laptop I'm carting around so Mr C's suggestion isn't going to work for me.  (I guess the whole laptop thing was kinda important :P).  Works a treat for when I'm on a different computer at work though.

Cheers anyway guys, I was hoping I wouldn't have to resort to running a script every time I move but I guess that's not really a huge price to pay.

---

### Post by Mr. C. on 2008-02-27
I'm not sure what a laptop has to do with the problem.  I carry a laptop with me, both inside and outside my LAN, and have access to my services on the LAN without any configuration change.

Setup a local, caching split DNS on your LAN.  On your LAN, your laptop will use the DNS services and receive LAN, private IP addresses that allow hostname mapping to your server.

When you are on the WAN, you'll be using a public DNS, whicih maps to your WAN IP address where port forwarding occurs.

Its trivial.
MrC

---

