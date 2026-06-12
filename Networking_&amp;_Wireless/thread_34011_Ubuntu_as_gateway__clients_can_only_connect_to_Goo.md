---
title: "Ubuntu as gateway : clients can only connect to Google"
date: 2005-05-13
forum: Networking &amp; Wireless
---

### Post by LongLife on 2005-05-13
Hello,

I recenty installed Hoary 5.04 and configured the system to share my internet connection like explained in this howto :
 [http://www.ubuntulinux.org/wiki/ShareInternetConnection](http://www.ubuntulinux.org/wiki/ShareInternetConnection)
I made the nat, added the following lines at startup :
iptables -t nat -A POSTROUTING -o ethX -j MASQUERADE
$echo 1 > /proc/sys/net/ipv4/ip_forward

and gave the isp dns adresses to the client


Problem :
The Ubuntu gateway can browse any site without problem.
The client can ping all websites and get their IP adresses, but can only browse [www.google.fr](www.google.fr). With the other sites (eg : [www.sourceforge.net)](www.sourceforge.net)), the browser connects to the site but the transfert hangs up and the page doesn't appear. 

What could be the problem?
I suspect an IPV6 incompatibility

The gear :

I have a 2 Pc network linked with a single cable.
- The gateway :
Ubuntu Hoary 5.04
Dell Dimension 4550  (P4 2ghz)
Internal Ethernet 10/100 Intel network card
No firewall
Modem : Sagem Fast 800 USB with latest eagle-usb drivers

- The client :
Reh Hat 9
AMD K6-2 350
ISA 10 Mb realtek 8019 network card
No firewall

I also tried the following client with exactly the same result :
Mandrake 10.1
Dell Inspiron 8000
Internal Ethernet 10/100 Intel network card
No firewall

---

### Post by defkewl on 2005-05-13
Check the iptables rules

---

### Post by LongLife on 2005-05-17
I found the solution !
It was a MTU size problem. The MTU size of the connexion between the gateway and Internet is lower than the MTU size between the gateway and the clients

I had to add the following line to my iptables rules :
iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS -o eth0 --clamp-mss-to-pmtu

And it worked fine

If anybody wants more info about this look at this page (in French, sorry about that) :
[http://people.via.ecp.fr/~alexis/formation-linux/firewall.html](http://people.via.ecp.fr/~alexis/formation-linux/firewall.html) 

Thank for your help !

---

### Post by fergus.b on 2005-05-28
[QUOTE=LongLife]I found the solution !
It was a MTU size problem. The MTU size of the connexion between the gateway and Internet is lower than the MTU size between the gateway and the clients

I had to add the following line to my iptables rules :
iptables -A FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS -o eth0 --clamp-mss-to-pmtu

And it worked fine

If anybody wants more info about this look at this page (in French, sorry about that) :
[http://people.via.ecp.fr/~alexis/formation-linux/firewall.html](http://people.via.ecp.fr/~alexis/formation-linux/firewall.html) 

Thank for your help ![/QUOTE]
 I was having this exact same problem while trying to setup internet connection sharing for my iburst connection. Eventually I got it working using the firestarter wizard, which was mentioned in one of the other threads. You can install it using Synaptic (of Kynaptic).

---

