---
title: "Cannot connect to Internet (cable modem, PPTP)"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by cygnus81 on 2007-02-21
I followed the steps in [http://l3ech.net/~l3ech/cables_linux.php](http://l3ech.net/~l3ech/cables_linux.php) , created all the scripts and chmod'ed them.

However, I cannot connect to the Internet.

After boot, I have an IP address which seems ok (if I *ifdown eth1* and *ifup eth1* I get "No DHCP offers". But thats another issue..), and I can ping both my IP and my gateway IP (taken from /sbin/route).

However, I do not have any DNS addresses in /etc/resolv.conf (/etc/ppp/resolv.conf does not even exist), and I, obiviously, cannot ping [www.google.com](www.google.com), [www.ubuntuforums.org](www.ubuntuforums.org) or annywhere else.

Thanks for any help

---

### Post by ravsas3 on 2007-07-21
i don't know much about your problem but did you try google's ip: 216.239.37.99
all i can say is that if you can ping it successfully your problem is just a DNS one and you can get free DNS:
208.67.222.222
208.67.220.220
so if you get that right thank 'Docter' for that

---

