---
title: "WPA showing up as WEP"
date: 2008-01-16
forum: Networking &amp; Wireless
---

### Post by psavach on 2008-01-16
Ok, so I'm fairly new to linux and just had this problem.  I had Hardy installed and everything working fine with my wireless through ndiswrapper.  I reinstalled it (long story) and everything looked fine as far as the card went.   I tried to connect to my WPA2 secured network which went fine except that I needed to get my key. I rebooted my system while I was getting my key from my other computer.  When I came back to the laptop I tried to connect and all of a sudden my network was showing up as WEP secured instead of WPA2.  I hadn't done any installs or upgrades or anything like that that could have messed up my system.  I am using the network manager I think it's called (top right of screen).  So, does anyone have any suggestions as to what might be the problem here?

---

### Post by iamclueless on 2008-04-08
im having trouble connecting to my WPA secured router

only way wicd connects is if i drop all security

im having the same problem as the person above.  my WPA is being detected as WEP... is this the problem?

---

### Post by kutjara on 2008-04-08
> **psavach said:**
> Ok, so I'm fairly new to linux and just had this problem.  I had Hardy installed and everything working fine with my wireless through ndiswrapper.  I reinstalled it (long story) and everything looked fine as far as the card went.   I tried to connect to my WPA2 secured network which went fine except that I needed to get my key. I rebooted my system while I was getting my key from my other computer.  When I came back to the laptop I tried to connect and all of a sudden my network was showing up as WEP secured instead of WPA2.  I hadn't done any installs or upgrades or anything like that that could have messed up my system.  I am using the network manager I think it's called (top right of screen).  So, does anyone have any suggestions as to what might be the problem here?

My old Vaio TX650P had the same problem. Gnome network manager showed the connection as WEP, even though it had been set up as WPA2. I suspect this is just a bug in the way network manager displays security settings for certain cards. If your router is correctly set up for WPA/WPA2, then it won't suddenly allow PCs to connect to it using just WEP. You can be pretty confident you're connecting via WPA, regardless of what the label in nm-applet or WICD says.

---

### Post by Rmg12 on 2008-04-12
Yeah My WPA2 network keeps getting set as WPA and the password is set twice for some reason I change it and save but it gets reset its weird. But I use Hardy Heron.

---

