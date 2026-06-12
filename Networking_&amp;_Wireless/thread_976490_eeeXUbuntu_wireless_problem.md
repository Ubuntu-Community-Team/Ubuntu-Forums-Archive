---
title: "eeeXUbuntu wireless problem"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by sammy888 on 2008-11-09
Hey.
Well here's the problem:
My friend has Asus EEE PC 701, using wireless to access the internet.
At first he was using XANDROS distro and everything was doing fine.
Well, then he installed eeeXUbuntu distro and since then he can't connect to wireless.
Router shows there's 1 PC connected (that would be asus), but when he's trying to connect via browser / telnet / ..
any remote connection.. doesn't work.
He can ping router (and gets reply), but when try to ping some remote site / ip, packages are sent but there's no reply.

---

### Post by deltaprime on 2008-11-09
its most likely your router configuration. Check that with entering 192.168.0.1 in your web browser when connected. can you connect to google.com and other webpages? or is there no access to the internet at all? Make sure your card is not in monitor mode. And post the output of > iwconfig here.

good luck

deltaPRIME

---

### Post by sammy888 on 2008-11-09
Hey, he tried iwconfig. The output says "Mode: Managed".
So, he can connect to router via browser by typing 192.168.1.1 
Still, there's no access to internet at all.. i can ping 192.168.1.1
When he's try ping google.com or some other IP's / host's i get: 
>ping google.com
ping: unknown host google.com
>ping 89.142.54.1
From 192.168.1.1 icmp_seq=1 Destinatino Net Unreachable
From 192.168.1.1 icmp_seq=2 Destinatino Net Unreachable
...same pattern

Any ideas ?

---

