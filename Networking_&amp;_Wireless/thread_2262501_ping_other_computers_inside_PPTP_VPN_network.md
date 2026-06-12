---
title: "ping other computers inside PPTP VPN network"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by ddragas on 2015-01-25
Hi

I'm having trouble connecting to other computers inside PPTP VPN network. I can connect to VPN and ping machine where PPTP server is configured
Alse I've enabled net.ipv4.ip_forward=1 in /etc/sysctl.conf and issued sudo sysctl -p to appy changes

Can pls somebody point me in right direction

kind regards

ddragas

---

### Post by mbenson1000 on 2015-01-25
It's a long shot but when I tried to enable ip4 forwarding I accidently set ip6 forwarding by mistake.  The lines are almost identical in the config file.
It's worth double checking

---

### Post by ddragas on 2015-01-25
here is complete /etc/sysctl.conf  file 


# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See [http://lwn.net/Articles/277146/](http://lwn.net/Articles/277146/)
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#


what else do I have to change to be able to access other computers on network?

---

### Post by ddragas on 2015-01-26
anybody?

---

