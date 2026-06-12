---
title: "iptables port forwarding on localhost"
date: 2006-09-10
forum: Networking &amp; Wireless
---

### Post by alien^ on 2006-09-10
i have two network interfaces eth0 and eth2 both have dinamically asigned ips
lot of programs use eth0 and i don't see any options to change it to eth2 so i want forward ports tcp 50666 and udp 4444 from eth0 to eth2 and if something comes to eth2 on those ports it goes to eth0 ports
i think it is possible with iptables i tried a few things but nothing worked :'(

---

### Post by kidders on 2006-09-10
Hi there,

It's very likely I'm misinterpreting, but it almost seems as if you're asking how to use iptables to forward traffic from one network interface to another, so you can avoid configuring your applications!

Wouldn't it be simpler to change one line in a few config files? Getting what you **seem** to be asking to work in practice is ... well ... non-trivial.

---

### Post by alien^ on 2006-09-10
i have went through all menu and all config files there nowhere were set option which network interface to use it seems that they are program are using eth0 as default with no easy way to change it

---

### Post by kidders on 2006-09-10
Hmmm...
What programs are you referring to?

---

### Post by alien^ on 2006-09-10
one of the programs which i want to forward is ktorrent

---

### Post by kidders on 2006-09-10
Oh I see... So you have two internet connections, and you want to force certain applications to use the one of them, without altering your default gateway, so other applications will prefer to use the other.

If you want to use iptables, the closest you'll easily get to achieving this is probably by redirecting outgoing packets destined for eth0 to eth2 on the ports you know you applications like to use. In the case of bittorrent however, this is likely to fail ... or at least only partially work. You could improve your chances by manually specifying your IP in Ktorrent's settings (which will be a pain, since it's dynamically assigned), or by using UPnP. Such an approach would probably work fine with, say, a web browser, though.

Proxying is perhaps the most obvious thing to try, although I'd say it would be a *real* pain to get bittorrent to work well under such circumstances.

In general, it would not be sensible for "client" applications such as Ktorrent to allow you to specify which network interface you want it to use ... such decisions are made by the underlying operating system, based on routing information it has gathered from your network environment. (When you referred initially to the idea of manually specifying network interfaces, I had assumed you were talking about servers.) In my opinion, trying to manually route packets to the wrong interface could all to easily wreck your head until you wish you'd never been born!

Are there any other applications you'd like to try this with?

---

