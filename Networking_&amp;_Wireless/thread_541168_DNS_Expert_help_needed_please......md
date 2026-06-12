---
title: "DNS Expert help needed please....."
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by Pinnocchio on 2007-09-02
OK  Here's the deal.

I am trying to configure one of my machines to be a DNS and DHCP server (so thereby effectively a DDNS server), I'm doing this as an excercise in understanding as well as managing my network easier.

I have named working fine and have managed to configure DNS resolution somewhat, however I either am not understanding something or am missing something.

What I want to do is as follows:-

Server serves DHCP address's to machines on the LAN.  Most of the machines on the LAN get served a fixed IP address as specified in the dhcpd.conf file.  This address should then be passed to the DNS part of the server (on the same box) and the DNS server should then be able to respond to nslookup requests with the correct response.  Reverse DNS lookups should also work correctly.

So far I've only been able to get nslookup to respond to address's that have been hard entered into the DNS server (I'm using webmin to manage the DNS server), reverse address's also have to be hard entered into the DNS server.  I cannot get DHCP address's that have been issued to automatically get registered in the DNS server.

I've read the two following documents extensively and played with this for about a week...but have now hit a brick wall.

[http://swelltech.com/support/webminguide/ch08.html#figbindcreateslave](http://swelltech.com/support/webminguide/ch08.html#figbindcreateslave)

[http://ops.ietf.org/dns/dynupd/secure-ddns-howto.html](http://ops.ietf.org/dns/dynupd/secure-ddns-howto.html)

Can someone who has extensive experience of configuring this stuff please tell me:-

1.  Should reverse address's automatically get set up by the DNS server (Bind9)?  If so how?

2.  What on earth do I need to do to get an address that's hard coded in the dhcpd.conf file to hand off the details to the DNS server so I don't have to hard code it again.

HELP!!!!

---

### Post by Pinnocchio on 2007-09-03
bump

any help gratefully received

---

