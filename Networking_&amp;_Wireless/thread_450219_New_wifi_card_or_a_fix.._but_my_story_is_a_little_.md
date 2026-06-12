---
title: "New wifi card or a fix?.. but my story is a little more interesting :)"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by showty on 2007-05-21
Hi.. I have two PCs, very different specifications (one is an older Athlon system, the other is a modern Pentium 4 system). The only thing they have in common is their wifi card, a WG311Tv2

They both run Ubuntu 7.04 Feisty (and have run 6.10 and 6.06 before). Both of them suffer slow and intermittent wifi dropouts, making the internet virtually unusable. Browsing is semi-acceptable, but updating is a pain as most packages fail due to losing connection with the server and online games drop out and are choppy. I can't stream video from my media pc (which runs Windows) either.

The unfortunate thing is that the WG311T is one of the most highly recommended wifi cards for Ubuntu. But unfortunately, for me, its the worst thing ever. I'm getting a slight upgrade soon, and in that upgrade I want to include a new wifi cards for my PCs so they can run Ubuntu properly.

These cards run fine in Windows, its just Ubuntu under the madwifi Atheros drivers.

Suggestions on how to fix the problem are appreciated, as well as alternative wifi cards I can consider purchasing. Haha, other than the WG311T :P

Thanks!

---

### Post by handaxe on 2007-05-21
Is this a new "Feisty" problem or was it there with previous versions of Ubuntu? You do not say...

HA

PS: of help (or further frustration ...)?

[https://bugs.launchpad.net/ubuntu/+s...ger/+bug/37821]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/37821")

---

### Post by Mike'sHardLinux on 2007-05-21
One of the problems with recommending a specific model # of hardware is that sometimes, the manufacturer will change the hardware configuration and continue to sell it as the same or similar model #.  People think they are getting the same product, when in fact they may be getting a totally different chip(set). The fact that yours is a "V2" makes me believe this is the case in your situation.

Can you type lspci at the commandline and tell us what controller is being reported? Be sure you are telling us the wireless and not the ethernet controller.

I also had bad luck with a WGT311 a few months ago, with Edgy, I think. I still have it somewhere.......

I am currently (in Feisty) using a cheapo Trend Micro card that has an Atheros AR5212 chip. I was having trouble using Network Manager, but since I removed it and installed wicd, I have been getting a solid connection for 2 days now.

edit: Handaxe, thanks for that link!! That was the issue I was having this weekend. Like I said, I removed network-manager and instead use wicd, and we'll see if it continues to be solid.....

---

### Post by handaxe on 2007-05-21
Glad it helped MHL.

For general info:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

You can always re-install NM if you will, so nothing lost...

Wicd has worked for many folks in dealing with issues apparent under NM.  That written, Wicd is not perfect and cannot help where there are fundamental problems between card/driver and "helper" progs like wpa_supplicant, iwlist etc.
Both Wicd and NM use wpa_supplicant so you will see the point.

HA

---

### Post by showty on 2007-06-03
Okay.. uninstalling network-manager helped, but it was still ultimately unusable.

Installing wicd didn't help either..

Please, can someone offer me another suggestion? I need help!

---

### Post by showty on 2007-06-03
Please help? I'm stuck in Windows until someone can help me out and get me back onto Ubuntu with working net..

Sorry for being annoying, but I really need this fixed :(

---

### Post by handaxe on 2007-06-04
@showty..

Did you read the bug report I linked above and did you follow (at least one) link to another bug report?

Some workarounds are suggested there, including uninstalling n-manager (Wicd will likely have the same issue as n-m for the same reasons...).

Beyond those ideas, there is no quick fix I fear.

Sorry,
HA

---

### Post by showty on 2007-06-07
Yeah, I uninstalled network-manager, tried it without having Wicd installed as well.

Would a different distro work? I love Ubuntu, but if it doesn't have net I'll have to settle for another one.. preferably one with madwifi-ng built in?

---

### Post by handaxe on 2007-06-07
Sometimes things work elsewhere...... pcs and laptops are a collection of different variables that can play together in strange ways.

People write good things about PCLinuxOS but they also do so about others.  If you have good broadband it cannot hurt to try a few.  Those with liveCDs of course give you the benefit of a quick trial.

I would Google madwifi-ng with the names of a few distros and read a bit....

HA

---

### Post by showty on 2007-06-08
> **handaxe said:**
> If you have good broadband it cannot hurt to try a few.
My ISP mirrors many distros quota free ;)

I can try Fedora Core, but that doesn't have madwifi-ng does it?

---

### Post by Sendervictorius on 2007-06-10
I have had problems with the slow madwifi driver on feisty. After trying all manner of remedies with marginal improvements, I eventually removed and blacklisted the madwifi drivers (rmmod) and installed ndiswrapper and the windows driver. It was magic:  the best network performance I've had.

---

