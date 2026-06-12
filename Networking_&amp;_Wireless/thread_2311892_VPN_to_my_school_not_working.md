---
title: "VPN to my school not working"
date: 2016-01-30
forum: Networking &amp; Wireless
---

### Post by jacebennest on 2016-01-30
Heyo,

Just having some issue connecting to my school's VPN to do some work. I've attached the instructions i got from my prof. I was able to set it up on my Mac book w/o issue, but can't seem to figure it out. My buddy was having issues with this last semester on Ubuntu. but then said that it randomly worked one time... I'd rather not wait for that.

here's my conf file:

 [connection]
id=OC
uuid=0336be64-3f4e-49cf-907a-94f9ff37e27c
type=vpn
autoconnect=false
permissions=user:my_name:;
secondaries=
timestamp=1453841132

[vpn]
gateway=klo-cis-vpn-1.okanagan.bc.ca
require-mppe=yes
user=300******
refuse-eap=yes
refuse-chap=yes
password-flags=1
refuse-pap=yes
service-type=org.freedesktop.NetworkManager.pptp

[ipv4]
dns-search=
method=auto

[ipv6]
dns-search=
method=auto


Everytime i connect i get connection failed message

Triple checked my username and pwd. like i said, i got it working on my mac. 

Any help would be greatly appreciated!! :)

---

