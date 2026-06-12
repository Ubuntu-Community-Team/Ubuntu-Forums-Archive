---
title: "Can Connect to VPN (PPTP) But Cannot Access Network Resources"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by webmaster_ph on 2008-08-11
hi all,

recently set up a pptp server here at the office so that i can access it from home. i followed these instructions:

[Install PPTP Server - Step 1]("http://ubuntuforums.org/showthread.php?t=826815&highlight=set+vpn")

[Install PPTP Server - Step 2]("http://ubuntuforums.org/showthread.php?t=854660&highlight=pptp+server+install")

[Configure VPN Client]("http://ubuntuforums.org/showthread.php?t=487480&highlight=pptp+server+install")

i can connect to the office network but i cannot access the network resources e.g. nfs shares, other workstations, etc. can somebody point out what's wrong with my setup? below are the configuration files.

```
###############################################################################
# $Id: pptpd.conf 4255 2004-10-03 18:44:00Z rene $
# 
# Sample Poptop configuration file /etc/pptpd.conf
#
# Changes are effective when pptpd is restarted.
###############################################################################

# TAG: ppp
#       Path to the pppd program, default '/usr/sbin/pppd' on Linux
# 
#ppp /usr/sbin/pppd

# TAG: option
#       Specifies the location of the PPP options file.
#       By default PPP looks in '/etc/ppp/options'
#
option /etc/ppp/pptpd-options

# TAG: debug
#       Turns on (more) debugging to syslog
#
#debug

# TAG: stimeout
#       Specifies timeout (in seconds) on starting ctrl connection
#
# stimeout 10

# TAG: noipparam
#       Suppress the passing of the client's IP address to PPP, which is
#       done by default otherwise.
#
#noipparam

# TAG: logwtmp
#       Use wtmp(5) to record client connections and disconnections.
#       
logwtmp

# TAG: bcrelay <if>
#       Turns on broadcast relay to clients from interface <if>
#       
#bcrelay eth1

# TAG: localip
# TAG: remoteip
#       Specifies the local and remote IP address ranges.
#
#       Any addresses work as long as the local machine takes care of the
#       routing.  But if you want to use MS-Windows networking, you should
#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.

#       use IP addresses out of the LAN address space and use the proxyarp
#       option in the pppd options file, or run bcrelay.
#       
#       You can specify single IP addresses seperated by commas or you can
#       specify ranges, or both. For example:
#
#               192.168.0.234,192.168.0.245-249,192.168.0.254
#       
#       IMPORTANT RESTRICTIONS:
#
#       1. No spaces are permitted between commas or within addresses.
# 
#       2. If you give more IP addresses than MAX_CONNECTIONS, it will
#          start at the beginning of the list and go until it gets
#          MAX_CONNECTIONS IPs. Others will be ignored.
#
#       3. No shortcuts in ranges! ie. 234-8 does not mean 234 to 238,
#          you must type 234-238 if you mean this.
#            
#       4. If you give a single localIP, that's ok - all local IPs will
#          be set to the given one. You MUST still give at least one remote
#          IP for each simultaneous client.
#
# (Recommended)
#localip 192.168.0.1
#remoteip 192.168.0.234-238,192.168.0.245
# or
localip 192.168.0.100
remoteip 192.168.0.150-160

```

```
##############################################################################
# $Id: pptpd-options 4643 2006-11-06 18:42:43Z rene $
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
refuse-pap
refuse-chap
refuse-mschap
# Require the peer to authenticate itself using MS-CHAPv2 [Microsoft
# Challenge Handshake Authentication Protocol, Version 2] authentication.
require-mschap-v2
# Require MPPE 128-bit encryption
# (note that MPPE requires the use of MSCHAP-V2 during authentication)
require-mppe-128
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

```

---

### Post by guille79es on 2008-08-12
Hi,
have you try to activate the bcrelay on the private interface?
File pptpd.conf

---

### Post by webmaster_ph on 2008-08-12
no. but according to the instructions, it doesn't need to be.

what's it for?

---

### Post by webmaster_ph on 2008-08-13
ok. so i enabled bcrelay and port forwarding too. but no luck...

does anybody have a short setup instructions out there?

the pptp server is behind a router by the way: d-link di-634m.

---

### Post by crazy_cat on 2008-08-27
still no luck? i've just been SSHing in.  it's more trouble and doesnt reroute all my network traffic.

---

### Post by webmaster_ph on 2008-08-30
finally found the solution! you just have to configure your routing tables after logging into your vpn server. from there you could mount nfs shares, etc. i'll post a short script for this soon. stand by.

---

### Post by michwill on 2009-10-09
> **webmaster_ph said:**
> finally found the solution! you just have to configure your routing tables after logging into your vpn server. from there you could mount nfs shares, etc. i'll post a short script for this soon. stand by.

Any update here?

---

### Post by emjay86 on 2009-11-27
Hi there..

I got the same problem as describes here. Kan i pls see the solution? What route needs to be added?

---

### Post by bdaman80 on 2009-11-28
I have the same problem, could you please elaborate on your solution

---

### Post by shahverdy on 2011-04-01
may be still helpful, I had the same problem and I solved it with the following:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

---

### Post by keithspg on 2011-05-31
tried the iptables line. No dice. 

When I am on the physical network, my shortcuts in nautilus will go to and mount the drives. When I am on the VPN, nothing. In terminal, I can see the shares. Running the standard smb.conf. My workgroup at home is 'workgroup', My domain at work is "Domain"

```
net -l share -S 10.10.1.10
```

shows the network shares

```
smbclient -L 10.10.1.10
```

shows the shares as well and appends:

```
session request to 10.10.1.10 failed (Called name not present)
session request to 10 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
```

I cannot browse anything in Nautilus I cannot connect even on the command line. If I try to connect it on the command line:

```
smbclient //10.10.1.10/Directory
Enter blah's password: 
Domain=[DOMAIN] OS=[Windows Server (R) 2008 Standard 6002 Service Pack 2] Server=[Windows Server (R) 2008 Standard 6.0]
Connection to SERVER-ADMIN failed (Error NT_STATUS_BAD_NETWORK_NAME)
```

this is on 11.04 up to date. I am running samba 3 (not the experimental samba 4). It worked under 10.10.

I have googled and searched and am stumped. 

Any help appreciated.

---

### Post by alcapone-g on 2013-03-04
Once you made vpn connection that is working open shell
and type
smbclient -U user //ip-remote-computer/remote_share
it will ask you for password on remote computer for user on remote computer
after correct password you get
smb> now you type commads you want 
to exit smb> type exit

---

