---
title: "Wired internet issue in Hardy"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Kevin Fischer on 2008-05-03
After upgrading to hardy (fresh install), I could no longer access the internet via ethernet. I know the internet is working; I've attached other computers to it, and when I reinstalled Gutsy I had internet access.

Here is the relevant lspci output:
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)

The strange thing is that it seems to think that I have network connectivity, but I don't get assigned an IP or anything. Anyone else had a problem like this in the upgrade?

---

### Post by aguill2 on 2008-05-03
I'm having the same problem. I've looked through all sorts of guides and such, but none of them actually deal with a wired internet problem. 

My Ubuntu computer was able to connect to the internet via ethernet cable in Gutsy after a fresh install, but after I upgraded to Hardy last night, I haven't been able to do anything in order to connect to the internet.

> 00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)


I'm getting the exact same thing. And I can also get on the internet through other computers connected to the wireless network that my Ubuntu computer is directly connected to. 

Please help!

---

### Post by MattBD on 2008-05-03
What kind of router are you using?

---

### Post by Kevin Fischer on 2008-05-03
Netgear WGT624 v3

---

### Post by MattBD on 2008-05-03
I was thinking it might be a D-Link one as they seem to have a lot of problems, but this solution might be of use anyway. Try using [OpenDNS]("http://www.opendns.com/"), there's instructions on the website. That might resolve the issue.
I've had problems with getting online with my D-Link router before, and it was something to do with the firmware not playing well with Linux sometimes - the router should forward packets to your ISP's domain name server, but sends it to the router's IP address instead, but using OpenDNS generally resolves this issue.

---

### Post by Kevin Fischer on 2008-05-03
I'll give it a try. Thanks.

---

### Post by luckyjonny on 2008-05-05
Yep, myself and a friend of mine have been enduring the same problem with Hardy Heron with the Asus Striker Extreme motherboard, which also has MCP55 ethernet. The workarounds listed in the comments of [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836") bug report work, until its fixed. Hope that helps :)

---

### Post by Kevin Fischer on 2008-05-18
That did it, thanks!

---

