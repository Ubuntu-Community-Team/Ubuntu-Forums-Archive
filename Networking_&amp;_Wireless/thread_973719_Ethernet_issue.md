---
title: "Ethernet issue"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by noremac on 2008-11-06
Out of no where, a couple hours ago my internet stopped working on my desktop. After finding out that others in my apartment complex had internet (apartment supplies the internet) I knew it was my end. Having two ethernet cards on my motherboard, I moved the cable over and sure enough it started working. 

However, my conky and more particularly vnstat are configured to this ethernet card, eth1. Having months of stats saved up, I'd rather not have to lose that. I tried restart the network drivers by

```
sudo /etc/init.d/networking restart
```

and didn't do a thing for me. The other card works just fine still. 

The only thing I have not done is a restart of the system. Uptimes are rather precious to me and figured I would try for some minor help before I restarted. I have a feeling a simple restart may fix the issue...

Appreciate any help,

-Cameron

---

### Post by noremac on 2008-11-07
Well, I have restarted now and still no luck.

It appears I am getting an IP from my apartment complex's router when I am connected to my original eth1 card, but it wont ping any address or anything. 

I really want to know why this card is screwy but not the other. I would rather not just say Meh and go along with this one.

-Cameron

---

### Post by noremac on 2008-11-07
Well, I dont know what the problem was but I tried hooking my old router that I stopped using back up. 

After messing with the settings inside the router and having no success at getting the internet working with it, I hooked my connection back up straight to the computer and the eth1 connection that stopped working, and it was working again. Seems odd...

-C

---

