---
title: "WiFi Repeater With Airbase-ng &amp; isc-dhcp-server + Internet Connection"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by Xaotique on 2015-07-03
I'm trying to make a WiFi repeater out of my laptop with two wireless adapters.  I have a TP-LINK TL-WN722N set up in monitor mode on wlan1 and a BCM43142 in managed mode on wlan0 connected to a wireless network.

What I'm trying to do is allow someone to connect to my airbase-ng network and use the network access provided on wlan0.

So far I have the wireless network broadcasted and the dhcp server allows me to connect.  I cannot get internet access though.

[b]What I've Run{/b]
```
ifconfig wlan1 downiw dev wlan1 set type monitor
ifconfig wlan1 up


airbase-ng -e "OpenWifi" -c 1 wlan1 1>/dev/null 2>/dev/null &


ifconfig at0 10.0.2.1 netmask 255.255.255.0
ifconfig at0 up
route add -net 10.0.2.0 netmask 255.255.255.0 gw 10.0.2.1


iptables --flush
iptables --table nat --flush
iptables --delete-chain
iptables --table nat --delete-chain
iptables -P FORWARD ACCEPT
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE


dhcpd -cf /etc/dhcp/dhcpd.conf at0 1>/dev/null 2>/dev/null &


echo 1 > /proc/sys/net/ipv4/ip_forward

```

**/etc/dhcp/dhcpd.conf**
```
option domain-name-servers 8.8.8.8, 8.8.4.4;default-lease-time 700;
max-lease-time 8000;


option T150 code 150 = string;
deny client-updates;
one-lease-per-client false;
allow bootp;
ddns-updates off;
ddns-update-style none;
authoritative;


subnet 10.0.2.0 netmask 255.255.255.0 {
        interface at0;
        range 10.0.2.2 10.0.2.254;
        option routers 10.0.2.1;
        option subnet-mask 255.255.255.0;
        option broadcast-address 10.0.2.255;
        option domain-name-servers 8.8.8.8;
        allow unknown-clients;
}
```

---

