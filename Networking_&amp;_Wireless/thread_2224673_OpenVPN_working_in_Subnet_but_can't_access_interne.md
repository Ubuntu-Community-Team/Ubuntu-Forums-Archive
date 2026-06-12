---
title: "OpenVPN working in Subnet but can't access internet"
date: 2014-05-17
forum: Networking &amp; Wireless
---

### Post by JohnGalt131 on 2014-05-17
I have openvpn installed on my raspberry pi running debian. I can connect to the vpn and access the computers on my home network, but I can't get to the internet. I assume this is a route problem, but as far as I can tell, my routes seem correct.

# route 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         myrouter.local  0.0.0.0         UG    0      0        0 wlan0
10.10.0.0       10.10.0.2       255.255.255.224 UG    0      0        0 tun0
10.10.0.2       *               255.255.255.255 UH    0      0        0 tun0
10.20.20.0     *               255.255.255.0   U     0      0        0 wlan0

10.10.0.0 255.255.255.224 is my vpn network. 10.20.20.0 255.255.255.0 is my home network.

I have internet on the vpn server (pi). So, if I ssh into the server, I can get to the internet, but not through the browser.



root@raspberrypi:/home/pi# ifconfig
eth0      Link encap:Ethernet  HWaddr b8:27:eb:14:4e:5a
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:553 errors:0 dropped:5 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33441 (32.6 KiB)  TX bytes:300 (300.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1492 (1.4 KiB)  TX bytes:1492 (1.4 KiB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.10.0.1  P-t-P:10.10.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:79662 (77.7 KiB)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:da:97:53
          inet addr:10.20.20.250  Bcast:10.20.20.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4896 errors:0 dropped:146 overruns:0 frame:0
          TX packets:4906 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:855935 (835.8 KiB)  TX bytes:602345 (588.2 KiB)

any help is appreciated.

---

### Post by JohnGalt131 on 2014-05-17
Forgot to mention


iptables -t nat -A INPUT -i wlan0 -p udp -m udp --dport 1194 -j ACCEPT

iptables -t nat -A POSTROUTING -s 10.10.0.0/24 -o wlan0 -j SNAT --to-source 10.20.20.1

---

### Post by spynappels on 2014-05-17
Is IPv4 forwarding enabled?

```
cat /proc/sys/net/ipv4/ip_forward
```

---

### Post by JohnGalt131 on 2014-05-17
IP forwarding is enabled.

I added


   # Allow traffic initiated from VPN to access LAN
    iptables -I FORWARD -i tun0 -o eth0 \
         -s 10.10.0.0/24 -d 10.20.0.0/24 \
         -m conntrack --ctstate NEW -j ACCEPT

    # Allow traffic initiated from VPN to access "the world"
    iptables -I FORWARD -i tun0 -o eth0 \
         -s 10.10.0.0/24 -m conntrack --ctstate NEW -j ACCEPT

    # # Allow traffic initiated from LAN to access "the world"
    # iptables -I FORWARD -i eth0 -o eth1 \
    #      -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT

    # Allow established traffic to pass back and forth
    iptables -I FORWARD -m conntrack --ctstate RELATED,ESTABLISHED \
         -j ACCEPT

    # Notice that -I is used, so when listing it (iptables -vxnL) it
    # will be reversed.  This is intentional in this demonstration.

    # Masquerade traffic from VPN to "the world" -- done in the nat table
    iptables -t nat -I POSTROUTING -o eth0 \
          -s 10.10.0.0/24 -j MASQUERADE

    # Masquerade traffic from LAN to "the world"
    iptables -t nat -I POSTROUTING -o eth0 \
          -s 10.20.0.0/24 -j MASQUERADE

and that seems to have fixed it.

---

