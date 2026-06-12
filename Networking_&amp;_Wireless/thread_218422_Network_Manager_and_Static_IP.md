---
title: "Network Manager and Static IP"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by ubuts3 on 2006-07-18
Hi All!

I try to use kernel 2.16.15-26-386 with GNOME Network Manager. I have disabled all interfaces except lo in /etc/network/interfaces to make UBUNTU 6.06 GNOME work with network manager. I can see interfaces in Network manager.
I don't know how to assign static ip/netmask and gateway for wireless and ethernet to use them in network manager. Anyone knows?

---

### Post by fadumpt on 2006-07-18
For wireless profiles, you might want to install Wifi Radar, it makes it a lot easier to have custom locations for your connections.

As far as Network Manager, if you click Properties for your device and change the drop down box from DHCP to manual (i think), you can input your static IP information there.  DNS information can be keyed in on the third tab over on window that shows your devices (sorry, don't have ubuntu up right now)  

Is that what you are asking?  Or am I way off on this one? :)

---

### Post by ubuts3 on 2006-07-18
If You touch anything (change any property) using System->Administration->Networking You write changes to /etc/network/interfaces and network manager can't see network interfaces after reboot (read my first post). This is not the way You can do it.

---

### Post by michaeljb2005 on 2006-08-02
You could consider using netapplet in conjunction with wifi radar (like he said).  That combination works pretty well for me.

---

