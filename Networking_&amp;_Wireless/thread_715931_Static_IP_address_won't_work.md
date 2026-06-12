---
title: "Static IP address won't work"
date: 2008-03-05
forum: Networking &amp; Wireless
---

### Post by SBucher on 2008-03-05
In ubuntu server 6.06.2 server, I am able to grab an address using DHCP and ping anything on my network and the internet.  As soon as I switch it to static (using the config below) and restart the network, I cannot ping anything.  Any ideas?

auto eth0
iface eth0 inet static
  address 172.17.1.8
  netmask 255.2555.255.0
  gateway 172.17.1.10

I can ping the gateway no problem using DHCP and I have other Windows servers using this same gateway, so I have no clue why this will not work.

---

### Post by Eiríkr on 2008-03-05
As a first guess, I'd say it's your bogus netmask -- you've got one too many fives in there.  

> netmask 255.255**_5_**.255.0

HTH,

Eiríkr

---

### Post by drdrewdown on 2008-03-05
if the subnet was just a typo & that doesn't fix it, i would bet its a DNS issue.. have you modified/added DNS servers?

if you can ping

64.233.167.104

but not [www.google.com](www.google.com)

its a dns issue.

modify your /etc/resolv.conf

add open dns servers or your isp's dns servers

opendns servers are
208.67.222.222
208.67.220.220

good luck

---

