---
title: "Ubuntu PXE Server in KVM libvirt won't forward client IP to internet"
date: 2021-10-14
forum: Networking &amp; Wireless
---

### Post by raydude on 2021-10-14
Hello,

I'm setting up an Ubuntu Server in KVM virt-manager to be a PXE server for an embedded ARM device on my Gentoo laptop.

PXE, NFS, and the ARM bootable linux image are all working.

The Ubuntu server can ping the internet, but the ARM embedded device can't.

Details:

There are two physical ethernet devices on my laptop: It's primary Gig-E device (eno1) and a USB3 Gig-E device (enp5s0f4u1u1).

In virt-manager I have the following configuration:

First NIC acts as gateway to internet for the server.
Bridge Device (to eno1), virbr0, virtio. Setup with NetworkManager. (IP: 192.168.122.48, GW: 192.168.122.1) <- These IP addresses are unique and not related to any other network.

Second NIC is LAN for embedded ARM devices.
Macvtap device (to enp5s0f4u1u1), virtio. (IP: 192.168.1.2, clients get DHCP in 192.168.1.0/24)

I'm using dnsmasq as the dhcp and pxe server. The client PXE boots just fine.

/proc/sys/net/ipv4/ip_forward = 1 on both the virtual amd64 Ubuntu server and my native AMD64 Gentoo laptop.

The ARM client can ping 192.168.1.2 and 192.168.122.48, but cannot ping 192.168.122.1 or 8.8.8.8 and DNS fails. The ARM client can ssh to the virtual Ubuntu server and visa-versa. The native Gentoo laptop can ssh to the Ubuntu server VM and visa-versa.

ARM embedded routing table:
```
Frankie_Baby ~ # route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.2     0.0.0.0         UG    1002   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1002   0        0 eth0

```

Virtual AMD64 Ubuntu routing table:
```
root@mcprod:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.122.1   0.0.0.0         UG    100    0        0 enp1s0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp6s0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 enp1s0
192.168.122.1   0.0.0.0         255.255.255.255 UH    100    0        0 enp1s0
```

Native AMD64 Gentoo routing table:
```
threads /etc # route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.10.1       0.0.0.0         UG    100    0        0 eno1
10.1.10.0       0.0.0.0         255.255.255.0   U     100    0        0 eno1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0
```

ARM native embedded kernel version:
```
Frankie_Baby ~ # uname -a
Linux Frankie_Baby 5.11.0-wtec #1 SMP Sun Oct 10 09:55:25 PDT 2021 armv7l ARMv7 Processor rev 0 (v7l) Altera SOCFPGA GNU/Linux
```

Ubuntu VM linux kernel version:
```
root@mcprod:~# uname -a
Linux mcprod 5.4.0-88-generic #99-Ubuntu SMP Thu Sep 23 17:29:00 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```

Gentoo native kernel version:
```
threads ~ # uname -a
Linux threads 5.14.10-gentoo #1 SMP Sat Oct 9 00:42:48 PDT 2021 x86_64 AMD Ryzen 7 4800H with Radeon Graphics AuthenticAMD GNU/Linux
```

This worked when I was using WIFI as my internet gateway. It stopped working when I added the second Ethernet adapter. I can't go back to WIFI because the WIFI router is too far away and network performance is bad.

I've tried enabling nftables on both the Ubuntu server and the Native Gentoo to see if I could stop the packets from being filtered. Made no difference, but not 100% sure I did that correctly.

I suspect there is a security issue. I also need to figure out what logs to look at for errors to get some clue that way.

Does anyone have any idea what I'm missing?

Thanks in advance.

---

### Post by Tadaen_Sylvermane on 2021-10-14
You need some nftables / iptables settings to get from the internal 192.168.1.* to the 192.168.122.* lan / gateway. The ip_forward toggle just allows it to forward. Still have to tell it WHAT to forward.

*EDIT* I do not know ip tables or nftables. That being said with enough googling anything is possible. This script I've been working on configures a router on boot. It works. I had some odd issues with trying to use the multi wan part. Maybe you can find what you need? The interface_iptables_func function specifically.

*EDIT 2* line 98 may be helpful as well.

[https://gitlab.com/jmgibson1981/homescripts/-/blob/master/router/homerouter.sh](https://gitlab.com/jmgibson1981/homescripts/-/blob/master/router/homerouter.sh)

---

### Post by raydude on 2021-10-15
Thanks Tadaen.

You were right. I needed to add forwards to nat the devices.

I had to add forwards for both the VM, and my laptop to complete the connection. The other issue I had was a misconfigured DNS on the dnsmasq setup in the Ubuntu VM.

For myself and others who look for this in the future, here is a simple bash script to setup NAT between two interfaces:

> #!/bin/bash -e

EXTIF=enp1s0
INTIF=enp6s0

iptables-restore <<-EOF
*nat
-A POSTROUTING -o "$EXTIF" -j MASQUERADE
COMMIT
*filter
:INPUT ACCEPT [0:0]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -i "$EXTIF" -o "$INTIF" -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
-A FORWARD -i "$INTIF" -o "$EXTIF" -j ACCEPT
COMMIT
EOF

In Gentoo, you can save your iptables for next boot by running '/etc/init.d/iptables save'

In Ubuntu run apt install iptables-persistent and it will automatically grab your current iptables settings and save them for the next boot.

---

### Post by Tadaen_Sylvermane on 2021-10-16
Glad it works. Please make sure to mark this thread solved.

---

