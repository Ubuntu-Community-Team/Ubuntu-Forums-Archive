---
title: "[SOLVED] Unable to get valid IP address"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by Trevor4706 on 2007-10-08
This is a follow-up to an earlier post I made almost two months ago.

My ISP (Bell Sympatico) recently upgraded my DSL service and sent me a new modem, a 2Wire Model 2701HG-G Gateway.  It is a combined DSL modem and wired/wireless router.  Wired connection to the router is no problem for any of my XP or Linux boxes. 

I have a dual-boot laptop, XP and Kubuntu Feisty.  Wireless connection to the 2Wire router with my Gigafast WF728-AEX adapter is no problem for XP.  Another story in Kubuntu.  The wireless network is recognized (correct ESSID), WEP code demanded and entered, but no connection ever successfully made.  I have tried Gnome Network Manager, KNetworkManager, WICD and Wifi Radar.  None have been able to get a valid IP address from the router.  Occasionally I achieve an "associated" state, but an invalid IP address in the 169.254.8.xxx family will show up, and connectivity will of course be zero (my router's IP addresses are in the 192.168.2.xxx family).  I have tried all combinations of firewall active/inactive, automatic/static IP addresses, WEP enabled/disabled with no success.  

I have no difficulty connecting in Kubuntu at any local wireless hotspots, so the problem has to be in communication between my laptop and the 2Wire Gateway.   I have a few questions, and would appreciate any help/suggestions.

Are there any known issues between Feisty and 2Wire Gateways?

Can you think of anything else I can try to get a successful connection?

As I try to solve this, which wireless network manager would you recommend I use (presently have Wifi Radar installed).

:confused:Trevor4706

---

### Post by solstace on 2007-10-08
Me too - though for me I'm seeing the problem either with WPA2-enabled Apple Airport or Belkin 7003 54G base stations, consistantly when using Ubuntu 7.04 with all relevant firmware and software updates applied.

Seems to be tied to issues with particular models of base station rather than anything else...

Any ideas?

---

### Post by Trevor4706 on 2007-11-08
After weeks of trying many of the fixes suggested in this foum, including Wlanassistant and Wicd, I was convinced the new router was not the problem; rather it had to do with the software's inability to resolve 128 bit WEP encryption. I re-installed KNetwork Manager and tried various levels of WEP.  Eureka, using 128 bit encryption, but with a 13 character ASCII key instead of a 26 character Hex key connection is swift and stable.:)

Go figure!

---

