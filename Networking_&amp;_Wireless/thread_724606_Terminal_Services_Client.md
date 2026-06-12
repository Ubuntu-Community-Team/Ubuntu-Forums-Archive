---
title: "Terminal Services Client"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by WildeBeest on 2008-03-14
I have a problem with the Terminal Services Client. When I try to connect it fails with a Unable to resolve host error.

I can see the windows nodes with the File Browser.

I entered the fields as follows:

Computer: [COLOR="Navy"]Name of my windows machine.[/COLOR]
Protocol: [COLOR="Navy"]RDP[/COLOR]
User name: [COLOR="Navy"]login name[/COLOR]
Password:[COLOR="Navy"] ********[/COLOR]
Domain: [COLOR="Navy"]Blank - since I use a workgroup[/COLOR]
Client Hostname: Ubuntu machine name.


I can connect when I enter the IP address. Since the windows boxes I'm using obtain their IP addresses via DHCP using them is not an option.

How can I connect using the machine name?

---

### Post by pana.corbului on 2008-03-15
You could try using reservations in dhcp server for those machines and use ip.

---

### Post by koenn on 2008-03-15
you need some sort of name resolution. What do you use for dhcp and dns ?

---

### Post by WildeBeest on 2008-03-15
Linksys wireless access point and router.

---

### Post by koenn on 2008-03-15
Apparently it does only DNS forwarding and doesn't offer name resolution of addresses its dhcp server handed out, or you wouldn't have a problem.


1-
If it supports dhcp reservations (check the config web interface or a user guide) you can assign fixed addresses to the relevant hosts, and rdp them via ip address (as suggested before), or list the addresses and names in the /etc/hosts file of the macvhines you rdp from. 

2-
A slightly more elaborate, but more convenient solution is to run your own dhcp and dns server. you could e.g. install dnsmasq on a spare pc. as a dhcp server, dnsmasq hands out IP addresses, and remembers the hostnames it gave the address to. As a dns server, it will translate names back to addresses. 
You would configure dnsmas to
- do dhcp
- do dns for your LAN; automatically for dhcp-hosts, from its hosts file for LAN hosts with static addresses
- forward dns requests that it can't annswer (internet hosts) to your ISP DNS or a service such as OpenDNS

The computers on your LAN would have to be configured to use the dnsmasq server as DNS server, but that's something that can be handled through dhcp

you'd have to disable the dhcp server on your router, because you can't have 2 competing dhcpservers on a network. 

This also means the PC running dnsmasq will have to be always on, so other computers can get dns and dhcp service from it.


3-
on some linksys routers you can install linux and other software, so you could actually run dnsmasq on the router; same sollution, but without the extra PC

---

