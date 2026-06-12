---
title: "Slow  internet with firefox."
date: 2007-04-27
forum: Networking &amp; Wireless
---

### Post by moc on 2007-04-27
Hi,

I've been running Edgy eft on my labtop for a couple of weeks now.
In the beginning I had no problem connecting to the internet with Firefox.

However, in the last couple of days this has surely degraded. 
After a while Firefox gets so slow looking up hosts and transferring data,  that it is practically unusable.
After reboot, it works again for a while but eventually gets slow again.
Also.. very often Firefox immediately responds with "Can't find server..", although I'm positive the hosts are available.. I've verified this on XP.

I've found a suggestion for a fix, which relates to disabling IPv6:
gksudo gedit /etc/modprobe.d/blacklist
then add:
blacklist ipv6

That didn't solve the problem, which I also suspected. Because how could it work in the first place then?

Does anyone have an idea what is causing this ?? Is it a virus?... or could it be related to some system updates I've recently installed?

regards
/moc

---

### Post by ho277 on 2008-04-18
Try this homepage:

techxplorer.com/2007/02/22/slow-browsing-using-firefox-on-ubuntu/ 

In addition, try installing Swiftfox, made exclusively for Linux platforms.

---

