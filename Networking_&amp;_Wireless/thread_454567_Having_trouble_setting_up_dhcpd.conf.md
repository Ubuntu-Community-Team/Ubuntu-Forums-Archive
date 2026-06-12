---
title: "Having trouble setting up dhcpd.conf"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by identitet5000 on 2007-05-25
Yep.. can't seem to figure it out. This is my /etc/dhcpd.conf:


option domain-name "venus.lan";


#option subnet-mask 255.255.255.0;
default-lease-time 600;
max-lease-time 7200;

subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.254;
}

option domain-name-servers 195.54.122.199;
filename "ubuntu/feisty/alternate/install/netboot/pxelinux.0";



but, when executing 
root@venus:/# dhcpd eth0


I get this:

/etc/dhcpd.conf line 12: parameters not allowed after first declaration.
option domain-name-servers 195.54.122.199;
                                          ^
/etc/dhcpd.conf line 13: parameters not allowed after first declaration.
filename "ubuntu/feisty/alternate/install/netboot/pxelinux.0";
                                                             ^
Configuration file errors encountered -- exiting
exiting.



Anyone have a clue? About to go nuts here.. =)

---

### Post by lcomunia on 2007-08-20
May be your problem is that you are trying to set the domain server outside the brackets {}
Here I attaching a working example that can help you out


default-lease-time 10800;
max-lease-time 1814400;

authoritative;

# eth1 subnet configuration
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.150;
  option domain-name-servers 200.71.192.4, 200.71.192.5;
  option domain-name "vgl.cl";
  option routers 192.168.1.254;
  option static-routes 10.35.151.0 192.168.1.230;
  option broadcast-address 192.168.1.255;
}

---

