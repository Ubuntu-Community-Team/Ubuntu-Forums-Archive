---
title: "/etc/network/interfaces seems to be automagically &quot;updated&quot;?"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by wirawan0 on 2007-10-03
Hi,

I have a puzzle here. I am using Feisty (7.04). I like the network configuration applet (nm-applet), which allows me to change my "location" in an instant, and configure the network settings in different places (home, work, friend's house, etc.). But I have something that I don't like, which may or may not be related to nm-applet/network-admin itself. I typically leave a network-admin window open, BTW, so that I can change my network location at any time. I use this Feisty on a laptop, and I suspend to RAM and resume repeatedly without problem.

Here's what I don't like. I have two interfaces here, eth0 is the wired network:

> 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:00.0 0200: 14e4:165d (rev 01)


and eth1 is the wireless network, Intel chip:

> 
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:03.0 0280: 8086:4220 (rev 05)


Those lines are the output of lspci and lspci -n, respectively. At home, I have the two network devices configured, and I choose to automatically enable eth1 (i.e. the eth1 entry in network-admin is checked, while the eth0 entry is unchecked, although it is configured with its IP address, etc., should it need to be turned on). So there is this line in /etc/network/interfaces:

> 
auto eth1


and no "auto eth0" line. At work, I do it the other way around. So I have a second location in network-admin, which enables eth0 and disables eth1 by default. Again, both eth0 and eth1 are configured, since I can connect to network with either, but I strongly prefer eth0 (faster).

However, on some occasions, using "home" location, I found that a line "auto eth0" is inserted. I don't know who inserted this line, but it was there. When I bring this laptop to work, plug in an ethernet cable, and resume the computer, then I can find that "auto eth0" line also, which wasn't there before, IIRC. This happens _BEFORE_ I change the setting to "work" location. This is irksome. I could reset this by re-setting the network location, but I don't want this all the time. If there is bug somewhere, we better remove it.

Another problem. Occasionally, I found that my network connection at work changed from "eth0" to "eth1" without my doing anything. This is terrible. Can network-admin do this by itself, somehow?

Anybody has experience with this kind of problem? Please comment up, folks! Don't just view this post and walk away if you know something.

Wirawan

---

### Post by Paris Heng on 2007-10-03
It is not automatically updated if u configured in /etc...., you must restart the network, there is a command there.

---

### Post by wirawan0 on 2007-10-04
Ahem... I think I may know what's going on. Somewhat. I looked at the data file of network-admin, which is located at /root/.gnome2/network-admin-locations/XXX (where XXX = your location, e.g. office, home, etc.). This is my "home" location, BTW. As I said before, I set eth1 to be active and eth0 to be nonactive by default. There, the settings for eth0 is this:

> 
[eth0]
auto=true
active=false
configured=true
config-method=static
ip-address=192.168.0.176
ip-mask=255.255.255.0
gateway-address=192.168.0.1
network-address=
broadcast-address=


Pretty obvious, eh? The "auto" switch is ON, but "active" is OFF. Why is this? I don't quite know. What I know is that this is the first "location" I made. What's mysterious to me is "when does an interface obtain its `auto' status?" It's not clear when and what makes auto = true or false. If you know, please let me know in this forum! I looked at the source code of gnome-system-tools for a while, but I still cannot figure it out.



Wirawan

---

