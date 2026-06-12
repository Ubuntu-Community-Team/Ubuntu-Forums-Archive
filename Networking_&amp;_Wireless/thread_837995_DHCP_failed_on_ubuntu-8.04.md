---
title: "DHCP failed on ubuntu-8.04"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by cheesewizz on 2008-06-23
Hello there

installation of ubuntu on my desktop was fine.
my purpose of this is to UP the firestarter as my internet sharing with a basic firewall...

the requirements are:

Two Lan Card

eth0 - for ISP IP
eth1 - for internatl ip which is start tom192.168.1.1

1. firestarter - installed
2. DHCP3-Server - Installed
3. webmin for my web administration - installed


but when i try to restart the dhcp3 it gives me an error

Failed to start dhcpd:
Starting DHCP server    dhcpd3----fail!


My config file:

ddns-update-style interim;
ignore client updates;

subnet 192.168.1.0 netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
openton domain-name-servers localhost, localhost2;
option ip-forwarding off;
range dynamic-bootp 192.168.1.2 192.168.1.254;
default-lease-time 21600;
max-lease-time 43200;
}


please anyone can help me...
please please please...

thanks

---

### Post by Webdawgz on 2008-06-23
Why dont you do a static IP address config on the second network card, instead of DHCP.
just as a test.

---

### Post by Iowan on 2008-06-23
> **cheesewizz said:**
> 
My config file:

ddns-update-style interim;
ignore client updates;

subnet 192.168.1.0 netmask 255.255.255.0 {
option routers 192.168.1.1;
option subnet-mask 255.255.255.0;
[COLOR="Red"]openton[/COLOR] domain-name-servers localhost, localhost2;
option ip-forwarding off;
range dynamic-bootp 192.168.1.2 192.168.1.254;
default-lease-time 21600;
max-lease-time 43200;
}

Typo??

---

### Post by cheesewizz on 2008-06-23
> **Webdawgz said:**
> Why dont you do a static IP address config on the second network card, instead of DHCP.
just as a test.

hello

My configuration:
eth0:

from ISP ADDRESS


eth1: second lan card

IP Address: 192.168.1.2
Subnet: 255.255.255.0
gateway: 192.168.1.1
DNS1: 192.168.1.1
DNS2: none


if i do this my internet connection will be disconnect
i dont know why but if i remove the IP address on the 2nd lan card the internet will be resume in a few second...


hmmm very weird...

please need help


thanks

---

