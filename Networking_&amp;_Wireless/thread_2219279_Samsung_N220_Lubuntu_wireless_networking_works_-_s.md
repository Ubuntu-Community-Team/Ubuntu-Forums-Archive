---
title: "Samsung N220: Lubuntu wireless networking works - sometimes!"
date: 2014-04-23
forum: Networking &amp; Wireless
---

### Post by Andy3142 on 2014-04-23
Wireless networking on my Samsung N220 Lubuntu netbook sometimes works, but not reliably.

--- Windows laptops working on the same router work perfectly.

--- The Linux machine used to work. I don't know, but maybe the problems relate to installing, then un-installing, OpenDNS for this machine. But that was on a different router, I never installed any software, and I deleted the network inside OpenDNS so not sure how that could affect things.

--- When I boot up, at first a few webspages load perfectly OK. In a minute or two however, they all stop loading.

--- At that point, when it fails, I can ping eg [www.bbc.co.uk]("http://www.bbc.co.uk") by IP address, but cannot "ping www.bbc.co.uk."  But the windows machine works fine, so the basic downstream DNS is OK.  I've checked in "edit network connection", and the linux machine is set to "DHCP automatic" and there is no trace of the OpenDNS nameservers.

--- When it fails, I cannot access bbc.co.uk by typing the IP address in the browser.

--- For a few days, this fix worked: to do 
> sudo dhcpcd -d eth0
This would reliably get the www running again. However this has now stopped working. It was always strange, because I had to specially download dhcpcd for the job.

--- Also for a few days, re-starting the wireless connection to the router got things working, now that also seems not to work.

All in all it seems very close to working, but not quite. Suggestions gratefully received.

Andy
Bristol UK

---

