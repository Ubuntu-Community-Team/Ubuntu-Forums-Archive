---
title: "DELL Truemobile 1180 help"
date: 2006-12-14
forum: Networking &amp; Wireless
---

### Post by k2pow on 2006-12-14
Hi I just used the latest ndiswrapper to install drivers for my Dell Truemobile 1180 usb adapter. The drivers were all successfully installed but my card still isnt working. Im guessing that I am not using the right drivers. On the wiki list it said to install the win98 inf and then manually move the win98 sys files. I tried this but it didnt work. IF any one has this card and got it to work can you please tell be what drivers you used.

---

### Post by k2pow on 2006-12-14
Anyone got this adapter?

---

### Post by Aeo on 2007-10-04
I dont know if i got longer than you but... i get iwlist from my Truemobile 1180.. 
I used the **WL-683D **drivers and took win2k dont know if thats the right.. gonna try winxp right now..

[DRIVERS SITE]("http://www.usb-drivers.com/drivers/199/199747.htm")
(you need to register and than thats the right drivers)

but if you make 

**# rmmod prism2_usb **

first. and get the green light shut down, i did ifconfig wlan0 down..

and than you make 

**# modprobe ndiswrapper**

so the green light gose upp again.. 

try that.. I will tell you if i get futher....


/Aeo:)

---

### Post by Aeo on 2007-10-04
I have lookt some more and it dose not mater wich drivers you use.. its like the same.. when you have installd them be shure that the conflict drivers are removed from modprobe.. becuse it wont work unless... it will take like a minuit before it shows the network(s) but it will come.. the onely thing i dident get to work was that i did nog got it to connect .. it shows the network but it wont get contact with the accespoint...

---

