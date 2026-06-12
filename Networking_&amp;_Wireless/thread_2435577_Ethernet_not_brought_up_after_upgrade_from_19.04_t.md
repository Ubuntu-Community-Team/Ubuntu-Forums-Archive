---
title: "Ethernet not brought up after upgrade from 19.04 to 19.10"
date: 2020-01-22
forum: Networking &amp; Wireless
---

### Post by Freek07 on 2020-01-22
I had everything working in 19.04 and upgraded to 19.10 yesterday.
One of the things that broke and I still haven't fixed is network configuration. The settings are in /etc/network/interfaces, the name of the device is correct, but it still does not work, the system wakes up with the given device down. Even if I bring it up (ifconfig enp3s0 up) it is without ip.

Any ideas? I can see the awahi-daemon doing something in logs.

Here's the config (the name is correct!):

auto lo
iface lo inet loopback

allow-hotplug enp3s0
iface enp3s0 inet static
    address 192.168.1.20
    netmask 255.255.255.0
    gateway 192.168.1.1
    dns-nameservers 193.2.1.66 193.2.1.72
    mtu 1500

LOG (the last line is after I config'd it manually via ifconfig ...):
Jan 22 19:18:28 R3 kernel: [    0.622614] r8169 0000:03:00.0 enp3s0: renamed from eth0
Jan 22 19:18:29 R3 NetworkManager[1180]: <info>  [1579717109.3681] ifupdown: guessed connection type (enp3s0) = 802-3-ethernet
Jan 22 19:18:29 R3 NetworkManager[1180]: <info>  [1579717109.3789] manager: (enp3s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Jan 22 19:19:40 R3 kernel: [   77.209248] r8169 0000:03:00.0 enp3s0: Link is Down
Jan 22 19:19:43 R3 NetworkManager[1180]: <info>  [1579717183.9162] device (enp3s0): carrier: link connected
Jan 22 19:19:43 R3 kernel: [   80.856496] r8169 0000:03:00.0 enp3s0: Link is Up - 1Gbps/Full - flow control off
Jan 22 19:19:43 R3 kernel: [   80.856512] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
Jan 22 19:19:45 R3 avahi-daemon[1162]: Joining mDNS multicast group on interface enp3s0.IPv6 with address fe80::692:26ff:fed1:214a.
Jan 22 19:19:45 R3 avahi-daemon[1162]: New relevant interface enp3s0.IPv6 for mDNS.
Jan 22 19:19:45 R3 avahi-daemon[1162]: Registering new address record for fe80::692:26ff:fed1:214a on enp3s0.*.

// here I did manual ifup 
Jan 22 19:20:30 R3 NetworkManager[2982]: <info>  [1579717230.2739] ifupdown: guessed connection type (enp3s0) = 802-3-ethernet
Jan 22 19:20:30 R3 NetworkManager[2982]: <info>  [1579717230.2784] device (enp3s0): carrier: link connected
Jan 22 19:20:30 R3 NetworkManager[2982]: <info>  [1579717230.2790] manager: (enp3s0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)

// ...and manual ifconfig
Jan 22 19:20:55 R3 avahi-daemon[1162]: Joining mDNS multicast group on interface enp3s0.IPv4 with address 192.168.1.20.
Jan 22 19:20:55 R3 avahi-daemon[1162]: New relevant interface enp3s0.IPv4 for mDNS.
Jan 22 19:20:55 R3 avahi-daemon[1162]: Registering new address record for 192.168.1.20 on enp3s0.IPv4.

---

### Post by pcfan1234 on 2020-01-22
19.10 uses Netplan, if you haven't disabled it. Please check that. It is a boot option in the /etc/default/grub file.

---

### Post by peab on 2020-02-04
I had a similar problem after a BIOS upgrade. Check that /etc/netplan/50-cloud-init.yaml refers to enp3s0 . In my case the name of the interface changed from the one I got from installation.
If this is the case for you, fix it and run "netplan apply".

---

