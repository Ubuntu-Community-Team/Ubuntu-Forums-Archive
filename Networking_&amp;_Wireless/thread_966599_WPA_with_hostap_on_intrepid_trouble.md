---
title: "WPA with hostap on intrepid trouble"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by itakeupspace on 2008-11-01
I have an old Compaq Armada 7400 that I've run Xubuntu on for some time.  The wireless card is a Senao EL-2011CD (one of the prism chipsets).

I put 8.10 on it this week, and I can't get the wireless to work with the hostap/hostap_cs drivers.  It works fine when it's using orinoco/orinoco_cs/hermes, even when the hostap modules are also loaded.  I can connect to unsecured and WEP networks that way, but I need to be able to also use WPA.  

When I boot with orinoco/orinoco_cs/hermes blacklisted, I can't connect to any networks.  NetworkManager will do its orbit thing and light up the two green lights quickly, then keep spinning until it times out and asks for your password again.  I've also tried connecting using the low level techniques in this thread ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)), to no avail.

Could one of the gurus perhaps shed some light on this, or offer some suggestions?

---

