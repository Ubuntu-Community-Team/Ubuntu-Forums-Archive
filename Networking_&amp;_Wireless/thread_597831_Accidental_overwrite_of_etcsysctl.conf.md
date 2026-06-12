---
title: "Accidental overwrite of /etc/sysctl.conf"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by arpnuke on 2007-10-30
I was following this guide to share my internet connection:  [http://ubuntuforums.org/showthread.php?t=91370&highlight=howto+share+internet+connection]("http://ubuntuforums.org/showthread.php?t=91370&highlight=howto+share+internet+connection")

Rather than open up /etc/sysctl.conf, I put in #echo "net.ipv4.ip_forward = 1" > /etc/sysctl.conf

I used > instead of >> so the file was overwritten.  What package owns that configuration file?  I'm guessing this can be fixed by reinstalling the package that owns that configuration file.  Is there any way for me to determine that package or does anyone know?

---

### Post by kerry_s on 2007-10-30
don't panic, there's nothing important in there, the settings are just commented out.
here's mine->

```

#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# Uncomment the following to stop low-level messages on console
#kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net/ipv4/icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net/ipv4/icmp_ignore_bogus_error_responses = 1
# 
# Do not accept ICMP redirects (prevent MITM attacks)
#net/ipv4/conf/all/accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net/ipv4/conf/all/secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net/ipv4/conf/all/send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net/ipv4/conf/all/accept_source_route = 0
#
# Enable TCP Syn Cookies
#net/ipv4/tcp_syncookies = 1
#
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1


```

---

### Post by arpnuke on 2007-10-30
Thanks for the quick response.  I'm glad to hear that everything is still okay.

---

