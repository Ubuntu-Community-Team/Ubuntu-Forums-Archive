---
title: "internet connection sharing from ubuntu to xp using crossover cable."
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by BilliShere on 2008-06-20
Hi! like the title says i have to ics my ubuntu computer which to my windows xp computer. unfortunately after fooling around a bit it doesnt work.
yes my ubuntu computer contains two ethernet cards, eth0 which is connected to the cable modem and eth1 which connects to the winxp computer via a crossover cable.  

so here's what i did.
i open up network from sytem/administration/network. i set eth0 to dhcp in properties. it was in roaming mode before.

eth1 which was in roaming mode also was then configured to static ip address. ip address was set to 192.168.0.1 and subnet mask to 255.255.255.0. the gateway address was left blank.

then i install firestarter. in its initial run i set eth0 as the internet connection, eth1 as local network and then enable internet connection sharing. 

on the other computer (winxp) under network connections, i set the ipv4 stuff to ip address 192.168.0.2, subnet mask automatically becomes 255.255.255.0 and the gateway is set to 192.168.0.1

it didnt work, after a few restarts of both host and guest, still no internet on the xp computer. so i open up sysctl after some research on ubuntu forums and uncomment out the ipv4 packet forwarding. restarted and still no internet on the xp computer. i run xpantispy and unclick hide computer in network and disable network crawling. still no internet on that computer. i try pinging on the ubuntu computer "ping 192.168.0.2"
and its just hangs on the first line that reads

PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.

--- 192.168.0.2 ping statistics ---
1058 packets transmitted, 0 received, 100% packet loss, time 1058599ms

wth?i have no idea whats going wrong, i even uninstalled firestarter and still no internet on the guest computer. the internet on the ubuntu computer which is directly connected to the internet still works!

given up hope, i turn to ubuntuforums and make this thread to see if someone can help me. 

here below is the important portions of my sysctl file.. i believe it might have something to do with the problem.




---------------------

# Functions previously found in netbase
#

# Comment the next two lines to disable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# This disables TCP Window Scaling ([http://lkml.org/lkml/2008/2/5/167](http://lkml.org/lkml/2008/2/5/167))
#net.ipv4.tcp_syncookies=1
-------------------------------------------

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
# Log Martian Packets
#net/ipv4/conf/all/log_martians = 1
#
# Always defragment packets
#net/ipv4/ip_always_defrag = 1
net.ipv4.ip_forward=1:(:(
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.ip_forward=1

---

### Post by superprash2003 on 2008-06-21
try this [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by BilliShere on 2008-06-21
wow. err. umm...
thats quite complicated.. 

"Its a stupid thing we learned during testing, this will result in a LOT of malfunctions, so make sure you don’t do stupid things like we did!
We tested all of this on a fresh install of Gutsy Server that is fully updated on Feb 20 2008."

and that right there is a deterrent lol.
meh.
i think ill go buy a router. anyone mind referring a good router built for ubuntu? lol
or is there a still a solution to fixing this ics problem?

---

