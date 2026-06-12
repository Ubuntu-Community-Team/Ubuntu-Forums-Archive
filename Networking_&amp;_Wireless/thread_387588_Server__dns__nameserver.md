---
title: "Server / dns / nameserver"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by Shevilie on 2007-03-18
Well I know some linux / unix and I have a running server elsewhere on the internet.. Now I want to have my own at home, actually I want two :) The problem is that I am behind a router (I got full access to it, but I got only one WAN IP So I need it) Now I have my own domain and I can set the records there so they point to my WAN IP..

IE

web.mydom.com - 80.80.80.80
remote.mydom.com - 80.80.80.80

Now I know how to portforward, but I want so I i use link number one It goes to 10.0.0.2 and if I use link number 2 it goes to 10.0.0.3

(Linksys router)

---

### Post by Floppyjoe on 2007-03-18
> **Shevilie said:**
> Well I know some linux / unix and I have a running server elsewhere on the internet.. Now I want to have my own at home, actually I want two :) The problem is that I am behind a router (I got full access to it, but I got only one WAN IP So I need it) Now I have my own domain and I can set the records there so they point to my WAN IP..

IE

web.mydom.com - 80.80.80.80
remote.mydom.com - 80.80.80.80

Now I know how to portforward, but I want so I i use link number one It goes to 10.0.0.2 and if I use link number 2 it goes to 10.0.0.3

(Linksys router)

You can route traffic from web.mydom.com to 10.0.0.2 and
route traffic from remote.mydom.com:81 to 10.0.0.3.
You would have to set up the second server to listen to port 81 for incoming connections.

---

### Post by Shevilie on 2007-03-18
Well I would like to avoid the port things / wouldn't use two different hostnames then :P

---

### Post by Floppyjoe on 2007-03-18
Unless you have a special router that can differentiate between the two host names I don't see another way of easily doing that. But then I'm not all that knowledgeable in this area. Plus you can still use two different names.

---

### Post by dbott67 on 2007-03-18
I think FloppyJoe is right on this one.  Most home routers will forward based on port # only.  Using a different port # as FJ suggests would be the easiest.

Having said that, you *may* be able to setup a vhost on 10.0.0.2 that re-directs to 10.0.0.3.

Configure the external DNS so that both  **web.mydom.com** and **remote.mydom.com** are pointed to the external IP of your router.  Setup port-forwarding on port 80 to go 10.0.0.2.  Using Vhosts in Apache, create 2 sites on 10.0.0.2:
- web.mydom.com (contains actual web content)
- remote.mydom.com (redirects to content located on another server, ie. 10.0.0.3)

In IIS, this is fairly straight-forward, although I've never done it in Apache, so I don't know the steps involved in re-directing.

The other unknown is if the router will pass the vhost name through (allowing it to be read by Apache and ultimately to the correct vhost directory).

You may be up for a bit of trial & error.

-Dave

---

### Post by Shevilie on 2007-03-18
Thabk you :) I'll try the redirecting :)

---

### Post by Mr. C. on 2007-03-18
Some DNS services will provide URL redirects or URL frames, so you can have:

web1.mydom.com - xx.xx.xx.xx:80
web2.mydom.com - xx.xx.xx.xx:81

Routers deal in IP addresses only and don't care about the data payload inside an HTTP request, which contains the URI.  The router will not strip such information; URIs are available to any receiving service.

As other's have suggested, your options are:

  - 2 listening ports (which implies two port fowards)
  - use virtual hosts with 1 IP listener
  - use redirects from web1 server to web2 server

MrC

---

### Post by dbott67 on 2007-03-18
> **Mr. C. said:**
> Routers deal in IP addresses only and don't care about the data payload inside an HTTP request, which contains the URI.  The router will not strip such information; URIs are available to any receiving service.

This is good to know --- I've never tried it on a home router.  I've only done the unique ports option.

Thanks.

-Dave

---

