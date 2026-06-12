---
title: "How to forward port"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by satya_461 on 2007-05-25
Hi ,

 I am unable to forward port. I am trying to configure azureus but  always gives me NAT error. After searching for some time, I came to know i have to use iptables to forward a port.

  Also, Bitcomet works in windows by just giving proxy server address and port. Seems auto portforwarding is enabled in it.  From ubuntu, using wine and bitcomet , I am able to download but  I am not able to see the list of files I am downloading. So I cant stop it.

 The details I knew:
My internal ip, 
gateway address, 
external ip (from whatismyp.com).

I cant configure router as this is from company network ;).
So with these details I want to forward a port 7777.
and I want to see Azureus NAT test to be passed??:(
how do I??

Please help..
Please let me know if any further details required

Thanks,
Satya.

---

### Post by joft on 2007-05-25
If your computer is connected to your company's router, only, and if it accesses the internet by exactly this connection, only, and the router is untouchable for you - then you will never be able to forward a port.
Port forwarding/NAT is a matter of a router and not of an end-point, like your PC is. The router of your comapny needs to be configured to forward the port you wish to your internal IP.
There simply is no other way - sorry, that's the way NAT (and port forwarding) work.

---

### Post by satya_461 on 2007-05-25
> **joft said:**
> If your computer is connected to your company's router, only, and if it accesses the internet by exactly this connection, only, and the router is untouchable for you - then you will never be able to forward a port.
Port forwarding/NAT is a matter of a router and not of an end-point, like your PC is. The router of your comapny needs to be configured to forward the port you wish to your internal IP.
There simply is no other way - sorry, that's the way NAT (and port forwarding) work.


Oh is it??:( then I wonder how is it working in windows without touching router).. This is the  only reason I had to use windows.

---

### Post by joft on 2007-05-26
Hmmm, the only way which allows an end-point client to "configure" the router is the UPnP protocol. That means an application "tells" the router to forward a port via this special protocol. But, usually UPnP should be disabled to prevent security holes in a company's network - at least IMO.
So if your company really allows UPnP, that means "making some router configuration options  available to normal users", and you enabled UPnP in azureus (under Linux), then I have no clue, why it is not working. Hmmm ...

---

### Post by fenian on 2007-05-26
If its working in windows find out which port azureus is using in windows and use the same settng for azureus in ubuntu.

---

### Post by satya_461 on 2007-05-31
Yup Azureus 3.0.1.2 is working in windows, It is working with random port but not in Ubuntu. I also tried with the same port in Ubuntu..Still it didn't work. Azureus with exact configuration is working in windows but not in Ubuntu.Very strange..

Bitcomet with wine doesn't show the files I am downloading/downloaded and there is no way to  stop it. I have forcely quit the application.. seems like I have to adjust with this.. :)

---

