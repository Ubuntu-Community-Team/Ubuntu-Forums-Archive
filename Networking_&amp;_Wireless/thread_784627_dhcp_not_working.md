---
title: "dhcp not working"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by redss on 2008-05-06
My ubuntu fiesty system is not able to get an ip address from my router via dhcp.  How can I release and re-request an ip address via dhcp?  (I don't know the command)

Any additional troubleshooting hints will be greatly appreciated.

Thanks!

---

### Post by superprash2003 on 2008-05-06
try sudo /etc/init.d/networking restart
 or 
ifdown eth0 and then ifup eth0 where eth0 is the network card

---

