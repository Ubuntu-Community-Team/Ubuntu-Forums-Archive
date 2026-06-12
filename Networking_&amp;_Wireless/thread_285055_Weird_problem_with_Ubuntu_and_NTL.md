---
title: "Weird problem with Ubuntu and NTL"
date: 2006-10-26
forum: Networking &amp; Wireless
---

### Post by finferflu on 2006-10-26
Hi all,
I'm having a very strange problem..
I've just had installed my NTL broadband connection, and I've got two laptops with Ubuntu (Dapper Drake) installed. My one (Acer Travelmate 433) and my friend's (IBM Thinkpad A21m) are both connected to the same line through a hub, which is connected to the router. 
The point is that I can easily get connected to the internet (just plugging the cable in - the connection gets recognised as DHCP), but my friend can't. I've also tried to plug his computer straight into the router, but there's no way his machine recognises the connection: I've tried with several Activate/Deactivate in the Networking menu, with many reboots and also pppoeconf, but no result.

In the past we were able to share the connection into another house, with another company (Boltblue), and another router, using the same hub...

Is there anyone that can lead me to a solution?

Thanks a lot for your time..

---

### Post by kidders on 2006-10-26
Hi there,

Tinkering with PPPoE is the wrong thing to do afaik ... you should undo any PPoE-related stuff you've tried, if you can. If you're using cable broadband, a DHCP client should be all you need.

---

### Post by finferflu on 2006-10-26
Well, I didn't tweak with PPPoE, I just used it to see whether it could find anything... I didn't actually continue the wizard... So there's nothing to undo, I guess..

---

### Post by kidders on 2006-10-27
Hey again,

You know, it occurs to me that this may not work for you at all ... Assuming NTL in Manchester works the same way as NTL in Dublin (which, of course, may *not* be the case), I don't think two PCs will be able to share the same direct connection to the modem. This should've struck me before now ... sorry :confused:

My NTL cable modem assigns PCs its own external IP address. That never really bothered me, since I've never needed to plug two computers into it, but afaik it will prevent you from doing so :-( Instead, I have an old PIII acting as a router between NTL and my own PCs, handling my NAT, firewall, etc.

NTL customer support will be able to confirm this for you, but as far as I can tell, you have two options:

[LIST=1]
[*]Put a hardware router or a crappy old PC (with iptables & two network adapters) between you and NTL, and leave it on all the time.
[*]Configure one (or all) of your computers to act as software routers, so they can access the internet independently *and* share the connection with anything else that happens to be plugged into them.
[/LIST]

I hope this helps.

**Edit:** My modem is an NTL 250 ... unlike other modems, it seems to allow no user-end configuration whatsoever :-(

---

### Post by finferflu on 2006-10-27
Hi, thanks for your reply.

I think I've found out the problem. I was reading [a tutorial]("http://homepage.ntlworld.com/robin.d.h.walker/cmtips/swap.html#swap") and I think the main problem is that I need a router, rather than a hub, to handle my connections. In fact, due to my ignorance, I called my ntl:250 a router, but it actually is a modem. I would need to connect the modem to the router, an the laptops to the router. The main problem is that the modem is only able to register one MAC address a time, so everytime I want to connect one laptop to the internet, I need to switch the modem off for 10 seconds, and turn it on again. I tried with my friend's laptop and it worked. 
So I think I need a router, and I'll need to follow this procedure:
> If the device you have just connected to the STB is a router, then you should perform the registration procedure via a web browser in one of the LAN clients of the router, although it will be the MAC address of the WAN port of the router that you will be registering, not that of the PC running the browser. When you have completed the MAC registration page (or you are asked to close the browser and restart), restart the router (or make it request a new DHCP lease), not the PC.
(quoted from [http://homepage.ntlworld.com/robin.d.h.walker/cmtips/register.html#pacereg](http://homepage.ntlworld.com/robin.d.h.walker/cmtips/register.html#pacereg))
To my understanding I will just need to turn the modem off, connect the router and the laptops, and then turn it back on. 

But before spending money for a router, do you think what I said is plausible?

Thanks for your time.

---

### Post by kidders on 2006-10-27
What you've said is exactly right :-) Most ISPs supply routers with their connection equipment; it just so happens that NTL doesn't seem to. How typical lol.

The easiest solution is to buy a router, like you said. Depending on your hardware though, there may be (trickier but cheaper) alternatives, that involve one or other PC acting as a middle-man for the other.

The choice is yours :-)

---

### Post by finferflu on 2006-10-27
Ok, thanks again for your reply!
I'm not very good at networking (as you might have understood) so I  would like to have no middle-men around :p 
I was also thinking about a wireless router (since I've seen good improvements on wireless in Edgy Eft).. It doesn't depend on the ISP, right?

Thank you.

---

### Post by kidders on 2006-10-27
> **finferflu said:**
> Ok, thanks again for your reply!
I'm not very good at networking (as you might have understood) so I  would like to have no middle-men around :p 
I was also thinking about a wireless router (since I've seen good improvements on wireless in Edgy Eft).. It doesn't depend on the ISP, right?

Thank you.

Yeah, the cheapskate solution is a bit messy, alright. You should be fine with almost any router (wireless or not) that you find, _provided it is happy to accept an IP address via DHCP_, which you shouldn't take for granted.

Happy hunting!

---

### Post by finferflu on 2006-10-27
Thanks!
I've ended up buying the cheapest one I could find: [http://www.aria.co.uk/ProductInfoComm.asp?ID=22746](http://www.aria.co.uk/ProductInfoComm.asp?ID=22746)

I'm only a student, I can't afford such losses of money :D 
We'll see how it goes on Monday. :D

---

### Post by finferflu on 2006-10-30
Good. The router has come, and my shared connection works.

There's only one issue: when I turn off one computer, and turn it back on, it won't get connected again. What I need to do is to turn off both computer, the router and the modem, then turn the router and the modem on, and finally turn the computers on. That's how I get my shared connection back. It's very frustrating, and moreover I don't even know why I need such a procedure. What's wrong?

Thank you.

---

### Post by mooscape on 2006-10-30
:KS Aah! This sounds like my problem.  I also have two machines connected via a hub to my cable modem (Scientific Atlanta).  The second machine cannot get ipv4 on this modem with DHCP.  (Although this seems to work everywhere else I connect)  Will keep you posted if I get results....

---

### Post by finferflu on 2006-10-30
Well, if the hub is connected to a modem, that's the problem.
You need to get a router in order to get a shared connection. The hub is not able to handle multiple connections if it's only connected to a modem. 
If you read my previous post, you'll see that I was trying to do the same thing, and I had to buy a router.

Hope this helps.

---EDIT---
Actually you could give a look to this: [http://homepage.ntlworld.com/robin.d.h.walker/cmtips/homelan.html](http://homepage.ntlworld.com/robin.d.h.walker/cmtips/homelan.html)

---

### Post by mooscape on 2006-11-11
Have bought a new Linksys wrt54g (version 7) router.  Now both machines are up and running beautifully on the internet.  :D

---

