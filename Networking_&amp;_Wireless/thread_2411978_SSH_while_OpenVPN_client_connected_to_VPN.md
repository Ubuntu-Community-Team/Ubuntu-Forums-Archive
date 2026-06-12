---
title: "SSH while OpenVPN client connected to VPN"
date: 2019-02-06
forum: Networking &amp; Wireless
---

### Post by alex508 on 2019-02-06
Hello, I know similar questions have been asked before but believe me, I've spent hours and hours trying to figure this out and I just can't seem to get it to work.

I have OpenVPN server running on my ASUS router and I can remote SSH to my server on my home network with no problem. Once I start the OpenVPN client on my server, however, I lose SSH control because, from what I've read, my ssh packet responses are now being routed through the VPN tunnel.

I need to force all ssh responses to route through my default gateway (ASUS router). I've tried using "ip route add" with different combinations of options but I just can't seem to figure this one out. Your help is appreciated, thanks in advance.

---

### Post by The Cog on 2019-02-06
I don't understand your network setup there.You say your VPN server is on your home network. And I guess your router is on your home network. So you are making a tunnel from your home server to your home router? That doesn't make sense to me. I guess you are ssh-ing in from outside on the internet using port forwarding, is that right?

---

