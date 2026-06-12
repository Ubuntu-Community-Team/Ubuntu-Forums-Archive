---
title: "Internet Issue - Linksys WRT54G2"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by MadJP on 2011-02-28
Basically I cant connect to the internet using the router. 

Specifically, I am on the net now via cat5e cable connected directly to my modem asking for help. I have tried reseting the router using the reset button and reconfiguring using my lan cable but am unable to "connect" with the router or login to 192.168.1.1 . I know the router was reset as the SSID is back to the original "linksys" and when i try to connect wirelessly it says i am "connected" but i cannot browse the internet. I tried connecting wirelessly and reconfiguring the router SSID and net password using 192.168.1.1 and managed to change the settings, but still no internet wireless or wired...... 

At this point I am at a loss, I'm using a fresh install of Ubuntu 10.04LTX. Any suggestions? They would be greatly apreciated.

---

### Post by cavh on 2011-02-28
Suggest going through the support section on the Linksys website first then come back here if no luck with that. It's been a while since I messed with a Linksys box. If I remember correctly there are some lights that flash a certain colour if all is well - are there any warning lights where you would otherwise expect a green colour signal?

---

### Post by pricetech on 2011-02-28
Cable modems "marry" themselves to the MAC address of the device that's attached to them.  Reset your router again so it's back to factory defaults, then unplug your computer from the modem and plug the router into it.  Then power cycle the cable modem and wait for it to finish posting.  You might possibly have to reboot your router, but it should pick up an IP once the modem starts communicating with it.

---

