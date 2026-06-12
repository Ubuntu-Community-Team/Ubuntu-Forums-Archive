---
title: "Wireless N sometimes requires using sudo DHClient!"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by RMuscaritolo on 2010-06-15
Hey guys/girls,

Recently for about the past couple weeks, I've noticed a lot of connection issues with my home wireless N connection on my Ubuntu 10.04 laptop.

I know, "join the club", right. But this one seems pretty specific. When failing to automatically connect to my N network, I've pinned down the problem to DHCP... 

Basically after watching the wireless connection timeout again and again, I tried using a static IP to troubleshoot. Immediately I was able to connect without any further issues. 

Of course, my Windows boxes have no problem connecting to the network, but I wanted to look into this more because Ubuntu and Linux in general is just too good to giveup at this point.

So after narrowing the issue down to DHCP, I discovered that a workaround for my problem is start the connection to the Wireless network and than immediately run a "sudo dhclient wlan0" in a terminal. With this method, I'm able to connect nearly every time.


Does this happen for anyone else? Any ideas for a more permanent fix I could try, besides using a static IP? (I like to fix problems instead of just avoiding them =p )


BTW, running on a Dell XPS M1210 laptop - Ubuntu 10.04 (fully updated) and before anyone asks restarting the Router itself did not help, lol.


Thanks for your help!
-Rocco

---

### Post by RMuscaritolo on 2010-06-16
Shameless bump!

---

