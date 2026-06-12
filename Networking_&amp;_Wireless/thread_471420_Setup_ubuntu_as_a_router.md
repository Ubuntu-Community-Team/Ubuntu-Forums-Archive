---
title: "Setup ubuntu as a router"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by Cannon9559 on 2007-06-12
Hi guys (and maybe gals),

what i would like to do is setup my system to be the router for my home. I do have 2 wired NIC cards, and one wireless. I would like for the computer to broadcast a wireless signal so that i can connect to the internet with my laptop. I also have a couple of computers that need to connect to the "router" with cables, i think i need a switch to do this. This computer would basically need to provide DHCP, DNS, and do port forwarding. The reason why i want to do this is because i want a more powerful router, and seeing as how this is already a $1500 machine that should be able to handle it just fine, i don't see why i should go and buy another router that might break in a couple of months like my last 2 did.

Any help would be great, even if you were to point me to a great DIY page. I have found one that uses webmin, but found it to be unsuccessful in my case, so i would prefer to do it all manually. 

Thnx again.

---

### Post by nutz on 2007-06-12
This would be useful.

---

### Post by Mr. C. on 2007-06-12
How about spending a little time learning about routing:

Take a look at Routing Notes and Lab: [http://cis68c2.mikecappella.com/](http://cis68c2.mikecappella.com/)

Once you have that, we'll get to the rest.

MrC

---

### Post by spd106 on 2007-06-12
Here is another guide to try  [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

---

### Post by Cannon9559 on 2007-06-12
:pWow, thnx guys. These links should help alot. Silly me missed that one on the community website....lol. Thnx spd106. And thnx Mr. C, that link looks like an awesome resource for linux, I should atleast be an intermediate to advanced linux user if i go through all of that carefully.

Thnx again guys.......if I have other problems then I know where to come.:p

---

### Post by stchman on 2007-06-12
> **Cannon9559 said:**
> Hi guys (and maybe gals),

what i would like to do is setup my system to be the router for my home. I do have 2 wired NIC cards, and one wireless. I would like for the computer to broadcast a wireless signal so that i can connect to the internet with my laptop. I also have a couple of computers that need to connect to the "router" with cables, i think i need a switch to do this. This computer would basically need to provide DHCP, DNS, and do port forwarding. The reason why i want to do this is because i want a more powerful router, and seeing as how this is already a $1500 machine that should be able to handle it just fine, i don't see why i should go and buy another router that might break in a couple of months like my last 2 did.

Any help would be great, even if you were to point me to a great DIY page. I have found one that uses webmin, but found it to be unsuccessful in my case, so i would prefer to do it all manually. 

Thnx again.

You can buy a decent Linksys wireless router for under $50.  I have had my Linksys for a long time and it has never broken.

Not to mention that you have to keep a $1500 PC on all the time.  Think about the power consumption of a fully loaded PC vs a router.

If you are doing to setup a PC as a router for the challenge sake I can respect that.

---

### Post by nutz on 2007-06-12
If you have a server that runs 24x7 then adding routing responsibilities to it doesn't have any real cost provided no change to the network topography is required to make it happen.

The question is what would be the benefits to moving routing functions to the server versus a dedicated device on the network like a simple linksys router?

---

### Post by stchman on 2007-06-13
> **nutz said:**
> If you have a server that runs 24x7 then adding routing responsibilities to it doesn't have any real cost provided no change to the network topography is required to make it happen.

The question is what would be the benefits to moving routing functions to the server versus a dedicated device on the network like a simple linksys router?

I 100% agree that is that computer runs 24/7 then by all means.  I already said that if this person is doing this for the challenge then I commend them.  I was just pointing out that if they are doing it to save a few bucks then I just wanted to point the fact that a router consumes almost no power compared to a PC.

---

### Post by Cannon9559 on 2007-06-15
Actually, yeah, this server is on 24/7....it's running my "clan's" Battlefield 1942 server and our Teamspeak server. I didn't want to have to go out and buy a good router, or even a cheap one for that matter. I have had 2 routers now, the first is still working ok, but has some problems with port forwarding, and it is essential that i get the best port-forwarding i can get. That is why I would like to just setup the server to do it's own port forwarding, im hoping that the process will be simpler, and that it will speed up the network connections a bit. Now, also on the plus side....... It will also just sound cool when I can tell my buddies that I am running linux for my server and my router.

I have also been playing around with another linux called OpenWrt, if you guys have heard of it. It actually installs on router itself, which is really neat. Problem is, is that it's a &$*# to get it to work. And if you mess up, then good-bye router.

---

### Post by _newbie on 2007-06-15
why don t you try [http://www.freesco.org/?](http://www.freesco.org/?) I used it once and it should do the work for you... It s small.. It s easy to install... it s a router... and it is Linux :-) On the other hand... it is not really challenging to set it up:p 

...just realised it has very limited wifi support. should have read the original post more carefully...

---

