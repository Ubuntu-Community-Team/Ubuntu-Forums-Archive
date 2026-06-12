---
title: "Wireless card / wifi adapter issues"
date: 2015-03-17
forum: Networking &amp; Wireless
---

### Post by Ontario999 on 2015-03-17
Hello everyone,

I'm totally new to Linux/Ubuntu so forgive me if these questions have been answered countless times before.  

I recently dual-booted my HP laptop with Ubuntu 14.04 LTS but my internet browsing speeds are super slow with Ubuntu.  I thought at first it might have been my router, so I bought a new one.  That didn't fix the problem so I bought a wifi adapter.  Guess what?  That didn't work either!

I'm not entirely too sure what to post here but I gather the following will be useful:

My built in wireless card (terminology?) is a REALTEK 8188EE.  

My wifi adapter (which I would prefer to use instead of the built in REALTEK one) is a D-Link DWA-171

Any ideas what might be causing the problem?

I have searched online to see if I can disable my built in wireless card and install drivers for the D-Link adapter but I have no idea how to use "terminal".  

Any help is GREATLY appreciated!

---

### Post by DarkSapphire on 2015-03-17
A simple non-terminal way, is to click on the launcher button in the top left corner in the dock.  Then search additional drivers.  After that simply wait for them to search for new drivers.  It will search the drivers for you.  If it doesn't find any, it will use proprietary drivers.  It appears those are what you are using right now.  Best of luck!

---

### Post by Ontario999 on 2015-03-17
Hi Dane917,

Thanks for replying!

I tried what you suggested and the only driver that appears on the list appears to be my graphics card.  

Beneath that, there is a section that says, "No proprietary drivers are in use".  I take it my wireless adapter and/or wireless card drivers should appear here?

---

### Post by Geoffrey_Arndt on 2015-03-18
For install of D-Link adapter:  [http://ubuntuforums.org/showthread.php?t=2168426](http://ubuntuforums.org/showthread.php?t=2168426)

---

### Post by Ontario999 on 2015-03-18
> **Geoffrey_Arndt said:**
> For install of D-Link adapter:  [http://ubuntuforums.org/showthread.php?t=2168426](http://ubuntuforums.org/showthread.php?t=2168426)

I noticed this the other day but I have no idea how to install it.  

Terms like "make clean" and "sudo" seem really daunting.  lol

---

### Post by Bucky Ball on 2015-03-18
*Thread moved to **Networking & Wireless**.*

Welcome. I like your chances better here. ;)

Same link, but see chili's advice [here]("http://ubuntuforums.org/showthread.php?t=2168426&p=12951821&viewfull=1#post12951821"). Just follow their instructions and post back if you have an issue.

---

### Post by Geoffrey_Arndt on 2015-03-19
There is a way to fix the wireless issues very simply (without any code, use of terminal commands, etc.).

And that is to get a 100% "compatible" usb-wireless adapter.   In other words, just plug it in and it will see (detect) all in area wireless networks.  (note:  cost about $10 usd).

The key thing here is to know up-front (before you buy) what brands/models fit that requirement?   One that works out of the box - - (tested on 1 desktop and 3 laptops) is:

[http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1426784194&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter+150mbps](http://www.amazon.com/Panda-Ultra-Wireless-Adapter-150Mbps/dp/B00762YNMG/ref=sr_1_1?s=pc&ie=UTF8&qid=1426784194&sr=1-1&keywords=panda+ultra+wireless+n+usb+adapter+150mbps)

---

