---
title: "invalid access point?"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by freddiethehawaiian on 2006-07-24
so my problems are these:
1. i am new to linux and unbuntu
2. i only have a wireless connection for the computer i am using and
3. i have no idea how to connect to the router.

that said here's what i have and the results of iwconfig eth0:

wireless card- linksys wmp54g
router-        linksys wrt54g

iwconfig-
IEEE 802.11b/g  ESSID:"home"  Nickname:"Broadcom 4318" 
         Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
         RTS thr: off   Fragment thr: off
         Link Quality:0  Signal level:0  Noise level:0 
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
         Tx excessive retries:0  Invalid misc:0   Missed beacon:0

did i miss anything or am i stupid? please help.

---

### Post by NewDisciple on 2006-07-25
The problem as far as I can tell is with your mac address which is your access point. If you have KWiFimanager installed it may give you the appropriate mac address if the scan picks up your
router.  I'm fairly new at this myself so I'm just throwing out a quick idea.  Did you confiure your wireless with networking or network manager or some other application?  Can you connect to your router itself by entering its IP address in the URL line of your browser.  For example: [http://192.168.1.1/](http://192.168.1.1/).  Well this should keep you busy for a little bit.  Good Luck!  Keep at it, you will eventually get it.

---

