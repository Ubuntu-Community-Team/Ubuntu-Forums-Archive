---
title: "VPN Problems"
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by slonnik on 2006-10-27
Colleagues, i tried to establish vpn connection but failed. I keep establishing for several weeks, i don't wanna loose beautfull ubuntu please help.

Providers data

my IP 172.19.104.185
default gateway 172.19.104.1
network mask 255.255.255.0
DNS: 195.128.64.3
DNS: 194.87.0.9
VPN: 172.19.104.1


options.pptp
###############################################################################
# $Id: options.pptp,v 1.1 2005/02/18 01:40:23 quozl Exp $
#
# Sample PPTP PPP options file /etc/ppp/options.pptp
# Options used by PPP when a connection is made by a PPTP client.
# This file can be referred to by an /etc/ppp/peers file for the tunnel.
# Changes are effective on the next connection.  See "man pppd".
#
# You are expected to change this file to suit your system.  As
# packaged, it requires PPP 2.4.2 or later from [http://ppp.samba.org/](http://ppp.samba.org/)
# and the kernel MPPE module available from the CVS repository also on
# [http://ppp.samba.org/](http://ppp.samba.org/), which is packaged for DKMS as kernel_ppp_mppe.
###############################################################################

# Lock the port
lock

# Authentication
# We don't need the tunnel server to authenticate itself
noauth

# We won't do EAP, CHAP, or MSCHAP, but we will accept MSCHAP-V2
#refuse-eap
#refuse-chap
#refuse-mschap

# Compression
# Turn off compression protocols we know won't be used
#nobsdcomp
#nodeflate

# Encryption
# (There have been multiple versions of PPP with encryption support,
# choose with of the following sections you will use.  Note that MPPE
# requires the use of MSCHAP-V2 during authentication)

# [http://ppp.samba.org/](http://ppp.samba.org/) the PPP project version of PPP by Paul Mackarras
# ppp-2.4.2 or later with MPPE only, kernel module ppp_mppe.o
# {{{
# Require MPPE 128-bit encryption
#require-mppe-128
# }}}

# [http://polbox.com/h/hs001/](http://polbox.com/h/hs001/) fork from PPP project by Jan Dubiec
# ppp-2.4.2 or later with MPPE and MPPC, kernel module ppp_mppe_mppc.o
# {{{
# Require MPPE 128-bit encryption
#mppe required,stateless
# }}}

&#1092;&#1072;&#1081;&#1083; &#1086;&#1087;&#1080;&#1089;&#1099;&#1074;&#1072;&#1102;&#1097;&#1080;&#1081; &#1090;&#1091;&#1085;&#1077;&#1083;&#1100; /etc/ppp/peers/vpn

defaultroute
pty "pptp 172.19.104.1 --nolaunchpppd"
name j600h27
remotename PPTP
file /etc/ppp/options.pptp
ipparam vpn
deflate 15,15

&#1092;&#1072;&#1081;&#1083; interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 172.19.104.185
netmask 255.255.255.0
up route add -net 172.19.0.0 netmask 255.255.0.0 gw 172.19.104.1 dev eth0
dns-nameservers 195.128.64.3


before calling pon vpn, command route shows the following

root@slonnik:/home/slonnik# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.19.104.0    *               255.255.255.0   U     0      0        0 eth0
172.19.0.0      172.19.104.1    255.255.0.0     UG    0      0        0 eth0

i succeeded to ping gateway and vpn server

after calling pon vpn route shows (by the way when i call route system hangs up for a while)

root@slonnik:/home/slonnik# pon vpn
root@slonnik:/home/slonnik# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.19.104.1    *               255.255.255.255 UH    0      0        0 ppp0
172.19.104.0    *               255.255.255.0   U     0      0        0 eth0
172.19.0.0      172.19.104.1    255.255.0.0     UG    0      0        0 eth0
default         *               0.0.0.0         U     0      0        0 ppp0

failed to ping sutes
root@slonnik:/etc/init.d# ping [www.ru](www.ru)
ping: unknown host [www.ru](www.ru)

when i ping ip not host ([www.ru](www.ru)) it fails again.

Pleeeeeease help me #-o

---

### Post by slonnik on 2006-10-27
pleeease help me ](*,)

---

### Post by slonnik on 2006-10-27
sorry for moving up message

---

### Post by patrick295767 on 2006-11-01
Try mb the packages knet ; kvpnc ... : 
apt-get -f install knet kvpnc

Good luck

Greetings

---

