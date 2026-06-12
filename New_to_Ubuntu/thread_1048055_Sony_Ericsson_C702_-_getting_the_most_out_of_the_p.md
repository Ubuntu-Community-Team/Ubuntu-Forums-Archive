---
title: "Sony Ericsson C702 - getting the most out of the phone on Ubuntu"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by scorpfromhell on 2009-01-23
Hi all,

I have been trying to use my Sony Ericsson C702 to the maximum functionality possible on Ubuntu, but was rather restricted to mere transfer of the media files in the "Media Transfer" mode of C702 (you get this as soon as you connect the phone to the computer via USB).

"Phone Mode" allows using the phone as a Mobile Broadband modem for the computer, but somehow I have not been successful in making use of the internet connection on my computer for connecting C702 to the internet rather than via GPRS. It should be possible when the following setting is chosen on C702 but does not happen.

```
 Menu -> Settings -> Connectivity -> USB -> USB Network -> USB network type -> Via computer 
```

Also, I have been successful in using C702 as a Mass Storage Media by using the workaround provided in [this post]("http://ubuntuforums.org/showpost.php?p=6513274&postcount=75"). But am unable to manage podcasts. I use gtkpod for my iPod, but that doesn't recognize C702, nor does Rhythmbox. I have to manually manage my podcast files now. :(

I haven't tried bluetooth/obex since I gather that there are some bugs which are being worked upon.

I haven't tried wammu/gammu for syncing my contacts, tasks, etc.

I have setup Viking to make use of the GPS files captured by the GPS Tracker app in C702. Viking allows overlaying the route we have captured with maps from various sources including Google Maps.

So if somebody knows 
[LIST]
[*]how to make use of the USB network for connecting C702 to the internet available on the computer's LAN
[*]an app to manage the podcasts
[/LIST]
it would be most helpful :)

Thanks in anticipation!

Regards,
Prem
[http://scorpfromhell.blogspot.com](http://scorpfromhell.blogspot.com)

---

### Post by StefanPieter on 2009-05-03
I chose

Menu -> Settings -> Connectivity -> USB -> USB Network -> USB network type -> Phone as modem

and it worked like a charm.

---

### Post by freddano on 2009-08-31
Your phone needs to be in "phone-mode" (or whatever the term is in english) 

After that you need to set up a dhcp-server on the ubuntu-computer. 

Set up a static, private ip-number on usb0, for example 192.168.0.1

Then set up a dhcp-server to answer requests on usb0. Here is my configfile.

/etc/dhcp3/dhcpd.conf
#Begin /etc/dhcp3/dhcpd.conf

ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
    option routers 192.168.0.1;
    option subnet-mask 255.255.255.0;
    option domain-name-servers 130.238.4.133;
    option ip-forwarding off;
    range dynamic-bootp 192.168.0.100 192.168.0.254;
    default-lease-time 21600;
    max-lease-time 43200;
}
# End dhcpd.conf

Connect the phone and start the dhcp3-server. 

You can try if it works by doing a broadcast-ping.

$ ping -b 192.168.0.255

WARNING: pinging broadcast address
PING 192.168.0.255 (192.168.0.255) 56(84) bytes of data.
64 bytes from 192.168.0.100: icmp_seq=1 ttl=64 time=2.64 ms

After that you need to set up the computer as a NAT.
Make sure you clean out any old rules.

# The following needs to be done as root. sudo /bin/bash or something.

iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT

#Next, set up the NAT.

#!/bin/sh
#
# this script requires iptables package to be
# installed on your machine


# Where to find iptables binary
IPT="/sbin/iptables"

# The network interface you will use
# WAN is the one connected to the internet
# LAN the one connected to your local network
WAN="eth0"
LAN="usb0"
# First we need to clear up any existing firewall rules
# and chain which might have been created
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X

# Default policies: Drop any incoming packets
# accept the rest.
$IPT -P INPUT ACCEPT #If this isn't here you won't be able to access internet on the # linux-machine
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT

# To be able to forward traffic from your LAN
# to the Internet, we need to tell the kernel
# to allow ip forwarding
echo 1 > /proc/sys/net/ipv4/ip_forward

# Masquerading will make machines from the LAN
# look like if they were the router
$IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE

# Accept any connections from the local machine
$IPT -A INPUT -i lo -j ACCEPT
# plus from your local network
$IPT -A INPUT -i $LAN -j ACCEPT


#After this, you should be able to use the internet-features of your phone without using #3g/GSM/EDGE or whatever, but instead use your computers internet connection. 
#Of course, you need to change these settings to 
Hope this helps.

---

### Post by ElSlunko on 2009-09-18
Any progress on finding something for podcasts? I just bought a sony phone this week and have been playing around with the features and noticed a section for podcasts in the menu system.

My phone model is w518i.

---

