---
title: "[SOLVED] Strange hostname at router dhcp table"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by sepp.toth on 2008-06-24
Hi there,

I've got a Lan network at home with 2 Ubuntu 8.04-desktop pc, 1 Ubuntu 7.10-server pc and 1 XP pc. Yesterday, I did a fresh 8.04-server install to my server box. But, when I looked at the router's dhcp table there was a strange entry (random numbers, binary like strings) at the client hostname next to the server's ip. The router is a Linksys Befw11s4 ver4, with firmware version 1.45.3, Jul 11 2003.

There wasn't any such things with 7.10-server, and just for the testing, I did a fresh install of 7.10-server today and the client hostname was just fine.

Because of this I can't "fix" the IP-s in the hosts file and it's a bit annoying.

Does somebody have something like this, or know a workaround?

Thanks,
Sepp

---

### Post by sepp.toth on 2008-07-01
It looks like I have found a solution after googling aroung the web, and tried out a couple of distros. When I installed Debian, I found there aren't any hostname in the routers dhcp client list, so googled it and found a really old thread here:
[http://ubuntuforums.org/showthread.php?t=55564]("http://ubuntuforums.org/showthread.php?t=55564")

Just needed to edit the dhclient.conf and type the hostname to the send host-name line.

---

