---
title: "Load Balance two isp broadband connections"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by juanhidalgo on 2008-05-03
Hi

I currently have a Kubuntu box with three NICs: 

eth0: WiMax broadband inet connection
eth1: LAN
eth2: ADSL broadband inet connection

I'd like to know if there is a way to use those two internet links to route to the entire LAN, and load balance traffic between both.

I'm currently using one of those two links, wich I set up using the following tutorial: [http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

Is there a way to load balance both inet links, and make some kind of failover where if any of those links go down, nobody notices it?

I'm pretty newbie on all these, can anyonne give some guidance?

Thanks a lot!

---

### Post by SpaceTeddy on 2008-05-04
i've been searching for this on google for a while now (as this is a  question that interests me aswell - although i don't have anywhere to test it)... however i did come accross some interesting pages that might do what you want to do. However, as far as i can tell, they all shape their traffic on the destination network (i.e. if all clients use go to the SAME site, they will not balance)... but then i did not read the stuff through. So you might have to do that yourself.

So, here are the pages i found
[[COLOR="Blue"]http://www.the-scream.co.uk/forums/t7306.html[/COLOR]]("http://www.the-scream.co.uk/forums/t7306.html")
[[COLOR="Blue"]http://lartc.org/howto/lartc.rpdb.multiple-links.html[/COLOR]]("http://lartc.org/howto/lartc.rpdb.multiple-links.html") and from there [[COLOR="Blue"]http://www.ssi.bg/~ja/#routes[/COLOR]]("http://www.ssi.bg/~ja/#routes")
this is about hardware solutions of your problem [[COLOR="Blue"]http://www.dslreports.com/forum/r20329613-Load-balancing-router[/COLOR]]("http://www.dslreports.com/forum/r20329613-Load-balancing-router")
this is a distro that specializesed in this field (or so i think) [[COLOR="Blue"]http://www.pfsense.com/[/COLOR]]("http://www.pfsense.com/")
and this is the most usefull i could find, really [[COLOR="Blue"]http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/[/COLOR]]("http://blog.taragana.com/index.php/archive/how-to-load-balancing-failover-with-dual-multi-wan-adsl-cable-connections-on-linux/")

i hope this gives you some clue on what is possible and what is not... i am sorry i am no more help than that. I am very new to this field (load balancing) aswell :)

---

