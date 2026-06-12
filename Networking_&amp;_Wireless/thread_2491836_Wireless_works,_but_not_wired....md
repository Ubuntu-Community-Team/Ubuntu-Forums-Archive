---
title: "Wireless works, but not wired..."
date: 2023-10-22
forum: Networking &amp; Wireless
---

### Post by bfloeagle on 2023-10-22
I've got an old laptop where I just upgraded Ubuntu 20.06.4 to Ubuntu 22.04.3 on a dual boot laptop with Windows 10 (two different physical drives, if that matters, no issues with wired or wireless networking in Ubuntu 20).  Both wired and wireless cards are detected in Windows and Linux.  Both NICs get DHCP IP addresses from my router.  After the upgrade though, when running Ubuntu, only the wireless card actually connects to the internet.  When just my wired card is enabled and connected, I get the "Destination host unreachable" messages on pings.  DNS lookups obviously fail as well.  If I manually configure my wired network card, I get the same results.  I upgraded one more version to 23.10 thinking maybe something was missed and nothing changed.  

```

andy@asus-rog:~$ ping 1.1.1.1
PING 1.1.1.1 (1.1.1.1) 56(84) bytes of data.
From 192.168.30.101 icmp_seq=1 Destination Host Unreachable
From 192.168.30.101 icmp_seq=2 Destination Host Unreachable
From 192.168.30.101 icmp_seq=3 Destination Host Unreachable
From 192.168.30.101 icmp_seq=4 Destination Host Unreachable
From 192.168.30.101 icmp_seq=5 Destination Host Unreachable
^C
--- 1.1.1.1 ping statistics ---
6 packets transmitted, 0 received, +5 errors, 100% packet loss, time 5043ms
```

Here is the monkeywrench...  Wired and wireless work fine when I boot into Windows.  Both also work fine if I boot into Medicat USB and run mini Windows 10.  But it continues to fail when I boot into a recent Linux live distro from a USB drive.  I tried Debian 12, Ubuntu 22, Mint 21, PopOS 22, Kali 2023.3, and Gentoo 2023-10-15 (figuring at least Gentoo wasn't based on Debian/Ubuntu).    

I originally thought it was a driver issue, but if that was the case, why am I able to get an IP address from DHCP...  Here are the details prior to turning wifi on...
```

andy@asus-rog:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 50:46:5d:eb:a0:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.30.101/24 brd 192.168.30.255 scope global dynamic noprefixroute enp4s0
       valid_lft 6058sec preferred_lft 6058sec
    inet6 fe80::51c6:fe21:42a1:b597/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether dc:85:de:5e:e9:99 brd ff:ff:ff:ff:ff:ff
```

And afterwards with wifi on...
```

andy@asus-rog:/etc/netplan$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 50:46:5d:eb:a0:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.30.101/24 brd 192.168.30.255 scope global dynamic noprefixroute enp4s0
       valid_lft 3802sec preferred_lft 3802sec
    inet6 fe80::51c6:fe21:42a1:b597/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether dc:85:de:5e:e9:99 brd ff:ff:ff:ff:ff:ff
    inet 192.168.70.110/24 brd 192.168.70.255 scope global dynamic noprefixroute wlp3s0
       valid_lft 4402sec preferred_lft 4402sec
    inet6 fe80::22cf:7be6:4deb:7b3a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```


 Here's the lspci output for the networking cards...
```

03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
```

I'm now leaning towards a routing issue but I'm not sure.  Even when I manually configure the network settings, using both automatic and manual route settings, I can't get to anything outside of the wired NIC to respond.  Turn on the wifi, everything works.  Turn it off, back to square one.  Is anyone else using the AR8151 on a modern kernel?  Anyone run into this before?  I'm pulling my hair out because I know the card cable works from the two Windows installs (though I did try other cables and ports on my router to be sure).  The only thing I see common across all those Linux distros is the kernel and I'm not skilled enough to say if that would impact routing...

Some extra details...

The drivers appear to be loading:
```
andy@asus-rog:/$ lsmod | grep atl
atl1c                  77824  0
```

When the wifi is off, route takes a few seconds to come back with this information...
```
andy@asus-rog:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.30.1    0.0.0.0         UG    20100  0        0 enp4s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.30.0    0.0.0.0         255.255.255.0   U     100    0        0 enp4s0
```

Turn the wifi on and route returns results immediately...
```
andy@asus-rog:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    600    0        0 wlp3s0
default         _gateway        0.0.0.0         UG    20100  0        0 enp4s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp4s0
192.168.30.0    0.0.0.0         255.255.255.0   U     100    0        0 enp4s0
192.168.70.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0
```

When the wifi is on, "_gateway" resolves to this:
```

andy@asus-rog:~$ nslookup _gateway
Server:        127.0.0.53
Address:    127.0.0.53#53

Name:    _gateway
Address: 192.168.70.1
Name:    _gateway
Address: 192.168.30.1
```

But turn the wifi off...
```

andy@asus-rog:~$ nslookup _gateway
;; communications error to 127.0.0.53#53: timed out
;; communications error to 127.0.0.53#53: timed out
```

II don't think DNS is the issue since pings to IP addresses don't work but I'm grasping for straws...  Any help would be appreciated.  Thanks!

---

### Post by bfloeagle on 2023-11-01
Anyone have a wild guess?  I haven't made any progress unfortunately...

---

### Post by chili555 on 2023-11-01
> 2: enp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 50:46:5d:eb:a0:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.**[COLOR="#FF0000"]30[/COLOR]**.101/24 brd 192.168.30.255 scope global dynamic noprefixroute enp4s0
       valid_lft 3802sec preferred_lft 3802sec
    inet6 fe80::51c6:fe21:42a1:b597/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether dc:85:de:5e:e9:99 brd ff:ff:ff:ff:ff:ff
    inet 192.168.**[COLOR="#FF0000"]70[/COLOR]**.110/24 brd 192.168.70.255 scope global dynamic noprefixroute wlp3s0
       valid_lft 4402sec preferred_lft 4402sec
    inet6 fe80::22cf:7be6:4deb:7b3a/64 scope link noprefixroute 
       valid_lft forever preferred_lft foreverAre these connected to the same router??? Are these addresses acquired by DHCP? Or are they set to static IP addresses in Network Manager? Something doesn't look right.

---

### Post by bfloeagle on 2023-11-01
Same router (pfSense) using different VLANs to separate wired and wireless traffic.  DHCP addresses being served on each VLAN, no static settings in Network Manager (though I have tried that and it didn't help).

---

