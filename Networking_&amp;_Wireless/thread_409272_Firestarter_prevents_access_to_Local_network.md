---
title: "Firestarter prevents access to Local network"
date: 2007-04-14
forum: Networking &amp; Wireless
---

### Post by antrillion on 2007-04-14
I just installed firestarter, and then tried to ping another computer on my local network (192.168.0.1).  I get:

ping: sendmsg: Operation not permitted

If I ping a website, such as [www.goolge.se](www.goolge.se) it works just fine, the only problem seems to be accessing the local area network, which runs through the eth0 adapter on my computer (internet is conencted to eth1).

If I stop the firewall from firestarter, I can successfully ping the other computer on my local network again.

In the firestarter Preferences->Network Settings eth1 is listed as the "Internet connected network device", and eth0 is listed as the "Local network connected device".

I can't seem to figure out anything that will allow full access through the local network, which is what I want.

How can I fix this?

Btw, running Ubuntu 6.10.

Sincerely, Antrillion

---

### Post by 454redhawk on 2007-04-14
> **antrillion said:**
> I just installed firestarter, and then tried to ping another computer on my local network (192.168.0.1).  I get:

ping: sendmsg: Operation not permitted

If I ping a website, such as [www.goolge.se](www.goolge.se) it works just fine, the only problem seems to be accessing the local area network, which runs through the eth0 adapter on my computer (internet is conencted to eth1).

If I stop the firewall from firestarter, I can successfully ping the other computer on my local network again.

In the firestarter Preferences->Network Settings eth1 is listed as the "Internet connected network device", and eth0 is listed as the "Local network connected device".

I can't seem to figure out anything that will allow full access through the local network, which is what I want.

How can I fix this?

Btw, running Ubuntu 6.10.

Sincerely, Antrillion

Its a firewall. Its supposed to block access unless configured otherwise.

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

---

### Post by antrillion on 2007-04-14
> **454redhawk said:**
> Its a firewall. Its supposed to block access unless configured otherwise.

[http://www.fs-security.com/docs.php](http://www.fs-security.com/docs.php)

Thanx, but I am very aware of the fact that it is a firewall, that's why I installed it. However, I do not wish for it to firewall any of my local LAN traffic, only traffic to the internet.

---

### Post by Malac on 2007-04-14
> **antrillion said:**
> Thanx, but I am very aware of the fact that it is a firewall, that's why I installed it. However, I do not wish for it to firewall any of my local LAN traffic, only traffic to the internet.
Under [Edit->Preferences] then [Firewall->ICMP Filtering] check that "Enable ICMP Filtering isn't ticked or if it is tick allow ping and pong.

---

### Post by antrillion on 2007-04-14
It is not ticked, and no changes I make there make any difference. However, I did note that when I checked "enable internet connection sharing", some LAN traffic seemed to go through, although Samba requests were blocked and seemed to come through the other adapter (the internet one) for some reason. 

I don't need, nor want internet connection sharing. I simply want the local network separate from the internet in every way, and I want to be able to send any traffic over it, while firewalling only the internet connection.  Feels like I've tried every setting in this program, what am I missing here?

EDIT: I now removed firestarter and installed Guarddog instead. This program seems to be doing what I want it to, so problem was solved this way instead.

---

