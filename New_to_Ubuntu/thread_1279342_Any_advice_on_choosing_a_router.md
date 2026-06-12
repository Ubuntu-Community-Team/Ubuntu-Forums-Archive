---
title: "Any advice on choosing a router"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by Nemo0075 on 2009-09-30
Hello all,

  I am in the market for a router, for the first time ever.  I am already overwhelmed by the mountain of choice and specs but what I worry about most is will it play nice with Ubuntu.  I am running 9.04 64 bit.  I plan on buying a wireless router either gigabit or extreme n, however I plan on using it for a wired network, at least for a while.  I will be using it to stream media to a PS3.  I have been told by some friends of mine that D-Link gear is the way to go these days but they all run Windows and I have come to learn it's best to be cautious when buying gear for a Linux box. Thanks for your help.

---

### Post by pawhtiobo on 2009-09-30
Hi :)
 
How much do you think spending in the router? for diferent prices, we got lots of choices...i already used lots of diferents routers attached to my PC and never had a single problem...usually it's fastest using linux than windows...
 
see ya...

---

### Post by starcannon on 2009-09-30
Linksys/Cisco
[http://www.google.com/products/catalog?hl=en&source=hp&q=linksys+gigabit+router&um=1&ie=UTF-8&cid=3925938517796816475&ei=ZtLDSt2fIYHitgOF2pC2Cg&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers](http://www.google.com/products/catalog?hl=en&source=hp&q=linksys+gigabit+router&um=1&ie=UTF-8&cid=3925938517796816475&ei=ZtLDSt2fIYHitgOF2pC2Cg&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers)
Thats the way to fly if your gonna buy an appliance.

Setup guide for the WRT310N in an Ubuntu network:
[http://ubuntuforums.org/showthread.php?t=990817](http://ubuntuforums.org/showthread.php?t=990817)

Or.... you could make one out of an old laptop/server/desktop computer. Buy a couple different Network interface cards to put in, and a Linux friendly WiFi card with the specs you want; and spend a weekend geeking out. :) Prolly best to just by a Linksys/Cisco :D

---

### Post by Nemo0075 on 2009-09-30
> **pawhtiobo said:**
> Hi :)
 
How much do you think spending in the router? for diferent prices, we got lots of choices...i already used lots of diferents routers atached to my PC and never had a single problem...usually it's fastest using linux than windows...
 
see ya...

I have no problem spending $100-$200 if warranted.  So if I get what you are saying is any router should/could do.  I see many threads about "my wireless isn't working," but that likely has more to do with network card rather than the router?

Thanks for the quick replies!

---

### Post by pawhtiobo on 2009-09-30
> **starcannon said:**
> Linksys/Cisco
[http://www.google.com/products/catalog?hl=en&source=hp&q=linksys+gigabit+router&um=1&ie=UTF-8&cid=3925938517796816475&ei=ZtLDSt2fIYHitgOF2pC2Cg&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers](http://www.google.com/products/catalog?hl=en&source=hp&q=linksys+gigabit+router&um=1&ie=UTF-8&cid=3925938517796816475&ei=ZtLDSt2fIYHitgOF2pC2Cg&sa=X&oi=product_catalog_result&ct=result&resnum=2#ps-sellers)
Thats the way to fly if your gonna buy an appliance.
 
Or.... you could make one out of an old laptop/server/desktop computer. Buy a couple different Network interface cards to put in, and a Linux friendly WiFi card with the specs you want; and spend a weekend geeking out. :) Prolly best to just by a Linksys/Cisco :D
 
Thats also a good choice :D
 
If you want to do a little tweaking you can use the DD-WRT linux based firmware and unlock all you router possibilities ;). I own an old Asus WL500g Premium with the DD-WRT firmware and it rock's in both OS's...
 
see ya...

---

### Post by pawhtiobo on 2009-09-30
Hi :)
 
Yes, usually are the wireless cards that messup the things, just one advise, prefer altheros or Cisco chipsets, the Intel and Broadcom chipets are not so good as the first ones...but this is just an opinion ;).
 
see ya...

---

### Post by RedRat on 2009-09-30
I am inclined to go with the Cisco/Linksys routers. I just had to replace my old Linksys (it was 5 years old and crapped out) and the new one works fine.

---

### Post by Sir Jasper on 2009-09-30
Hi,

My only thought is; are wired routers more secure than wireless ones?

My regards

---

### Post by nhasian on 2009-09-30
yes.  if you dont have any wifi devices, then dont enable the wifi radio in the router.  If you will be using wifi then make sure you are using WPA/WPA2 with AES encryption.  Do not use TKIP encryption as it has been circumvented.

> **Sir Jasper said:**
> My only thought is; are wired routers more secure than wireless ones?

---

### Post by Mark Phelps on 2009-10-01
I've used several different brands of routers, wired and wireless, and have found that the CISCO/Linksys tended to work the best.

Since they generally provide a web interface for setup and configuration, it really doesn't matter what OSs you're running on the networked machines.

As to security, wired is generally more secure than wireless simply because a physical connection is needed to access the network (in most cases).

Although opinions vary, I've found through personal experience that setting up wireless security to use both WEP/WPA of some form AND Mac Address filtering provides security that is very hard to crack -- pretty good protection against neighborhood attempts to access your broadband connection.

---

### Post by starcannon on 2009-10-01
> **Sir Jasper said:**
> Hi,

My only thought is; are wired routers more secure than wireless ones?

My regards

Wireless networks are always going to be less secure than wired networks. It's the nature of the beast; its a bit like comparing if one's car is more likely to get in a crash while driving during rush hour, or while sitting in one's garage.

---

### Post by doas777 on 2009-10-01
I avoid linksys. I do like Cisco, but they are a touch expensive, and you don;t really get your money;s worth with home routing.

i use a combo of Cisco, Trendnet, Netgear, and DLink for my network.

my advice is figure out what you need, and what you have (both in terms of existing equipment/cabling and monetarilly), then hop on newegg or wherever and start comparing models. then pick one.

---

### Post by sammcj on 2009-10-01
Make your own!

Get an old computer (600-1200MHz) and put two cheap network cards in it.

Install PfSense[ http://pfsense.org/]("http://pfsense.org/")

It's a very simple install process, it boots from the liveCD the first time and you simply choose 'install to hard drive'.

I've been using PfSense for years and have found it very stable and I installed squid (which was literally three tick boxes to install and setup) to cache my internet traffic.

-Make's it very easy to forward ports etc...
-More stable / reliable than a small embedded router (they're small CPU's can't handle as many IO transactions and have a tendency to over-heat in time / need reboots).

---

### Post by doas777 on 2009-10-01
+1 for pfsense

---

### Post by mikehenson on 2009-10-01
I have found that a $50.00 linksys router with DD-WRT = $300.00 router. I have installed DD-WRT on a linksys router and have been very pleased.

[http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php)

Router: linksys WRT54G V2.2 

MSH

---

### Post by lordyosch on 2009-10-01
I'd say netgear. Mine is a rangemax, just plug in and go. Web based interface, talks to ubuntu, wxp, wii, Android phones, pinnacle showcenter.

Jay

---

### Post by LewRockwell on 2009-10-01
as part of your research, understanding these will provide addtional insight:


[http://en.wikipedia.org/wiki/DD-WRT](http://en.wikipedia.org/wiki/DD-WRT)

[http://www.dd-wrt.com/dd-wrtv3/index.php](http://www.dd-wrt.com/dd-wrtv3/index.php)

[http://en.wikipedia.org/wiki/OpenWrt](http://en.wikipedia.org/wiki/OpenWrt)

[http://openwrt.org/](http://openwrt.org/)

[http://en.wikipedia.org/wiki/Tomato_firmware](http://en.wikipedia.org/wiki/Tomato_firmware)

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

[http://en.wikipedia.org/wiki/Wireless_router](http://en.wikipedia.org/wiki/Wireless_router)

[http://en.wikipedia.org/wiki/WRT54G](http://en.wikipedia.org/wiki/WRT54G)

[http://en.wikipedia.org/wiki/WRT54G#Third-party_firmware_projects](http://en.wikipedia.org/wiki/WRT54G#Third-party_firmware_projects)

[http://www.pcmag.com/article2/0,2817,2320101,00.asp](http://www.pcmag.com/article2/0,2817,2320101,00.asp)

[http://www.freeantennas.com/projects/template/index.html](http://www.freeantennas.com/projects/template/index.html)

[http://www.wi-fiplanet.com/tutorials/article.php/3841896](http://www.wi-fiplanet.com/tutorials/article.php/3841896)

.

---

### Post by starcannon on 2009-10-01
> **doas777 said:**
> I avoid linksys. I do like Cisco, but they are a touch expensive, and you don;t really get your money;s worth with home routing.

i use a combo of Cisco, Trendnet, Netgear, and DLink for my network.

my advice is figure out what you need, and what you have (both in terms of existing equipment/cabling and monetarilly), then hop on newegg or wherever and start comparing models. then pick one.
Cisco makes Linksys, so please don't take this as a flame/challenge, but I am a bit curious why one would choose Cisco, but avoid Linksys. I currently take care of a few small office networks, and a couple of them run old Cisco PIX 501's connected to Linksys 48port Switches, they are rock solid. I myself run an old Linksys B/G router, indeed it replaced my old Linksys B router simply because I wanted G, I've never worn one out, I just replace when they go obsolete; I'm looking at going for an N router soon myself.

Anyway, just curious, feel free to pm it to me so as not to hijack this thread to much.

GL and HF

---

### Post by doas777 on 2009-10-01
> **starcannon said:**
> Cisco makes Linksys, so please don't take this as a flame/challenge, but I am a bit curious why one would choose Cisco, but avoid Linksys. I currently take care of a few small office networks, and a couple of them run old Cisco PX 501's connected to Linksys 48port Switches, they are rock solid. I myself run an old Linksys BG router, indeed it replaced my old Linksys B router simply because I wanted G, I've never worn one out, I just replace when they go obsolete; I'm looking at going for an N router soon myself.

Anyway, just curious, feel free to pm it to me so as not to hijack this thread to much.

GL and HF

<preamble>this is likely constructive so I'll leave it in the channel.</preamble>

well, to be honest, i've just seen too many of them fail before their time. Cisco's tend to  either be DOA or to work for years, but it sometimes feels like the blue linksys's faint from a stiff breeze. 

I came to this opinion prior to the cisco purchase, and that may have changed at some point, but I have been led to believe that Cisco;s involvement with linksys is just print on a sticker, when it comes to the manufacturing/development. 

that and for a long time, all you needed to do to learn how to infiltrate most of them was google "hack linksys wireless router". they use some unsafe defaults for ease of use (UPNP for instance) and i guess i just feel like they contribute to non-techs using stupid configurations. the vast majority of open home wifi networks I come across are called simply "linksys".

so thats just my two bits. may be write, wrong, or in the middle.

good discussion. cheers,
Franklin

---

### Post by Nemo0075 on 2009-10-01
Thanks for all the great idea's.  The make one out of an old PC idea sounds like a fun project but not possible at the moment.  My only goal in all of this is to run a network cable to a PS3 (will own one soon) to be able to share media files.  The whole wireless part is irrelevant to me ( I know PS3 has wireless built in) at the moment but could prove useful in the future.  I found a highly rated Cisco/Linksys router that is interesting:

[http://www.ncix.com/products/index.php?sku=17408&vpn=WRT54GL&manufacture=Linksys&promoid=1081](http://www.ncix.com/products/index.php?sku=17408&vpn=WRT54GL&manufacture=Linksys&promoid=1081)

but I am leaning more towards the Linksys WRT310N only because it is N rather then G.  

Will do some more reading and searching.

---

### Post by NinjaNumberNine on 2009-10-01
I got [this one]("http://www.amazon.com/gp/product/B000BTL0OA/ref=olp_product_details?ie=UTF8&me=&seller="), works totally flawless, plug-n-play. Linksys is great brand!

---

### Post by Garyhans on 2009-10-01
I am linksys all the way. Easy to configure..  works like  charm.

---

### Post by starcannon on 2009-10-01
> **doas777 said:**
> <preamble>this is likely constructive so I'll leave it in the channel.</preamble>

well, to be honest, i've just seen too many of them fail before their time. Cisco's tend to  either be DOA or to work for years, but it sometimes feels like the blue linksys's faint from a stiff breeze. 

I came to this opinion prior to the cisco purchase, and that may have changed at some point, but I have been led to believe that Cisco;s involvement with linksys is just print on a sticker, when it comes to the manufacturing/development. 

that and for a long time, all you needed to do to learn how to infiltrate most of them was google "hack linksys wireless router". they use some unsafe defaults for ease of use (UPNP for instance) and i guess i just feel like they contribute to non-techs using stupid configurations. the vast majority of open home wifi networks I come across are called simply "linksys".

so thats just my two bits. may be write, wrong, or in the middle.

good discussion. cheers,
Franklin

Yeah, I hear ya. I go through my router and set it all up, but your right, I see many routers in my neighborhood that have default router name, presumably default password to the admin gui; and a wack of them with unsecured wifi. That said, the same can be true of any of the consumer grade routers, they all have an outta the box default setting, and they are all vulnerable for the same reasons if one does not take time to set the equipment up. The longevity issue you spoke of, I've just not had that problem, I even put one is a pretty rough environment, the drop ceiling of a greasy kitchen, where it is hot, and greasy up there(don't ask why, it was considered necessary so I did it), it was upgraded, but it never died; when I took it down for the client, it was covered in a film of grease (presumably from the deep fryer), and still worked great, though looked rough, the heat and grease had made all the stickers lift and curl up lol.

Anyway, it may be time to give Linksys another consideration; the deal with tech that I try to remember is never to become loyal to a brand. What is awesome today can suck tomorrow, and what sucks today can be awesome tomorrow. I think ATi and Nvidia are great other tech examples of that rule, I used to use nothing but ATi, now I use nothing but Nvidia, and I'd switch again tomorrow in a heartbeat if I felt it would benefit me.

Your running good gear, I have and will again run all the brands you listed, just was curious about your opinion about linksys was all.

GL and HF

---

### Post by erilidon on 2009-10-01
Linksys!

---

### Post by lyndaj70 on 2009-10-01
My favourite router is Netgear.  It is easy to set up and not too expensive.  If you have a Mac or Windows box around, you can go with an Apple router.  Those are actually my personal favorite as far as installation ease go, but I don't know anything about attempting to set them up in Linux - they are a breeze if you have a mac or windoze box around tho.

D-Link routers never like me, I guess I hold my mouth wrong :confused:

The rest are okay.  Last linksys router I had went belly up in less than a year, same with my boyfriend's.  We bought them together so it may have been a bad lot tho.  Instead of griping we just bought new ones cause we're hard on them lol!

Wired routers are more secure, but if you want to increase security on a wireless you can not only encrypt but filter by MAC address. That won't prevent a determined hacker, but it helps.

Peace!

---

### Post by anewguy on 2009-10-01
Just my 2 cents worth - I've used many routers over the years, Netgear, Linksys, etc., etc..  I only had problems with 1, and it was a USED router that was supposed to have been new when I purchased it from a well known retailer.  That was my only problem.

Be sure to get "enough" - you may not have need for wireless right now, but basically all of the cheap routers you will find at most major retailers are wireless with 4 or so wired ports as well.  As mentioned elsewhere, just turn off the router radio in the router setup.  Also, be sure to get a router that supports a wide variety of WEP and WPA/WPA2 security.  I have had problems in the past getting WPA2/AES working on a given router with Linux, so just be sure it has a variety of options (WPA,WPA2,64 bit and 128 bit encryption, TKIP, AES, etc.).

Just my 2 cents worth.  A router to support these is relatively cheap - sometimes on sale at various retailers in the $30 range, usual prices in the $40-$60 range.  Usually you can get them cheaper on Ebay, but you need to know exactly what the model for sale supports.


Dave :)

---

### Post by LewRockwell on 2009-10-02
for present and future discussion and reference:

[http://www.wi-fiplanet.com/tutorials/article.php/3841896](http://www.wi-fiplanet.com/tutorials/article.php/3841896)

.

---

### Post by pricetech on 2009-10-02
Nobody was ever fired for buying Cisco.

Linksys is OK, but I've never been that fond of them personally.

I've never met a d link that was more than an expensive paperweight.

Trend makes some pretty good stuff at a very affordable price, but I"ve never used any of their routers, so I can't say how good they are.

Netgear made good stuff, and I guess they still do, but I swore off them because of rampant stupidity in non technical areas of their business.

The "old computer" option is probably best left as a long term project for when you've learned enough to do it right.

Just one man's opinions.

---

### Post by Nemo0075 on 2009-10-09
After reading and researching for an eternity I finally bought a Linksys WRT310N.  For a week I was on the fence between the WRT310N and the D-Link DIR655.  I chose the Linksys for a few reasons, mostly non technical.  The Cisco name means something to me because I worked for a manufacturer that used to build Cisco commercial hardware.  The quality was quite good, however I undestand that might not be the case for end user products.  I like the fact that if I feel the need to play with third party firmware, I can, however, I doubt I will ever feel inclined to.  One of the main reasons was I find the Linksys looks much better and this piece of hardware will be out in plain view.  Lastly it was $30 off this week at the local big box store.  I plan on testing it out this weekend.  Thanks for all the help and recommendations:P

---

### Post by LewRockwell on 2009-10-09
> **Nemo0075 said:**
> After reading and researching for an eternity I finally bought a Linksys WRT310N.  For a week I was on the fence between the WRT310N and the D-Link DIR655.  I chose the Linksys for a few reasons, mostly non technical.  The Cisco name means something to me because I worked for a manufacturer that used to build Cisco commercial hardware.  The quality was quite good, however I undestand that might not be the case for end user products.  I like the fact that if I feel the need to play with third party firmware, I can, however, I doubt I will ever feel inclined to.  One of the main reasons was I find the Linksys looks much better and this piece of hardware will be out in plain view.  Lastly it was $30 off this week at the local big box store.  I plan on testing it out this weekend.  Thanks for all the help and recommendations:P

keep us posted on your progress

you might bookmark this for future reference:

[http://www.dd-wrt.com/phpBB2/viewtopic.php?p=201608&sid=5c7c3270ce359011c9649e3c66b2d979](http://www.dd-wrt.com/phpBB2/viewtopic.php?p=201608&sid=5c7c3270ce359011c9649e3c66b2d979)

.

---

### Post by RedRat on 2009-10-09
> **Nemo0075 said:**
> After reading and researching for an eternity I finally bought a Linksys WRT310N.  For a week I was on the fence between the WRT310N and the D-Link DIR655.  I chose the Linksys for a few reasons, mostly non technical.  The Cisco name means something to me because I worked for a manufacturer that used to build Cisco commercial hardware.  The quality was quite good, however I undestand that might not be the case for end user products.  I like the fact that if I feel the need to play with third party firmware, I can, however, I doubt I will ever feel inclined to.  One of the main reasons was I find the Linksys looks much better and this piece of hardware will be out in plain view.  Lastly it was $30 off this week at the local big box store.  I plan on testing it out this weekend.  Thanks for all the help and recommendations:P

Yes I think a good choice, Linksys/Cisco are reputable companies. Particularly keep us informed about how it plays with Ubuntu. I am toying with the idea of moving up to an n-router over my current g-router.

---

### Post by erilidon on 2009-10-10
> **Nemo0075 said:**
> After reading and researching for an eternity I finally bought a Linksys WRT310N.  For a week I was on the fence between the WRT310N and the D-Link DIR655.  I chose the Linksys for a few reasons, mostly non technical.  The Cisco name means something to me because I worked for a manufacturer that used to build Cisco commercial hardware.  The quality was quite good, however I undestand that might not be the case for end user products.  I like the fact that if I feel the need to play with third party firmware, I can, however, I doubt I will ever feel inclined to.  One of the main reasons was I find the Linksys looks much better and this piece of hardware will be out in plain view.  Lastly it was $30 off this week at the local big box store.  I plan on testing it out this weekend.  Thanks for all the help and recommendations:P

You can never go wrong with a Linksys. But I notice that this is still a 802.11n draft router. Is wireless N ever going to become a standard, that is get out of being draft.

---

### Post by RedRat on 2009-10-10
> **erilidon said:**
> You can never go wrong with a Linksys. But I notice that this is still a 802.11n draft router. Is wireless N ever going to become a standard, that is get out of being draft.

I think, or thought, that it is supposed to be finalized in 2009 or 2010. But as long as he stays with Linksys/Cisco routers and cards for the computer, he should be ok for awhile even if changes are made to the final standard. Perhaps others here might have experience with say Linksys playing with D-link cards/routers. Do they have compatibility problems??

---

