---
title: "Lubuntu 17.04 Wired network can't access internet"
date: 2017-06-19
forum: Networking &amp; Wireless
---

### Post by yamanqui on 2017-06-19
Hello,

I'm pretty new to Linux, but I decided to install Linux in an old machine that was working with Windows XP. First I installed Ubuntu, and while everything worked out of the box, it was quite slow, so I decided to test Lubuntu.

Unfortunately the ethernet internet is not working under Lubuntu, and I can't figure out why. Since apparently the network does work. I can connect thru ssh from the Lubuntu machine into my other machine in the same network, and the Lubuntu machine does get an IP address from my router, but I can't connect to the internet.

Here are some tests I've done:

Here it appears that the network does get an IP address from my router:
```
yama@yama-lubuntu:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
        valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
        valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 4c:72:b9:d2:18:31 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.72/24 brd 192.168.1.255 scope global dynamic eno1
        valid_lft 84485sec preferred_lft 84485sec
    inet6 fe80::f9ad::c80a:27f5:e1f4/64 scope link
        valid_lft forever preferred_lft forever
yama@yama-lubuntu:~$
```

And I CAN connect to another machine in the same network (where I'm writing this question):
```
yama@yama-lubuntu:~$ ssh 192.168.1.65
Password:
Last login: Mon Jun 19 16:54:56 2017
Yamas-MacBook-Pro:~ yama$
```

But I can't reach the internet:
```
yama@yama-lubuntu:~$ ping www.google.com -c 5
ping: www.google.com: Name or service not known
yama@yama-lubuntu:~$
```

```
yama@yama-lubuntu:~$ ping 173.194.42.244 -c 5
ping: 173.194.42.244 (173.194.42.244) 56(84) bytes of data.

--- 173.194.42.244 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4093ms

yama@yama-lubuntu:~$
```

Any help would be much appreciated, since I have no clue what I'm missing.

Thank you.

---

### Post by TheFu on 2017-06-19
I can't ping that IP either. What about 8.8.8.8?  That's a google DNS server. We see a few common issues here. One of them is DNS misconfiguration, but all connectivity is fine. Since you can ping your router, it isn't a LAN connectivity issue.  Most likely, it is DNS.

---

### Post by yamanqui on 2017-06-20
You're probably right, I don't know where I get that [COLOR=#000000][FONT=&amp]173.194.42.244[/FONT][/COLOR] was google IP.

The ping to 8.8.8.8 works fine:
```
yama@yama-lubuntu:~$ ping 8.8.8.8 -c 5
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=60 time=32.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=60 time=40.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=60 time=95.9 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=60 time=75.2 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=60 time=43.3 ms

--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 32.553/57.510/95.980/24.130 ms
yama@yama-lubuntu:~$
```

So it does appear to be a DNS misconfiguration. Could you help me configure the DNS, I really don't know where that's done on Lubuntu. I tried to made changes to /etc/network/interfaces, but that didn't work:

Previous content of /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

My changes to /etc/network/interfaces, that also didn't work
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth0  iface eth0 inet static
  address 192.168.1.50
  netmask 255.255.255.0
  gateway 192.168.1.254
  network 192.168.1.0
  broadcast 192.168.1.254
  dns-nameservers 8.8.8.8 8.8.4.4
```

---

### Post by TheFu on 2017-06-20
eth0 isn't the correct device.  According to the post above, eno1 is the device you should be using.  In 16.04 and later releases, the device names get some funky name based on the MAC. The days of eth0 are gone.

Also, 
```
  network 192.168.1.0
  broadcast 192.168.1.254

```aren't needed/wanted. The netmask and IP provide the values AND if incorrect, life will suck.  For example, the .254 for broadcast is probably wrong based on the IP/netmask.

---

### Post by chili555 on 2017-06-20
> eth0 isn't the correct device.Indeed!!

I suggest that you set /etc/network/interfaces something like:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eno1
iface eno1 inet static
  address 192.168.1.50
  netmask 255.255.255.0
  gateway 192.168.1.254
  dns-nameservers 8.8.8.8 8.8.4.4
```Reboot and test:```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by yamanqui on 2017-06-20
Thanks, everything works after setting my /etc/network/interfaces to:
```
# interfaces(5) file used by ifup(8) and ifdown(8)auto lo
iface lo inet loopback


auto eno1
iface eno1 inet static
  address 192.168.1.50
  netmask 255.255.255.0
  gateway 192.168.1.254
  dns-nameservers 8.8.8.8 8.8.4.4
```

Now, I just like to know if there is a way to keep the DNS working, but also use an automatic dhcp IP, instead of a static one.

---

### Post by TheFu on 2017-06-20
```
auto eno1
iface eno1 inet dhcp
```
doesn't work?  FYI, the manpage for **interfaces** is pretty good.

---

### Post by chili555 on 2017-06-20
I suggest that you comment out the settings you added:```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

#auto eno1
#iface eno1 inet static
#  address 192.168.1.50
#  netmask 255.255.255.0
#  gateway 192.168.1.254
#  dns-nameservers 8.8.8.8 8.8.4.4
```Make certain that IPv4 settings in Network Manager is set to Automatic (DHCP). [https://i.stack.imgur.com/Lu4y0.png](https://i.stack.imgur.com/Lu4y0.png) 

Reboot and show us:```
ip addr show
nmcli -f 'IP4.DNS' dev show
ping -c3 www.ubuntu.com
```

---

