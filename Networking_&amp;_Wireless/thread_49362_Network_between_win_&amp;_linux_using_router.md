---
title: "Network between win &amp; linux using router"
date: 2005-07-16
forum: Networking &amp; Wireless
---

### Post by HAMM3R on 2005-07-16
Hey everyone.  Im a total n00b to networking.  What i need to do is set up a network (where I can share files and use a VNC) using only a router.  Its a standard 4 port router with a NAT firewall.  What I have now, is the cable broadband cord connected to my modem.  Then, a cable from the modem connects to my router.  And cables from my router connect to my 2 computers.  How can i set this up to be able to share files, possibly printers, and use remote desktop (VNC).  Can someone please point me to a tutorial showing how to do this?  TIA TIA TIA TAI!!  :) 

Best Regards,

Austin Hammer

---

### Post by nemin on 2005-07-16
[QUOTE=HAMM3R]Hey everyone.  Im a total n00b to networking.  What i need to do is set up a network (where I can share files and use a VNC) using only a router.  Its a standard 4 port router with a NAT firewall.  What I have now, is the cable broadband cord connected to my modem.  Then, a cable from the modem connects to my router.  And cables from my router connect to my 2 computers.  How can i set this up to be able to share files, possibly printers, and use remote desktop (VNC).  Can someone please point me to a tutorial showing how to do this?  TIA TIA TIA TAI!!  :) [/QUOTE]
OK, well this is more a general networking question than a Ubuntu one, but here we go :)

Routers are usually configured to use DHCP for the internal network. So when you connect your two computers to the router, you'll automaticly receive an IP and gateway-address, so your internal network is basically set-up then. 
Next, have a look at the documentation of the router about how to configure the internet connection. Usually, you'll have to connect from one of your comptuters to the IP-address of the router and configure a few things then. Then you'll probably have to configure the gateway settings on your two computers to point to the router. 
After all this, internet should work on both computers:D

For file/printer sharing, read [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba). For other network question, [http://ubuntuguide.org/#networking](http://ubuntuguide.org/#networking) is a good place.

Good luck.

---

### Post by HAMM3R on 2005-07-18
Thanks m8!    :)

---

