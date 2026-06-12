---
title: "how to get pptp clients' IPs into the DNS"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by perler on 2008-03-25
Hi,

i have installed a PPTP server in ubuntu 7.10 to connect with windows clients to it. this works perfect.

for browsing smb shares on the server and on the client machines (which is important) i installed a samba server which works as WINS server, this works fine too.

now, for another service on the VPN, i need to properly resolve the windows machine names by DNS.

on a "real LAN" i would provide the IPs by DHCP and would dynamically update the bind DNS server from DHCP, which is usually a pain in the *** to get working, but in the end is possible.

with the VPN described above i don't know where to begin with to get this working, because there is no DHCP server with which to feed the DNS.

so, i need either 

a) a way to connect the samba WINS server to bind9, because the WINS server already can resolve the windows machine names

or

b) to provide my VPN clients an IP with a regular DHCP server which i suppose is not possible with PPTP(?) - i'm not bound to pptpd, it should just be a a VPN which is natively supported by windows XP/Vista

or

c) ??

any ideas?

PAT

---

