---
title: "[SOLVED] nslookup time discrepancy"
date: 2008-11-04
forum: Networking &amp; Wireless
---

### Post by mike310z on 2008-11-04
In short in Ububntu 8.10

If I specify the IP address of a dns to nslookup on the command line  it takes 0m0.022s to reslove [www.google.com](www.google.com) and if I let the system specify the same dns it takes 0m2.034s

Its the same dns server (see below), can it really take Ubuntu 2 seconds to provide nslookup with the dns name 208.67.222.222 ?  I think it does and it correlates very well with how long firefox says its looking up say [www.google.com](www.google.com) and then how fast it loads.

My actual connection speed is high as proven by speedtest, dslreports etc and is about 2.21 MegaBytes/s

The two results below summaries the many tests I did, can anyone tell me how to get the faster performance in normal operation ?


time nslookup [www.google.com](www.google.com)
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
[www.google.com](www.google.com)	canonical name = google.navigation.opendns.com.
Name:	google.navigation.opendns.com
Address: 208.67.217.230
Name:	google.navigation.opendns.com
Address: 208.67.217.231


real	0m2.034s
user	0m0.000s
sys	0m0.004s



mike@desktop:~$ time nslookup [www.google.com](www.google.com) 208.67.222.222
Server:		208.67.222.222
Address:	208.67.222.222#53

Non-authoritative answer:
[www.google.com](www.google.com)	canonical name = google.navigation.opendns.com.
Name:	google.navigation.opendns.com
Address: 208.67.217.231
Name:	google.navigation.opendns.com
Address: 208.67.217.230


real	0m0.022s
user	0m0.000s
sys	0m0.008s

---

### Post by mike310z on 2008-11-04
To fix this you need to delete the dns servers that your ISP gave you.
I changed the dns server IPs in my router, but aparrently even after powercycling everything Ubuntu sticks to the old ones.
To fix this edit /etc/resolv.conf and remove the slow dns servers IP address, you can use the above method to test the speed of a dns server.

If you don't set the new dns IPs in your router or 'FIX' them some other way I suspect you may end up picking up bad dns server names again by way of DHCP

sudo  vi   /etc/resolv.conf

---

