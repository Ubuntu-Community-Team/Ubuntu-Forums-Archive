---
title: "Wireless Networking"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by Toodifficult on 2007-11-02
Jeeze... how difficult can it be to choose a unique username on here?

Anyway...

It's clear from the many threads on here that one of the major problems with Linux at the moment is wireless networking.

I'm not singling out Kubuntu for any unfair treatment here all the distros seem to suffer issues of one form or another, it's just that Kubuntu is the lastest distor that I'm trying out.

I just don't understand why it is just so damned difficult to get WiFi working under Linux, I mean if Microsoft can do it why can't the collected wisdom of the open source community?

The latest woe is with Kubuntu 7.10.  Many things with WiFi just seem fundamentally broken.  I am currently using the live DVD on a T42 Thinkpad.  Initially things look promising.  The KDE network manager shows my WiFi AP and identifies it as protected by WPA.  So far so good.  I enter my WPA key and off it goes to try and connect except it fails because I use static addressing and KDE NM seems to expect DHCP.  No problem... I reconfigure the ath0 interface to have a static address... and that's the last time KDE NM detects my WiFi AP.  No amount of coaxing seems to be able to get it to detect my WiFi network again.  Even switching back to DHCP does no good.  And after that KDE NM offers me only WEP keys which are no good to me.

It is a complete frustration.  Why can't it work out of the box without all this messing around?  It really shouldn't be this difficult.

---

### Post by frankly.de on 2007-11-02
My problem is very similar: Everything works all right while I let the Networkmanager do it's job in establishing a connection with my router. Trouble is that on the router DHCP is disabled as I use static Ips in the network. So while a connection to the router is established, the machine remains without IP (and gateway, DNS....) which obviously is not enough.
So, I think, not a problem, it is easy enough to enter the necessary data by the manual configuration option. However even though all the data is there, there is no way I can coax the system to contact the router to establish the connection. Under iwconfig I get all the IPsettings, but encryption (and a few other details which I don't remember) are shown as off, although I clearly chose the WPA2 option and entered the correct password (or should it be that Ubuntu does not support question marks as part of the password - although this is no problem when using the automatic mode).

Any suggestions?

---

### Post by Lambert on 2007-11-02
> **Toodifficult said:**
> 

It's clear from the many threads on here that one of the major problems with Linux at the moment is wireless networking.


I just don't understand why it is just so damned difficult to get WiFi working under Linux, I mean if Microsoft can do it why can't the collected wisdom of the open source community?

It is a complete frustration.  Why can't it work out of the box without all this messing around?  It really shouldn't be this difficult.

It's not microsoft that does it, it's the manufactures of the wireless devices. There is a driver that is needed for the operating system (either winxp or gnu/linux etc..) to exchange data with the device. Most of the manufactures don't write drivers that work with gnu/linux nor do they provide specs on their devices so the community can write them. Some of the drivers out there are reverse engineered where basically somebody spends countless hours analyzing the device or activity with the device, documents things, then trying something and adjusting from there.

Wireless is getting better but it still is a very weak area for linux. Just recently the frame work was being laid to simplify some things in wireless for manufactures and improvements will continue. Some of the improvements will come simply because some bigger manufactures like Dell, HP, and Lenovo are offering products with linux preinstalled. They will push for drivers.

Until that point where manufactures provide the same support for alternate operating systems, it will continue to have problem areas.

One thing anybody can do is contact the manufacture of the device, let them know you want to use gnu/linux as your operating system on their pc and you would appreciate better support from them on their drivers. You may get a blanket response from them on why they don't but if they get enough feedback, at some point some exec will see what's happening and realize what needs to be done. That's why Dell now supports a system with preinstalled ubuntu.

---

