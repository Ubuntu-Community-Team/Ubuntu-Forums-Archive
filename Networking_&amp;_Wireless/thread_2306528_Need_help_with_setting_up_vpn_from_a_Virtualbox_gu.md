---
title: "Need help with setting up vpn from a Virtualbox guest"
date: 2015-12-16
forum: Networking &amp; Wireless
---

### Post by James Wilde on 2015-12-16
I have an MBP running Mavericks, with VirtualBox 5.0.0 and a Ubuntu 14.04 guest.  I want to run Boxpn VPN from the guest.  The host is connected to my network via wifi - not Apples, but a D-Link 11n usb stick.


I've got the openvpn and pptp instructions for Ubuntu, but nothing works unless I have the guest set up for ethernet.  Bridging doesn't work or rather I have not yet succeeded it getting it working.


Any help much appreciated or merely a url to a solution.


Thanks in advance.

---

### Post by James Wilde on 2016-02-08
OK, this is not a bounce, but an attempt to describe my setup and experiments so far and a request for help with finding a solution.

My setup is a machine running OSX (at present I've stopped at Mavericks, 10.9) and with Ubuntu 14:04 TLS guests in Virtualbox. Sometime in the future I might revert to Ubuntu as host also, but for the time being OSX has certain advantages which outweigh the disadvantages.


What I want to do is to run VPN from a Ubuntu guest to my VPN supplier's US outlet, from another to their UK outlet, from a third to their Icelandic outlet and from a fourth to their Swedish outlet.


I use OpenVPN, and for better or worse, I use BoxPN as my supplier.  I'm prepared to change BoxPN if necessary, but I'll need a serious reason to change from OpenVPN.


Once I had the system working to the US but I had a bit of bad luck with updating the guest and had to scrap it, and since then I have not been able to get this to work. I'm convinced the problem lies in the routing table, but I've experimented all I can and have not been able to get it working.


One important factor:  I'm trying to do this on a laptop, which means that there is only one route to the router, and that is over wifi using a D-Link 11n usb adapter - unless I insert a second usb network connector and send some traffic over that, if necessary, although I can't offhand see why I would need to.


Ask me any questions you like about what I've installed to try and make it work, how I've configured things, what my hardware consists of, etc.

---

