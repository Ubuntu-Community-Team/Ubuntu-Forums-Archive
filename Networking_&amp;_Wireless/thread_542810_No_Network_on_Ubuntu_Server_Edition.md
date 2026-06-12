---
title: "No Network on Ubuntu Server Edition"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by blast on 2007-09-04
Hi all,
I've just installed Ubuntu Server Edition on an AMD 64 machine.  During installation I'm pretty sure the installer recognised my network card, because it detected that there was no DHCP server on my network.

So... I manually configured.  Now that the OS is installed I've no network connection.  There are no ping responses on the internal network.

What should my first checks be in this situation?  There is no GUI at the moment, so I'm in terminal mode...



Thanks!


Regards
Stu

---

### Post by blast on 2007-09-04
further to this

from the machine, I can ping 127.0.0.1 and 192.168.1.20 and that's fine... I just can't ping anything on the network, or vice-versa!

ifconfig tells me that eth0 and lo are up

Regards
Stu

---

### Post by Siph0n on 2007-09-04
127.0.0.1 is the same as localhost, so that will always work. Its just pinging  yourself.... Though 192.168.1.20 is on the network. Is your router giving u that IP address? Have you tried pinging your router???

---

### Post by blast on 2007-09-04
hi there
that's a static IP that I've assigned. 

I switched on my DHCP server temporarily... and ran dhclient... but the machine does not find the DHCP server.


Thanks


Regards
Stu

---

