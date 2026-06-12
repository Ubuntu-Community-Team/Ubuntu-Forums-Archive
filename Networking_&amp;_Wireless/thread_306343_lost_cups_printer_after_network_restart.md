---
title: "lost cups printer after network restart"
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by dave37 on 2006-11-24
My network printer, brother mfc-8840d has been working fine for months in dapper, set up as smb://BRN_3899D6/BINARY_P1  Well I couldn't leave well enough alone and decided to get the network scanner function working.  I added 192.168.2.180 BRN_3899D6 to /etc/hosts and as well dabbled in the cupsd file (which I backed up first of course) and upon restarting the network, I'm a genius, the scanner is working.  Then I removed the changes, restarted the network, and ever since I can't print unless I have the 192.168.2.180 BRN_3899D6 in the /etc/hosts file.

Any ideas, it's not a big thing as it's a home network and I can leave the reference in hosts.conf, but I'd prefer not to (I've set the printer to static ip now as there are lots of ip addresses left on the router)

What I'd like to do is somehow resolve the printer mac address in etc/hosts but can't figure out how.  If I could it would solve my printing and scanning problems for good.

Thanks all!

---

