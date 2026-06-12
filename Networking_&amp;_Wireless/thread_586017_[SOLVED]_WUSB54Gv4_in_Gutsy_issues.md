---
title: "[SOLVED] WUSB54Gv4 in Gutsy issues"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by MariusSilverwolf on 2007-10-21
First and foremost, Wieman1 and Zoinks, you guys wrote up some awesome tutorials for getting the Ralink drivers to work.  You guys rock.

That fact nothwithstanding, here's what I've learned from following both Tutorials to the letter:

The LinksSys WUSB54Gv4 USB Wireless Network Adapter does NOT want to work in Gutsy with the AMD64 flavor.  At all.

In Fiesty, the Serial Monkey rt2x00 Legacy drivers picked up the card, and as long as I dropped down to WEP instead of using WPA I could connect no problem.  After the upgrade to Gutsy, I was caught in the endless loop of my Wireless network being detected, being prompted by Network Manager for the encryption password, sitting for 30 to 60 seconds, and repeating.

First, I ran through Wieman1's tutorial.  Like a few others, when I Blacklist the rt2500usb driver in /etc/modprobe.d/blacklist, I see NO Wireless Network Adapters in Network Tools.  I suspect this is because NDISWrapper is 32-bit, and I need to recompile it for AMD64 architecture.  I tried following the NDISWrapper on AMD64 Tutorial, but there's no Debian folder within the latest package, and none of the files I need to alter to recompile exist anywhere on my system.

So, having to give up on NDISWrapper, I happened upon Zoinks tutorial and my hope was renewed.  For a time.  BUT, the only driver package from Serial Monkey that will bind to the card is the rt2x00 legacy version of rt2500usb.  rt2500, rt2570, and rt73 all fail, no matter how many times I remove previous modules or how many alterations I make to aliases and interfaces.

So, until the rt2x00 legacy driver package can be fixed to actually let me connect to my wireless network -- which I've tried with WPA, WEP, and open without any luck -- I'm dead in the water.  I may just pick up a reel of CAT5 and run a line under the house to connect from the router to the PC via hardline.  For the drop on each end and the run in between I should only need about 100 feet of cable and 60 feet of pvc conduit.

Just thought I'd share my war story.  If anybody else has found a way to get that confounded piece of hardware to actually connect to a wireless network and get past the router, I'd love to hear it.  I'd rather not crawl around under a house in Florida when it's still 90 degrees with 70% humidity outside during the day.

---

### Post by wieman01 on 2007-10-24
> **MariusSilverwolf said:**
> First and foremost, Wieman1 and Zoinks, you guys wrote up some awesome tutorials for getting the Ralink drivers to work. You guys rock.

That fact nothwithstanding, here's what I've learned from following both Tutorials to the letter:

The LinksSys WUSB54Gv4 USB Wireless Network Adapter does NOT want to work in Gutsy with the AMD64 flavor. At all.

In Fiesty, the Serial Monkey rt2x00 Legacy drivers picked up the card, and as long as I dropped down to WEP instead of using WPA I could connect no problem. After the upgrade to Gutsy, I was caught in the endless loop of my Wireless network being detected, being prompted by Network Manager for the encryption password, sitting for 30 to 60 seconds, and repeating.

First, I ran through Wieman1's tutorial. Like a few others, when I Blacklist the rt2500usb driver in /etc/modprobe.d/blacklist, I see NO Wireless Network Adapters in Network Tools. I suspect this is because NDISWrapper is 32-bit, and I need to recompile it for AMD64 architecture. I tried following the NDISWrapper on AMD64 Tutorial, but there's no Debian folder within the latest package, and none of the files I need to alter to recompile exist anywhere on my system.

So, having to give up on NDISWrapper, I happened upon Zoinks tutorial and my hope was renewed. For a time. BUT, the only driver package from Serial Monkey that will bind to the card is the rt2x00 legacy version of rt2500usb. rt2500, rt2570, and rt73 all fail, no matter how many times I remove previous modules or how many alterations I make to aliases and interfaces.

So, until the rt2x00 legacy driver package can be fixed to actually let me connect to my wireless network -- which I've tried with WPA, WEP, and open without any luck -- I'm dead in the water. I may just pick up a reel of CAT5 and run a line under the house to connect from the router to the PC via hardline. For the drop on each end and the run in between I should only need about 100 feet of cable and 60 feet of pvc conduit.

Just thought I'd share my war story. If anybody else has found a way to get that confounded piece of hardware to actually connect to a wireless network and get past the router, I'd love to hear it. I'd rather not crawl around under a house in Florida when it's still 90 degrees with 70% humidity outside during the day.
Marius, 

Have you used the 64-bit Windows driver or the 32-bit version? We had a similar case 2 days ago and the guys would solve it on its own by using the 64-bit version. So it was not a matter of replacing "ndiswrapper" in fact. Mind trying once again?

---

