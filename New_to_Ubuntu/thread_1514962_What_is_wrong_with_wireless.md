---
title: "What is wrong with wireless?"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by Superdarion on 2010-06-21
I think many people have thought about this and maybe even posted, but I couldn't find posts asking this general question:

What is wrong with wireless in ubuntu (or maybe linux as a whole)?

I mean seriously, in the last 3 years or so the only problem that my friends and family keep asking me about is wireless when it comes to ubuntu. It is ALWAYS wireless.

Sometimes it works here but not there, works for open wireless but not protected or just plain doesn't work at all.

I had never encountered this problem personally because I use wired networks at my computers, so up to now it had always been friends' computers talking over the phone, which is far from ideal. This time, though, I'm trying to set up this dell computer and it just won't let me! After a few fresh installs and a 2-day period during which it worked flawlessly, it just doesn't want to work anymore! The things that worked the last fresh install -2 days ago- won't work anymore. Nothing works.

This is not me asking for a solution for my particular problem. I'm doing that on my own as I type. I just want to know what the hell is the problem with wireless. Why is there ALWAYS trouble with wireless cards? Is it the vendors? Is it ubuntu? Is it just me having bad luck?!

---

### Post by lolzwut on 2010-06-21
because a lot of times the drivers aren't built for *nix

---

### Post by ankspo71 on 2010-06-21
> **Superdarion said:**
>  I'm trying to set up this dell computer and it just won't let me! After a few fresh installs and a 2-day period during which it worked flawlessly, it just doesn't want to work anymore! The things that worked the last fresh install -2 days ago- won't work anymore. Nothing works.

Hi, my wireless connection seems to do this from time to time in *ubuntu too. I find it easier to delete the bad connection, reboot, then create a new connection using the exact same configurations, instead of fighting with the existing connection. That always seems to temporarily fix it for me, at least for another week or two. I have seen that if I disable my connection or don't perform a proper shutdown, it will stuff it up again. I have to leave mine as connected for best results.
Hope this helps.

---

### Post by sanderj on 2010-06-21
I heard 75% of the ISP helpdesk calls are ... Wifi related. So Wifi itself is a pain, and it's not OS related.

---

### Post by wesleybishop on 2010-06-21
I have found Ubuntu to be better than windows as far as wireless goes. I had so many problems with wireless in windows.

---

### Post by oldsoundguy on 2010-06-21
Most wireless issues are with laptops.

Most laptops have the cheapest chipsets available for the on board things such as sound/Wi-Fi and even  video display on some.  Increases the margin of profit.

MANY (too many) of those chipset makers rush out an order and then are constantly trying to upgrade them for windows to correct the garbage that was in them in the first place.  IF this is so for Windows, since very few of those  chipset makers co-operate with Linux in any way, the drivers for that crap have to be backwards re-engineered constantly for Linux.

You get what you pay for in a laptop.  If you expect a 600 buck laptop to function as well as a 3000 laptop, you are deluding yourself.

---

### Post by A_M_S on 2010-06-21
I'm fighting with random wireless disconnections  for 2 years. 

wireless technology is relatively new and its not so stable and Well integrated in Linux and Windows as ethernet.

I hope they can improve wireless integration in future OS releases.

And as has been said before the drivers also can be a problem.

---

### Post by walt.smith1960 on 2010-06-21
I think oldsoundguy is onto something. Cheapie integrated functions.  Integrated sound/WinModems, anyone?  Touch wood but I've had decent luck with WiFi.  Intel, Atheros and RealTek chipsets.  I have a TrendNet (realtek chip) USB adapter which has been plug & play since Ubuntu 8.10. I had to enable backports for the Atheros chipset for 9.04. You could either find a wireless adapter that works or plug into a wired connection and try enabling backports.  Some find that  enabling backports  cause as many problems as they cure so YMMV.    It seems N adapters are particularly troublesome.

---

### Post by ram2500 on 2010-06-21
I find that Broadcom chipsets work decent once activated through Hardware Drivers. In both my experiences, I have used two different laptops (my own laptop and my laptop issued by my work) with Ubuntu, and both had Broadcom chipsets. WiFi is still a new technology as it's only been around for about a decade. It wasn't until 2005-2006 when it became standard on laptops, so it's really a technology *less* than a decade old. Before, only the premium models had wireless features. Now, even the $198 Black Friday deals at Walmart carry wireless:p.

I must say that Ubuntu 9.04 did work with my wireless card (Broadcom) without ANY configuration. It worked out of the box. When I upgraded to 9.10 and again to 10.04, I had to download the drivers through the Hardware Drivers utility (no big deal). I suppose if you roll back a version or two, you might find that your card (oddly enough) works out of the box. If you get a newer version, a wireless driver for your particular card may not work probably because the driver for the card may be for a card a couple years old and may be taken out of the new version for space limitation reasons. I think that is likely the case in my situation. As with everything, a lot of hardware is being introduced to the market, and with the older hardware that becomes less common, newer drivers for devices must be included with Ubuntu so that newer hardware will work. As usual, there's still many items that will not work out of the box because of licensing restrictions or because they are not out-of-date.

---

### Post by Windows Nerd on 2010-06-21
Likely because there are _sooo_ many different chipsets out there, and many are not built with *nix in mind and do not release open-source drivers, Linux-specific drivers, or release their exact hardware specifications so that people can write good drivers for them; resulting in many developers and driver writers to have to reverse-engineer drivers, resulting in them not working as well or simply not functioning at all. 

And as whomever posted above there said, it is the use of cheap network and wireless card in laptops in the first place which are unreliable and also crappily made.

There is the same issue when it comes to making drivers for graphics cards: because of the sheer bulk of cards and some companies (*caugh* ATi)  Cnot releasing Linux drivers or hardware specifacations many people have problems with such catds

Scott

---

