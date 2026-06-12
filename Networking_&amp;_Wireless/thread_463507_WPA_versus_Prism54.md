---
title: "WPA versus Prism54"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by bredelet on 2007-06-03
Any news of WPA support for the Prism54 chipset?
I read somewhere that wireless drivers that support Linux Wireless Extensions v19 also support WPA, is it possible to retrofit the islsm driver with WEv19 support and get WPA working?

My wireless card is a Netgear WG511. I am concerned about the safety of my network with anything less than WPA.

> May 30th, 2006
awaldram  
A Carafe of Ubuntu

 	
Re: WPA does not work
to clear thinks up a bit

we are talking two chipsets here

prism/orinoco

and prism54

the 3com is the prism54
the original thread starter was using a built in orinoco

the hostap driver is ONLY usefull for orinoco/prism NOT your 3com card

your 3com card will work with the islsm and prism54
both drivers are developed by prism54.org with the islsm being the new al singing all dancing support anything 11g related in the prism54 family but DOES NOT support WPA in its present development.

the Prism54 driver is the older version that only support prism54 chipsets upto V2 but does support WPA unfortenatly our good devs have bust this in their rush to get islsm working .

---

### Post by bredelet on 2008-06-21
I am happy to report that WPA works in Feisty/Linux 2.6.20 using wpa_supplicant. However the option does not show in the Network Manager and it says that the encryption for this access point is not supported by my card. I did not try Gutsy yet.

---

