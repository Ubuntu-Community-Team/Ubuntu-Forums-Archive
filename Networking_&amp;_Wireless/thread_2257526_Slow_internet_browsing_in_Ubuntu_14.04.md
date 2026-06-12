---
title: "Slow internet browsing in Ubuntu 14.04"
date: 2014-12-20
forum: Networking &amp; Wireless
---

### Post by c-m on 2014-12-20
I'm using ubuntu 14.04 on my desktop machine and find that 50-60% of the time I'm having internet connection problems. i.e pages do not load or take an eternity to load.

My actual network connection is fine, speed test report good results, and if I boot into Windows I get good results. My Macbook is also fine, so it's just the Ubuntu setup.

I've seen reports of super slow wifi using ubuntu 14.04 but I'm on a good wired connection. 

I switched my DNS to google 8.8.8.8, 8.8.4.4 and that helped initially, but I don't think that's the answer, as I'm still experiencing problems.

When it's bad, it's so bad I have to reboot, and then usually the speed is fine.

Any suggestions?

---

### Post by r.stiltskin on 2014-12-21
Using DHCP or have you manually configured the ethernet connection?

What do you have in /etc/network/interfaces?

"When it's bad, it's so bad I have to reboot, and then usually the speed is fine."  -- So when does it get bad?

---

### Post by c-m on 2014-12-21
I've never touched /etc/network/interfaces. It contains
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

It's not really a case of it getting bad, it's a case I start the computer and the conenction is too slow. I restart the computer and it's fine. It never goes from being fine to being slow. It just starts up being one or the other.

It happens with DCHP, but I manually set the IP and gateway and then tried 8.8.8.8 and 8.8.4.4 as the nameservers to see if that helped. It didn't.

---

### Post by SuperFreak on 2014-12-21
Perhaps try a different browser

---

### Post by Lars Noodén on 2014-12-21
What kind of connection are you using, ethernet or wireless?  I'm having similar issues with 14.04 LTS but only on the wireless and only sometimes.  Ethernet seems to be fine.  But on the wireless interface, the connection is not only often slow, it can also disappear completely.

---

### Post by r.stiltskin on 2014-12-21
Are you experiencing this problem with only 1 particular browser?  If so, which one?  Have you tried other browsers?

Was this a clean install of 14.04, or a version upgrade?

Does the problem exist for all user accounts?  Have you tried creating a completely new user and testing the browser in that login?

---

### Post by houstonbofh on 2014-12-22
This can be a DNS issue, or an add issue. (Or both)  Modern web pages withhold display of content until all of the ads have loaded. (Idiots)  And since ads come from many places, slow DNS kills you.

Start with downloading namebench and getting a fast DNS.  But also load and run adblock+ and I bet things go quicker.

---

