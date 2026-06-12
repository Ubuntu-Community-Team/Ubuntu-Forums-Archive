---
title: "Ubuntu server as an ipv6 router"
date: 2023-09-07
forum: Networking &amp; Wireless
---

### Post by Alex_Filonov on 2023-09-07
OK, now I'm posting how I created ipv6 router using Ubuntu 22.04 server and several questions which are not resolved yet.

I was tinkering with isc-dhclient and it was working. But it didn't solve the problem of changing radvd settings when ISP changes prefix. So I was finally able to make prefix delegation work using Erik Nygren's advice here: [https://erik.nygren.org/dhcpv6-pd-on-ubuntu-2204.html]("http://erik.nygren.org/dhcpv6-pd-on-ubuntu-2204.html").
It's also required to set accept-ra to 2, which is done using John Siu's advice (here: [https://johnsiu.com/blog/linux-router/](https://johnsiu.com/blog/linux-router/)).
I'm using shorewall and shorewall6 as firewalls, settings are pretty close to what John Siu is using.
Everything is working fine. But there are still questions about DNS. I'm using Bind. There is no problem with ipv4, because both DNS servers have static IP addresses. Questions about ipv6:

1. Is there a way to set specific addresses within allocated prefix for DNS servers? If so, is there a way to use these addresses as DNS servers for internal devices? For example, I have prefix like 2601:0:0:0::/64, is it possible to give DNS servers addresses 2601:0:0:0::::1 and 2601:0:0:0::::2 and somehow communicate them to all clients?
2. How to send to Bind ipv6 addresses of internal clients? Because clients receive addresses from radvd, is it possible to send this information to Bind? The only way I see so far is to use local discovery, I can write some scripts, but it's not very reliable way, is it?

Of course, all internal ipv4 communication is working perfectly, and Bind resolves external ipv6 addresses using forwarding to Google DNS, but I would still want to have complete ipv6 solution for internal network.

---

### Post by Alex_Filonov on 2023-09-08
OK, people say that you can create address within allocated prefix using netplan:

[FONT=inherit]ethernets:[/FONT]
[FONT=inherit]eth0:[/FONT]
[FONT=inherit]ipv6-address-token:[/FONT][FONT=inherit]"::f6d1:cbfa"

Information from here: [https://serverfault.com/questions/1109805/configuring-ubuntu-22-04-to-generate-the-interfacepart-of-an-ipv6-staticly](https://serverfault.com/questions/1109805/configuring-ubuntu-22-04-to-generate-the-interfacepart-of-an-ipv6-staticly)

Haven't tried it yet, will report when I try.

Looks like there is no way to set up internal DNS when you use SLAAC. I will search more, but there is little hope. If anybody has some info, please, reply.

[/FONT][/COLOR]

---

