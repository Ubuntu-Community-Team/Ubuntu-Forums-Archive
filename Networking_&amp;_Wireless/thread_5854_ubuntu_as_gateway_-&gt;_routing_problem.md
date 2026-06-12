---
title: "ubuntu as gateway -&gt; routing problem"
date: 2004-11-22
forum: Networking &amp; Wireless
---

### Post by ubuntu_demon on 2004-11-22
Hi,

I'm trying to let ubuntu act as a gateway. The pc has 2 networkcards. Internet works on my ubuntu pc. But internet didn't work on my other pc.  I installed firestarter and I did the firestarter network wizzard. And I tried some things with route. Now I can't even connect to my other pc.

I want to be able to have internet acces 

Here's my ifconfig :

===

eth0      Link encap:Ethernet  HWaddr *********************
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe39:8984/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:580931 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:703878061 (671.2 MiB)  TX bytes:926 (926.0 b)
          Interrupt:217 Memory:f7ff4000-0

eth1      Link encap:Ethernet  HWaddr *********************
          inet addr:82.217.233.230  Bcast:82.217.233.255  Mask:255.255.255.0
          inet6 addr: fe80::92e0:4cff:fe39:5c13/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:412917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:197403369 (188.2 MiB)  TX bytes:5851760 (5.5 MiB)
          Interrupt:225 Base address:0xd400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68588 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68588 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5031461 (4.7 MiB)  TX bytes:5031461 (4.7 MiB)

===

Here's my route  :

===

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
82.217.233.0    *               255.255.255.0   U     0      0        0 eth1
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         82-217-233-1.ca 0.0.0.0         UG    0      0        0 eth1


===

Here's my etc/network/interfaces :

===

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
name INTERNET

auto eth0
iface eth0 inet static
name LAN
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0

---

### Post by ubuntu_demon on 2004-11-22
After a reset of my other pc (192.168.0.216). It's reachable again. But I can't reach internet from it. 

It's not a configuration issue of that pc because when I was using XP as gateway it could reach internet.

---

### Post by ubuntu_demon on 2004-11-23
Maybe the NAT part of the firestarter wizard doesn't work.

---

### Post by p!=f on 2004-11-23
If I get it correctly...
You have one PC with 2 network cards. You can get on the Internet from this PC, right? But other computers connected on that second card can't, correct?

Do you have IP forwarding turned on?
```

 * 16:51:05 * pef @ agonicus *
[~] > cat /etc/network/options
ip_forward=yes
spoofprotect=yes
syncookies=yes

```

I have similar setup but I don't use Firestarter but I've found Shorewall to be much easier to set up with a perfect documentation and examples on their website or in the shorewall-doc package.
I also use dnsmasq for DHCP and caching nameserver. It's also pretty easy to set up.

---

### Post by ubuntu_demon on 2004-11-23
Yes I have a pc with two networkcards that has to be a gateway for the other pc.

no I didn't have ip_forward on. I tried to set it to on and restarted my network by :

sudo ifdown eth0 eth1
sudo ifup eth0 eth1

and logged in onto my other pc and tried pinging a site. Didn't work.

What does syn_cookies=on do ?

---

### Post by p!=f on 2004-11-23
```

sudo /etc/init.d/networking restart

```
would be better as I'm aware if{up,down} doesn't load options in /etc/network/options.

Syncookies:
[http://cr.yp.to/syncookies.html](http://cr.yp.to/syncookies.html)

Did you ping an IP address or a hostname?
If a hostname, your internal clients are not "translating" IP addresses to hostnames. You need to set up some caching nameserver or put appropriate DNS servers in /etc/resolv.conf on every client.

---

### Post by ubuntu_demon on 2004-11-23
now I also did this :

iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

and I did /etc/init.d/networking restart

Now I can ping to IP's but DNS doesn't work.

interfaces of my other pc (the one where dns doesn't work) :

iface eth0 inet static
  address 192.168.0.216
  netmask 255.255.255.0
  gateway 192.168.0.1
  dns-nameservers 213.73.255.52 213.73.255.53 213.132.189.250

---

### Post by p!=f on 2004-11-23
[QUOTE=demon666_nl]
Now I can ping to IP's but DNS doesn't work.[/QUOTE]
Already answered 2 posts above. :)

---

### Post by ubuntu_demon on 2004-11-23
The pc where DNS doesn't work for did work when the gateway runned XP.

---

### Post by ubuntu_demon on 2004-11-23
THNX!

I edited /etc/resolv.conf and added my providers' nameservers

(apparently XP was caching the nameservers)

---

