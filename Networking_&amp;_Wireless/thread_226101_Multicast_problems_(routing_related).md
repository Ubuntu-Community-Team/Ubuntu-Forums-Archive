---
title: "Multicast problems (routing related)"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by Thraxes on 2006-07-30
Hi, I am trying to run a small media server in my unis media lab. There is a weird problem though: The system won't do any multicasting in the IP range of the media lab, specifically 192.168.45.x, it also won't accept SSH sessions or VNC connections. The system can be pinged though and it can do a unicast stream to another computer.

The weirdness starts though when I change the IP range from the mlab range to the EE range 192.168.43.x . Now suddenly everything works! Multicast, SSH, VNC... the lot. This is still while connected to the same wall socket and switch!

Because of the multicast problems I checked the machines routing tables and while in the EE range it had a normal looking table, but the mlab table is bare. There are no DHCP servers at all on the network (pen & paper DHCP) and there are no other servers in the mlab IP range, just a bunch of WinXP clients. The IP address is not used anywhere else on the network (first thing I checked).

I tried adding the routing info by hand at first and got it to work, I had to reboot the system though before I got around to adding the routes to the startup. No problem I think, I know what I have to do... well now I get an error which says something about adding a hardroute into rom... or something in that nature. I can't remember the exact error because it was a few days ago and I am not at the machine right now (1 in the morning here ;)).

What could be causing these problems? I am thinking that the server is running fine because in one netrange it works with no problems and that my problems lie in the network in general. Any pointers to what might be causing this? I will be trying out a different network card tomorrow (current one is the onboard network of an Asus A7V-333X board), I have a el cheapo realtek and a Intel dual port card lined up for testing... somehow I doubt though that this is the problem.

Any suggestions would be most welcome!

---

### Post by mips on 2006-07-31
Supply a bit more info. What is pc ip address and network connect to. Where do you want the multicast traffic to go. You did provide some info but it is not to clear.

Has multicast been configured on the routers and swiches. From what I recall this config has to be done for every network/router/switch if I'm notmistaken, did it a few years ago so a bit fuzzy.

---

