---
title: "[Lubuntu 13.10] Port forwarding not working"
date: 2014-01-06
forum: Networking &amp; Wireless
---

### Post by mihnea13 on 2014-01-06
I`m trying to open a port to acces from the internet (not from LAN) so that it can serve as a listening port for Nicotine+ (a client app for soulseek) but I simply cannot get it to work. I`ve created the neccesary rule in the router`s settings but the port I chose is still closed, as tested by various websites (ipfingerprints.com, canyouseeme.org etc). I`m sure I`ve done this correctly because over the years I`ve added numerous rules for the same router and everything worked (I was using Windows though). 

I`ve tried enabling ufw (it was initially disabled) and also added a rule there for the same port number, like this:  

```
sudo ufw allow 443
``` 

This is my first time port forwarding in Ubuntu, so please let me know what I`m not doing right.

P.S. I know the security risks involved in opening acces to a port.

---

### Post by sanderj on 2014-01-06
IMHO: Do NOT install ufw. So remove it for now.

Using UPnP it was easy for me:

I had "UPnP" activated on my router
I installed nicotine+ and miniupnpc on my Ubuntu.
I started nicotine+, went to Edit -> Settings -> Server. On the right hand side, I checked "Use UPnP to fix portmapping". Click op Apply, exit, restart, and ... bingo: port forwarded.

[http://tools.slsknet.org/porttest.php?port=2234](http://tools.slsknet.org/porttest.php?port=2234) says "IP: 83.x.y.z Port: 2234/tcp open. Your router and Soulseek client is configured correctly."

upnpc -l confirms this:

```
 4 TCP  2234->192.168.0.105:2234  'libminiupnpc' '' 0
```

PS: I will not react to posts saying UPnP is insecure. HTH

---

### Post by mihnea13 on 2014-01-07
Thanks, using UPnP solved it.

---

