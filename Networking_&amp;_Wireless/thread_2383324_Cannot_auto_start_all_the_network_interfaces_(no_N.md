---
title: "Cannot auto start all the network interfaces (no NetworkManager)"
date: 2018-01-23
forum: Networking &amp; Wireless
---

### Post by Menion on 2018-01-23
Hi guys
I am running an x86_64 Ubuntu server Xenial installation
I am trying to bring up some interfaces automatically via /etc/network/interfaces which looks like:

```

# The loopback network interface
auto lo enp1s0 tap0 enp1s0.4


iface lo inet loopback


iface enp1s0 inet dhcp


#iface tap0 inet dhcp
iface tap0 inet static
        hwaddress ether 00:06:5B:3C:55:C0
        address 192.168.55.4
        netmask 255.255.255.0
#       gateway 192.168.182.1
#       pre-up /usr/sbin/tunctl -t tap0 ; /bin/true
        pre-up /sbin/ip tuntap add dev tap0 mode tap
iface tap0 inet6 auto
        pre-up /sbin/modprobe -q ipv6 ; /bin/true


iface enp1s0.4 inet static
        address 192.168.44.1
        netmask 255.255.255.0
        vlan-raw-device enp1s0

```

The comment you see are experiments I did trying to figure out which is the problem, that actually is: tap0 is not created after boot, but if I do a "sudo ifup tap0" it is created with no problem.
But if I don't start enp1s0.4 then tap0 is automatically created....
From the comments you see that I have changed tools to create tap0, actually the other odd things is that if I create enp1s0.4 via vconfig, then the problem is the other way around, so tap0 is created and not enp1s0.4, then if I remove tap0 enp1s0.4 is created....
I have googled a little bit around and I see that there have been some race condition issue with VLAN interfaces and ifup scripts, but I am not sure if in my case it is the same problem or not
syslog show just nothing, so I am a little bit lost here. Any help would be very very appreciated!
Bye

---

