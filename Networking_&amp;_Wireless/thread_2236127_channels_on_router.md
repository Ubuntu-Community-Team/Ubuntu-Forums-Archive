---
title: "channels on router"
date: 2014-07-24
forum: Networking &amp; Wireless
---

### Post by AnotherKevin on 2014-07-24
I have a Belkin N-450 DB. We're having some intermittent poor connections on all devices. When viewing the network from Fing, I see channels 1-14, however when I go to the router's admin page, it only shows 1-11. Of those channels, 11 is the best (poor strength), 1 is next best (very poor strength) and 2 through 10 don't show a signal. These readings hold true on three separate device types (PCs, Android smart phones, Android Tablets). Channels 12,13 and 14 are MUCH better and they show as very strong and present when viewing the network via Fing, but they aren't present in the router's settings. 

Can any one help with this?  Belkins no help (they want to be paid to talk to tech spt).  Tom's Hardware is getting no replies...  You guys are my last hope!  :-)

---

### Post by TheFu on 2014-07-25
Ch 14 is illegal to use in the USA. I think it is only legal in Japan.

For 2.4Ghz, only ch 1, 6, 11 do not overlap.  Using other channels interferes with those 3 channels and should be avoided, unless you live in compressed housing and don't have a choice.  Use 5Ghz whenever possible, but that doesn't work well through any obstructions (walls) regardless of the material.

Wired ethernet is so much better than wifi.  If you can't switch to wired ethernet or even powerline ethernet, then the only solution may be to get a quality access point (AP) like Ubuquiti makes for $80.  Their stuff is amazing and blows away the consumer-level stuff.

BTW, I used to design wifi networks for a living ... I use wired ethernet whenever possible after learning about issues with wifi - even when it seems to be working fine, it is dropping packets and the bandwidth varies wildly. Wifi is a last resort tool.

---

### Post by AnotherKevin on 2014-08-02
> **TheFu said:**
> Ch 14 is illegal to use in the USA. I think it is only legal in Japan.

For 2.4Ghz, only ch 1, 6, 11 do not overlap.  Using other channels interferes with those 3 channels and should be avoided, unless you live in compressed housing and don't have a choice.  Use 5Ghz whenever possible, but that doesn't work well through any obstructions (walls) regardless of the material.

Wired ethernet is so much better than wifi.  If you can't switch to wired ethernet or even powerline ethernet, then the only solution may be to get a quality access point (AP) like Ubuquiti makes for $80.  Their stuff is amazing and blows away the consumer-level stuff.

BTW, I used to design wifi networks for a living ... I use wired ethernet whenever possible after learning about issues with wifi - even when it seems to be working fine, it is dropping packets and the bandwidth varies wildly. Wifi is a last resort tool.


Please pardon me for not catching your reply sooner.  Kind of get used to some questions never getting replies...

Yes, I posted this question to some other places (including Tom's Hardware, receiving no replies) and did some exhaustive searches and pretty much came to the conclusion you have here.  Ethernet is very convenient, but not too reliable.  I'll check out your recommendations.  

Thanks, TheFu, for your help.  It is VERY appreciated...

Kevin

---

### Post by AnotherKevin on 2014-08-02
Due to the info I obtained via private message, I now believe the answer to my problem with the Belkin router is to replace it with a non Belkin router...  They appear to have a lousy track record...

Thanks!

Kevin

---

### Post by TheFu on 2014-08-02
a) why not set your forum settings to email replies?

b) Ethernet is extremely reliable - WIFI is not.  Ubiquiti has been great in our deployments compared to cheap, home, wifi options.

c) The only cheap routers that I haven't had issue with are "buffalo" - I've been burned by ... netgear, linksys, belkin, cisco, tp-link, d-link, SMC ... that's enough I suppose.  When looking for a replacement router, always, always, always look for aftermarket-firmware compatibility (tomato, dd-wrt, openwrt, pfsense, ipcop, ...) and don't get bogged down in "specs". The tp-link router looked great on spec, but wouldn't stay up over 12 hrs at a time.  Tried non-stock firmware and it was jsut as bad.

While I'm here - any PM is for paid support, I my mind.

---

### Post by AnotherKevin on 2014-08-10
> **TheFu said:**
>   ...

...
While I'm here - any PM is for paid support, I my mind.


I do not pay for support, hence no help from Belkin.  However, when some one *IS* good enough to be paid for their expertise, I listen.

That being said, I merely thought it nice to post what I believe to be a satisfactory resolution to my issue for the benefit of others.  That resolution, in this case, is to replace my Belkin router.  I'll be doing that with YOUR advice in mind, also...

Again, thank you.

Kevin

---

