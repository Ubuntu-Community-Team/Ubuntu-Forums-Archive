---
title: "Connecting ubuntu to internet thru a win xp pppoe connection"
date: 2006-10-19
forum: Networking &amp; Wireless
---

### Post by debianist on 2006-10-19
Hi everybody,

I have a win xp pc, connected to internet thru pppoe. I have also a laptop win ubuntu (dapper drake) installed. I want to use the window's connection to be able to access internet from my laptop.

what I did:

1- I installed 2 network adapters. on the windows pc, one adapter for local lan (between ubuntu laptop and win pc; called hereafter win-ubuntu adapter) and the other for the pppoe internet connection; called hereafter internet adapter. pc and laptop are connected thru a 5-port hub.

3- I set eth0 on ubuntu laptop to use DHCP.
4- setting the win-ubuntu adapter on the windows pc(
     ip: 192.168.0.1
     netmask: 255.255.255.0
     no gateway, no dns (since the dns and gateway are determined automatically by the provider when connected-this is what i've been told, and its working on windows :o )

5- internet adapter ip: 198.14.2.114

whats happening?

- I can ping win to ubuntu, but not the opposite.
- I can't access internet from my ubuntu laptop.

any suggestions??

Any help would be appreciated :)

---

