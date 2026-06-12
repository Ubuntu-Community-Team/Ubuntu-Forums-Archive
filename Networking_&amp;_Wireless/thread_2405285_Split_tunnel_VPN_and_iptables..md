---
title: "Split tunnel VPN and iptables."
date: 2018-11-03
forum: Networking &amp; Wireless
---

### Post by undeadmechanic on 2018-11-03
This is my first post here in 6 years(!) and I am chasing after some assistance with iptables. First up, I must admit that networking is very much NOT my area of expertise, so please forgive my ignorance.

My setup:

Ubuntu server 18.04 LTS
Split tunnel via OpenVPN
Only deluge daemon and web-ui daemon running as vpn user.
I have nginx reverse proxy to allow access to the deluge web-ui (which I won't really need if I can get this to work).

I followed this [guide]("https://www.htpcguides.com/force-torrent-traffic-vpn-split-tunnel-debian-8-ubuntu-16-04/") when configuring this and had to make adjustments for several differences, but everything is working beautifully so far. However, I need to be able to access the deluge daemon via the thin client/GTK UI from outside my LAN.

Here is a paste of  /etc/openvpn/iptables.sh

```
#! /bin/bash
# Niftiest Software – www.niftiestsoftware.com
# Modified version by HTPC Guides – www.htpcguides.com

export INTERFACE="tun0"
export VPNUSER="vpn"
export LOCALIP="[COLOR=#3366ff]192.168.1.0/24[/COLOR]"
export NETIF="[COLOR=#ff0000]enp4s0[/COLOR]"

# flushes all the iptables rules, if you have other rules to use then add them into the script
iptables -F -t nat
iptables -F -t mangle
iptables -F -t filter

# mark packets from $VPNUSER
iptables -t mangle -A OUTPUT -j CONNMARK --restore-mark
iptables -t mangle -A OUTPUT ! --dest $LOCALIP -m owner --uid-owner $VPNUSER -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT --dest $LOCALIP -p udp --dport 53 -m owner --uid-owner $VPNUSER -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT --dest $LOCALIP -p tcp --dport 53 -m owner --uid-owner $VPNUSER -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT ! --src $LOCALIP -j MARK --set-mark 0x1
iptables -t mangle -A OUTPUT -j CONNMARK --save-mark

# allow responses
iptables -A INPUT -i $INTERFACE -m conntrack --ctstate ESTABLISHED -j ACCEPT

# block everything incoming on $INTERFACE to prevent accidental exposing of ports
iptables -A INPUT -i $INTERFACE -j REJECT

# let $VPNUSER access lo and $INTERFACE
iptables -A OUTPUT -o lo -m owner --uid-owner $VPNUSER -j ACCEPT
iptables -A OUTPUT -o $INTERFACE -m owner --uid-owner $VPNUSER -j ACCEPT

# all packets on $INTERFACE needs to be masqueraded
iptables -t nat -A POSTROUTING -o $INTERFACE -j MASQUERADE

# reject connections from predator IP going over $NETIF
iptables -A OUTPUT ! --src $LOCALIP -o $NETIF -j REJECT

# Start routing script
/etc/openvpn/routing.sh

exit 0
```

I have NO idea how to go about accomplishing this on my own as I have very little experience with networking beyond configuring basic items.

Basically, if I can just get tcp:58846 accessible from the outside, I should be set.

Any input/suggestions would be greatly appreciated.

Thanks
David

---

