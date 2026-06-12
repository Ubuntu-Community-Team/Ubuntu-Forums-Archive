---
title: "Asking if you knowedable people can solve a domain name? Routing problem?"
date: 2019-03-22
forum: Networking &amp; Wireless
---

### Post by adrian-h on 2019-03-22
I am learning how to do things and use several small low power computers rather than one decent computer for playing with, my desk top PC is a separate machine I tend not to play with.

I have managed to run up a vehicle tracking system on an old machine and now for the sake of it I am trying to run phpb on another.

So for example I use one of the redirect services to redirect [http://vehicle.adrian.net](http://vehicle.adrian.net)  ( not real ) back to my home WAN IP.  I then forward port 80 requests to a small server within my home network.  That is fine it works OK.

Now I also want to have [http://phpbb.adrian.net](http://phpbb.adrian.net) (again not real) to my home WAN IP and forward that to a different machine to serve that.  I can not use port forwarding as they will both use the same port 80, or 443 if https.

It seems my home router can only do port forwarding (game and application sharing it calls it?) so is there a way once it has been passed to a machine on my network to decide which internet requests are ,meant for it and which should be forwarded to another machine?  Can UFW do this on CNAME.  That last restriction I have is that the machines are single network port units so I do not have ETH0 and ETH1.  If there a low cost router that could solve this issue so that everything port 80/443 is passed to an internal router and then on to the correct server based on if it comes in for [http://vehicle.adrian.net](http://vehicle.adrian.net), or [http://phpbb.adrian.net](http://phpbb.adrian.net).

Am I over complicating it for myself.  I know that if I had a good machine with good resources I could probably run Apache2 and have several virtual hosts, but I use low power thin clients to play with running 16.04 at present.

Thanks

Adrian

---

### Post by Jaffray on 2019-03-22
If you setup nginx in the middle and then setup seperate server {} for each.  It will use the "server_name" and the "proxy_pass" variables.  If you research that it should solve your issues.

---

### Post by adrian-h on 2019-03-22
I will have a look at what nginx is, not something I recognise, but does that mean I need three PC,s?

Just read the intro page and it sounds likes it's above my level of understanding, but I will continue to read.

Adrian

---

