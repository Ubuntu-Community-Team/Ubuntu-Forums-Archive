---
title: "Internet shareing with IP Tables and external 2 nics - depending on connection"
date: 2016-07-22
forum: Networking &amp; Wireless
---

### Post by adriqn on 2016-07-22
Hi there, I hope someone will be able to help me.  I have a small pc I run in the car that acts as a media server for the kids tablets.  Its running ubuntu 16.04 server edition and plex media server.  It has an onboard wifi card that is set up using hostapd and dnsmasq to act as a hotspot for the kids tablets to connect to.  In addition there is an onboard ethernet card which connects via dhcp.  I have used IP tables to share the internet connection to the wifi hotspot.  This is great when there is a wired network connection but obviously that doens't happen in the car.  I was thinking of either adding an additional wifi dongle connecting to my phones 4G or buying a 4G usb modem.  My question is, can I have a rule in the IP tables to forward internet traffic from the Ethernet card when connected or the additional wifi dongle instead?

My /etc/network/interfaces file
```
auto lo wlp3s0 enp2s0f5
iface lo inet loopback

iface enp2s0f5 inet dhcp

auto wlp3s0
iface wlp3s0 inet static
        address 192.168.12.1
        netmask 255.255.255.0
        network 192.168.12.0

```

My dnsmasq.conf
```
listen-address=127.0.0.1
listen-address=192.168.12.1
bind-dynamic
dhcp-range=192.168.12.1,192.168.12.254,255.255.255.0,24h
dhcp-option-force=option:router,192.168.12.1
dhcp-option-force=option:dns-server,192.168.12.1
dhcp-option-force=option:mtu,1500
no-hosts

```
My hostapd.conf
```
beacon_int=100
ssid=CarAP
interface=wlp3s0
driver=nl80211
channel=1
ignore_broadcast_ssid=0
ap_isolate=0
hw_mode=g
wpa=2
wpa_passphrase=xxxxxxxxx
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

```
My rc.local file
```
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o enp2s0f5 -j MASQUERADE

```

I added this to the sysctl.conf
```
et.ipv4.ip_forward=1
```

Thanks

---

### Post by SeijiSensei on 2016-07-22
I would think you could just include both rules in the ruleset.  One or the other will be invoked based on matching the "-o" constraint.  Without the Ethernet connected, the rule you have now will be ignored, and if there is a rule for the wifi output, that will be matched and used.

If that doesn't work, you might need to write a simple bash script that chooses one or the other rule based on which interface is up.  Something like this:
```

#!/bin/bash

if [ "$(cat /sys/class/net/enp2s0f5/operstate)" = "up" ] 
then
    /sbin/iptables --table nat -A POSTROUTING -o enp2s0f5 -j MASQUERADE
else 
    /sbin/iptables --table nat -A POSTROUTING -o wlp3s0 -j MASQUERADE
fi

exit 0

```

---

### Post by adriqn on 2016-07-22
thanks, will try it and see what happens :)

---

