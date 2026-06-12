---
title: "OpenVPN client issues"
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by p-stone on 2016-04-21
Hi everyone. 

I've installed openvpn server on my openwrt router using [this guide]("https://www.loganmarchione.com/2015/08/openwrt-with-openvpn-server-on-tp-link-archer-c7/"). The client connects fine using the config file specified and openvpn connect on my android phone, but I'm having issues connecting from my ubuntu laptop. I'm running 16.04. I can connect to openvpn fine, and I see a new tun interface created pulling an IP, but I'm unable to connect to anything, including the server LAN IP 10.8.0.1. I am able to ping the router of my local network, as well as my local IP and my openvpn IP (10.8.0.2) but that's it. Here's my route information with the VPN connected:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.8.0.1        0.0.0.0         UG    50     0        0 tun0
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wls1
10.8.0.0        0.0.0.0         255.255.255.0   U     50     0        0 tun0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wls1
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wls1
<VPN ext IP>  192.168.0.1     255.255.255.255 UGH   600    0        0 wls1

```
and without:
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wls1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wls1
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wls1
```

Here's my client config:
```
#specify TUN vs. TAP (if you're not sure, you want TUN)
dev tun

#specify protocol to use (default is UDP)
proto udp

#Certificate information
ca   ca.crt
cert user1.crt
key  user1.key

#client settings
client
remote-cert-tls server
#remote openwrt 1194
remote <VPN ext IP> 1194

```

I've scoured the internet for solutions but as near as I can tell I have this all set up correctly. Any tips or troubleshooting suggestions would be greatly appreciated.

---

### Post by May_Masters on 2016-04-25
Well first of all you server needs to do port-forwarding.
```

sudo sysctl -w net/ipv4/ip_forward=1 
```

and in your openvpn's server config you'll need to specify the network (or single host) you'd like to reach:
```
push "route 192.168.2.0 255.255.255.0"
```


... and don't forget:
```
systemctl daemon-reload
```

---

### Post by p-stone on 2016-04-25
> **May_Masters said:**
> Well first of all you server needs to do port-forwarding.
```

sudo sysctl -w net/ipv4/ip_forward=1 
```

and in your openvpn's server config you'll need to specify the network (or single host) you'd like to reach:
```
push "route 192.168.2.0 255.255.255.0"
```


... and don't forget:
```
systemctl daemon-reload
```

My server is on my OpenWRT router. I can connect ok through my android phone, so I'm pretty sure it's a client issue on my Ubuntu laptop.
Port forwarding is enabled:
```

uci add firewall forwarding
uci set firewall.@forwarding[-1].src="vpn"
uci set firewall.@forwarding[-1].dest="wan"
uci add firewall forwarding
uci set firewall.@forwarding[-1].src="vpn"
uci set firewall.@forwarding[-1].dest="lan"
uci commit firewall

```
Routes are pushed:
```

#push a local route to your clients (allow your clients to access the server's network)
uci add_list openvpn.myvpn.push="route 10.10.1.0 255.255.255.0"

```

---

### Post by p-stone on 2016-06-08
Fixed it. I had to enable LZO data compression on the client.

---

