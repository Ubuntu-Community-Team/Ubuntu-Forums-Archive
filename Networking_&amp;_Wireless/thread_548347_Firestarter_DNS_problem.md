---
title: "Firestarter DNS problem"
date: 2007-09-11
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2007-09-11
Good day everyone!
I have installed firestarter and enabled Internet Connection Sharing (NAT) there. But I get one trouble about it: Let's say server is 192.168.0.1. When I set DNS as 192.168.0.1 for the clients it doesn't work. :( Direct IP ping works perfectly though. Clients configured with static IPs. Where's my mistake? Thank you!

EDIT: again, this is rather strange, but I found [this screenshot ]("http://firestarter.sourceforge.net/manual/pictures/wizard3.png")in [a guide]("http://firestarter.sourceforge.net/manual/wizard.php") and it doesn't look close to [the picture that I see]("http://www.fs-security.com/docs/pics/wizard3-small.jpg") when I run the wizard... What's going on?

---

### Post by kidders on 2007-09-12
Hi there,

This may seem like a dumb question, but it *does* have to be asked! Are you running a DNS server on 192.168.0.1?

---

### Post by PryGuy on 2007-09-14
Well, the answer is dumber anyway... :)
Yes, my server IP is 192.168.0.1. I perfectly understand what is DNS server but how do I install it?

---

### Post by kidders on 2007-09-14
Your last post is confusing! If you *do* have a DNS server on your network ("Yes, my server IP is 192.168.0.1"), then you don't need to install another one ("but how do I install it"). You see, even if you did, you may wind up having to forward DNS queries to your local network's DNS server anyway, and it doesn't seem to want to respond to your requests.

What software is your network's DNS server running? Do you have administrative access to it? If so, can you post its configuration & perhaps a little detail on how your network is organised? I may be able to suggest some changes.

---

### Post by PryGuy on 2007-09-15
Well, of course it is confusing! I didn't have to deal with networking much before, sorry...:oops: My thoughts are, client sends a query to a DNS server with a name, DNS server looks up and finds a match (or forwards it to a parent DNS server if not) and opens up a resource. I set the 'name server' as 192.168.0.1 for clents but nothing happens. Where's my mistake?

192.168.0.1 runs Ubuntu Feisty and Firestarter and yes I can administer the system.

I have a small LAN connected via D-Link DI-824VUP+ router to a server (192.168.0.1). Router's own DHCP server is turned off. Server connects to internet via AnyData ADU-300A CDMA modem. All clients have static IPs from 192.168.0.2 to 192.168.0.6

---

### Post by Synflux on 2007-09-15
Hi,

What DNS server is set on your 192.168.0.1 box? Have you tried setting your clients DNS to the same as the server's? 

You should only need to set the default gateway to 192.168.0.1 on the clients and use the same dns as the server?

---

### Post by PryGuy on 2007-09-15
Isn't it built in into default Ubuntu installation? I tried to install bind9 but system said that I've got dnsutils installed. 

Setting the parent DNS (the one that server gets) works fine, but I think it is more correct to use 192.168.0.1.

---

### Post by kidders on 2007-09-21
> **PryGuy said:**
> Setting the parent DNS (the one that server gets) works fine, but I think it is more correct to use 192.168.0.1.You're right about that, I suppose ... it would perhaps be more elegant.

Bind9 doesn't come preinstalled by default, but you can set it up yourself if you want to. Most people tend not to bother, unless they have a specific reason for wanting a local DNS service, but running one does have certain advantages.

I would recommend finding a good howto to follow though ... DNS servers can be a little bit tricky.

---

