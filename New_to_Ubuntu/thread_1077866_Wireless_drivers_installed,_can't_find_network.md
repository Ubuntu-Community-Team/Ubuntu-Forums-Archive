---
title: "Wireless drivers installed, can't find network"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by monpolo on 2009-02-22
Obviously, I'm a nooblet, why else would I be in this part of the forums? I've scoured through guides and have come to a dead-end. Please correct me if any of my assumptions are wrong and of course all help will be greatly appreciated.

I am pretty sure my wireless card drivers are installed correctly because the light is on saying that the card is activated when I flip the switch on. I am using a Dell Inspiron 1520 laptop with a built in wireless card Dell 1390 mini if I recall correctly. I am working off a wired connection right now but I can not find any wireless connections with my card. Yes it is turned on haha. I've installed ndiswrapper and ndisgtk. Under system->admininstration->windows wireless devices  I see the driver for my card. 

I know I rambled there and am probably not providing enough information but if anyone could let me know what they need to know to help me through this I could really use the help. I've been a slave to windows for a decade and I'm ready to move past it.

Thank you

PS Running 8.10

=============================EDIT============================
Not sure if there's an option to close this thread but I have fixed my issue. I don't know exactly what I did but my computer managed to find NEW drivers for my card and I enabled them so now it works just fine.

---

### Post by ibuclaw on 2009-02-22
If you know the ESSID of the router you are connecting to and the WEP-key/WPA Passphrase, then you should be able to explicitly set it in the network-manager applet, then it will connect as soon as it discovers it.

Regards
Iain

---

### Post by monpolo on 2009-02-22
Tried that. My router is broadcasting it's ssid and when I try to connect manually like that it just says network disconnected.

---

