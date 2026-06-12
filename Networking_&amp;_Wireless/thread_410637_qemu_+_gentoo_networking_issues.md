---
title: "qemu + gentoo networking issues"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by davidsampson on 2007-04-16
I am trying to setup a qemu vm under Feisty with Gentoo as the Guest OS.  I have tap/tun networking setup, and gentoo sees the interface, but I am unable to connect to my computer, the network, or the internet.  Using net-setup eth0 under gentoo, I give it the following info:
Wired
Static IP: 10.0.1.7
Broadcast: 10.0.1.255
Netmask: 255.255.255.0
Gateway: 10.0.1.6 (My Hosts tap0 ip addy)
DNS:  205.152.37.23 (My isp's dns server)

But when I run ping 10.0.1.6 from the guest, or ping 10.0.1.7 from the host, it's unreachable.  An ifconfig reveals that the interface is active, but it isn't recieving. Any ideas?

---

