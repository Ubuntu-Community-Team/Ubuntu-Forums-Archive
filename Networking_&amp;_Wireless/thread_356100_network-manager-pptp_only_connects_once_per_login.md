---
title: "network-manager-pptp only connects once per login"
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by cez801 on 2007-02-08
I have installed the network-manager and network-manager-pptp and set up a VPN connection to a windows server at work.

And it works well.
But only seems to work once per login. If I connect, then disconnect, I can not connect again unless I log out and log back in.d 
When I attempt to connect the second time, I get an error: Could not start the VPN connection 'work' due to a connection error. VPN Connection failed.



I followed the instructions here, to get it working:
[http://shiny.thorne.id.au/2007/01/pptp-from-ubuntu.html](http://shiny.thorne.id.au/2007/01/pptp-from-ubuntu.html)

And here:
[http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php](http://www.dailytechnology.net/how_to_setup_vpn_in_ubunty_edgy_eft.php)


BTW: I  did try using pptp-config to begin with  but could not get it working, and I do like the network-manager (for managing my wireless, works great).

---

### Post by cez801 on 2007-02-08
Actually, I have just checked again. It seems to be time based - not based on the login. Once I have disconnected, I need to waiting somewhere between 30minutes -> 1 hour to reconnect.

My work has 3 gateways vpn1, vpn2, vpn3 - but I can not use any of them once I have logged in once.

---

