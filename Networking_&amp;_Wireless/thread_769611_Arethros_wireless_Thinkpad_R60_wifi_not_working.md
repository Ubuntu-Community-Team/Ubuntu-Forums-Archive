---
title: "Arethros wireless Thinkpad R60 wifi not working"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by olegnep on 2008-04-26
The wifi on my laptop has never worked with my netgear wgr614 v6 wireless router while running a linux distro , any linux distro (including ubuntu). google has given me no working answers so i finally got around to asking for help directly. i am fairly experienced with linux but am still not too comfortable with the command line ("tell me what to type" skill level ) 

I have a thinkpad r60 with a 1.83 ghz 2 core duo processor , 512 mb of ram stock (upgraded to 2 gb) , 1024 x 786 display,my wifi chipset is an atheros - AR5212 802.11abg NIC (ThinkPad 11a/b/g Wireless LAN Mini Express Adapter (AR5BXB6)).

any ideas?

---

### Post by yamagami on 2008-05-28
Hi, 
Have you ever resolved this issue? 
I have the same problem on my thinkpad T61p. It gets wierder: when I attach a pcmcia atheros card, which is recognized as the same chipset, it works without a problem. the intenral card doesn't. 
Harel

---

### Post by yamagami on 2008-05-28
Hi
I solved my problem by getting the latest madwifi off svn and recompiling it, and then recompiling the latest wpa_supplicant against that madwifi source. Works great!
Harel

---

