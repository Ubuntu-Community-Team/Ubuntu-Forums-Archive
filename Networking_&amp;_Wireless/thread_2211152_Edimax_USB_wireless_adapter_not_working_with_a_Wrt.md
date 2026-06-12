---
title: "Edimax USB wireless adapter not working with a Wrt54G router"
date: 2014-03-14
forum: Networking &amp; Wireless
---

### Post by Jim_Lynch on 2014-03-14
Running 12.04 on a lenovo desktop. I have a Cisco E3000 router that's not connected to the wan in a remote lab.  It just serves as a switch for some local systems.  I can connect to it fine with the USB dongle.  I can't connect to a Wrt54g router in the other room.  iwlist wlan0 scan sees the other router just fine.  I connect but it spins for a while and then tells me "bad password".  It failed using network-manager so I replaced it with wicd, since I've had better luck with it in the past.  That didn't help.  I have a laptop that also has wicd on it and it connects just fine.  I've compared the settings in the two systems and they appear to be identical.  Passwords are the same, I even had someone else sit down and type in the password from scratch for me.  :)  The router is using wpa2, hex.  

The E3000 was running the default software but a month ago I installed dd-wrt.  The system in question connected via the dongle to both configurations.  I also  use the same (model) dongle on a R-Pi at home connected to an ASUS router running EasyTomato.

I attempted to connect using a different computer (old Dell Dimension) in the lab running Lubuntu 12.04 using the same dongle and had similar results.  It also got the bad password.  I'll be at the lab later today and will gather more info.  

Thanks for any suggestions.

Jim.

---

