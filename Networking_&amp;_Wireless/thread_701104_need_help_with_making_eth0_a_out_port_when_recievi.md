---
title: "need help with making eth0 a out port when recieving wireless through ath0"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by waldo899 on 2008-02-19
well the title basically says it all i want to receive internet through my wireless card but put the signal out through the eth0 i know it can be done on windows because thats how my friend has his xbox on internet and i dont wanna route a 100 foot cable all the way up to my room just to get internet so any help at all would be greatly appreciated thanks in advance

---

### Post by julian67 on 2008-02-19
> **waldo899 said:**
> well the title basically says it all i want to receive internet through my wireless card but put the signal out through the eth0 i know it can be done on windows because thats how my friend has his xbox on internet and i dont wanna route a 100 foot cable all the way up to my room just to get internet so any help at all would be greatly appreciated thanks in advance

you need to do a little research on NAT/Masquerading (aka Internet Connection Sharing in MS Windows). Probably the simplest way to achieve this in Ubuntu while using gui tools is to install  Firestarter (a front end for iptables, in effect a firewall) and follow the guide [Internet connection sharing]("http://www.fs-security.com/docs/connection-sharing.php") and also the guides here on ubuntuforums. It's pretty easy stuff and I use this same method so my wireless adapter is the internet gateway and my LAN connects through my wired connection. It's easy/basically identical to do it either way. 

Another easy way to do this is to use firehol, a command line config tool for iptables, which is also very easy to set up if you follow the tutorial found at [http://firehol.sourceforge.net/]("http://firehol.sourceforge.net/"). Both methods should work equally well (they have for me).

---

