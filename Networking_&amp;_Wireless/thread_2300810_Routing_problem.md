---
title: "Routing problem"
date: 2015-10-28
forum: Networking &amp; Wireless
---

### Post by extremis11 on 2015-10-28
I have a PC with 2 NICs, 1 used for Internet access and the other to connect to another PC through a SWITCH; i have configured /etc/network/interfaces as follows:

auto eth0
iface eth0 inet static
  address xxx.xxx.xxx.61
  gateway xxx.xxx.xxx.1
  netmask 255.255.255.0
  network xxx.xxx.xxx.0
  broadcast xxx.xxx.xxx.255
  dns-nameservers xxx.xxx.xxx.100


auto eth1
iface eth1 inet static
  address 192.168.1.1
  gateway xxx.xxx.xxx.61
  netmask 255.255.255.0
  network 192.168.1.0
  broadcast 192.168.1.255

where xxx.xxx.xxx.xxx is a public Internet address and 192.168.1.xxx a local private address. I have also configured /etc/network/interfaces of a second PC connected to the first through the unmanaged SWITCH as follows:

auto eth0
iface eth0 inet static
  address 192.168.1.2
  gateway 192.168.1.1
  netmask 255.255.255.0
  network 192.168.1.0
  brodcast 192.168.1.255


First PC's networking is working fine, second PC's networking is not routed outside the local network, for example when i try to ping google.com, i get

ping 178.59.100.217
--- 178.59.100.217 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 3999ms


i can ping 192.168.1.1 though, so traffic is routed to the first PC just fine. How can i make it routed to the Internet, so i can install updates for example?


Thank you in advance,
                                  Kostas

---

### Post by SeijiSensei on 2015-10-29
1) Make sure the directive "net.ipv4.ip_forward=1" in /etc/sysctl.conf is enabled by removing the "#" from the start of the line.

2) Add the line
```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```
to the file /etc/rc.local.

Now reboot, and see if you can ping 8.8.8.8.

---

### Post by extremis11 on 2015-10-29
Thank you very much, that works just fine!

---

### Post by SeijiSensei on 2015-10-29
Please go to "Thread Tools" at the top of the page and mark your thread [Solved].

Glad I could help!

---

