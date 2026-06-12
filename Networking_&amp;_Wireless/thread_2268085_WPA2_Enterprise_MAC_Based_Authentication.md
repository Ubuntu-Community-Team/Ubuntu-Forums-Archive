---
title: "WPA2 Enterprise MAC Based Authentication"
date: 2015-03-06
forum: Networking &amp; Wireless
---

### Post by kyle13 on 2015-03-06
I am looking to setup my Ubuntu laptop to authenticate to my wireless network using the MAC Address (or station-id as it is sometimes referred to). Every option, except TLS, requires me to put a user name and password in. For the TLS, I don't want to create a cert for each system I need to connect to the wireless. Is there anyway to configure the wireless to use WPA2 Enterprise, but only use the MAC address?

---

### Post by TheFu on 2015-03-06
I don't know the answer to your question, but are you sure this is an idea even worth considering?

MAC addresses can be spoofed - trivially. They are not tied to anything.  Look up "arp poisoning" for more.
Every packet sent - even when encrypted - has the MAC in the clear. It is required for wifi and ethernet to work at all.

MAC based filtering is possible on most routers/APs - but it is like posting a sign outside an open door asking people to not steal.  Lots of tools for wifi hacking automatically spoof MACs. [http://lifehacker.com/5916339/circumvent-wi-fi-time-limits-at-coffee-shops-by-spoofing-your-mac-address](http://lifehacker.com/5916339/circumvent-wi-fi-time-limits-at-coffee-shops-by-spoofing-your-mac-address) ... shows how wide spread this knowledge is.

---

### Post by kyle13 on 2015-03-06
I know MAC's can be spoofed. The biggest issue is I am running dual SSID (one for me, one for guest) and I want to secure the one for me with some MAC Filters (which can be done on the AP, but affects both). I know on Switches you can do MAC auth mainly for devices that won't allow a user name to go in (such as a printer). Domain computers also general auth with the wireless or wired with the MAC first so you can talk to the domain, otherwise you get knocked into the guest network and can't talk to your DC.

It is possible it is something that needs to be done at my Wireless AP, but I won't know that until my replacement AP arrives.

---

