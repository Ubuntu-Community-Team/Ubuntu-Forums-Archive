---
title: "WUSB54G on Gutsy Gibbon"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by Erky on 2007-10-22
Hello,

I had my Linksys WUSB54G USB Wireless adapter working on my desktop while I was using Feisty Fawn (7.04). It took me awhile to get that working. Now that I upgraded to Gutsy Gibbon, it no longer works. Can anyone help me with my problem?

---

### Post by MariusSilverwolf on 2007-10-22
As posted here: [http://ubuntuforums.org/showthread.php?t=586017](http://ubuntuforums.org/showthread.php?t=586017)

First and foremost, Wieman1 and Zoinks, you guys wrote up some awesome tutorials for getting the Ralink drivers to work. You guys rock.

That fact nothwithstanding, here's what I've learned from following both Tutorials to the letter:

The LinksSys WUSB54Gv4 USB Wireless Network Adapter does NOT want to work in Gutsy with the AMD64 flavor. At all.

In Fiesty, the Serial Monkey rt2x00 Legacy drivers picked up the card, and as long as I dropped down to WEP instead of using WPA I could connect no problem. After the upgrade to Gutsy, I was caught in the endless loop of my Wireless network being detected, being prompted by Network Manager for the encryption password, sitting for 30 to 60 seconds, and repeating.

First, I ran through Wieman1's tutorial. Like a few others, when I Blacklist the rt2500usb driver in /etc/modprobe.d/blacklist, I see NO Wireless Network Adapters in Network Tools. I suspect this is because NDISWrapper is 32-bit, and I need to recompile it for AMD64 architecture. I tried following the NDISWrapper on AMD64 Tutorial, but there's no Debian folder within the latest package, and none of the files I need to alter to recompile exist anywhere on my system.

So, having to give up on NDISWrapper, I happened upon Zoinks tutorial and my hope was renewed. For a time. BUT, the only driver package from Serial Monkey that will bind to the card is the rt2x00 legacy version of rt2500usb. rt2500, rt2570, and rt73 all fail, no matter how many times I remove previous modules or how many alterations I make to aliases and interfaces.

So, until the rt2x00 legacy driver package can be fixed to actually let me connect to my wireless network -- which I've tried with WPA, WEP, and open without any luck -- I'm dead in the water. I may just pick up a reel of CAT5 and run a line under the house to connect from the router to the PC via hardline. For the drop on each end and the run in between I should only need about 100 feet of cable and 60 feet of pvc conduit.

Just thought I'd share my war story. If anybody else has found a way to get that confounded piece of hardware to actually connect to a wireless network and get past the router, I'd love to hear it. I'd rather not crawl around under a house in Florida when it's still 90 degrees with 70% humidity outside during the day.

---

### Post by Erky on 2007-10-23
bump. Please help! I am desperate at this point!

---

### Post by webbie180 on 2007-10-23
Try this,
[http://ubuntuforums.org/showthread.php?t=588045]("http://ubuntuforums.org/showthread.php?t=588045")

---

### Post by AlexMono94 on 2007-10-23
try my tutorial and see if that works. [http://www.ubuntuforums.org/showthread?=t588045&](http://www.ubuntuforums.org/showthread?=t588045&)

---

### Post by wieman01 on 2007-10-24
> **MariusSilverwolf said:**
> As posted here: [http://ubuntuforums.org/showthread.php?t=586017](http://ubuntuforums.org/showthread.php?t=586017)

First and foremost, Wieman1 and Zoinks, you guys wrote up some awesome tutorials for getting the Ralink drivers to work. You guys rock.

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

### Post by Erky on 2007-10-25
bump.

---

### Post by AlexMono94 on 2007-10-25
ive changed my tutorial, please try it again

---

### Post by Erky on 2007-10-28
bump.

---

### Post by wieman01 on 2007-10-29
> **Erky said:**
> bump.
A few users have offered solutions & tutorials in this thread. Why don't you try any of them and post if you need help... I don't see a reason why you should bump this up, help has been offered on a number of occasions. What is the issue?

---

### Post by dburnett77 on 2007-10-29
I'd try WiCD, from:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

It will uninstall Network Manager, and you can usually connect with wireless better.  I also like the fact you can use hidden ESSID with it, as I do.

---

### Post by Erky on 2007-11-04
Thank you everyone who tried to help, but I got it working on my own. I'm not really sure what I did to fix it, but it worked. Thanks again!

---

