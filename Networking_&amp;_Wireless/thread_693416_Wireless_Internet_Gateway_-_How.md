---
title: "Wireless Internet Gateway - How"
date: 2008-02-11
forum: Networking &amp; Wireless
---

### Post by dscheste on 2008-02-11
Hello,

I am trying to turn my Ubuntu MythTV PVR into an internet router. I have a couple computers upstairs I would like to connect to the PVR via cables as those do not have wireless cards. My PVR does. I am using RT2500 driver and it works just fine. I am using WEP and did not have any major problems with it. As my PVR "brings" internet upstairs, I want to be able to use my PVR as a gateway and just connect to its LAN card in order to get online.

Here is what I have tried so far with no success, any help is greatly appreciated.

1. Firestarter - what a disaster. Does not work. Just does not.

2. Trying to set things up. My wireless card that brings internet in is RA1. The card on PVR I want to plug in is eth0.

```
ifconfig eth0 192.168.1.1

iptables -t nat -A POSTROUTING -o RA1 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward

```
Added  “net.ipv4.ip_forward = 1&#8243; to /etc/sysctl.conf
and followed up with 
```
/etc/init.d/networking restart
```

at no avail.

The /etc/network/interfaces looks like this:
> iface lo inet loopback
auto lo

iface ra1 inet dhcp
wireless-key s:#####
wireless-essid ##########

auto ra1

iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0

auto eth0



My /etc/dhcpd.conf  looks like this:

> subnet 192.168.0.1 netmask 255.255.255.0 {
        option routers 192.168.0.1;
        option subnet-mask 255.255.255.0;
        option domain-name-servers pvr;
        range dynamic-bootp 192.168.0.169 192.168.1.253;
        default-lease-time 21600;
        max-lease-time 43200;
}




Funny thing, once I have both card on, no internet is available on the PVR either, as soon as I kill eth0 and keep only RA1 online, I get online.

Thank you.

---

### Post by dscheste on 2008-02-15
bump

---

