---
title: "Need help getting a WLAN NIC to work (or help chosing a new card that will work)"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by stromdal on 2008-04-25
I am a newbie at Linux and I am having problems getting my wireless NIC to work on a desktop PC (Ubuntu 7.10, I&#8217;ll soon upgrade to the newly released 8.04).

I have a D-Link DIR-615 wired/wireless router that I use as a private network gateway. At the moment, my WinXP desktop PC and WinXP laptop PC both connect to this router by WLAN (with WPA-PSK) while the Linux desktop PC connects by wire. I would, for several reasons, like to physically move this router to the WinXP desktop PC location. This would mean that the WinXP desktop would connect by cable and the Linux desktop would connect by WLAN &#8211; I&#8217;ll simply transfer the WLAN NIC to the Linux PC. 

The card that is currently installed in my WinXP desktop box is a D-Link DWL-G520M PCI card that, according to this list ([https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)), is not known to work in Linux. 

So my question is this: what network card should I buy that will let me get wireless NW on my Linux desktop PC with minimum fuzz? I would like to buy one as cheap as possible but I do want some kind of WPA. The card would have to work (with WPA) with my DIR-615 router, but after checking all D-Link products I cannot find one suitable. Would a Belkin, Linksys or Netgear card work? I&#8217;d like to buy an USB card for the flexibility, but that&#8217;s not a requirement. 

I just want a card that will give me WPA-WLAN on Linux at a reasonable cost and with manageable fuzz.

Does anyone have a suggestion? 

With a clear step-by-step installation manual the &#8220;minimum fuzz&#8221; requirement is negotiable. I found this ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) installation manual for installing &#8220;any&#8221; wireless network card using ndiswrapper, but the instructions &#8220;[&#8230;] apply only when using the x86 Alternate CD [&#8230;] not to the Ubuntu Desktop CDs&#8221;. I think I installed the Desktop CD version of Ubuntu (it&#8217;s been almost a year since I installed) &#8211; how can I check what version I have? Is there a similar installation manual for Ndiswrapper for the Desktop version? In a perfect world I would get my existing DWL-G520M to work, but I doubt I would succeed, at least with any kind of WPA.

---

### Post by stromdal on 2008-04-27
Over on LinuxQuestions I got a tip about A-Link WL54USB. Anyone have any experience with this NIC? What routers are you using it with?

---

