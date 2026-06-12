---
title: "[Server 8.04] DHCP/DNS problem"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by frade on 2008-07-09
I can't access the server through its 'new' hostname. it is accessible by IP and by it's DNS entry (nslookup), but not by its new host name.
I searched around and already added 'send host-name "machineA";' to /etc/dhcp3/dhclient.conf and restarted several times and it didn't work.
i have a lamp setup.

Anyone out there had this problem before, or know a solution?

Not sure if it's relevant, this is a virtual machine.
There are also a winXP, win2k3 on the same host. 
They dont have the same problems.

---

### Post by Oak37 on 2008-07-13
Hi,
I had this problem as well and the dhcpclient configuration didn't seem to work but I think it was because I was editing it incorrectly. My dhclient.conf file was just a single line compared to previous versions of Ubuntu which were more verbose. When I read the instructions I assumed you had to replace the entry for *request host-name* with *send host-name "machine"*. This was the wrong way of doing it, instead I added *send host-name "<hostname>";* before the other line in the configuration file. After a restart it worked for me. Maybe try again with "<hostname>" instead of "machineA", the <> brackets might make the difference.

---

