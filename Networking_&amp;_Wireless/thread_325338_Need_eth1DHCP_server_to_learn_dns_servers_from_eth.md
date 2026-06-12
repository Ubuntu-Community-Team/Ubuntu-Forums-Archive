---
title: "Need eth1:DHCP server to *learn* dns servers from eth0:DHCP client"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by drokmed on 2006-12-25
Greetings,

I'm building a basic firewall with two nics.

Eth0 points to the WAN/Internet, uses dhcp client to get IP info, dns info, etc.

Eth1 points to internal LAN, is static, and provides dhcp services

If I *manually* plug in the dns server addresses, it works.  Here is my  /etc/network/interfaces

option domain-name "changedjustforhere.com";
option domain-name-servers 68.238.112.12, 68.238.96.12;
option routers 192.168.1.1;
default-lease-time 86400;
ddns-update-style none;
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.100 192.168.1.199;
  default-lease-time 14400;
  max-lease-time 172800;
}

My question: is there a way for the dhcp server to *learn* the dns server addresses, and use them automatically?

Can I do this without installing bind9, or do I have to build a local dns server to get what I want.

Thanks for reading,

Daryl

---

### Post by Rippey on 2006-12-25
this could be a silly question, but why should your dhcp server know your dns addresses?
as far as I know a dhcp server only give out ip addresses to al the hosts on your lan and provides them with a defaultgateway address.
I could be wrong though.
post some more specific details on what you're trying to acomplish and I'll have a look. :)

---

### Post by drokmed on 2006-12-26
A dhcp server provides an IP address, netmask, broadcast, default route, dns server addresses (for domain name resolution)

The server learns the dns addresses from the dhcp client on eth0.  I want the dhcp server to use the addresses it learns, as opposed to manually adding them in.  There must be a way, I just haven't figured it out yet.

---

### Post by Rippey on 2006-12-26
try putting the default gateway in as dns, if your router is configured right it should put the dnsrequests trough to the right server.

---

