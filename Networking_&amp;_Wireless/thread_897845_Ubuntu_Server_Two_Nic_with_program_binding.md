---
title: "Ubuntu Server Two Nic with program binding"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by brady@wisc on 2008-08-22
I am running Ubuntu Server 8.04.  Here is the ideology of what I want to do.  I want a samba share over one nic only and ssh/ftp over the other nic only.  Both of the nics are on the same ip range and same gateway.  

I have Dell PowerEdge with dual 10/100/1000 nics.  I have both of these nics setup with static IP addresses (192.168.1.248 & 192.168.1.246). Although, they seem not to be setup correctly because both of the ip address go through the same nic. I want to be able to access my Samba shares through the 192.168.1.246 nic only.  On the other nic, 192.168.1.248, I want to be able to access SSH/proftpd.  I already have configured SSH to work only on 192.168.1.248, but cannot get proftpd or samba to do the same. 

Here is my network interface config file:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.248
gateway 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

# The secondary network interface

auto eth1
iface eth1 inet static
address 192.168.1.246
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

Here is my resolv.conf file:
search mshome.net
nameserver 192.168.1.1

---

### Post by simpleone on 2008-08-22
for Samba:
[http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BINDINTERFACESONLY](http://us1.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#BINDINTERFACESONLY)

---

### Post by simpleone on 2008-08-22
for proftpd:
[http://www.proftpd.org/docs/directives/linked/config_ref_DefaultAddress.html](http://www.proftpd.org/docs/directives/linked/config_ref_DefaultAddress.html)
[http://www.proftpd.org/docs/directives/linked/config_ref_VirtualHost.html](http://www.proftpd.org/docs/directives/linked/config_ref_VirtualHost.html)

---

