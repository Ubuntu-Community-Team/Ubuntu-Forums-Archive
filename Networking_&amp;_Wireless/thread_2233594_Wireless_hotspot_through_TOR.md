---
title: "Wireless hotspot through TOR"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by davidedepau1996 on 2014-07-09
I'm trying to create a wireless hotspot that pipes all its connections through TOR, so that I can browse safely on devices that do not support TOR (non-rooted android phones, smart TVs, etc.)
I'm not really good with networking though, so I just tried to merge a script to [create a TOR network interface]("http://www.howtoforge.com/how-to-set-up-a-tor-middlebox-routing-all-virtualbox-virtual-machine-traffic-over-the-tor-network") and one that creates a wireless network through another wireless interface.
I can connect to the network and dhcp works, but I cannot load pages.
 Here's what I've got:

Script to get everything going (root)
```
#!/bin/bash

# destinations you don't want routed through Tor
NON_TOR="192.168.1.1/24"

# Tor's TransPort
TRANS_PORT="9040"

# your internal interface
INT_IF="tornet0"

iptables -F
iptables -t nat -F
iptables -t nat -I POSTROUTING -s 172.16.0.0/24 -j MASQUERADE
for NET in $NON_TOR; do
 iptables -t nat -A PREROUTING -i $INT_IF -d $NET -j RETURN
done
iptables -t nat -A PREROUTING -i $INT_IF -p udp --dport 53 -j REDIRECT --to-ports 53
iptables -A FORWARD -i $INT_IF -p udp -j DROP
iptables -t nat -A PREROUTING -i $INT_IF -p tcp --syn -j REDIRECT --to-ports $TRANS_PORT

ssid="TORSpot"
passwd="noneofyourbusiness"
dest="wlan0"
src="tornet0"

echo "interface=${dest}
driver=nl80211
ssid=${ssid}
channel=5
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=${passwd}
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP" > /etc/hostapd/hostapd.conf

echo "ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;
log-facility local7;
option domain-name-servers 208.67.220.220,208.67.222.222 ;
subnet 10.42.43.0 netmask 255.255.255.0 {
  range 10.42.43.50 10.42.43.70;
  option subnet-mask 255.255.255.0;
  option broadcast-address 10.42.43.255;
  option routers 10.42.43.1;
}" > /etc/dhcp/dhcpd.conf

ifconfig "${dest}" 10.42.43.1/24
iptables -t nat -A POSTROUTING -s 10.42.43.0/24 -o "${src}" -j MASQUERADE
iptables -A FORWARD -s 10.42.43.0/24 -o "${src}" -j ACCEPT
iptables -A FORWARD -d 10.42.43.0/24 -m state --state ESTABLISHED,RELATED -i "${src}" -j ACCEPT
echo 1 >/proc/sys/net/ipv4/conf/all/forwarding
echo "INTERFACES=${dest}" >/etc/default/dhcp
dhcpd "${dest}"

# touch /var/log/hostapd.log
# chown root:www-data /var/log/hostapd.log
# chmod 662 /var/log/hostapd.log

hostapd /etc/hostapd/hostapd.conf # | tee /var/log/hostapd.log

```

/etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.1.84
    netmask 255.255.255.0
    gateway 192.168.1.1
    broadcast 192.168.1.255

auto tornet0
iface tornet0 inet static
    address 172.16.0.1
    netmask 255.255.255.0
    bridge_ports none
    bridge_maxwait 0
    bridge_fd 1

    up iptables -t nat -I POSTROUTING -s 172.16.0.0/24 -j MASQUERADE
    down iptables -t nat -D POSTROUTING -s 172.16.0.0/24 -j MASQUERADE
```

Can anybody help me simplify it and fix it, maybe removing the tornet0 interface and applying the rules directly to wlan0?

Thanks.

---

### Post by davidedepau1996 on 2014-07-10
I managed to accomplish it by (partially) following these instructions: [http://www.se7ensins.com/forums/threads/how-to-build-a-tor-wireless-hotspot-with-raspberry-pi.1069306/](http://www.se7ensins.com/forums/threads/how-to-build-a-tor-wireless-hotspot-with-raspberry-pi.1069306/)

---

