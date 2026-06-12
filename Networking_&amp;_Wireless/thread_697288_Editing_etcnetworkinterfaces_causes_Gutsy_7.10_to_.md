---
title: "Editing /etc/network/interfaces causes Gutsy 7.10 to crash"
date: 2008-02-15
forum: Networking &amp; Wireless
---

### Post by peterbe on 2008-02-15
I have Gutsy 7.10 installed in a Averatec 3280 laptop, and have been trying to configure /etc/network/interfaces for various locations, so I can select them either manually or by automatic detection of the networks. (I want fixed IP's or dhcp address detection in various locations, specific ESSID's in some locations, special routing in some locations, etc.) This has worked in earlier versions of Ubuntu, on the same computer.

The problem I am having is that when the interfaces file is written, very often the system crashes with I blank screen. I have tried using ifdown plus stopping the network daemon (/etc/init.d/networking stop) in various combinations, but most of the time the system crashes. This happens either when I edit the file with gedit or vi, or when I edit a copy of the file, then copy it to interfaces.

Right now, what I am doing is adding some lines to /etc/init.d/networking to do that copy in the "start)" case. Then if I stop and start networking the new version of the file will get copied; I have to be careful to shut down the interface in use first.

Obviously, this is not normal behavior, and it makes modification of /etc/network/interfaces very difficult.

---

### Post by Phulerock on 2008-02-15
Coud you show me you /etc/network/interface file with your fixed ip configuration.

---

### Post by peterbe on 2008-02-15
Here is the /etc/network/interfaces file. However, the editing problem
occurs with much simpler interfaces files. I have a user script which
enables me to select any of the stanzas below manually.

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo ath0
iface lo inet loopback

# The primary network interface

# this defines the default selection when booting
mapping ath0
        script /usr/local/sbin/echo-ath0-home

iface ath0-home inet static
        address 192.168.2.13
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        up route add -host 208.201.231.80 gw 192.168.2.3
        up route add -host 208.201.231.82 gw 192.168.2.3
        dns-nameservers 192.168.2.201
        dns-search belew
        wireless-essid yyyyyyyyyyy
        wireless-key xxxxxxxxxxxxxx

iface ath0-ucsc inet dhcp
        wireless-essid cruznet

iface ath0-dhcp inet dhcp

iface ath0-pizza inet dhcp
        wireless-essid PacificAvePizza

iface eth0-home inet static
        address 192.168.2.13
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1
        up route add -host 208.201.231.80 gw 192.168.2.3
        up route add -host 208.201.231.82 gw 192.168.2.3
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.2.201
        dns-search belew


iface eth0-dhcp inet dhcp


This is my script for selecting interfaces and their attributes as
defined in the interfaces file:

#!/bin/bash
echo "Select LAN/Wireless connection"

n=1
while [ x$n != "xq" ]
do
echo "Connect to:"
echo -n " h:ath0-home u:ath0-ucsc d:ath0-dhcp e:eth0-home p:Pizza E:eth0-dhcp q:exit"
echo -n ": "
  read n rest
  case "$n" in
    h)
      echo Home Wireless on ath0
      sudo ifdown eth0
      sudo ifdown ath0
      sudo ifup ath0=ath0-home
      ;;
    u)
      echo UCSC Wireless on ath0
      sudo ifdown eth0
      sudo ifdown ath0
      sudo ifup ath0=ath0-ucsc
      ;;
    p)
      echo Pac.Pizza Wireless on ath0
      sudo ifdown eth0
      sudo ifdown ath0
      sudo ifup ath0=ath0-pizza
      ;;
    d)
      echo Wireless - dhcp
      sudo ifdown eth0
      sudo ifdown ath0
      sudo ifup ath0=ath0-dhcp
      ;;
    e)
      echo Home LAN - static
      sudo ifdown eth0
      sudo ifdown ath0
      sudo ifup eth0=eth0-home
      ;;
    E)
      echo Home LAN - dhcp
      echo Home LAN - static
      sudo ifdown eth0
      sudo ifdown ath0
      sudo ifup eth0=eth0-dhcp
      ;;
    *)
      n=q
      ;;
  esac

done

This works fine.

---

### Post by peterbe on 2008-02-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/192252](https://bugs.launchpad.net/ubuntu/+bug/192252) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have appended a link to my report of this bug on Launchpad.

---

