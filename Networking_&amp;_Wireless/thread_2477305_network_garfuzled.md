---
title: "network garfuzled"
date: 2022-07-20
forum: Networking &amp; Wireless
---

### Post by dgermann on 2022-07-20
Friends--

The short version of my saga:

Synopsis: previously used this computer to connect to network and internet via vpn, and had no problems. Yesterday I started having problems (running now in the office, so a direct connection to the lan), and they get worse as they get better. Read on, if you dare.

Change yesterday: I had a reliable tech service move a graphics board (GeForce GTX 1060 3GB) from another computer into this one. There are three screens attached, each an hp lv2311.

The computer: 4 cores @ 3.20GHz; 7.6G memory. Running 20.04.4 LTS.

Symptoms: At bootup, I currently can ping other computers on the lan, but not google.com. I get “Temporary failure in name resolution”

Partial fix: After about 4 or 6 hours of googling and trying various things, I came upon this series of steps (from [https://askubuntu.com/questions/1369661/ubuntu-20-04-network-no-longer-working]("https://askubuntu.com/questions/1369661/ubuntu-20-04-network-no-longer-working"), and [https://www.nixcraft.com/t/rtnetlink-answers-file-exists-on-linux-what-it-meant/3650]("https://www.nixcraft.com/t/rtnetlink-answers-file-exists-on-linux-what-it-meant/3650")):

  ```
sudo ip link set enp3s0 down
  sudo ip addr flush enp3s0
  sudo ip link set enp3s0 up
  sudo dhclient -r
  sudo dhclient enp3s0
```

After this I can connect to the Internet and to the lan. All works fine, for a bit....

But wait, there's more:

1. It does not hold after a reboot.

2. After a few minutes running a browser (firefox or chrome), kworker starts using 60-80% of cpu, and the browser is usually over 45%. Consequently, the computer is unusable. If I renice under top to +19, it helps momentarily, but not enough to even move the cursor around.

Other things going on that might have clues or just be irrelevant:

A. At bootup it does not mount directories from two servers which are in fstab. This is a minor annoyance. It says something about cifs error connecting to socket, right at the end of bootup. Perhaps it is because the network is not connecting properly.

B. One message that scrolled past at some time said 
```
nouveau DRM: GPU lockup--switching to software fbcon.
```

C. Early on, trying to get it to ping even the lan, I tried to set up netplan. There were no files in /etc/netplan, and I added 01-network-manager-all.yaml, and also tried sudo netplan generate and sudo netplan apply and they did nothing as far as I could see. Even after re-installing netplan which it said was the latest version. Some other commands I issued at various times which sometimes helped me connect to the lan, and sometimes made no difference, and none persisted after a reboot:

```
sudo ifconfig enp3s0 192.168.0.13
sudo nmcli networking off
sudo nmcli networking on
```

D. I have in this process, when I was connected, run 
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get autoclean && sudo apt-get autoremove
```

So the system is up to date.

This whole thing has me stumped. Can you help me un-garfuzle this network?

Thanks!

---

### Post by TheFu on 2022-07-21
Run
```
$ sudo ubuntu-drivers autoinstall
```
then reboot.

That should install the approved, tested, proprietary nvidia driver for your OS and GPU.
If that doesn't also fix the DNS resolution issue, post back and we can address it directly.

There are many moving parts in your setup. VPN, normal networking, new hardware, drivers.  Try to fix 1 thing at a time. The nvidia drivers is the easiest and I think there was a problem 1-2 weeks ago where those drivers, somehow (I have no idea how or way), screwed up networking.

---

### Post by dgermann on 2022-07-22
@TheFu 

Wonderful to see you answering me! You have helped me with several things in the past! And amazingly, that has not stopped you from helping me again.

I ran the command you suggested. It ran through screens full of things. After reboot, the screen/display issues seem to have resolved, and the disk usage has been down into ranges that seem to me normal.

But after rebooting, there was still no connection to the Internet (it did connect to the lan), and the auto mounts from fstab did not mount. To get the Internet I again ran:
```
sudo ip link set enp3s0 down
sudo ip addr flush enp3s0
sudo ip link set enp3s0 up
sudo dhclient -r
sudo dhclient enp3s0
```

I have not rebooted since.

So the Internet networking issue and the automounts from fstab are what need attention from me, and nudges from you, please.

Thank you for helping me, TheFu!

---

### Post by TheFu on 2022-07-22
Good that the GPU stuff is cleared up.

For network troubleshooting, we need to gather facts first.
[https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](https://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) has steps, in a specific order, to run.

Do those and report back.  I suspect a DNS issue. The steps in that link will determine if that is true or not.

---

### Post by dgermann on 2022-07-22
@TheFu--

Thank you.

These results are from running the computer as it is while the networking is up. I will reboot in a bit and run them again, in case that is a better test:

```
doug@wind:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether fc:aa:14:a7:06:1a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.13/24 brd 192.168.0.255 scope global noprefixroute enp3s0
       valid_lft forever preferred_lft forever
    inet6 fe80::feaa:14ff:fea7:61a/64 scope link 
       valid_lft forever preferred_lft forever
doug@wind:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
doug@wind:~$ ping router
PING router (192.168.0.1) 56(84) bytes of data.
64 bytes from router (192.168.0.1): icmp_seq=1 ttl=64 time=0.474 ms
64 bytes from router (192.168.0.1): icmp_seq=2 ttl=64 time=0.346 ms
64 bytes from router (192.168.0.1): icmp_seq=3 ttl=64 time=0.365 ms
^C
--- router ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2056ms
rtt min/avg/max/mdev = 0.346/0.395/0.474/0.056 ms
doug@wind:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=55 time=14.1 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=55 time=15.2 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=55 time=12.9 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 12.918/14.090/15.229/0.943 ms
doug@wind:~$ ping google.com
PING google.com (142.250.190.110) 56(84) bytes of data.
64 bytes from ord37s35-in-f14.1e100.net (142.250.190.110): icmp_seq=1 ttl=114 time=14.3 ms
64 bytes from ord37s35-in-f14.1e100.net (142.250.190.110): icmp_seq=2 ttl=114 time=13.1 ms
64 bytes from ord37s35-in-f14.1e100.net (142.250.190.110): icmp_seq=3 ttl=114 time=13.1 ms
^C
--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 13.077/13.489/14.255/0.541 ms
doug@wind:~$ ping www.abc.com
PING d2iwv1xxkqpmiz.cloudfront.net (99.84.160.55) 56(84) bytes of data.
64 bytes from server-99-84-160-55.ord52.r.cloudfront.net (99.84.160.55): icmp_seq=1 ttl=242 time=14.3 ms
64 bytes from server-99-84-160-55.ord52.r.cloudfront.net (99.84.160.55): icmp_seq=2 ttl=242 time=14.3 ms
64 bytes from server-99-84-160-55.ord52.r.cloudfront.net (99.84.160.55): icmp_seq=3 ttl=242 time=13.2 ms
^C
--- d2iwv1xxkqpmiz.cloudfront.net ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.163/13.920/14.306/0.535 ms
doug@wind:~$ dmesg |grep eth[0-9]
[    4.901212] r8169 0000:03:00.0 eth0: RTL8168g/8111g, fc:aa:14:a7:06:1a, XID 4c0, IRQ 33
[    4.941183] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    5.352104] r8169 0000:03:00.0 enp3s0: renamed from eth0
doug@wind:~$ sudo lshw -C network
[sudo] password for doug: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: fc:aa:14:a7:06:1a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:d000(size=256) memory:f7900000-f7900fff memory:f2100000-f2103fff
doug@wind:~$ ifconfig -a
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.13  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::feaa:14ff:fea7:61a  prefixlen 64  scopeid 0x20<link>
        ether fc:aa:14:a7:06:1a  txqueuelen 1000  (Ethernet)
        RX packets 481028  bytes 342206499 (342.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 369811  bytes 74395505 (74.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 10328  bytes 1071198 (1.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 10328  bytes 1071198 (1.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

doug@wind:~$ more /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.

nameserver 192.168.0.1
doug@wind:~$ route 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router          0.0.0.0         UG    100    0        0 enp3s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
doug@wind:~$ dmesg |grep enp3s0
[    5.352104] r8169 0000:03:00.0 enp3s0: renamed from eth0
[   36.107764] r8169 0000:03:00.0 enp3s0: Link is Down
[   42.475280] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   42.475290] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[  559.581925] r8169 0000:03:00.0 enp3s0: Link is Down
[  577.056050] r8169 0000:03:00.0 enp3s0: Link is Down
[  583.396892] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[10962.426354] r8169 0000:03:00.0 enp3s0: Link is Down
[10968.797544] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[17348.718888] r8169 0000:03:00.0 enp3s0: Link is Down
[17355.237514] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[17385.917354] r8169 0000:03:00.0 enp3s0: Link is Down
[17392.317508] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[17897.528345] r8169 0000:03:00.0 enp3s0: Link is Down
[17904.000911] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
doug@wind:~$ 
```

That is all for the moment. Back in a bit.

---

### Post by dgermann on 2022-07-22
@TheFu--

Here is everything I did after the reboot:

```
doug@wind:~$ ping router
PING router (192.168.0.1) 56(84) bytes of data.
64 bytes from router (192.168.0.1): icmp_seq=1 ttl=64 time=0.393 ms
64 bytes from router (192.168.0.1): icmp_seq=2 ttl=64 time=0.361 ms
64 bytes from router (192.168.0.1): icmp_seq=3 ttl=64 time=0.370 ms
^C
--- router ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2038ms
rtt min/avg/max/mdev = 0.361/0.374/0.393/0.013 ms
doug@wind:~$ ping google.com
ping: google.com: Temporary failure in name resolution
doug@wind:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=55 time=13.5 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=55 time=13.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=55 time=13.2 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.182/13.311/13.485/0.127 ms
doug@wind:~$ sudo mount -avvv
[sudo] password for doug: 
/                        : ignored
/boot                    : already mounted
none                     : ignored
mount.cifs kernel mount options: ip=192.168.0.203,unc=\\torus\client,vers=2.1,nobrl,uid=1000,gid=200,user=doug,pass=********
/sam/client              : successfully mounted
mount.cifs kernel mount options: ip=192.168.0.203,unc=\\torus\apps,vers=2.1,nobrl,uid=1000,gid=200,user=doug,pass=********
/sam/apps                : successfully mounted
/sam2/client             : ignored
/sam2/apps               : ignored
mount.cifs kernel mount options: ip=192.168.0.201,unc=\\earth\personal,vers=2.1,nobrl,uid=1000,gid=1000,user=doug,pass=********
/sam/personal            : successfully mounted
doug@wind:~$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether fc:aa:14:a7:06:1a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.13/24 brd 192.168.0.255 scope global noprefixroute enp3s0
       valid_lft forever preferred_lft forever
    inet6 fe80::feaa:14ff:fea7:61a/64 scope link 
       valid_lft forever preferred_lft forever
doug@wind:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    20100  0        0 enp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
doug@wind:~$ ping router
PING router (192.168.0.1) 56(84) bytes of data.
64 bytes from router (192.168.0.1): icmp_seq=1 ttl=64 time=0.377 ms
64 bytes from router (192.168.0.1): icmp_seq=2 ttl=64 time=0.367 ms
64 bytes from router (192.168.0.1): icmp_seq=3 ttl=64 time=0.365 ms
^C
--- router ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2040ms
rtt min/avg/max/mdev = 0.365/0.369/0.377/0.005 ms
doug@wind:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=55 time=13.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=55 time=14.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=55 time=13.2 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 13.233/13.725/14.269/0.424 ms
doug@wind:~$ ping google.com
ping: google.com: Temporary failure in name resolution
doug@wind:~$ ping www.abc.com
ping: www.abc.com: Temporary failure in name resolution
doug@wind:~$ dmesg |grep enp3s0
[    5.289147] r8169 0000:03:00.0 enp3s0: renamed from eth0
[   32.613007] r8169 0000:03:00.0 enp3s0: Link is Down
[   39.011685] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control rx/tx
[   39.011693] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
doug@wind:~$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: enp3s0
       version: 0c
       serial: fc:aa:14:a7:06:1a
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 ip=192.168.0.13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:d000(size=256) memory:f7900000-f7900fff memory:f2100000-f2103fff
doug@wind:~$ ifconfig -a
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.13  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::feaa:14ff:fea7:61a  prefixlen 64  scopeid 0x20<link>
        ether fc:aa:14:a7:06:1a  txqueuelen 1000  (Ethernet)
        RX packets 805  bytes 338685 (338.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 574  bytes 130444 (130.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3473  bytes 280919 (280.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3473  bytes 280919 (280.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

doug@wind:~$ more /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
# 127.0.0.53 is the systemd-resolved stub resolver.
# run "systemd-resolve --status" to see details about the actual nameservers.

doug@wind:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         router          0.0.0.0         UG    20100  0        0 enp3s0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 enp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp3s0
doug@wind:~$ sudo ip link set enp3s0 down
doug@wind:~$ sudo ip addr flush enp3s0
doug@wind:~$ sudo ip link set enp3s0 up
doug@wind:~$ sudo dhclient -r
doug@wind:~$ sudo dhclient enp3s0
doug@wind:~$ systemd-resolve --status
Failed to get global data: Unit dbus-org.freedesktop.resolve1.service not found.

doug@wind:~$ 
```

Immediately after that I posted this message. (I had to run the last 5 commands to get access to the Internet.)

So what clues have we here?

Thanks, TheFu! (Is that other site your own?)

---

### Post by TheFu on 2022-07-22
You need to run the commands when the internet is NOT working.  Showing a working network isn't helpful for troubleshooting a network failure, unless you can compare the working and non-working results, then interpret those differences.

I bet ping 8.8.8.8 works, but ping google.com does not. That means it is a DNS issue, not a network issue.  That has been common here thanks to systemd-resolved not working.  But until we see the failure, we won't actually know.

The quick fix is this:
```
echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf
```
But that only lasts until systemd decides to rerun or a reboot.  I don't use systemd-resolved, but you can search these forums for issues with that.  Again, only if the stuff I'm guessing above is truly the issue. If not, it is something else completely.

---

### Post by dgermann on 2022-07-22
@TheFu--

Thanks.

Post #4 was before the reboot while the Internet was working; #5 was after reboot, when Internet was **not** working. Does that give you what you need to diagnose, or do I need to run something else?

Yes, #5 shows ping 8.8.8.8 works but ping google.com did not. So you are suggesting that is a DNS issue, if I am reading your post correctly, and that I should search the forums here. If so, what do I need to search, please?

Thanks, TheFu!

---

### Post by TheFu on 2022-07-22
Sorry, I missed that.

```
doug@wind:~$ ping google.com
ping: google.com: Temporary failure in name resolution
```

It is a name resolution, DNS, problem. It is not a network issue - neither LAN or WAN network issue.

---

### Post by dgermann on 2022-07-22
@TheFu--

That's OK. It was easy to miss. I perhaps should not post twice in succession.

Just to record what I did, and I think it fixed it:

I was following [https://superuser.com/questions/1427311/activation-via-systemd-failed-for-unit-dbus-org-freedesktop-resolve1-service]("https://superuser.com/questions/1427311/activation-via-systemd-failed-for-unit-dbus-org-freedesktop-resolve1-service") and ran these commands:

```
$ systemctl status systemd-resolved.service
$ systemctl enable systemd-resolved.service
```

The first reported the connection as "inactive (dead)," so I ran the second. It created a pair of symlinks. I rebooted. It seems to be holding, after several reboots.

So thank you for pointing me in the right direction, TheFu!

I will mark this solved, and run off to try to figure out why those fstab entries are not getting automounted.

---

