---
title: "Ubuntu Lucid 10.04"
date: 2013-11-08
forum: Networking &amp; Wireless
---

### Post by frits_goed on 2013-11-08
Hi there, 

im quite new at UBUNTU,

but i have a problem with the VNC.

I use the VNC for a display screen (loop).

But now i cant connect it with TightVNC Viewer. 

[I]Error in TightVNC Viewer:tightvnc viewer no connection could be made because the target machine actively refused it 

[/I]Roughly translated it.

So when i run iptables --list,

it says: accept from anywhere tcp dpt:5900.

when i check for open ports:
port 22 and port 631 are open.

BTW the server used to do just fine, but now i cant make out the problem or why.

Is it the server? is it the host? is it the port?

Please help. Have been digging through years of ubuntu threads but cant find my solution. or it didnt work.

---

### Post by sudodus on 2013-11-08
Hi,

Ubuntu 10.04 is quite old. The server flavour has long time support for 5 years but the desktop flavour has only 3 years, so it has passed end of life, and will not get security updates for desktop specific packages.

So if your Ubuntu 10.04 is a server, the security support should be OK, but if your Ubuntu 10.04 is a desktop, you'd better install a currently supported version, for example 12.04 LTS.

-o-

I don't know if there might be problems to connect a current version of *TightVNC Viewer *to an old server. I hope someone who knows better about that will find this thread and tell us :-)

---

### Post by frits_goed on 2013-11-08
Okey Thx for the intel!

---

