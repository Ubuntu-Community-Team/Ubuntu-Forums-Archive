---
title: "Broadcom BCM4309 wireless still not working"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by Ozor Mox on 2007-03-12
Hi, I've been on Ubuntu for about a week now and other than my wireless card's complete refusal to work I have been very happy with my new operating system. Unfortunately, unless I can get it to work, I'm probably going to have to switch back to Windows as my laptop loses quite a bit of its usefulness when wireless is not working.

My thread in the beginners forum has died out so now I call upon the Ubuntu wireless gurus to save me from having to defect back to the dark side!

So here's what I've tried so far. I have blacklisted the default Broadcom driver, as with that I had an entry for "wireless network" in the networking interface but could do nothing with it. I could enter an SSID, WEP and so on, but it would not activate. So next is ndiswrapper. I found my BCM4309 chipset on the ndiswrapper page under three different wireless cards, and eventually worked out that I need the bcmlw5a.inf file along with the bcmlw5.sys file (I think that's correct) after extracting numerous different EXE files and updating ndiswrapper-utils. At this point I have ndiswrapper telling me my hardware and driver are both correct and active, and now wireless network again appears in the networking interface but...that's it! No ability to enable or use the network, the same as with the native driver!

What am I missing? Do I just need the final step or is this completely not going to work?

---

