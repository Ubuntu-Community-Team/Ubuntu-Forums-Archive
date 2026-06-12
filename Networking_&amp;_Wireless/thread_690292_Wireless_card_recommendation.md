---
title: "Wireless card recommendation?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by freebeer on 2008-02-07
Hi guys!

I'm hoping that I can get a recommendation as to which wireless card (or family) that I should be buying.  I have checked the compatibility list and it's rather daunting (and sometimes conflicting) source.  Also my situation may be a little different than the norm.

Scenario:  I want to build an Ubuntu (probably 7.10 or perhaps 8.04 if it's released) box for my 73 year old father.  He'll use it primarily for email and web browsing.  (Mostly web browsing.)  It really doesn't make much sense for him to subscribe to his own internet account for the amount of use he'd get out of it.  I live next door to him and so I thought I'd allow him wireless access through my router.

The challenge:

1) Find a wireless card that is relatively easy to set up and maintain - "works out-of-the-box" would be ideal for me as I've never set up wireless on a linux box before and I'd much prefer a minimal amount of tweaking or future maintenance.  This is not a "must" requirement.  If there's a good card out there that can be tweaked further for better reception, I'm willing to go that route, too.

2) The wireless card/router combo needs to be able to connect reasonably well over a line-of-site distance of approximately 150 meters/yards.  I'm willing to change routers if need be to get better range.  (Footnote: I ran a test on the weekend on a Dell XP lappy with a broadcom chipset wireless (built-in) adapter.  I was able to connect, but not reliably (very weak signal).  I did not place the router in an optimal position for this test - I wanted to see if I could get a signal from its present (and preferred) location.) My current router is a D-Link WBR-1310 if that helps any.

Any recommendations or insights would be appreciated.  I've done some googling and have taken note of certain products that claim wider reception, but they fail to quantify that claim in any material way.

Thanks!

---

### Post by sbazin on 2008-02-07
Either the D-link WDA-1330 or WDA-2320 PCI cards should work with an Ubuntu install.  I've not tried one myself but I've spoken to people who have gotten them up an running out of the box.  Both these should work very well with your router.  Also if reception is a problem you could look into the the D-Link WBR-2310 router as it has better range than the 1310.  Everyone's situation can be different but if you buy any of these products from a retail store (such as FutureShop) you can easily return them if they don't work.

---

### Post by freebeer on 2008-02-07
Thanks.  I'll look into those specifically.  I'm not necessarily tied in with any particular manufacturer, although I've had satisfactory results with the D-Link products.

I'm still open to any other recommendations or observations should anyone else care to jump in.  :D

---

### Post by rustybronco on 2008-02-07
Jumping in...
150 meters is a long way for a normal wireless card, is a directional antenna/cantenna (preferably a gain antenna) a possibility for the router/wireless card? (just food for thought)

---

### Post by freebeer on 2008-02-07
It's a possibility.  I looked into that a bit (some time ago) and I haven't entirely ruled it out but I've noticed that there are other possibilities, too... like cards with better/longer range (perhaps in tandem with an equivalent router) or simply(?) an improved antennae.  The options are numerous, but trying to figure out which will actually work (or has the greatest chance of working) is difficult to track with any degree of certainty.  

Thanks for your suggestion!

---

### Post by rustybronco on 2008-02-07
[http://ubuntuhcl.org/pub/manufacturers.php?category_id=32](http://ubuntuhcl.org/pub/manufacturers.php?category_id=32)
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
I use a linksys wpc54gr "rangebooster" [http://ubuntuhcl.org/pub/reviews.php?product_id=503](http://ubuntuhcl.org/pub/reviews.php?product_id=503) with wpa1 but you would need the "rangebooster" router to be effective.
wpc54gr [http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1138744085400](http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&pagename=Linksys%2FCommon%2FVisitorWrapper&cid=1138744085400)
> RangeBooster technology is a compatible add-on to standard Wireless-G which increases your wireless network's range up to two times, and its throughput by up to 35%. and it's working well with hardy alpha 4

---

### Post by dca on 2008-02-07
You know, unless there's out of the box support for a particular WiFi card, you're gonna' have to get your hands dirty.  Some provide the this but not the firmware, some work out of the box needing nothing more than config in nm-applet, some require windows driver & ndiswrapper utility, and some you try all the above and the da*n thing still doesn't work.  
 
As far as PCI cards for PC(s), I've only gotten lucky w/ Atheros chipsets and Linux distro(s) that include latest vers of MadWifi.  
 
As far as laptops, those that had Intel Pro Wireless 2xxx-series worked out of the box because of integration in the kernel or Intel-supplied firmware or drivers that installed on the fly.  Forget about the 3945-series, from what people are telling me it's kind of flaky.  
 
Not to mention, I was never much for hacks that allow a WiFi card to quasi-work but not xmit at correct speeds or the whole dropping the signal after every twenty minutes of use requiring a reboot or banging your head against the screen.
 
Well, that's my rant.  You can look here:  [http://ubuntuhcl.org](http://ubuntuhcl.org)

---

### Post by freebeer on 2008-02-07
Thanks for the links and input, folks.  It's appreciated.  I was thinking that I'd probably have to use a "boosting" card, plus "boosting" router.  I'll probably try a boosting card first (I'd have to get a wifi card anyways) and then step up to the router if it's needed. 

BTW, is reception/transmission affected by other wireless devices such as phones?  I'm assuming the phones and wifi cards would have to be in the same band, but I really don't know.

---

### Post by rustybronco on 2008-02-08
> **freebeer said:**
> 
BTW, is reception/transmission affected by other wireless devices such as phones?  I'm assuming the phones and wifi cards would have to be in the same band, but I really don't know.yes they can be affected by cordless phones, microwaves (iirc 2.450 ghz ) or even arcing power lines (generates a wide band of frequencies), anything that generates a frequency in the 2.4 ghz range.

---

