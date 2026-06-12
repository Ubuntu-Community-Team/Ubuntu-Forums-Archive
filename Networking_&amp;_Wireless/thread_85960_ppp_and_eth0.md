---
title: "ppp and eth0"
date: 2005-11-03
forum: Networking &amp; Wireless
---

### Post by priam on 2005-11-03
Hello,

I have an issue with my ppp connection over a PCI 56k modem and my eth network existing on the same breezy install (and hoary for that matter).  Basically i can dial whether my eth is activated or not, but as soon as it is i cannot access anything except by ip address...

I understand that this is a DNS problem, however i do not know how to set it up so that the PPP connection is the default route to the internet. As soon as i activate the eth0 connection it kills my ppp DNS settings. Can anyone help me??

Also i need to know how to share the ppp connection.  I have it setup to work in my winxp install, so the hardware infrastructure is all there, so i just need to know how to activate internet connection sharing...

Oh and i'm using breezy kubuntu... 

Thank you

PRIAM

---

### Post by spd106 on 2005-11-04
I think the best bet would be to install firestarter. This is a simple firewall that will protect you from the internet, while also allowing you to share internet connections. It's basically a gui front end to iptables.

Alternatively have a look in the /etc/resolv.conf file, there should be a nameserver entry. If you add your ISP's dns server, it should work. 

Good luck

---

### Post by priam on 2005-11-06
Thank you, i will try this tommorow.  

I will post again if i have any difficulties...

Priam

---

### Post by domkle on 2005-11-06
priam
Had the same problem.
The solution is to install bind9. (use synaptic)
Firestarter is a good hint, bind9 is a necessity

Cheers

---

### Post by priam on 2005-11-07
What is bind9 exactly?

Priam

---

### Post by mips on 2005-11-08
[http://www.bind9.net/](http://www.bind9.net/)

Do a search for 'bind' in Synaptic and you wil find it.

---

