---
title: "LTSP Server &amp; Dnsmasq"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by 11seashell11 on 2013-09-06
I have an ltsp server that is running dnsmasq.

My thin clients work great. They get DHCP from my dhcp server, and boot from my ltsp-server with no problem. They also have internet access.

With my ltsp server, I can connect to it with ssh remotely, so it is connected to the internet, but it can't access the internet. sudo apt-get update fails, and so does ping [www.google.com](www.google.com) even though I am connected to the server through ssh over the internet from my home office. If I run sudo /etc/init.d/dnsmasq stop then the internet works fine on the server but as soon as I restart dnsmasq, the internet stops working again.

Here is my /etc/dnsmasq.d/ltsp.conf:

```
# Sample configuration for dnsmasq to function as a proxyDHCP server,# enabling LTSP clients to boot when an external, unmodifiable DHCP
# server is present.
# The main dnsmasq configuration is in /etc/dnsmasq.conf;
# the contents of this script are added to the main configuration.
# You may modify the file to suit your needs.


# Don't function as a DNS server:
port=0


# Log lots of extra information about DHCP transactions.
log-dhcp


# Dnsmasq can also function as a TFTP server. You may uninstall
# tftpd-hpa if you like, and uncomment the next line:
#enable-tftp


# Set the root directory for files available via FTP.
tftp-root=/var/lib/tftpboot


# The boot filename.
dhcp-boot=/ltsp/i386/pxelinux.0


# rootpath option, for NFS
dhcp-option=17,/opt/ltsp/i386


# kill multicast
dhcp-option=vendor:PXEClient,6,2b


# Disable re-use of the DHCP servername and filename fields as extra
# option space. That's to avoid confusing some old or broken DHCP clients.
dhcp-no-override


# PXE menu
pxe-prompt="Press F8 for boot menu", 3


# The known types are x86PC, PC98, IA64_EFI, Alpha, Arc_x86,
# Intel_Lean_Client, IA32_EFI, BC_EFI, Xscale_EFI and X86-64_EFI
pxe-service=X86PC, "Boot from network", /ltsp/i386/pxelinux


# A boot service type of 0 is special, and will abort the
# net boot procedure and continue booting from local media.
pxe-service=X86PC, "Boot from local hard disk", 0


# If an integer boot service type, rather than a basename is given, then the
# PXE client will search for a suitable boot service for that type on the
# network. This search may be done by multicast or broadcast, or direct to a
# server if its IP address is provided.
#pxe-service=x86PC, "Install windows from RIS server", 1


# This range(s) is for the public interface, where dnsmasq functions
# as a proxy DHCP server providing boot information but no IP leases.
# Any ip in the subnet will do, so you may just put your server NIC ip here.
dhcp-range=192.168.1.3,proxy


# This range(s) is for the private network on 2-NIC servers,
# where dnsmasq functions as a normal DHCP server, providing IP leases.
#dhcp-range=192.168.0.20,192.168.0.250,8h


# For static client IPs, and only for the private subnets,
# you may put entries like this:
#dhcp-host=00:20:e0:3b:13:af,10.160.31.111,client111,infinite



```

And, here is /etc/network/interfaces

```
# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto p7p1
iface p7p1 inet static
	address 192.168.1.3
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1



```

How should I set this up so that the LTSP server can access the internet with dnsmasq still running so that it doesn't disrupt the thinclients?

Thank You,
Shelwyn Becker

---

### Post by Emblem Parade on 2013-09-11
I assume by "access the Internet" you specifically mean DNS. In which case, simply enable the "port=0" line and do "sudo service dnsmasq restart". Should start working immediately.

I'd actually prefer a solution where dnsmasq doesn't have to proxy DNS, so I'd be happy if someone posted a better solution.

---

