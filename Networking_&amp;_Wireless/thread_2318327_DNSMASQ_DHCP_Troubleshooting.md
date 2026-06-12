---
title: "DNSMASQ DHCP Troubleshooting"
date: 2016-03-25
forum: Networking &amp; Wireless
---

### Post by dazz100 on 2016-03-25
Hello

I am trying to set up a pxe boot to install linux on an Alix SBC.

This does not require dns.  It does require DHCP and TFTP to work on my desktop.

I can't get dnsmasq configured to provide DHCP addresses.
it seems that dnsmasq doesn't have an option to provide very verbose syslog entries to aid troubleshooting.
If the conf file is wrong, dnsmasq just terminates without giving a reason.

Is there a way of getting more diagnostic messages out of dnsmasq??



I have set a static ip address of 192.168.1.110 which is outside the dynamic range specified in the  dnsmasq conf file.
I have also specified 

Below is my config file.  I have stripped out all of the inactive options.

```
# Configuration file for dnsmasq.
#


# Listen on this specific port instead of the standard DNS port
# (53). Setting this to zero completely disables DNS function,
# leaving only DHCP and/or TFTP.
port=0

# The following two options make you a better netizen, since they
# tell dnsmasq to filter out queries which the public DNS cannot
# answer, and which load the servers (especially the root servers)
# unnecessarily. If you have a dial-on-demand link they also stop
# these requests from bringing up the link unnecessarily.

# Never forward plain names (without a dot or domain part)
domain-needed
# Never forward addresses in the non-routed address spaces.
bogus-priv



# If you don't want dnsmasq to read /etc/resolv.conf or any other
# file, getting its servers from this file instead (see below), then
# uncomment this.
no-resolv

# If you don't want dnsmasq to poll /etc/resolv.conf or other resolv
# files for changes and re-read them then uncomment this.
no-poll


# Uncomment this to enable the integrated DHCP server, you need
# to supply the range of addresses available for lease and optionally
# a lease time. If you have more than one network, you will need to
# repeat this for each network on which you want to supply DHCP
# service.
dhcp-range=192.168.0.200,192.168.0.250,12h


# Set the boot filename for netboot/PXE. You will only need
# this is you want to boot machines over the network and you will need
# a TFTP server; either dnsmasq's built in TFTP server or an
# external one. (See below for how to enable the TFTP server.)
dhcp-boot=pxelinux.0


# Enable dnsmasq's built-in TFTP server
enable-tftp

# Set the root directory for files available via FTP.
tftp-root=/ftpdserver


# Set the limit on DHCP leases, the default is 150
dhcp-lease-max=50

# The DHCP server needs somewhere on disk to keep its lease database.
# This defaults to a sane location, but if you want to change it, use
# the line below.
#dhcp-leasefile=/var/lib/misc/dnsmasq.leases

# Set the DHCP server to authoritative mode. In this mode it will barge in
# and take over the lease for any client which broadcasts on the network,
# whether it has a record of the lease or not. This avoids long timeouts
# when a machine wakes up on a new network. DO NOT enable this if there's
# the slightest chance that you might end up accidentally configuring a DHCP
# server for your campus/company accidentally. The ISC server uses
# the same option, and this URL provides more information:
# http://www.isc.org/files/auth.html
dhcp-authoritative



# For debugging purposes, log each DNS query as it passes through
# dnsmasq.
log-queries

# Log lots of extra information about DHCP transactions.
log-dhcp

```

Below is my log file.

```

Mar 25 12:17:59 odessey NetworkManager[16255]: <warn> (eth1): DHCPv4 request timed out.
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> (eth1): canceled DHCP transaction, DHCP client pid 16295
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> NetworkManager state is now DISCONNECTED
Mar 25 12:17:59 odessey NetworkManager[16255]: <warn> Activation (eth1) failed for connection 'Ethernet connection 1'
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 25 12:17:59 odessey NetworkManager[16255]: <info> (eth1): deactivating device (reason 'none') [0]
Mar 25 12:17:59 odessey avahi-daemon[899]: Withdrawing address record for fe80::96de:80ff:fea4:7913 on eth1.
Mar 25 12:17:59 odessey avahi-daemon[899]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:17:59 odessey avahi-daemon[899]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 25 12:18:00 odessey avahi-daemon[899]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:18:00 odessey avahi-daemon[899]: New relevant interface eth1.IPv6 for mDNS.
Mar 25 12:18:00 odessey avahi-daemon[899]: Registering new address record for fe80::96de:80ff:fea4:7913 on eth1.*.
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Auto-activating connection 'Ethernet connection 1'.
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) starting connection 'Ethernet connection 1'
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> NetworkManager state is now CONNECTING
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> dhclient started with pid 16298
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Beginning IP6 addrconf.
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Mar 25 12:18:02 odessey avahi-daemon[899]: Withdrawing address record for fe80::96de:80ff:fea4:7913 on eth1.
Mar 25 12:18:02 odessey avahi-daemon[899]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:18:02 odessey avahi-daemon[899]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 25 12:18:02 odessey dhclient: Internet Systems Consortium DHCP Client 4.2.4
Mar 25 12:18:02 odessey dhclient: Copyright 2004-2012 Internet Systems Consortium.
Mar 25 12:18:02 odessey dhclient: All rights reserved.
Mar 25 12:18:02 odessey dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 25 12:18:02 odessey dhclient: 
Mar 25 12:18:02 odessey NetworkManager[16255]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Mar 25 12:18:02 odessey dhclient: Listening on LPF/eth1/94:de:80:a4:79:13
Mar 25 12:18:02 odessey dhclient: Sending on   LPF/eth1/94:de:80:a4:79:13
Mar 25 12:18:02 odessey dhclient: Sending on   Socket/fallback
Mar 25 12:18:02 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0xcec4042e)
Mar 25 12:18:03 odessey avahi-daemon[899]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:18:03 odessey avahi-daemon[899]: New relevant interface eth1.IPv6 for mDNS.
Mar 25 12:18:03 odessey avahi-daemon[899]: Registering new address record for fe80::96de:80ff:fea4:7913 on eth1.*.
Mar 25 12:18:05 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4 (xid=0xcec4042e)
Mar 25 12:18:09 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10 (xid=0xcec4042e)
Mar 25 12:18:22 odessey NetworkManager[16255]: <info> (eth1): IP6 addrconf timed out or failed.
Mar 25 12:18:22 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 25 12:18:22 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 25 12:18:22 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 25 12:18:19 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10 (xid=0xcec4042e)
Mar 25 12:18:29 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18 (xid=0xcec4042e)
Mar 25 12:18:47 odessey NetworkManager[16255]: <warn> (eth1): DHCPv4 request timed out.
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> (eth1): canceled DHCP transaction, DHCP client pid 16298
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> NetworkManager state is now DISCONNECTED
Mar 25 12:18:47 odessey NetworkManager[16255]: <warn> Activation (eth1) failed for connection 'Ethernet connection 1'
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 25 12:18:47 odessey NetworkManager[16255]: <info> (eth1): deactivating device (reason 'none') [0]
Mar 25 12:18:47 odessey avahi-daemon[899]: Withdrawing address record for fe80::96de:80ff:fea4:7913 on eth1.
Mar 25 12:18:47 odessey avahi-daemon[899]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:18:47 odessey avahi-daemon[899]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 25 12:18:49 odessey avahi-daemon[899]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:18:49 odessey avahi-daemon[899]: New relevant interface eth1.IPv6 for mDNS.
Mar 25 12:18:49 odessey avahi-daemon[899]: Registering new address record for fe80::96de:80ff:fea4:7913 on eth1.*.
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Auto-activating connection 'Ethernet connection 1'.
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) starting connection 'Ethernet connection 1'
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> NetworkManager state is now CONNECTING
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> dhclient started with pid 16300
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Beginning IP6 addrconf.
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Mar 25 12:18:50 odessey avahi-daemon[899]: Withdrawing address record for fe80::96de:80ff:fea4:7913 on eth1.
Mar 25 12:18:50 odessey avahi-daemon[899]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:18:50 odessey avahi-daemon[899]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 25 12:18:50 odessey dhclient: Internet Systems Consortium DHCP Client 4.2.4
Mar 25 12:18:50 odessey dhclient: Copyright 2004-2012 Internet Systems Consortium.
Mar 25 12:18:50 odessey dhclient: All rights reserved.
Mar 25 12:18:50 odessey dhclient: For info, please visit https://www.isc.org/software/dhcp/
Mar 25 12:18:50 odessey dhclient: 
Mar 25 12:18:50 odessey NetworkManager[16255]: <info> (eth1): DHCPv4 state changed nbi -> preinit
Mar 25 12:18:50 odessey dhclient: Listening on LPF/eth1/94:de:80:a4:79:13
Mar 25 12:18:50 odessey dhclient: Sending on   LPF/eth1/94:de:80:a4:79:13
Mar 25 12:18:50 odessey dhclient: Sending on   Socket/fallback
Mar 25 12:18:50 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3 (xid=0xccc62563)
Mar 25 12:18:52 odessey avahi-daemon[899]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:18:52 odessey avahi-daemon[899]: New relevant interface eth1.IPv6 for mDNS.
Mar 25 12:18:52 odessey avahi-daemon[899]: Registering new address record for fe80::96de:80ff:fea4:7913 on eth1.*.
Mar 25 12:18:53 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4 (xid=0xccc62563)
Mar 25 12:18:57 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5 (xid=0xccc62563)
Mar 25 12:19:02 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9 (xid=0xccc62563)
Mar 25 12:19:10 odessey NetworkManager[16255]: <info> (eth1): IP6 addrconf timed out or failed.
Mar 25 12:19:10 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 25 12:19:10 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 25 12:19:10 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Mar 25 12:19:11 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15 (xid=0xccc62563)
Mar 25 12:19:26 odessey dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13 (xid=0xccc62563)
Mar 25 12:19:35 odessey NetworkManager[16255]: <warn> (eth1): DHCPv4 request timed out.
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> (eth1): canceled DHCP transaction, DHCP client pid 16300
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) started...
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> (eth1): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> NetworkManager state is now DISCONNECTED
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> Marking connection 'Ethernet connection 1' invalid.
Mar 25 12:19:35 odessey NetworkManager[16255]: <warn> Activation (eth1) failed for connection 'Ethernet connection 1'
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0]
Mar 25 12:19:35 odessey NetworkManager[16255]: <info> (eth1): deactivating device (reason 'none') [0]
Mar 25 12:19:35 odessey avahi-daemon[899]: Withdrawing address record for fe80::96de:80ff:fea4:7913 on eth1.
Mar 25 12:19:35 odessey avahi-daemon[899]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:19:35 odessey avahi-daemon[899]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 25 12:19:36 odessey avahi-daemon[899]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:19:36 odessey avahi-daemon[899]: New relevant interface eth1.IPv6 for mDNS.
Mar 25 12:19:36 odessey avahi-daemon[899]: Registering new address record for fe80::96de:80ff:fea4:7913 on eth1.*.
Mar 25 12:19:54 odessey dbus[729]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Mar 25 12:19:54 odessey dbus[729]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar 25 12:19:54 odessey kernel: [ 8835.966222] systemd-hostnamed[16326]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Auto-activating connection 'Ethernet connection 1'.
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) starting connection 'Ethernet connection 1'
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> NetworkManager state is now CONNECTING
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful.
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> (eth1): device state change: config -> ip-config (reason 'none') [50 70 0]
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Beginning IP6 addrconf.
Mar 25 12:20:58 odessey avahi-daemon[899]: Withdrawing address record for fe80::96de:80ff:fea4:7913 on eth1.
Mar 25 12:20:58 odessey avahi-daemon[899]: Leaving mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:20:58 odessey avahi-daemon[899]: Interface eth1.IPv6 no longer relevant for mDNS.
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Mar 25 12:20:58 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) started...
Mar 25 12:20:58 odessey avahi-daemon[899]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.110.
Mar 25 12:20:58 odessey avahi-daemon[899]: New relevant interface eth1.IPv4 for mDNS.
Mar 25 12:20:58 odessey avahi-daemon[899]: Registering new address record for 192.168.1.110 on eth1.IPv4.
Mar 25 12:20:59 odessey NetworkManager[16255]: <info> (eth1): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Mar 25 12:20:59 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 5 of 5 (IPv4 Commit) complete.
Mar 25 12:20:59 odessey NetworkManager[16255]: keyfile: ipv4.address1: address 192.168.1.110/24 gateway 192.168.1.0
Mar 25 12:20:59 odessey NetworkManager[16255]: keyfile: ipv4.address1: address 192.168.1.110/24 gateway 192.168.1.0
Mar 25 12:20:59 odessey NetworkManager[16255]: <info> (eth1): device state change: secondaries -> activated (reason 'none') [90 100 0]
Mar 25 12:20:59 odessey avahi-daemon[899]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::96de:80ff:fea4:7913.
Mar 25 12:20:59 odessey avahi-daemon[899]: New relevant interface eth1.IPv6 for mDNS.
Mar 25 12:20:59 odessey avahi-daemon[899]: Registering new address record for fe80::96de:80ff:fea4:7913 on eth1.*.
Mar 25 12:20:59 odessey NetworkManager[16255]: <info> NetworkManager state is now CONNECTED_GLOBAL
Mar 25 12:20:59 odessey NetworkManager[16255]: <error> [1458861659.647405] [nm-system.c:1090] nm_system_replace_default_ip4_route(): (eth1): failed to set IPv4 default route: -7
Mar 25 12:20:59 odessey NetworkManager[16255]: <info> Policy set 'Ethernet connection 1' (eth1) as default for IPv4 routing and DNS.
Mar 25 12:20:59 odessey NetworkManager[16255]: <info> DNS: starting dnsmasq...
Mar 25 12:20:59 odessey NetworkManager[16255]: <warn> dnsmasq not available on the bus, can't update servers.
Mar 25 12:20:59 odessey NetworkManager[16255]: <error> [1458861659.649010] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Mar 25 12:20:59 odessey NetworkManager[16255]: <warn> DNS: plugin dnsmasq update failed
Mar 25 12:20:59 odessey NetworkManager[16255]: <info> Activation (eth1) successful, device activated.
Mar 25 12:20:59 odessey dbus[729]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Mar 25 12:20:59 odessey dnsmasq[16327]: started, version 2.68 cache disabled
Mar 25 12:20:59 odessey dnsmasq[16327]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth
Mar 25 12:20:59 odessey dnsmasq[16327]: DBus support enabled: connected to system bus
Mar 25 12:20:59 odessey dnsmasq[16327]: warning: no upstream servers configured
Mar 25 12:20:59 odessey dbus[729]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mar 25 12:20:59 odessey NetworkManager[16255]: <warn> dnsmasq appeared on DBus: :1.145
Mar 25 12:20:59 odessey dnsmasq[16327]: setting upstream servers from DBus
Mar 25 12:20:59 odessey dnsmasq[16327]: using nameserver 210.55.111.1#53
Mar 25 12:20:59 odessey dnsmasq[16327]: using nameserver 122.56.237.1#53
Mar 25 12:20:59 odessey ntpdate[16373]: Can't find host ntp.ubuntu.com: Name or service not known (-2)
Mar 25 12:20:59 odessey ntpdate[16373]: no servers can be used, exiting
Mar 25 12:21:18 odessey NetworkManager[16255]: <info> (eth1): IP6 addrconf timed out or failed.
Mar 25 12:21:18 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Mar 25 12:21:18 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Mar 25 12:21:18 odessey NetworkManager[16255]: <info> Activation (eth1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

---

### Post by wankel on 2016-05-13
> **dazz100 said:**
> 
Is there a way of getting more diagnostic messages out of dnsmasq??

I have this option in my dnsmasq.conf:

# Log lots of extra information about DHCP transactions.
log-dhcp

I use tail -f /var/log/syslog to see what happens when I let a system connect. This is what is logged: 


```
# tail -f /var/log/syslog|grep dnsmasq
May 14 00:06:18 fractal dnsmasq-dhcp[14041]: 2935452542 available DHCP range: 192.168.168.20 -- 192.168.168.120
May 14 00:06:18 fractal dnsmasq-dhcp[14041]: 2935452542 client provides name: tp
May 14 00:06:25 fractal dnsmasq-dhcp[14041]: 2935452542 available DHCP range: 192.168.168.20 -- 192.168.168.120
May 14 00:06:25 fractal dnsmasq-dhcp[14041]: 2935452542 client provides name: tp
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 available DHCP range: 192.168.168.20 -- 192.168.168.120
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 client provides name: tp
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 DHCPDISCOVER(eth1) 192.168.168.35 00:23:14:45:25:68
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 tags: eth1
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 DHCPOFFER(eth1) 192.168.168.35 00:23:14:45:25:68
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 requested options: 1:netmask, 28:broadcast, 2:time-offset, 3:router,
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 requested options: 15:domain-name, 6:dns-server, 119:domain-search,
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 requested options: 12:hostname, 44:netbios-ns, 47:netbios-scope,
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 requested options: 26:mtu, 121:classless-static-route, 42:ntp-server,
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 requested options: 121:classless-static-route, 249, 33:static-route,
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 requested options: 252, 42:ntp-server
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 next server: 192.168.168.2
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  1 option: 53 message-type  2
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option: 54 server-identifier  192.168.168.2
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option: 51 lease-time  1h
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option: 58 T1  30m
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option: 59 T2  52m30s
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option:  1 netmask  255.255.255.0
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option: 28 broadcast  192.168.168.255
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option:  6 dns-server  192.168.168.2
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size: 13 option: 15 domain-name  home.local
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option: 42 ntp-server  194.109.6.2
May 14 00:06:41 fractal dnsmasq-dhcp[14041]: 3630791710 sent size:  4 option:  3 router  192.168.168.1
May 14 00:06:45 fractal dnsmasq-dhcp[14041]: 3630791710 available DHCP range: 192.168.168.20 -- 192.168.168.120
May 14 00:06:45 fractal dnsmasq-dhcp[14041]: 3630791710 client provides name: tp
May 14 00:06:45 fractal dnsmasq-dhcp[14041]: 3630791710 DHCPDISCOVER(eth1) 192.168.168.35 00:23:14:45:25:68
```

... and that repeats.  

The laptop will get an IP for a short while, and than loses it again.  It is not working flawlessly yet, but it might help you on your way.

---

