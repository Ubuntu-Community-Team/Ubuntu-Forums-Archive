---
title: "wireless router tutorial"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by bjstabio on 2009-01-11
I have been using a wired router but want to switch to a WRT54GL wireless router.  Ubuntu 8.04 seems to know what to do with my wired router and I can connect to the internet without any setup on my part.  The wireless router won't connect to the internet, although my local network appears to be connected.  Is there a simple, easy to understand tutorial that will show me how to setup my wireless router?  Thanks for any help you can provide!

---

### Post by stanz on 2009-01-11
You'll need to follow the wireless router instructions to connect.
Usually its got an ip addy "http://192.0.0.1" you use in your browser address bar.
Once your in the router--you make adjustments.
Ya have the paperwork for it?

---

### Post by caro on 2009-01-11
I have a WRT54G.  If you are switching from a different router, I would use a wired connection to set the router up.  (Since you already have a router, I assume you know the basics).  Once you have the router working, adjust your wireless settings.  

I was lucky that my wireless card in my laptop recognized the wireless network with no difficulty.  Making sure I had the correct encryption and password was the only thing that took careful consideration.  Use WPA2 rather than WEP for better security.

---

### Post by bjstabio on 2009-01-11
There is no paperwork for it.  Everything must be on the installation disk.

---

### Post by stevoo on 2009-01-11
quick : 
Do you get an ip in the wireless mode ? 
-> iconfig command

System->Administration->Hardware Drivers.
Is there anything checked there  ?

---

### Post by stanz on 2009-01-11
caro ~ pictures say a thousand words!
I thought the wireless router was the problem -
get that working & it's all good!

---

### Post by bjstabio on 2009-01-11
I apologize for not being more specific.  At this time I don't have a box set up for wireless.  I'm trying to connect to the internet with my wireless router with a wired connection.

---

### Post by stanz on 2009-01-11
no prob...so your wired in right now.
does the ip addy in caro's pictures bring you into the router? (notice the addressbar)
to say.. follow caro's led...

oh ~ you can still view install docs on the disk, and go thru their instructions!
as in caro's pic - wireless needs to be turned on.

---

### Post by caro on 2009-01-11
> **bjstabio said:**
> I apologize for not being more specific.  At this time I don't have a box set up for wireless.  I'm trying to connect to the internet with my wireless router with a wired connection.

I thought the wireless connection was the problem too.

Usually the default IP address for a Linksys router is 192.168.1.1 or 192.168.0.1 and the DHCP range begins at 192.168.x.x, but that conflicts with my DSL modem's DHCP range so I had to change it to 192.168.10.1.

The default username is "admin" for Linksys (I think) and the password is left blank.  You will want to change those.  

I'm using the wireless router as my firewall and a DHCP server behind the DSL modem.  

Can you see your router from your computer?  Can you see the internet?

---

### Post by caro on 2009-01-11
> **stanz said:**
> caro ~ pictures say a thousand words!
I thought the wireless router was the problem -
get that working & it's all good!

stanz, i thought wireless was the problem but it looks like the router set up is the issue.

---

### Post by theozzlives on 2009-01-11
If it's a linksys router, open a browser and type 192.168.0.1. If this is the first time going to setup, your password will either be admin or administrator (username blank). I think I remember right (I use NetGear now).

---

### Post by stanz on 2009-01-12
Working yet?
From the wall plug, are you using the wired router - to the wireless router - to a pc?
and:
> At this time I don't have a box set up for wireless.
Does this mean you don't have a wireless card in there yet?
(your just trying to set things up?)

I hope ya got progress!!   :)

---

