---
title: "Cannot access server using public IP address after changing ISP"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by stepheny on 2014-01-11
I have recently moved house and have a new ISP (Kabel Deutschland). I kept my old WLAN (Netgear Wireless-N 300 Router. Model WNR2000v2) because it was already set up with all my wife's and my devices such as mobile phones, Kindles etc.

I set up the router to the new modem and everything is working fine and has internet access except for one problem.

The problem is that my HTTP server, which I connect to the router via ethernet cable, is accessible using the local IP address but not using the public address given by the ISP. I have the same problem with FTP, that is I can transfer using the local IP address but not the public IP address. I obtained the public IP address using [http://www.whatismyip.com/ip-address-lookup/](http://www.whatismyip.com/ip-address-lookup/) and other similar websites which all gave the same address. I have always used this method of accessing my server past and cannot understand what is preventing access now. I have switched off firewalls and checked blocking on the router, but to no avail.

I would really appreciate any explanation as to why I cannot access my server via the public IP address.

PS. I forgot to mention that I can ping the public IP address, It is just that I cannot access it via HTTP or FTP.

---

### Post by tomearp on 2014-01-11
There are various websites that will allow you to test for open ports:
[http://www.yougetsignal.com/tools/open-ports/](http://www.yougetsignal.com/tools/open-ports/) is one of them.

If you are sure everything is set up at your end (i.e. ports are forwarded to the correct internal IP, firewall on the router is not blocking anything, firewall on the server is not blocking anything, services are working correctly on the server) then it is possible that your new ISP is blocking the ports you are trying to use.
If you are hosting your HTTP and FTP servers on their default ports, 80 and 21, then it would be worth moving them into the range 1025-65535 and trying again to access them.

---

### Post by houstonbofh on 2014-01-11
Is the ISP providing you with a router or a modem?  If it is a router, it is doing NAT, and you need to either forward ports or set it in bridge mode.

If that is not the case, your new ISP could be filtering in bound "server" ports.

---

