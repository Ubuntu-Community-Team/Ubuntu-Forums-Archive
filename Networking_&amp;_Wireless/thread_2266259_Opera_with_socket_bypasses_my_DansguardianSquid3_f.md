---
title: "Opera with socket bypasses my Dansguardian/Squid3 filter"
date: 2015-02-21
forum: Networking &amp; Wireless
---

### Post by ecowan on 2015-02-21
I have a server set up with Dansguardian and Squid3 to filter internet traffic from the Ubuntu/Firefox laptops that my teenagers use. Now one of them has a cell phone with Opera with the 'sockets' setting. This bypasses my filter.
I have been reading and reading, but I'm not sure what would fix this. I did find and older HowTo, [http://archive09.linux.com/articles/113733](http://archive09.linux.com/articles/113733), that comes close, but a) it is based on an older Squid with different .conf settings and b) it is set up on a single self contained system, not a network filter.
Can someone suggest what would fix this, or point me to a HowTo?
Thanks. - Erny

I should add that I set my Asus RT-N66U router to refuse requests for port 80. This is supposed to force users to direct their http traffic through my server at 192.168.1.2:8080. But somehow the Opera browser ignores this.

---

### Post by ecowan on 2015-02-22
I have a clue.
Apparently Opera, when socket mode is set, uses port 1080. Does this mean that all traffic is sent through a proxy at Opera?
- Erny

---

### Post by ecowan on 2016-01-06
So I found a work around. I told my router to block traffic to port 1080 (Opera) and told the kids they had to switch to Firefox.
I'll mark this as [SOLVED].

---

