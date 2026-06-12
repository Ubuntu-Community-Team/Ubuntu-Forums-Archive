---
title: "DHCP configuration"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by Toet on 2007-02-07
solved it! I edited the wrong dhcpd.conf should have done (and did now) /etc/ltsp/dhcpd.conf.

Hi! I'm trying to setup a thin client which will boot of my server (ubuntu 6.10). Following the howto

[ThinClientHowto]("https://help.ubuntu.com/community/ThinClientHowto")

all went well. Accept that I can't start my dhcp3-server. This is normal cause I did not set up my /etc/dhcp3/dhcpd.conf correctly. I trying to do so, but it's not working.

Reading on the internet made me do the following:

added:

INTERFACES="eth0" 

to my /etc/default/dhcp3/dhcp3-server

added:

authoritative;

option domain-name-servers 192.168.1.1

subnet 192.168.1.7 netmask 255.255.255.0 {
        range 192.168.0.200 192.168.0.229;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.1.255;
        option routers 192.168.1.7;
}

to my /etc/dhcp3/dhcpd.conf

my ifconfig shows the following for eth0:

inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0

My server is connected to a broadband modem/router with address 192.168.1.1

Can somebody help me on this one?

---

### Post by Toet on 2007-02-07
solved

---

