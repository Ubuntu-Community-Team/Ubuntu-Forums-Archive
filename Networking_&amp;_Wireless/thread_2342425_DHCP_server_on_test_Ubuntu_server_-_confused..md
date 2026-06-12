---
title: "DHCP server on test Ubuntu server - confused."
date: 2016-11-06
forum: Networking &amp; Wireless
---

### Post by JayKay3OOO on 2016-11-06
Hi all.

I'm doing some testing with cobbler deployment server and it uses a dhcp server to give out addresses for clients to then install linux in an unattended manner usig pixe network boot.

I really don't understand what IP addresses I'm supposed to be using. My router already uses dhcp to give IPs to everything on my network.

The internet router gives out internal IP addresses in the range of 192.168.1.0 - 192.168.1.255

How then does the dhcp server installed on the ubuntu server hand out more IP addresses. 

Below is the standard DHCP template for cobbler (I've not changed anything, but it uses the same IP ranges that my router is giving).

subnet 192.168.1.0 netmask 255.255.255.0 {
     option routers             192.168.1.5;
     option domain-name-servers 192.168.1.1;
     option subnet-mask         255.255.255.0;
     range dynamic-bootp        192.168.1.100 192.168.1.254;
     default-lease-time         21600;
     max-lease-time             43200;
     next-server                $next_server;
     class "pxeclients" {

What I don't understand is:

[LIST]
[*]What subnet do I need to use or can I use the same IPs my router is giving out?
[*]What IP address do I need to set for my ubuntu server
[*]How can I use a DHCP server alongside the routers DHCP
[*]For pixe network boot client, can I use the standard 192.168.1 IP (remember the file above was pre-filled with these IP ranges)
[/LIST]

 I hope this made a bit of sense since I've been using dnsmasq as a stop-gap, but since I;m doing a lot of testing I really wanted to understand this.

Thanks.

---

