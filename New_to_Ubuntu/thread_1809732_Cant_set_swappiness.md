---
title: "Cant set swappiness"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by Sergio_ on 2011-07-22
Hi there, I am having problems with setting the swappiness. 
I have tried various methods, like "[I]Using your fav text editor, add vm.swappiness=(desired value) to the bottom of the file /etc/sysctl.conf
save the file and reboot[/I]". Also I have tried with the [SwapFaq]("https://help.ubuntu.com/community/SwapFaq") but then when I boot, the swappiness is in 60 again. What can I do?:confused:

---

### Post by Brushstroke on 2011-07-22
In a Terminal, run this command:

```
sudo gedit /etc/sysctl.conf
```You'll see this file open up: 

```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables.
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

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
#net.ipv6.conf.all.forwarding=1


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Ignore ICMP broadcasts
#net.ipv4.icmp_echo_ignore_broadcasts = 1
#
# Ignore bogus ICMP errors
#net.ipv4.icmp_ignore_bogus_error_responses = 1
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
**vm.swappiness=40**
```That part at the end, **vm.swappiness=40**, is something I added to this file to change my swappiness. Add that line to the file and set the swappiness to whatever you wish. Save it, and reboot. Your changes should be saved. :)

---

### Post by Sergio_ on 2011-07-27
Thx Brushstroke, I did what you said, and then I boot, and its the first time that the value stays!! (I did as root!)

---

### Post by Brushstroke on 2011-07-27
Great! Be sure to mark this thread as SOLVED.

---

