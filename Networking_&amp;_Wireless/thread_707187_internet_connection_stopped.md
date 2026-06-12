---
title: "internet connection stopped"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by nagaraj on 2008-02-25
using ubuntu linux 7.01 on a wired network with a dsl modem. 5 terminals all with ubuntu but two with xp as well. internet was working fine but stopped suddenly. internet works alright on xp. tried finding any recent changes but could not. i've absolutely no experience in solving problems of this kind nor do i understand meny technical terms discussed in these forums, only i'm hell bent on using linux. all help is welcome.
thanks in advance

---

### Post by wadesmart on 2008-02-25
Ok. So you have a router or hub connect to your DSL modem and then 5 computers connected to your router/hub. 

First, check your router to be sure you are assigning 5 IP addresses. 
Also, post back on the make and model of your router.

Now, in Ubuntu, in the top right hand side, look for the network icon - click it and chose Manual settings. When this comes up you should see Wired Connection. Does it say DHCP under it? 

On the DNS tab you might just look to be sure you actually have the DNS servers in there. This is done automatically. 

Did your ubuntu pcs go off line when your XP's went online?

---

### Post by stream303 on 2008-02-26
> **nagaraj said:**
> using ubuntu linux 7.01 on a wired network with a dsl modem. 5 terminals all with ubuntu but two with xp as well. internet was working fine but stopped suddenly. internet works alright on xp.

In this situation, I would force all machines to be absolutely certain of their primary and backup dns addresses, by placing these values *into the router setup page*.

If you don't know your ISP's dns addresses, a good alternative is to use the ones from [www.opendns.org](www.opendns.org) - take a look at the bottom right.

Putting the dns addresses into the router itself has taken so much pain out of mixed-environment setups for me that I wish I had a nickel each time.... :)

---

### Post by nagaraj on 2008-02-28
my adsl modem is hauwei smart AX MT841. and the modem as well as the pcs are connected through hubs.
actually i had installed ubuntu in one of the pcs and had sarted update and went for some otther work. when i came back an hour later the progress bar had stopped halfway and there was no internet connection.the other pcs on the LAN too could not connect to the net. with pressing engagements i could not check for the next 12 hrs. then i noticed that linux was not able to connect while XP could. ll that make it any easier for u people to find the trouble?

---

### Post by nagaraj on 2008-03-05
finally it worked! solution was damn simple. changed the dns in network setup.

---

