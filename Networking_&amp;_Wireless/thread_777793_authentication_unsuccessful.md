---
title: "authentication unsuccessful"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by xscottx3 on 2008-05-01
Hi, I am running a fresh Hardy Heron install and have gotten my dell 1390 wireless card to work, but I can't manage to get my VPNC to work. It asks for my password, then asks for it again and then gives me a message saying
vpnc: authentication unsuccessful. The password is correct and I am entering it correct.

Have been searching online madly for help, but I can't seem to find anything. Anyone have experience with making the vpnc to work? This is what I have in my /etc/vpnc/default.conf

IPSec gateway abc.de.fg.h
IPSec ID abcdefg
IPSec secret abcdefghij
Xauth username <abcdef>
Xauth password <abcdefg>

Thanks,
Scott

---

### Post by xscottx3 on 2008-05-01
Don't worry. I got rid of the vpnc and installed cisco vpn. Didn't want to initially, but it is working properly and I am happy. :)

---

