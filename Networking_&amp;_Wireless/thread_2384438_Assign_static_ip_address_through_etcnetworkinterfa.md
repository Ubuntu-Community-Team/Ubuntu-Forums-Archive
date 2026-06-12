---
title: "Assign static ip address through /etc/network/interfaces"
date: 2018-02-07
forum: Networking &amp; Wireless
---

### Post by ChrisRChamberlain on 2018-02-07
Hi all

Have 32bit Xubuntu 17.10 pc and need to assign ip address for LAN access.

/etc/network/interfaces is:-
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.91
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```

ifconfig returns:-```
enp0s16: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.18  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::1c5b:7e4e:25f7:c84f  prefixlen 64  scopeid 0x20<link>
        ether 00:0f:ea:14:35:70  txqueuelen 1000  (Ethernet)
        RX packets 549  bytes 473373 (473.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 349  bytes 40316 (40.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 119  bytes 8676 (8.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 119  bytes 8676 (8.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
Have tried substituting 'etho' with 'enp0s16' in /etc/network/interfaces, but does not produce required ifconfig output.

Ideas please?

TIA

---

### Post by chili555 on 2018-02-07
Please change the file to:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp0s16
iface enp0s16 inet static
address 192.168.0.91
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```Please be certain that the selected address 192.168.0.91 is outside of the range used for DHCP in the router so as to avoid collisions.

Reboot and show us:```
ifconfig
cat /etc/netplan/*.yaml
cat /etc/NetworkManager/NetworkManager.conf   
```

---

### Post by ChrisRChamberlain on 2018-02-07
chili555

Thanks for your reply.

ifconfig is :-
```
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 580  bytes 35952 (35.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 580  bytes 35952 (35.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
cat /etc/netplan/*.yaml is:-```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager
```
cat /etc/NetworkManager/NetworkManager.conf is :-```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
```

---

### Post by chili555 on 2018-02-07
> ifconfig is :-
Code:
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 580  bytes 35952 (35.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 580  bytes 35952 (35.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0What do you suppose happened to enp0s16?

Let's have a look at:```
lspci -nnk | grep 0200 -A3
```

---

### Post by ChrisRChamberlain on 2018-02-08
Output from lspci -nnk | grep 0200 -A3```
00:10.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Packard Bell B.V. Onboard RTL8111 on GA-8SIML Rev1.0 Mainboard [1631:7003]
	Kernel driver in use: 8139too
	Kernel modules: 8139cp, 8139too

```
Using code suggested disables internet access, so have reverted to using```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.91
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```
in ../interfaces, which is where we started.

---

### Post by chili555 on 2018-02-08
Changing the code back simply allows Network Manager to take back control of the ethernet interface. When the system reads your file here:```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.91
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```...it says, roughly, "I don't have any eth0 here in my system. There is nothing to do here." Network Manager takes over and you get connected.

If you want to set a static IP address, we need to do one of two things. Either troubleshoot why the file I recommended doesn't work, or else, simply set the static IP in Network manager, like this:

[ATTACH=CONFIG]278473[/ATTACH]

---

### Post by ChrisRChamberlain on 2018-02-09
Followed your suggestion and result is```
enp0s16: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.91  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::1c5b:7e4e:25f7:c84f  prefixlen 64  scopeid 0x20<link>
        ether 00:0f:ea:14:35:70  txqueuelen 1000  (Ethernet)
        RX packets 621  bytes 484259 (484.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 361  bytes 40202 (40.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 127  bytes 9636 (9.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 127  bytes 9636 (9.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
Many thanks for your perseverance, chili555. Job done!

---

