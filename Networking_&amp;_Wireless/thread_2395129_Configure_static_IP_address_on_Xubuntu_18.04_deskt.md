---
title: "Configure static IP address on Xubuntu 18.04 desktop"
date: 2018-06-27
forum: Networking &amp; Wireless
---

### Post by ChrisRChamberlain on 2018-06-27
Hi all

Trying to configure static IP address as follows:-

Original output from ifconfig
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.11  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::e2e3:2c57:3533:b12  prefixlen 64  scopeid 0x20<link>
        ether 00:18:8b:90:7b:b2  txqueuelen 1000  (Ethernet)
        RX packets 447  bytes 433313 (433.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 338  bytes 48072 (48.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 5  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 134  bytes 9287 (9.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 134  bytes 9287 (9.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
Output from ip link show
```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN mode DEFAULT group default qlen 1000
    link/ether 00:18:8b:90:7b:b2 brd ff:ff:ff:ff:ff:ff
```
Modified /etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.92
netmask 255.0.0.0
# network 192.168.0.0
# broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 8.8.8.8 8.8.4.4
```
Output from ifconfig after reboot
```
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 134  bytes 9287 (9.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 134  bytes 9287 (9.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
Any pointers, please as to how to correct the issue?

TIA

---

### Post by chili555 on 2018-06-27
Generally, networking in Ubuntu version 17.10 and later is handled by netplan and not /etc/network/interfaces.

In most desktop installations, the relvant netplan file reads:```
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: NetworkManager

```In other words, let the usually perfectly adequate Network Manager do all the work.

That is where I suggest that you set the static IP address. [http://3.bp.blogspot.com/-zXKEt3vxNg4/T58h-Cm1HJI/AAAAAAAAAjs/uOC0tCLcS4w/s1600/ScreenHunter_02%2BApr.%2B30%2B16.37.gif](http://3.bp.blogspot.com/-zXKEt3vxNg4/T58h-Cm1HJI/AAAAAAAAAjs/uOC0tCLcS4w/s1600/ScreenHunter_02%2BApr.%2B30%2B16.37.gif)

---

### Post by ChrisRChamberlain on 2018-06-27
chili555

Thanks for your reply.

The Xubuntu Network Connections dialogs differ from the Ubuntu dialogs, but by following your example, the desired result has been obtained.

Present output from ifconfig
```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.92  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::e2e3:2c57:3533:b12  prefixlen 64  scopeid 0x20<link>
        ether 00:18:8b:90:7b:b2  txqueuelen 1000  (Ethernet)
        RX packets 298  bytes 317513 (317.5 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 228  bytes 30227 (30.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 5  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 135  bytes 9431 (9.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 135  bytes 9431 (9.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Again, many thanks

---

