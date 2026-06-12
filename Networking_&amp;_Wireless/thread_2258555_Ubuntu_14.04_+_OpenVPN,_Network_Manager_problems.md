---
title: "Ubuntu 14.04 + OpenVPN, Network Manager problems"
date: 2014-12-28
forum: Networking &amp; Wireless
---

### Post by Andy_Lawson on 2014-12-28
Hi,


I use OpenVPN from my Ubuntu 14.04 laptop to connect back to my home firewall. This has been a working solution for quite a while, I think since Ubuntu 12.something.


Recently (last month or so) I've started noticing that the Network Manager VPN launcher does not work. Right clicking on the network manager applet, then browsing down to "VPN Connections" and selecting my VPN name results in no activity at all. I am just returned to my desktop. No activity is noted in syslog.


About 1 time in 5 the VPN actually runs and I get logged in fine.


I've tried restarting the network-manager service, and restarting wireless networking and disabling and re-enabling the network service, all to no avail. Sometimes a reboot fixes it, sometimes it just comes good after a few (5-10) tries.


Anybody able to offer any help?


Thanks!

---

### Post by G_M_Slater on 2015-01-02
I am experiencing the same problem when I run under Unity. If I log into Ubuntu Studio (XFCE) the Network Manager applet works normally. This is extremely frustrating since I prefer Unity...

---

### Post by Andy_Lawson on 2015-01-05
Just a little update - today my laptop started the VPN fine, but will not now stop it :(

I'd guess this indicates that the problem lies with the network manager, not the openvpn implementation....

---

### Post by marc-bolard on 2015-02-09
Hi,

I experienced the same problem on my config and actually find a solution totally by chance. To start the vpn connection I wish, I actually need to first click on "VPN Connections" in the Network Manager and then click on the connection I wish to start. If you just naviguate inside the menus to your vpn connection, it won't start but if you do click, then everything goes well 100%.

This probably explains why Andy had a "1 in 5" success rate.

Don't know if I'm clear enough but posted just in case it helps someone spare some time and nerves...

---

### Post by Andy_Lawson on 2015-02-09
> **marc-bolard said:**
> To start the vpn connection I wish, I actually need to first click on "VPN Connections" in the Network Manager and then click on the connection I wish to start.

Wow! That simple?

Let me make sure I understand what you're saying;
1. Click on the network icon on the title bar.
2. Click on the "VPN Connections" (do not just hover and allow the sub-menu to open).
3. Click on the VPN you wish to start.

I must admit, I haven't seen the problem for a while. Maybe I'm clicking on the sub-menu now - I don't really recall :)

Thanks Marc!

---

### Post by Andy_Lawson on 2015-03-31
'Fraid not. It's happening to me now, and explicitly clicking the menu options rather than allowing the menus to pop out doesn't seem to make any difference :(

---

