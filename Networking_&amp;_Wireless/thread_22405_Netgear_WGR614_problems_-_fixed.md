---
title: "Netgear WGR614 problems - fixed"
date: 2005-03-27
forum: Networking &amp; Wireless
---

### Post by akirafist on 2005-03-27
I want to post a solution that may help other people:

The Ubuntu network configuration tool apparently doesn't save the wireless config for a **second** location, even if you give it a profile name.  Looks like a bug.

For example:

I installed Hoary 5.04 at home - it recognized my Linksys router fine.

I went to my girlfriend's house this weekend, and tried to configure her WGR614 - didn't work no matter how much hair I pulled out.  Reason why?  Because Hoary 5.04 didn't update the /etc/network/interfaces file.

So here's the manual fix for anyone else having this issue:

[SIZE=3][COLOR=Red][B]In your netgear router config:
[/B][/COLOR][/SIZE]

Channel: 01
Authentication Type: Open System

[SIZE=3][COLOR=Red][B]Editing your interfaces file in Ubuntu:
[/B][/COLOR][/SIZE]

cp /etc/network/interfaces /etc/network/interfacesBACKUP
vim /etc/network/interfaces

Change to look like this near the bottom:

[B]iface eth1 inet dhcp
wireless-mode open[/B]
**wireless-essid mycomputer**  # <-- your ESSID

# hex is OK for wep key, ignore other thread that says convert to all integers, 
# and DO NOT include dashes like another thread suggests
**wireless-key C39DF473  **

#including the channel was important in my config
**wireless_channel 1**

This is how I got mine working, obviously YMMV.

(Keyword search friendly for later: netgear WGR 614 wireless router problem eth1 hoary)

---

