---
title: "I Lost my Loopback device..."
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by chronusdark on 2006-12-16
can someone help me i seem to have lost my loopback device and its breaking applications

this is my /etc/network/interfaces file

```
auto lo
iface lo inet loopback

auto eth0
#iface eth0 inet dhcp

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp


auto eth0
```

---

### Post by taurus on 2006-12-16
What does your /etc/hosts look like then?

```
cat /etc/hosts
```

---

### Post by chronusdark on 2006-12-16
```
127.0.0.1       localhost
127.0.1.1       lhanners-laptop

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

well it shows up in there....but when i type lo in the network applet it doesnt show up it says disconnected and apps keep complaining about it

---

### Post by taurus on 2006-12-16
What about 

```
ifconfig
```

---

### Post by chronusdark on 2006-12-16
wow nevermind...i fixed it

i just removed the extra 
auto eth0 line
and typed ifup lo

---

