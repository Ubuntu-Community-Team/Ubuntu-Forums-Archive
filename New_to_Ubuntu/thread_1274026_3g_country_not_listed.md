---
title: "3g country not listed"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by jonathan21 on 2009-09-24
zinmbabwe only recently joined the world of 3g.ubuntu picks up my 3g modem but country is not listed.does anyone know how to setup for a country not listed.

---

### Post by VipX1 on 2009-09-26
You don't have to use the set up like that you can do it manually. Just cancel the initial set up and right click on the NetworkManager icon in the top right of the desktop, the icon that shows the network status. Go to mobile broadband menu. Select Add+ Number = *99# 
All other setting are particular to the 3G operator you are using. I use vodafone in ireland and my APN is hs.vodafone.ie Username and p/word are both vodafone. I found that info by searching the Web. Also if you have the Windows software that came with USB modem and a Windows PC to run it up on have a look at the settings. Once it is working on the Windows desktop and you can use the settings that are in that supplier provided software. Type them into the Ubuntu mobile broadband Add+ settings..
Ubuntu NetworkManager is it's software for the USB modem so if you add the same settings it will work. I use 3G for workand both O2 and Vodafone work on my Ubuntu laptop very well. The interface (USB modem) is called ppp0 on the Ubuntu operating system so if you want to see if Ubuntu has activated it type *ifconfig *into a terminal and that will list all active interfaces. Also if it has not found it the following command is quicker than a reboot:```
sudo /etc/init.d/NetworkManager restart
```I hope that helps.

---

