---
title: "Ethernet not working on ubuntu 18.04 LTS"
date: 2019-01-07
forum: Networking &amp; Wireless
---

### Post by santiagomd3305 on 2019-01-07
Hello Community!

I've installed Ubuntu 18.04 LTS after than using Ubuntu 16.04. Nontheless, I had a wired connection error three days ago and I've not been able to fix it. My latptop is ASUS  x441U, 7.7 GiB ram, Intel Core i5-7200U COU @ 2.50GHz x4 and 64 bits.

 Problem: Wired connection fails. It appears connected, but not working. This problem appeared three days ago, after than an updating. Fortunately, my Wifi is working. Here I'll post some additional information:

```
sudo lshw -C network
*-network                 
       descripción: Ethernet interface
       producto: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       nombre lógico: enp2s0
       versión: 07
       serie: 88:d7:f6:6f:0a:d2
       tamaño: 100Mbit/s
       capacidad: 100Mbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=169.254.254.159 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:16 ioport:d000(size=256) memoria:ef200000-ef200fff memoria:e2100000-e2103fff
  *-network
       descripción: Interfaz inalámbrica
       producto: RTL8821AE 802.11ac PCIe Wireless Network Adapter
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:03:00.0
       nombre lógico: wlp3s0
       versión: 00
       serie: f0:03:8c:89:a3:ed
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuración: broadcast=yes driver=rtl8821ae driverversion=4.15.0-43-generic firmware=N/A ip=192.168.1.58 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       recursos: irq:17 ioport:c000(size=256) memoria:ef100000-ef103fff

```

Also
```

sudo dhclient -v enp2s0

Internet Systems Consortium DHCP Client 4.3.5
Copyright 2004-2016 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/enp2s0/88:d7:f6:6f:0a:d2
Sending on   LPF/enp2s0/88:d7:f6:6f:0a:d2
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.55 on enp2s0 to 255.255.255.255 port 67 (xid=0x1c641aef)
DHCPACK of 192.168.1.55 from 192.168.1.1
bound to 192.168.1.55 -- renewal in 43043 seconds.


```

and 
```
ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 169.254.254.159  netmask 255.255.0.0  broadcast 169.254.255.255
        inet6 fe80::1bd2:3ffb:13c9:c203  prefixlen 64  scopeid 0x20<link>
        ether 88:d7:f6:6f:0a:d2  txqueuelen 1000  (Ethernet)
        RX packets 1149  bytes 201149 (201.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1370  bytes 233412 (233.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Bucle local)
        RX packets 9506  bytes 732939 (732.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 9506  bytes 732939 (732.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.58  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::9de6:c4c2:e9f:c403  prefixlen 64  scopeid 0x20<link>
        ether f0:03:8c:89:a3:ed  txqueuelen 1000  (Ethernet)
        RX packets 24851  bytes 19089578 (19.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 25027  bytes 4006778 (4.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Thank you so much, I'm a beginner and I'm willing to assist in any additional info.


Update 1:
I'v modifyied the resolv.conf file and changed "nameserver 127.0.0.53" by "nameserver 8.8.8.8" and "nameserver 8.8.4.4". This "solution" is temporal

---

### Post by #&amp;thj^% on 2019-01-07
Just out of curiosity what dose this show:
```
cat  /etc/network/interfaces
```

---

### Post by santiagomd3305 on 2019-01-07
Hi 1Fallen
It's :
```

cat  /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by #&amp;thj^% on 2019-01-07
Hola santiagomd3305 and welcome to our forums. :D
Well i might not be of much help here but have you tried with:
```
sudo ifup enp2s0
```
you might need to install "ifupdown" first.
```
sudo apt install ifupdown
```
Now restart the network with:
```
systemctl restart network-manger
```
And I have had to disable the WiFi with "nm-applet" to force using the Ethernet.

---

### Post by santiagomd3305 on 2019-01-07
Thanks for you help. When I code "sudo ifup enp2s0", the output is:

```
 
Unknown interface enp2s0

```

---

### Post by #&amp;thj^% on 2019-01-07
What shows with:
```
cat /var/lib/dkms/r8168/8.043.02/build/make.log
```

---

### Post by santiagomd3305 on 2019-01-08
That directory doesn't exist. The "ls" output is following:

```

ls  /var/lib/dkms
dkms_dbversion  nvidia

```

---

### Post by #&amp;thj^% on 2019-01-11
Sorry for the long delay, I "barely" have any time to do a decent job at helping in the forums anymore. (At least in a timely manner. )
So what I have been able to deduce from your information thus far is,
[list][*]You have an upgraded version of 18.04. (Instead of a clean install)
[*]You report that, and I quote: "This problem appeared three days ago, after than an updating"
[*] So far you seem to have a driver "driver=r8169" that i can see for your device. But it should be built into kernel with "4.13 and newer"[/list]
For example for mine:
```
**ethtool -i enp0s25**
_driver: e1000e_
version: 3.2.6-k
firmware-version: 0.13-3
expansion-rom-version: 
bus-info: 0000:xx:xx.x (I added the "x's" for privacy)
supports-statistics: yes
supports-test: yes
supports-eeprom-access: yes
supports-register-dump: yes
supports-priv-flags: no

```
I have a friend i chat with from time to time so i will refer to his Blog, this "may" help you with your problem.
Found here: [https://www.unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/](https://www.unixblogger.com/how-to-get-your-realtek-rtl8111rtl8168-working-updated-guide/)
Also it seems someone else followed his guide with success here: [https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8](https://medium.com/@lgobinath/no-ethernet-connection-in-ubuntu-16-04-linux-mint-18-with-realtek-rtl8111-8168-8411-7ae2779dc9b8)
Any way i hope you either have this resolved by now or at the very least can get it working with those links.
Good Luck. ;)

---

### Post by santiagomd3305 on 2019-01-11
:) Thank you so much, 1fallen. You've done a lot and I appreciate it. I'll check those links and report the related results. Thank you again. :)

---

### Post by santiagomd3305 on 2019-01-20
1fallen, I've fixed the issue. You provided me some links that carry me on to read more about drivers and related things. But always a question was present: why could not I edit my DNS on ubuntu in the way that previous version allows me? So, before download a driver, I tried to find how I could edit "resolv.conf" and I could fix the problem. The solution is in this link: [https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/](https://www.techrepublic.com/article/how-to-set-dns-nameservers-in-ubuntu-server-18-04/) 

Thanks again 
:)

---

