---
title: "Squid to bypass a port restriction on a firewall"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by thusi02 on 2007-09-13
Hey all you experienced Gammers/Firewall security guru's

I am trying to have a few of my friends that are under heavy firewall try to play this game: Settlers ( [http://solito.free.fr/catane/game.php?id=2&type=full](http://solito.free.fr/catane/game.php?id=2&type=full) ) 

However, their firewall blocks port 4002. I tried to setup a squid proxy however, it still doesn't work for them. They go to like showmyip.com and it still shows them their own ip even through their proxy is set to use my squid proxy server any thoughts?

Cheers, 
Nathan

---

### Post by multi on 2007-09-19
I'm kinda new too to the wonderfull world of Ubuntu, but I think the way to go is to setup an SSH tunnel from the client machines to your squid proxy. They are then sending and receiving encrypted data from the clients machines through an allowed port in their firewall to your proxy. I can't realy tell you how to do this, but i've seen plenty of functional howto's on this forum. If the clients are running on Windows you might consider running Putty as SSH client. Ubuntu has a SSH server build in.

---

