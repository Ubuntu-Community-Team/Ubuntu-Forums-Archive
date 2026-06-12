---
title: "using network manager messed up my wireless"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by waldorf on 2006-12-11
So I used network manager from the beginning with a fresh install and everything was fine. Went to a cafe and couldn't connect using the network manager so I System>Administration>Networking and connect using that GUI (also had wifi radar running but didn't use it).

Go back home and network manager won't connect to my home network and System>Administration>Networking doesn't work either.

I can use a wired connection no problem. Wireless is working to the extent that it sees Homewirelessnetworkrouter, but cannot connect

](*,) 

Thanks in advance

---

### Post by scrooge_74 on 2006-12-11
humm I think that happend to me once.

open terminal window, and do sudo ifdown eth1 (or whatever you Pc gives to the wireless card)

then do sudo ifup eth1

and then try to go to the network manager

---

### Post by waldorf on 2006-12-11
thanks scrooge_74!

In the end the following worked. I had to disenable eth1 through the System>Administration>Networking GUI and then reboot so that the network manager could run the show.

I can't say I understand what happened, but it worked.

Thanks for taking the time to respond!

---

