---
title: "Can no longer connect to PEAP wireless network."
date: 2008-01-17
forum: Networking &amp; Wireless
---

### Post by Abram on 2008-01-17
Hello all,

I am currently using ubuntu 7.10 on my laptop, previously I have been able to connect to the wireless network at my university which uses WPA2, PEAP and MSCHAPv2.  It used to require that I configure the settings for the network every time I attempted to connect - which was fine since it only took a few moments.  However, now when I attempt to connect to the network - I get no prompt for security details and it attempts to connect, and then subsequently fails.

Im using a RT2500 (built in) wireless adaptor and I am at a loss as to why this has happened.  I was considering trying to install the RUtil that I had with the previous distroy of Ubuntu I used, howver that gave errors about not being able to store configurations, but still allowed a connection.

I still get the prompt to enter network details for any other network I attempt to connect to - be they WEP, WPA or WPA2..

Anybody got any ideas what could be causing this?  Would it be worth re-installing the network manager?  or is there a way I can remove any stored settings that the network manager may have for that wireless network?


Thanks in advance.


Abram

---

### Post by calraith on 2008-01-17
What's in your /etc/wpa_supplicant/wpa_supplicant.conf?

---

