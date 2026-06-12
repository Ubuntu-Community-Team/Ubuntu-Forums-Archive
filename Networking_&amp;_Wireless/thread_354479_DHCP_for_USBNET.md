---
title: "DHCP for USBNET"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by robotben on 2007-02-06
Hi

I am trying to configure a dhcp server to give an address to the device usb0.

If I modprobe usbnet and plug in my device, usb0 comes up.  I can't seem to get dhcp to work.

here is my dhcp.conf file:

ddns-update-style ad-hoc; 
option subnet-mask 255.255.255.0; 
option broadcast-address 192.168.0.255; 
option routers 192.168.0.1;
option domain-name-servers 192.168.0.1; 
max-lease-time 120; default-lease-time 120;

subnet 192.168.0.0 netmask 255.255.255.0 { 
   range 192.168.0.10 192.168.0.100;
} 

when I try to start the dhcp server, it says that I need to add a subnet.

please help!

---

