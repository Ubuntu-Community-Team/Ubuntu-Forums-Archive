---
title: "DHCP Server struggles"
date: 2014-09-22
forum: Networking &amp; Wireless
---

### Post by vimfuego on 2014-09-22
Hi All,

I'm using Webmin to try to set up Ubuntu 14.04 as a DHCP Server for home, however I am having some issues, when I attempt to start the server via Webmin this is the error...


[FONT=courier new]dhcpd self-test failed. Please fix /etc/dhcp/dhcpd.conf.
The error was: 
/etc/dhcp/dhcpd.conf line 112: subnet 192.168.0.1 netmask 255.255.255.0: bad subnet number/mask combination.
subnet 192.168.0.1 netmask 255.255.255.0 
                                       ^
Configuration file errors encountered -- exiting

Lines around 112 in /etc/dhcp/dhcpd.conf :

#    range 10.0.29.10 10.0.29.230;
#  }
#}
# LAN
subnet 192.168.0.1 netmask 255.255.255.0 {
    option domain-name-servers 192.168.0.1;
    option subnet-mask 255.255.255.0;
    option routers 192.168.0.1;
    range 192.168.0.2 192.168.0.100;[/FONT]

I thought 192.168.0.1 within netmask 255.255.255.0 would be ok.
Any advice would be appreciated.
Thanks.

---

### Post by SeijiSensei on 2014-09-22
The "subnet" is 192.168.0.0 with mask 255.255.255.0; 192.168.0.1 is a "host" address.

---

### Post by vimfuego on 2014-09-24
Oh how silly of me, thanks, that was exactly the issue.

---

