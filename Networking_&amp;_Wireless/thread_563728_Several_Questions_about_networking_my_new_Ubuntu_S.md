---
title: "Several Questions about networking my new Ubuntu Server"
date: 2007-09-30
forum: Networking &amp; Wireless
---

### Post by atjensen11 on 2007-09-30
I have spent many many hours now trying to get this new server up and running.  I have had small victories along the way, but I am still quite frustrated it is taking so long.

**System Description**
Dell computer
640 MB RAM
60 GB HD
one wired network interface card
static IP address of 192.168.100.2
located behind a DSL modem/router with a LAN IP address of 192.168.100.1 (wired)
Webmin is installed and configured
Shorewall is installed and mostly configured
Remote connection through Putty and SSH

**Remainder of Network Description**
Two Windows XP Home PC's
both connected wirelessly to DSL modem/router
dynamic IP addresses assigned through DSL modem/router DHCP
Dynamic DNS services through DynDNS
Static pulic IP address is not possible with my current ISP
DSL router is forwarding ports 22, 80, & 10000 to my Ubuntu server

**Desires for my Server**
Host multiple web sites (Apache virtual servers?)
Host FTP site
Perform network DHCP functions
Not sure if I need DNS server
Samba for file and print shares

**Questions**
Since I have confirmed that I cannot obtain a static public IP address with my current ISP, would I need to maintain a DNS server on my Ubuntu server?  BIND is currently installed, but I have no idea how to configure it.  I have seen many forum posts suggestion DNSMasq as well.

Does Apache's virtual servers require a DNS server to host multiple sites on the same physical machine?

I have installed ddclient to update my DynDNS account.  I have verified this works on a reboot, but how can I determine if it is working as a daemon?

I have Samba installed and somewhat configured.  I can now see the Ubuntu server in the Windows XP Network Neighborhood after opening several Shorewall firewall ports on the server.  However, the Windows machines cannot connect still?

This may be related to lack of DNS or hosts file configuration, but I can ping the server by LAN IP address, but not by server name.

That is probably enough right now.  Please comment where you can and let me know what pitfalls I should try to avoid.

Thanks.

---

### Post by atjensen11 on 2007-10-01
Well, I think I made some progress on my Samba setup.  I was able to successfully share folders from Samba and map them as Mapped Drives on my Windows XP boxes.

I have any issue that when one of the Windows boxes goes to sleep, it appears to loose the connection to Samba.  I am still working on this.

I think the think I would really like to get solved next is the DNS issue.  I am still hoping for comments on which is the easiest package for my network.

Thanks.

---

