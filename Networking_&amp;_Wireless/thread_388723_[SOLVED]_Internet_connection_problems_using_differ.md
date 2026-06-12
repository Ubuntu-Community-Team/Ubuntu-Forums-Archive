---
title: "[SOLVED] Internet connection problems using different adsl wireless routers"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by e_james on 2007-03-19
I have 2 adsl wireless routers. One is Netgear and one is Addon GWAR3000.
Both work adequately with Windows (XP SP2) but only the Netgear works with Ubuntu (Dapper and Edgy). With Windows the Addon seems to require DNS addresses to be set in the nic configuration but this doesn't seem to be sufficient for Ubuntu. I can ping the DNS addresses. 

From other threads I picked up a clue that ipv6 may be a factor. In the Edgy installation I found that turning off some of the ipv6 settings allowed Thunderbird and Firefox to function but not system updates.

In addition, when I add DNS addresses in the networking settings and the fiddle around with other tests, when I look again the DNS addresses have often disappeared!!

I would welcome any suggestions which might get the Addon working properly.

---

### Post by spd106 on 2007-03-21
For the DNS issue have you tried adding the server addresses to your /etc/dhcp3/dhclient.conf file.

I added this line to mine, it's pointed at opendns.com's servers
```
prepend domain-name-servers 208.67.222.222,208.67.220.220;

```

---

### Post by e_james on 2007-03-27
spd106

Thanks for the suggestion. I followed the advice above and it seems to have done the trick. I just switched on my laptop and it connected straight to the internet without a hint of difficulty. Sorry for taking some time to come back here but, for the moment, Windows is my main OS.

---

