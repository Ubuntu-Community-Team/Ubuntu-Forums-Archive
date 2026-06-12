---
title: "inetd in Ubuntu Edgy"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by Pollywoggy on 2007-01-13
I installed kubuntu two days ago and I have not installed any non-ubuntu packages.

I noticed today that ktalk was installed by default, so I went to /etc/inetd.conf to disable it, since I did not know that it was part of kde.  I disabled ktalk there but when I did 'killall -HUP inetd' nothing happened, nor did I find a startup script for inetd or xinetd in /etc/init.d/  Very odd and it turns out that neither xinetd nor inetd are installed on my system.  So if neither of those are installed, why even bother having /etc/inetd.conf?  Having it there will give users a false sense of security.

I discovered that ktalk is part of kde and I was able to remove it.  I think this is a bug in the kubuntu installer.  Either inetd should be installed or else that conf file should be removed.

---

