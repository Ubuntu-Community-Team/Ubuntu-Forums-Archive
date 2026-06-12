---
title: "Wireless DNS stopped working"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by petrojn on 2008-06-07
Normally I can fix problems like this but this one has got me stumped!?

My Compaq 8510w laptop network works normally when connected by an ethernet cable but when connected using wlan can no longer resolve dns.

I've played around with the nsswitch.conf file (made sure the hosts entry had "files dns") and changed the resolv.conf file to use my ISP domain server rather then the NAT router which works by default.

I can ping google's IP address but not resolve it. 

Maybe a bad hardy heron update somewhere - it was a week since I last used the wlan at home with this laptop.

Anyway I'm now stumped and any help would sure be appreciated!!

Cheers
Pete

---

### Post by superprash2003 on 2008-06-07
do you use static ip or DHCP?

---

### Post by petrojn on 2008-06-07
Dhcp

---

### Post by superprash2003 on 2008-06-07
try using opendns [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by petrojn on 2008-06-08
Thanks that didn't help though.

I have a wireless connection and a wired cable to the same router.  When I use NetworkManager to switch between interfaces the DNS stops working for the wireless interface only.  A different laptop using wireless with windows xp has no problems with that router so it's something with ubuntu on this laptop...

Here are details of my dhcp.conf if that helps (minus the commented lines):

send host-name "<hostname>";
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
timeout 30;

Very weird behaviour and strange that no one else has reported something similar...

---

### Post by petrojn on 2008-06-08
It turned out to be the lokkit firewall causing the issue!

Will try to find out why - it may also be because it was auto configured at work while using a wired connection.

---

