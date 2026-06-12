---
title: "[SOLVED] VPN route problem"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by EvilBro on 2008-11-08
I have set up a VPN connection with the networkmanager in 8.10. I am able to connect, but when I do all my network traffic goes over the connection. I suspect that I need to tell ubuntu that I only want to use the connection for certain addresses. I am however unable to figure out where I am supposed to do this (I think it is supposed to be done under 'Edit VPN'->'IPv4 Settings'->'Routes', but I haven't found something yet that explains to me what I am supposed to specify). Can someone enlighten me on this issue?

---

### Post by SabreWolfy on 2008-11-08
Slightly off-topic, but VPN generally appears to be quite broken on Intrepid. See [here]("http://ubuntuforums.org/showthread.php?t=973399") for a thread where I ranted about this briefly. There are also some links to VPN-related bugs. I've returned to Hardy because I need to use VPN and I wasted too much time trying to get it to work in Intrepid! :( I also couldn't figure out how to enter routing information into the configuration dialog and it is not possible to import VPN settings exported from Hardy.

---

### Post by EvilBro on 2008-11-08
> **SabreWolfy said:**
> Slightly off-topic, but VPN generally appears to be quite broken on Intrepid.
That maybe your personal experience, but VPN works for me. I get a connection and I can use it. My problem is that all my network traffic then uses that connection. The network manager changes the routing table. It just does this in a manner that is not as I want it to. This is what I need to change. Any help in that area would be appreciated.

---

### Post by SabreWolfy on 2008-11-08
Ok, well you're a lot better off than many of us then, as we couldn't get VPN connections to work anymore in Intrepid. I know the MPPE setting is not sticky, so possibly the routing settings are also not sticky.

---

### Post by EvilBro on 2008-11-08
just as a reference, the problem is solved here: [http://ubuntuforums.org/showthread.php?t=934946](http://ubuntuforums.org/showthread.php?t=934946)

---

### Post by yaleo on 2008-11-08
For me it does not solve the problem. 
After connecting to the VPN routing does not work. Instead I find two pretty stupid routes on my system:

remote_public_ip  my_local_router  255.255.255.255
remote_private_ip  my_local_router  255.255.255.255

after that I remove this #+ß?! manually and set my own route:

route add -net remote_vpn_ip netmask 255.255.255.255 dev ppp0

and everything works fine. By the way, I'm talking about PPTP VPN connections. But I also noticed that the Network Manager often forgets some settings. For me this new Network Manager is a complete disaster, look at
all the other problems with e.g. a static eth0 and network connectivity after reboot.

regards,
yaleo

---

### Post by gabba on 2008-11-15
For those who don't want to use the command line or manually edit routing tables, [**this post**]("http://ubuntuforums.org/showpost.php?p=6090152&postcount=6") describes how to direct only the needed traffic through the vpn with the Intrepid NetworkManager applet.

It took me hours to find this information. This new way of doing things is a big regression in usability compared to the last version: at least in Hardy most people could figure out the option, and there was an example provided.

To understand what's going on, it's interesting to compare the output of the command "route -n" before and after connecting to your vpn, and to read [**this page**]("http://www.idevelopment.info/data/Networking/Networking_Basics/ROUTERS_Gateways_Routing_Table.shtml") to make sense of the output.

---

### Post by SabreWolfy on 2009-04-24
For what it's worth, I found a solution to PPTP VPN in Jaunty (and presumably Intrepid too). Link [here]("http://ubuntuforums.org/showthread.php?t=1136020").

---

