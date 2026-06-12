---
title: "[HELP] Raspberry Pi VPN router"
date: 2017-11-05
forum: Networking &amp; Wireless
---

### Post by rizzle2 on 2017-11-05
Hi guys,

I know it's not Ubuntu related but I know this forum is a fountain of knowledge.

Im new to Pi and have basic understanding of linux and next to no network knowledge.

I configured my Pi to work as a Wifi access point following this tutorial:
[https://github.com/SurferTim/documentation/blob/6bc583965254fa292a470990c40b145f553f6b34/configuration/wireless/access-point.md](https://github.com/SurferTim/documentation/blob/6bc583965254fa292a470990c40b145f553f6b34/configuration/wireless/access-point.md)

This worked successfully and I can connect other devices to my Pi and connect to the internet on those devices. I now have a bridged connection; br0 

I then set up opevpn and configured my files there and that works fine too, my Pi's internet connection is running through the VPN.
I also enabled port forwarding (i have no idea what any of this means):

sudo nano /etc/sysctl.conf
uncommented 
```
#net.ipv4.ip_forward = 1

```

```
sudo iptables -A INPUT -i lo -m comment --comment "loopback" -j ACCEPT
sudo iptables -A OUTPUT -o lo -m comment --comment "loopback" -j ACCEPT
sudo iptables -I INPUT -i eth0 -m comment --comment "In from LAN" -j ACCEPT
sudo iptables -I OUTPUT -o tun+ -m comment --comment "Out to VPN" -j ACCEPT
sudo iptables -A OUTPUT -o eth0 -p udp --dport 1198 -m comment --comment "openvpn" -j ACCEPT
sudo iptables -A OUTPUT -o eth0 -p udp --dport 123 -m comment --comment "ntp" -j ACCEPT
sudo iptables -A OUTPUT -p UDP --dport 67:68 -m comment --comment "dhcp" -j ACCEPT
sudo iptables -A OUTPUT -o eth0 -p udp --dport 53 -m comment --comment "dns" -j ACCEPT
sudo iptables -A FORWARD -i tun+ -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o tun+ -m comment --comment "LAN out to VPN" -j ACCEPT
sudo iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE
```

The strange thing is the devices I am connecting  to my Pi don't run through the VPN. They connect to the Pi's access point but show the IP address of my router .

Additional info:

My Pi has a static IP but it is determined by the router rather than any OS configuration files

I think the iptables are the problem
output from ifconfig
```

br0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.103  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::ba27:ebff:fe09:15ee  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:09:15:ee  txqueuelen 1000  (Ethernet)
        RX packets 343  bytes 27588 (26.9 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 127  bytes 13878 (13.5 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether b8:27:eb:09:15:ee  txqueuelen 1000  (Ethernet)
        RX packets 343  bytes 27588 (26.9 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 127  bytes 15210 (14.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 72  bytes 5292 (5.1 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 72  bytes 5292 (5.1 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

tun0: flags=4305<UP,POINTOPOINT,RUNNING,NOARP,MULTICAST>  mtu 1500
        inet 10.9.0.14  netmask 255.255.255.255  destination 10.9.0.13
        inet6 fe80::9bf3:18f:cdef:a71e  prefixlen 64  scopeid 0x20<link>
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 100  (UNSPEC)
        RX packets 2  bytes 152 (152.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8  bytes 440 (440.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        ether b8:27:eb:5c:40:bb  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 276  bytes 27304 (26.6 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Any help?
Cheers

---

### Post by william.hua on 2017-11-05
This link should help. :)
[https://www.youtube.com/results?search_query=raspberry+pi+vpn+server](https://www.youtube.com/results?search_query=raspberry+pi+vpn+server)

Also port forwarding is when you allow applications running on specific ports to pass through your router. Your router has a firewall built-in which blocks all incoming connection requests for security. Port forwarding allows things like FTP, HTTP, and HTTPS (OpenVPN uses this) to pass through that firewall.

---

