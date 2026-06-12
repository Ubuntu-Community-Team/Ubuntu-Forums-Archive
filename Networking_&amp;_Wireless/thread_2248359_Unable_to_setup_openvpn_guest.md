---
title: "Unable to setup openvpn guest"
date: 2014-10-14
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2014-10-14
In the past I have been able to openvpn book with ease. In UbuntuGnome 14.04 I am having difficulty because creating a new vpn connection is not bringing up the template that needs to take the certificate locations. Instead all I get is the drop down box offering me to select the interface to use only  VPN. If I choose to create it  PPTP is offered or the import of a vpn configuration, despite having installed     " sudo apt-get install openvpn".

How do I get the correct template to present itself for openvpn to be created?

---

### Post by weatherman2 on 2014-10-14
Have you installed

```

network-manager-openvpn-gnome
network-manager-openvpn

```

?

---

### Post by Robbyx on 2014-10-14
That was the cause. Thank you.

---

