---
title: "iptables rules on startup"
date: 2014-03-22
forum: Networking &amp; Wireless
---

### Post by Erdem on 2014-03-22
Hello;

on my server i entered iptables rules for route and its working fine

```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -i eth0 -j ACCEPT
```

and run that command to save rules

```
sudo iptables-save > /etc/iptables_rules
```

after that i configured my interfaces file

```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        gateway 192.168.1.1
        wpa-ssid XXXXXXXXX
        wpa-psk  XXXXXXXXXXX
        pre-up iptables-restore < /etc/iptables_rules

auto eth0
iface eth0 inet static
        address 10.0.0.1
        netmask 255.255.254.0
```

problem is that rules not be activate at startup till i enter "echo 1 > /proc/sys/net/ipv4/ip_forward" again...

any help?

---

### Post by Lars Noodén on 2014-03-22
Have you tried setting *net.ipv4.ip_forward=1* in /etc/sysctl.conf ?
That should set sysctl for you when the machine boots.

---

### Post by Erdem on 2014-03-22
thank you
i enabled that line in the file and its working perfectly now :D
thanks again

---

