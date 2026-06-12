---
title: "question about openvpn server and client"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by secure bit on 2007-12-15
Hi Guys

I am wondering if anybody here can help ?

I have a LAN , its IP is : 192.168.1.0/255.255.255.0

lets call it  LAN A, now LAN A do not have internet

but there is a server on LAN A that do have internet, its IP is : 192.168.1.55

 I want any pc on LAN A to use internet by connecting over openvpn to the local server at 192.168.1.55

if I was using x509 certificates, then what are the client and server setting that should I have ?

thank you very much for help

---

### Post by andb on 2007-12-16
Sounds to me like what you need is to set the push "redirect-gateway" option.

By googling "openvpn secure internet access" I came up with a few helpful links for you:

[http://www.tweako.com/building_a_cheap_secure_wireless_wlan_infrastructure_with_openvpn_and_linux_an_advanced_tutorial_of_openvpn](http://www.tweako.com/building_a_cheap_secure_wireless_wlan_infrastructure_with_openvpn_and_linux_an_advanced_tutorial_of_openvpn)
[http://www.linux.com/feature/49990](http://www.linux.com/feature/49990)

This second one is with BSD, but the openVPN section is appropriate. They are both about wifi, but are just as appropriate for wired networks also.

Hope this helps, let me know if you need more.

---

### Post by secure bit on 2007-12-18
uh, thanks mate for help

I am about to check the links you've put

---

