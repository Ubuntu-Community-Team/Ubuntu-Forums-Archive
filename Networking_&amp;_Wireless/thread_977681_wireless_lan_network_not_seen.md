---
title: "wireless lan network not seen"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by carlosap on 2008-11-10
Hi all

I've been having problems with a wireless network i want to make

I got a pc with an ethernet card (eth0) connected to internet, and an usb wireless card (wlan0) which is supposed to be the gateway for the network.
Additionally i got a laptop with a wireless card (ath0)

My main goal is the laptop to connect to the pc using xsupplicant, but for now, the laptop doesn't even find the pc wifi card
The optional but desirable goal is to share the internet connection
This is my configuration for both computers, maybe you can see what i'm doing wrong 

------------------------------------------------

Configuration for PC:

wired connection:
eth0 ip: 172.24.9.166

wireless usb stick:
wlan0 ip: 192.168.80.1
mask: 255.255.255.0
gw: 172.24.9.166

using wep key in ascii, and the essid: "test-network"


Routes:

route del -net 192.168.80.0 gw 0.0.0.0 netmask 255.255.255.0  #delete the default route
route add -net 192.168.80.0 gw 192.168.80.1 netmask 255.255.255.0 #add the route to the mother network


Enabling the ipv4 forwarding:
modprobe iptable_nat
/sbin/sysctl -w net.ipv4.ip_forward=1
echo "1" > /proc/sys/net/ipv4/conf/default/rp_filter


Nat and iptables:

iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o wlan0 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i wlan0 -o eth0 -j ACCEPT
iptables -A FORWARD -j LOG

------------------------------

Configuration for the laptop

wireless in roaming mode

i can't find the pc in the wi-fi connection listing, and when i set it to connect to "test-network" with the wep key and all; the laptop just add it to the list and keep asking for the wep key, just like connecting to a "whatever-network"

-----------------------------

I've tried with firestarter, and with a static ip in the laptop 
say "192.168.80.20" or something, without luck



Thanks for your time

---

