---
title: "No internet connection"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by saby4237 on 2007-11-26
I'm virtually a newbie; installed Ubuntu 7.10 today, tried to manually configure a Static IP Address.. unchecked 'enable roaming', filled in the IP Address, Gateway, etc.. did everything that worked in Ubuntu 7.4.

 But alas, can't connect to the network.

I'm connected to a LAN through an ADSL Router (HUAWEI Quidway WA 1003A).

Any help would be greatly apprecieated!

---

### Post by mellowd on 2007-11-26
Why don't you get an IP via DHCP? That will at least show if you're connecting to the router.

---

### Post by moyazes on 2007-11-27
I would also recommend mellowd's suggestion.

Does your router have a single ethernet port or has a in-built 4-port hub ?

Do you see a link light when the cable is connected between the router and the computer ?

If you router has a single ethernet port you and you see no link light lit then you may need a cross-over cable.

---

### Post by saby4237 on 2007-11-27
My computer and router are part of a LAN and if I configure via DHCP there's an IP Address conflict with another computer on the LAN.  

 The 'ADSL', 'LAN', 'STATUS' are on and it seems I can get connected to the router, but not to the internet via router. 

 Thanks for the help (and any further help!)

---

### Post by mellowd on 2007-11-28
How is the lan connected? If they are connected via a Hub then you can't have 2 seperate IP's routing through the same device. 

The fact that it has an IP conflict when DHCP is enabled leads me to believe that the router cannpt see the 2 devices as 2 seperate devices

---

### Post by saby4237 on 2007-12-09
Problem resolved!
  When I manually configured to a Static IP, by default my Gateway Address was being saved as the DNS Address, giving rise probably to a conflict.
  I manually removed the default DNS Server address and saved the proper DNS Server address of my Broadband Service Provider. 
  Now full net connectivity has been established.

 Thanks a lot to all who helped. I've been encouraged to seek help in these forums whenever I'll be in trouble regarding Ubuntu.  :)

---

