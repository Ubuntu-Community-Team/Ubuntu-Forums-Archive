---
title: "Slow wireless"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by hundred1906 on 2008-05-02
Since upgrading to 8.04 my wireless link has become very slow. Has anyone else had this happen.

Incidentally, where do you find out what version of Ubuntu you actually have. Mine has what looks like a hair permed heron on the desktop. Is that a Dapper Drake?

---

### Post by Aearenda on 2008-05-02
```
cat /etc/lsb-release
``` will set the cat among the pigeons (oh sorry we haven't got to P yet...)

I've seen slow wireless on a bcm4306 card - lots of threads about that one around...

---

### Post by ushills on 2008-05-02
Try the following

```
sudo nano /etc/modprobe.d/blacklist
```

and add the following

```
blacklist ipv6
```

then 

```
sudo /etc/init.d/networking restart
```

---

### Post by leecho0 on 2009-05-06
Same thing happened to me. I used a realtek 8185 w/ 8.04 and it worked w/ ndiswrapper. But after I did a clean install, the wireless barely works. I also tried a dlink dwl-g122, edimax ew7318USg, but they're both really slow. 
(and no, blacklisting ip v6 didn't help)

---

