---
title: "Ettercap and ipv4 woes"
date: 2007-11-13
forum: Networking &amp; Wireless
---

### Post by c1rcu17 on 2007-11-13
I'm having a bit of trouble sniffing on my network. I'm trying to see if I can pull my hotmail password using ettercap and ARP poisoning. I can start the MITM attack, but when I start sniffing I get this error. ```
SEND L3 ERROR: 84 byte packet (0800:01) destined to 141.165.5.207 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Operation not permitted)
```
I think I need to enable ipv4 forwarding, and I thought I did that. Here is my sysctl.conf file. ```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
net.ipv6.conf.default.forwarding=1

net/ipv4/ip_forward=1
```

I uncommented the ipv4 line, and added the ```
net/ipv4/ip_forward=1
```line. Any ideas?

---

### Post by c1rcu17 on 2007-11-23
bump?

---

