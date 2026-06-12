---
title: "ruse traceroute"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by Rommidze on 2008-09-23
I need to traceroute a certain machine. It doesn't even reply on ping requests. The reason I need this is to block access to my resource for a certain block of internet provider. User is constantly changing it's IP and I can not block the whole ISP subnet because I loose other people. So I am thinking of blocking one of ISP routers.

I have tryed all of traceroute methods, but non of them works.

---

### Post by jpeddicord on 2008-09-23
Moved to Networking & Wireless.

---

### Post by willca on 2008-09-24
if you know a certain port that target machine you are trying to check on, instead of vanilla traceroute which uses icmp i think still....

try

tcptraceroute -n hostname or IP port

sudo apt-get install tcptraceroute

---

### Post by Rommidze on 2008-09-24
> **willca said:**
> if you know a certain port that target machine you are trying to check on...

It seem that it is firewalled and all ports are closed. :(

---

### Post by willca on 2008-09-24
wow thats tough.

The only way I can think of going about this if you can identify who needs to connect either by their source IP or by having them authenticate prior to hitting your server. Like have them do some tunneling of sorts.

Otherwise, unless you have a firm idea how the perpetrator user is abusing your server with its pattern of activity then an IDS might be able to do it for ya.

---

