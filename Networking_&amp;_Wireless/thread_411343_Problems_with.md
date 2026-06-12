---
title: "Problems with"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by ohmycar on 2007-04-16
So I  looked around the forums before I posted and went like 3 pages deep to find any posts that could help me out before I posted. So sorry If there was a solution out there, I was unable to find it.

Anyways, I re-installed Ubuntu 6.06 on my Dell Inspiron e1405 Laptop.
The only problem is that, my internal wi-fi card does not seem to be working.
When I go to System ->Administration->Networking, it shows me my wireless (eth1) and my wired (eth0).
It says they are both activated and everything, only when I go to properties for my wireless, it says signal strength is 0. It does not pick up my router. 

When I was using Xp , My card was working and it was able to pick up my router. I am not sure if this is a driver problem or what. I also tried plugging in an ethernet cord and that did that not well either. So I am not sure what is wrong with it.

The Wi-Fi light on my laptop blinks rather than staying solid. I am not sure what this means either. 
I want to install network-manager, but i do not know how to do so.

My internal wifi card is : Intel Intel(R) PRO/Wireless 3945ABG

Thanks.

- Ash

---

### Post by ClickForth on 2007-04-16
According to the Ubuntu Supported Cards wiki:


Make: Intel
Model: Pro/Wireless 3945 ABG (Centrino)
Supports network install: Untested
Supported in installed system: Yes
Works "out of the box": Yes
Comments: Works perfectly on a fresh Ubuntu 6.06 (Dapper) installation. On older versions, works if you manually install the ipw3945 module (from ipw3945.sf.net), the ipw3945 daemon and the ipw3945 firmware ucode (requires ieee80211 kernel support). Not detected at all on [WWW] my system. Automatically detected and correct drivers loaded on Edgy.

---

### Post by ohmycar on 2007-04-16
Yeah It used to work when I would install 6.06 right now it does not though. 

And I am not quite sure why either.

---

### Post by ohmycar on 2007-04-16
never mind, radnomly started working i think..

I disabled eth0 and eth1, waited a little bit, then re-enabled them, then it was able to pick up my router.
time to see if it fully works.

Edit: Well It was working up until I clicked OK in the network settings window , now it is back to the way it was before. :( , anyone know whats going on?

---

