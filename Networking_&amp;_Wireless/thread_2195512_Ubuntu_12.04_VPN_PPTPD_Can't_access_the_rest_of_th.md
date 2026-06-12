---
title: "Ubuntu 12.04 VPN PPTPD Can't access the rest of the network"
date: 2013-12-24
forum: Networking &amp; Wireless
---

### Post by network2 on 2013-12-24
Okay for starters I'm kind of new to Ubuntu Server. I've been using Red Hat / CentOS for many years and I have to say. I'm loving Ubuntu. The Package thats included stock are awesome!

Anyways I have tried this on different machines. (All of them running Ubuntu 12.04 Server). 

I can connect to the VPN but I am not able to see the rest of the network. Here is what I have.

/etc/pptpd.conf
----
###############################################################################
# $Id$
#
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################

# TAG: ppp
#    Path to the pppd program, default '/usr/sbin/pppd' on Linux
#
#ppp /usr/sbin/pppd

# TAG: option
#    Specifies the location of the PPP options file.
#    By default PPP looks in '/etc/ppp/options'
#
option /etc/ppp/pptpd-options

# TAG: debug
#    Turns on (more) debugging to syslog
#
#debug

# TAG: stimeout
#    Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#    Use wtmp(5) to record client connections and disconnections.
#
logwtmp

# TAG: bcrelay <if>
#    Turns on broadcast relay to clients from interface <if>
#
#bcrelay eth1

# TAG: localip
# TAG: remoteip
#    Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#
#    You can specify single IP addresses seperated by commas or you can
#    specify ranges, or both. For example:
#
#        192.168.0.234,192.168.0.245-249,192.168.0.254
#
#    IMPORTANT RESTRICTIONS:
#
#    1. No spaces are permitted between commas or within addresses.
#
#    2. If you give more IP addresses than MAX_CONNECTIONS, it will
#       start at the beginning of the list and go until it gets 
#       MAX_CONNECTIONS IPs. Others will be ignored.
#
#    3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#       you must type 234-238 if you mean this.
#
#    4. If you give a single localIP, that's ok - all local IPs will
#       be set to the given one. You MUST still give at least one remote
#       IP for each simultaneous client.
#
# (Recommended)
localip 192.168.7.200
remoteip 192.168.7.101-150
# or
#localip 192.168.0.234-238,192.168.0.245
#remoteip 192.168.1.234-238,192.168.1.245
----


/etc/ppp/pptpd-options 

-----
###############################################################################
# $Id$
#
# Sample Poptop PPP options file /etc/ppp/pptpd-options
# Options used by PPP when a connection arrives from a client.
# This file is pointed to by /etc/pptpd.conf option keyword.
# Changes are effective on the next connection.  See "man pppd".
#
# You are expected to change this file to suit your system.  As
# packaged, it requires PPP 2.4.2 and the kernel MPPE module.
###############################################################################


# Authentication

# Name of the local system for authentication purposes 
# (must match the second field in /etc/ppp/chap-secrets entries)
name pptpd

# Optional: domain name to use for authentication
# domain mydomain.net

# Strip the domain prefix from the username before authentication.
# (applies if you use pppd with chapms-strip-domain patch)
#chapms-strip-domain


# Encryption
# Debian: on systems with a kernel built with the package
# kernel-patch-mppe >= 2.4.2 and using ppp >= 2.4.2, ...
# {{{
#refuse-pap
#refuse-chap
#refuse-mschap
# Require the peer to authenticate itself using MS-CHAPv2 [Microsoft
# Challenge Handshake Authentication Protocol, Version 2] authentication.
#require-mschap-v2
# Require MPPE 128-bit encryption
# (note that MPPE requires the use of MSCHAP-V2 during authentication)
#require-mppe-128
# }}}




# Network and Routing

# If pppd is acting as a server for Microsoft Windows clients, this
# option allows pppd to supply one or two DNS (Domain Name Server)
# addresses to the clients.  The first instance of this option
# specifies the primary DNS address; the second instance (if given)
# specifies the secondary DNS address.
# Attention! This information may not be taken into account by a Windows
# client. See KB311218 in Microsoft's knowledge base for more information.
#ms-dns 10.0.0.1
#ms-dns 10.0.0.2
ms-dns 8.8.8.8
ms-dns 8.8.4.4

# If pppd is acting as a server for Microsoft Windows or "Samba"
# clients, this option allows pppd to supply one or two WINS (Windows
# Internet Name Services) server addresses to the clients.  The first
# instance of this option specifies the primary WINS address; the
# second instance (if given) specifies the secondary WINS address.
#ms-wins 10.0.0.3
#ms-wins 10.0.0.4

# Add an entry to this system's ARP [Address Resolution Protocol]
# table with the IP address of the peer and the Ethernet address of this
# system.  This will have the effect of making the peer appear to other
# systems to be on the local ethernet.
# (you do not need this if your PPTP server is responsible for routing
# packets to the clients -- James Cameron)
proxyarp

# Debian: do not replace the default route
nodefaultroute


# Logging

# Enable connection debugging facilities.
# (see your syslog configuration for where pppd sends to)
#debug

# Print out all the option values which have been set.
# (often requested by mailing list to verify options)
#dump


# Miscellaneous

# Create a UUCP-style lock file for the pseudo-tty to ensure exclusive
# access.
lock

# Disable BSD-Compress compression
nobsdcomp 

-----

# cat /etc/sysctl.conf | grep net.ipv4.ip_forward=
----
net.ipv4.ip_forward=1
----

cat /etc/rc.local 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
exit 0


Any help would be great.

---

### Post by network2 on 2013-12-24
Update: Does work if you add a route to the client side. How do I avoid having to add route on every client?

---

