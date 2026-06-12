---
title: "password not being accepted for wireless"
date: 2007-12-23
forum: Networking &amp; Wireless
---

### Post by sonicktruth on 2007-12-23
I am running Gutsy and have all of the latest updates and for some reason everytime I try and connect to my wireless I get the box asking for the password. I enter in the password and after about 30 seconds it comes back and asks for the password again. I've triple checked and made sure I'm entering in the correct password. I'm trying to connect to an actiontec dsl modem/wireless router.:(
ps-I have no problem connecting on my Mac

---

### Post by csat on 2007-12-23
Try out another network manager like wicd.  Check for it at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Observe Ubuntu download directions and pay attention that your current network manager is gone to be removed.

---

### Post by rustybronco on 2007-12-23
what wireless card/chipset are you using to connect to the dsl/wireless router?
this command in the terminal will help you find the chipset ```
 lshw -C network 
``` 

also see kevdogs finest in my signature for trouble shooting tips.

there are a host of guides on this forum for trouble shooting a wireless connection, how to install ndiswrapper+the window drivers for your chipset ect.

---

