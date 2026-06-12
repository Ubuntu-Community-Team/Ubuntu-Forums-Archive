---
title: "Create pppoe connections and routing traffic through each one"
date: 2007-07-13
forum: Networking &amp; Wireless
---

### Post by squirrelza on 2007-07-13
Hello,

I'm new here and new Linux/Ubuntu user. Anyways I've tackled my first problem. I need to figure out the easiest way to create two pppoe connections. After I've done that, I need to figure out how I can route specific traffic through one account, and other traffic through the other. 

Thanks!

---

### Post by squirrelza on 2007-07-13
Sorry for the bump. This is quite important!

---

### Post by mips on 2007-07-13
You are being very vague, you need to provide more information. ie route tables, ifconfig, what traffic you want to route to what networks etc.

---

### Post by squirrelza on 2007-07-13
> **mips said:**
> You are being very vague, you need to provide more information. ie route tables, ifconfig, what traffic you want to route to what networks etc.

Well it's nice to see another South African reply. This will make my life easier :) Basically what I want to do is set my router to bridge mode, and route all local traffic through one pppoe connection (an IS account), and route all international traffic through another pppoe connection (a SAIX account). This is how I did it on Windows (in conjunction with a program called Route Sentry, maybe you are familiar with it). I'm not sure how this can be done on Linux.

---

### Post by mips on 2007-07-13
How did you determine what was local & international with route sentry ?

I don't think it is impossible but it does not sound easy. It's not to hard to make rules based on certain networks/ip addresses though.

---

### Post by squirrelza on 2007-07-13
> **mips said:**
> How did you determine what was local & international with route sentry ?

I don't think it is impossible but it does not sound easy. It's not to hard to make rules based on certain networks/ip addresses though.

Route Sentry fetches some kind of route table from what I know. I am just looking for ANY way where I can separate local and international traffic (without using another computer). Would something like [this]("http://alm.za.net/ip/localroutes4.txt") help?

---

### Post by mips on 2007-07-13
Went to look up route sentry and came across this. "All "local" routes are stored in the localroutes.dat file found in the Route Sentry folder".

If you have the above info then it should not be to hard to do that is if you can extract the information. There must be a database somewhere with all local netoworks listed.

Alternatively you can get the information by telnetting to **public-route-server.is.co.za **and entering "show ip bgp" to see all local routes. This information can be extracted and you could build yourslef a custom routing table based on this.

---

### Post by mips on 2007-07-13
> **squirrelza said:**
> Route Sentry fetches some kind of route table from what I know. I am just looking for ANY way where I can separate local and international traffic (without using another computer). Would something like [this]("http://alm.za.net/ip/localroutes4.txt") help?

 I suspect route sentry pulls its info for local networks from the local route server I posted above.

This should be a piece of cake now that the information is easily accesible.

---

### Post by squirrelza on 2007-07-13
I have no idea on how about to do this. Ok so I've got a list of all the local IPs. What do I do now? I would search this on the internet, but I don't know what the term I'm trying to achieve is called!

---

### Post by mips on 2007-07-13
Your defualt route will point to the saix connection. If you have a default route to IS then you need to delete it and specify one for SAIX. Then you need to add a bunch of static routes for all the local traffic from the list.

Hang on while I find you some links.

---

### Post by mips on 2007-07-13
[http://ubuntuforums.org/showpost.php?p=1800905&postcount=12](http://ubuntuforums.org/showpost.php?p=1800905&postcount=12)
[http://ubuntuforums.org/showpost.php?p=950148&postcount=3](http://ubuntuforums.org/showpost.php?p=950148&postcount=3)
[http://www.linux.org/docs/ldp/howto/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html](http://www.linux.org/docs/ldp/howto/Adv-Routing-HOWTO/lartc.rpdb.multiple-links.html)
[http://gentoo-wiki.com/Dual_internet_connections](http://gentoo-wiki.com/Dual_internet_connections)
[http://gentoo-wiki.com/TIP_Dual-Homed_Gentoo_Server](http://gentoo-wiki.com/TIP_Dual-Homed_Gentoo_Server)

Make sure you understand what is permanent and what is not. I would hate for you to paste in 650 odd routes just to loose them on reboot.

I would get a list from the local route server which seems more up to date, pull it into a spreadsheet with multiple columns and delete all the columns you dont want and only save the ip data/mask as a txt file which you could then copy and paste to a config file.

---

### Post by squirrelza on 2007-07-13
Thanks. I'm going give this a go!

---

### Post by mips on 2007-07-25
And, how did it go ?

---

