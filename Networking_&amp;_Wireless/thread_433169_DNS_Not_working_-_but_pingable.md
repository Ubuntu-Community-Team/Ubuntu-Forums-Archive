---
title: "DNS Not working - but pingable?"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by Rob_Quads on 2007-05-04
I am trying to setup my laptop to Ad-hoc network to a desktop which has an internet connection (XP System running ICS)

The two machines are connected OK. I can ping the desktop fine (192.168.0.1). I can also ping an address on the web i.e. 212.58.224.82 which is [www.bbc.net.uk](www.bbc.net.uk)

BUT I can't get any DNS to work on my Ubuntu system. I have also tried putting in my desktops internet DNS addresses to resolve.conf. Again I can ping them fine.

The contents of my /etc/resolv.conf file is

nameserver 192.168.0.1
nameserver 194.168.4.100
nameserver 194.168.8.100

All the addreses above I can ping find it just wont do any DNS stuff. Any ideas??

---

### Post by mojoman on 2007-05-06
I assume 192.168.0.1 is to your router and that might be correct (I seem to remember that I too had this earlier on but now I don't. I think it slowed down the response time and that it was improved by adding the ISP's nameservers instead). Are 194.168.4.100 and 194.168.8.100 really the IP to your ISP's nameservers? Because it should be.

My resolv.conf look look this:

```
search bredbandsbolaget.se
nameserver 81.26.228.3
nameserver 81.26.227.3
```

/mojoman

---

