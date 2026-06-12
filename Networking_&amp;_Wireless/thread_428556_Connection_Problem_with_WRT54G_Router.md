---
title: "Connection Problem with WRT54G Router"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by russw1 on 2007-04-30
Okay, I am new to Ubuntu/Linux and have installed Feisty.  I have been able to connect to unprotected wireless networks in the neighborhood, including one called "linksys".  However, I cannot connect to my Linksys WRT54G V5 wireless router (firmware 1.02.0) even with the security disabled.  I can see it listed in the  available networks.  I can ping it using network tools on eth1, but it will not connect wirelessly. ( A cabled connection to the router does work.)

My wireless card is an Intel 2100, but that does not seem to be an issue since it will connect to other wireless networks.  I have tried many of the solutions posted here without success; I now have a clean install of Feisty and need help.   Any suggestions?

---

### Post by hodad on 2007-04-30
I'm also in need of guidance on the WRT54G.  DId a little research on Linux compatibility before buying the Linksys WRT 54G wireless router, and expected I'd have difficulty, but couldn't see any other choce but to "plunge in".  Seems that the Linksys with Realtek chips turned up as a good choice according to some postings. 

I need this thing to communicate wirelessly with my laptop. I'm trying to set up the laptop so that I can use it in "wireless hotspots", so I figured I'd try it at home with the wireless router first before going on the road.

 Can anyone provide the steps necessary to load the drivers so that we (me and the previous poster) can get these wireless routers to work?   

Thanks!

---

### Post by bionnaki on 2007-04-30
first of all, the router itself is not the problem. router's are essentially compatible with any OS. the problem has to do with your wireless card and the driver associated with it. run a search in the forums and wiki for your card (be specific about the make/model and type of driver it uses). you'll find out how to configure the card to use WEP, WPA, etc. But again, this has nothing to do with the router.

---

### Post by takakia on 2007-05-01
Try Wireless Assistant (search the repos) instead of Network manager (or KNetwork manager (Kubuntu).  It worked for me whereas I had a hard time with Knetwork manager.  

Set your router using wired connection and use 

set a essid
channel Auto
wireless mode 54g
shared key
wep 128 bits
use a secret passphrase 
copy your wepkey (something like 43E0411B127B22B7617F350XXXX - you can even copy paste).

once everything is set, use Wireless Assistant to setup wireless connection. enter the right entries. I should work if your wifi card in laptop is configured and working properly.

---

### Post by Floppyjoe on 2007-05-02
> **russw1 said:**
> Okay, I am new to Ubuntu/Linux and have installed Feisty.  I have been able to connect to unprotected wireless networks in the neighborhood, including one called "linksys".  However, I cannot connect to my Linksys WRT54G V5 wireless router (firmware 1.02.0) even with the security disabled.  I can see it listed in the  available networks.  I can ping it using network tools on eth1, but it will not connect wirelessly. ( A cabled connection to the router does work.)

My wireless card is an Intel 2100, but that does not seem to be an issue since it will connect to other wireless networks.  I have tried many of the solutions posted here without success; I now have a clean install of Feisty and need help.   Any suggestions?

Have you tried to connect to your wireless router with another computer wirelessly with success?
Has the wireless functionality of the router worked in the past?
Is it a new router? Maybe not functioning properly?

---

### Post by russw1 on 2007-05-02
Thanks to everyone.  It is all working fine now.  The router has always worked with 
XP  as did my laptop.  I switched to Ubuntu from XP and the wireless failed to connect.  I finally replaced the Intel 2100 wireless card in the laptop with an Intel 2200 and all is well and working perfectly.  I may have just been unlucky and had the wireless card die at the exact time I made the switch.  With the new card, everything connected on the first try even with WPA!

---

