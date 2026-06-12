---
title: "Could someone please explain the new network configuration files?"
date: 2018-12-18
forum: Networking &amp; Wireless
---

### Post by PeterK2003 on 2018-12-18
Previously I set the DNS servers via /etc/resolv.conf if I remember correctly.

After upgrading to 18.04 that file keeps getting over written when systemd-resolved is restarted.

I managed to get thing set correctly by editing the /etc/systemd/resolved.conf file.

After quite a bit of googling I found several different "correct" ways to set the DNS server.....

So what is is the correct way?  This seems so much more complicated than it needs to be....

---

### Post by TheFu on 2018-12-18
DNS settings in resolv.conf ended with 10.04.  In 12.04, those were moved into the interfaces file.  In 17.10 and later, again the method was changed - I think netplan is used.  Assuming you are on a server, not a desktop, the best guide I know is here:  [https://netplan.io/](https://netplan.io/)

Whenever looking for how-to with Ubuntu, always use the release in your search.  Also, the way a desktop manages those settings is different from how a server does it.

And I agree. It is more complex than necessary.  They've been trying to fix issues that I've never had since 2010. Such is the price of "progress."  For me, 10.04 was the perfect release and I'd still be using it provided it was supported.

[https://ubuntuforums.org/showthread.php?t=2403929](https://ubuntuforums.org/showthread.php?t=2403929) is a desktop 18.04 thread related.  Hopefully, it is of some help.

---

