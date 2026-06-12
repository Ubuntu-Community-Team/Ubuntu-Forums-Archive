---
title: "Switching wifi card drivers"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by Erunno on 2006-11-01
Hi all :)

Recently I switched from Gentoo to Kubuntu on my laptop to lessen the administrative activities but I have a huge problem now: Kubuntu won't connect to my university access point automatically anymore which used to work flawlessly when I was still running Gentoo. There are two key differences I can think of: Kubuntu uses wext (?) as the default driver (ndiswrapper on Gentoo, my PCMCIA network card was automatically detected by Kubuntu) and I used dhcpcd instead of dhclient.

So, before having to resort to deleting Kubuntu this weekend as a working wireless connection is a real deal breaker for me I wanted to ask the nice inhabitants of this forum for help.

Right now I'm using the KNetworkManager to access the network but when I'm at the campus it fails at the "Activating wireless device" stage. I can connect to the access point via iwconfig though but I won't receive a dhcp lease even if I invoke dhclient manually. The wireless network itself is unprotected, we have to use a vpn client to access the services.

1.) How do switch from wext to ndiswrapper ? I already installed ndiswrapper and the windows driver but it seems to me that Kubuntu is still using wext.

2.) Is there a way to change the default dhcp client ?

Help would be appreciated as I don't want to go through the time-consuming Gentoo installation again and would have to install Windows again :(

Cheers,
Erunno

---

