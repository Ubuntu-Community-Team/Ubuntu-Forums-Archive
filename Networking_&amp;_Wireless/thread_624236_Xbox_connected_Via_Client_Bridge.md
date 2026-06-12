---
title: "Xbox connected Via Client Bridge"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by Nowlan1971 on 2007-11-26
I am looking for a solution to my FTP problem I am having with my Xbox.


Background

My Ubuntu Desktop and Ubuntu Laptops were connected to the internet with DHCP  thru a D-link router, I had my Xbox running XBMC connected to the same router, so I could stream Shoutcast and FTP movies onto the HD of my Xbox with Gftp. 

Today 

I moved my Xbox to my TV room and I hooked my Xbox up to a linksys Router with the DD-WRT firmware, I have it set up in Client Bridge connection to the D-link router and have access to the internet that way, I am still able to stream Shoutcast, and get weather and such, But....

I am no longer able to FTP my Xbox. Xbox is on Static IP 192,168.1.157, in XBMC, the assigned IP is 192.168.1.116, I tred FTP to both of these IP but no luck.


Thanks

Am I missing anything in the Client Bridge set up I may not know about.

---

### Post by mellowd on 2007-11-27
Are you able to ping or trace to the xbox?

---

### Post by Nowlan1971 on 2007-11-27
I am not able to ping or trace the xbox by either IP

Thanks

---

### Post by mellowd on 2007-11-28
I'm not sure how this 'client bridge connection' works but it looks like you are making it overly complicated. Why are you connecting the xbox to a router, then to another router? Why not connect the xbox to the second router?

Also, why has the xbox got 2 seperate IP's? There should only be one.

What I can guess off the top of my head is that if you want to get to the xbox you probably need to browse to the IP of the second router. Remember on eash side of a layer 3 device (router) you have different subnets. The networks don't actually know where the other subnets are, the router does. 

You would probably then need to setup port forwarding on the router for it correctly work.

This is the reason I said it's overly complicated. It's possible to make it work but it'll take a fair bit of config.

---

### Post by Nowlan1971 on 2007-11-29
thanks mellowd,

I was looking around on the xbox last night, and noticed in the evox settings it is set to static ip of 192.168.1.157, and in the XBMC setting it is set for dhcp. I didn't get a chance to try changing the settings last night to test it. 

The reason I hve 2 routers setup, is so I can have my Xbox in my TV room, away from my DSL modem and router. I still wanted to stream  shoutcast, and I also have Xdsl installed incase I wanted to surf the net on my TV.  I don't have a XBox wireless adapter, and the Client Bridge Setup on the Router with the DD-wrt firmware is the easiest way to get my Xbox connected to the Internet.

thanks again

---

