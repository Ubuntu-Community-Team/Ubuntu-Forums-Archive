---
title: "IPconfig"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-08-27
Hey guys whats the command iin linux/ubuntu on checking your ipaddress n terminal?

---

### Post by slakkie on 2009-08-27
ifconfig -a

---

### Post by NoaHall on 2009-08-27
ifconfig

---

### Post by jeu on 2009-12-30
> **NoaHall said:**
> ifconfig

How can we use ifconfig or ip addr to display information such as default gateway, dns servers?

similar to ipconfig /all in Windows.

---

### Post by tom.swartz07 on 2009-12-30
if you want your external IP, you could use this

```
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

---

### Post by Geoff918 on 2009-12-30
or just go to something like:

[http://www.whatismyip.com](http://www.whatismyip.com)

It should have that in your router config as well.

---

### Post by jeu on 2010-01-22
> **tom.swartz07 said:**
> if you want your external IP, you could use this

```
wget -q -O - checkip.dyndns.org|sed -e 's/.*Current IP Address: //' -e 's/<.*$//'
```

Not really the the same, but a great tip!! I do this one also :-)

---

### Post by fromthehill on 2010-01-22
```
route
```
output is something like this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     303    0        0 wlan0
default         192.168.1.254   0.0.0.0         UG    303    0        0 wlan0

---

### Post by jeu on 2010-01-29
> **fromthehill said:**
> ```
route
```
output is something like this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     303    0        0 wlan0
default         192.168.1.254   0.0.0.0         UG    303    0        0 wlan0

Thanks, this is what I needed.

PS. "route -n" to display numerical. without it it will display the dns name of the router.

---

