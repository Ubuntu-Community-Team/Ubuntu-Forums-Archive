---
title: "Asus wl-500g WIRED - can only seem to get WAN on one machine ..."
date: 2008-03-08
forum: Networking &amp; Wireless
---

### Post by em3raldxiii on 2008-03-08
This problem has me totally stumped.  It seems like such an incredibly simple thing, and yet I cannot seem to find the correct thing to click on, or the correct thing to type in to get it going.  ***ANY*** advice or suggestions will be appreciated!!

Current arrangement:

Computer#1:  
IP:  192.168.1.103 (I have no idea where that came from, but there it is)
Wired to LAN port #1
Everything works.  I can connect to the router, to the USB HD thru the router, and I can connect to WAN with 100% normal, expected results.

Computer#2:
IP:  192.168.1.2 ... I think it came from one of my many attempts to configure it, one being manually entering the IP address in the DHCP settings of the router.  I have since gone back to auto DHCP
Wired to LAN port #2
Connecting to router admin works (192.168.1.1), and connecting to the USB HD thru the router also works.  I CANNOT make this computer connect to WAN, no matter what I try ...

If I type in *ifconfig* in comp#2, I get the usual blob of info, including the mac address and the ip address.  All seems normal and matches (as far as I can tell) the equivalents on comp#1.  However, if I try to ping ANY outside locale (such as google.ca), I get "Network is unreachable" immediately.

Please help ... anything!!!  Please!!!! :confused:

---

### Post by HereInOz on 2008-03-09
It looks like you have set the IP address of the troublesome machine manually.  I would recommend first up that you go into System > Administration > Network and removing all of your fixed IP addresses, and setting Roaming Mode on.

Have you tried pinging an actual IP address rather than a domain name?  If you can ping an IP address but not a domain name, then it is probably a DNS issue, and you may have to set the DNS servers manually in your network setup.

Also, please make sure that NAT is turned on in your router.  If it is an ISP supplied modem router, I have known ISPs to turn off NAT on the router, and this means that you can only connect one computer at a time through that router.

See if that helps.

---

