---
title: "[abandoned] Lubuntu 17.04 and No Internet"
date: 2017-08-06
forum: Networking &amp; Wireless
---

### Post by mik3e2 on 2017-08-06
I have a triple boot setup, Mint, Solus, and Lubuntu. When I installed Lubuntu 17.04 I could not update software or launch Firefox so ran the following commands and produced this output:

```
--> ping 8.8.8.8 -c 5
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=59 time=13.6 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=59 time=13.5 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=59 time=13.3 ms
64 bytes from 8.8.8.8: icmp_seq=4 ttl=59 time=13.6 ms
64 bytes from 8.8.8.8: icmp_seq=5 ttl=59 time=259 ms

--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 13.354/62.707/259.302/98.297 ms

--> dmesg | grep -e jme -e enp
[    2.761808] r8169 0000:02:00.0 enp2s0: renamed from eth0
[    4.735423] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    4.869315] r8169 0000:02:00.0 enp2s0: link down
[    4.869331] r8169 0000:02:00.0 enp2s0: link down
[    4.869491] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[    6.835684] r8169 0000:02:00.0 enp2s0: link up
[    6.835696] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready

--> sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 06
       serial: 50:e5:49:eb:29:2a
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168e-3_0.0.4 03/27/12 ip=192.168.10.15 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:24 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

--> cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

--> cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

--> dpkg -l network-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version        Architecture Description
+++-===============-==============-============-=========================================================
ii  network-manager 1.4.4-1ubuntu3 amd64        network management framework (daemon and userspace tools)

--> cat /var/log/syslog | grep etwork | tail -n 10
Aug  5 13:53:18 raven NetworkManager[725]: <warn>  [1501966398.4755] arping[0x7ff15000aee0,2]: arping could not be found; no ARPs will be sent
Aug  5 13:53:21 raven NetworkManager[725]: <info>  [1501966401.4759] manager: startup complete
Aug  5 13:53:24 raven NetworkManager[725]: <info>  [1501966404.4778] manager: WiFi hardware radio set enabled
Aug  5 13:53:24 raven NetworkManager[725]: <info>  [1501966404.4779] manager: WWAN hardware radio set enabled
Aug  5 13:57:58 raven gvfsd-network[1617]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Aug  5 13:58:02 raven gvfsd-network[1607]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Aug  5 13:58:06 raven gvfsd-network[1602]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Aug  5 13:58:09 raven gvfsd-network[1621]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Aug  5 13:58:13 raven gvfsd-network[1614]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted
Aug  5 13:58:17 raven gvfsd-network[1600]: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: The specified location is not mounted

--> ps aux | grep etwork
root       725  0.0  0.4 471256 16556 ?        Ssl  13:53   0:00 /usr/sbin/NetworkManager --no-daemon
mike      1617  0.0  0.2 448956  8584 ?        Sl   13:57   0:00 /usr/lib/gvfs/gvfsd-network --spawner :1.5 /org/gtk/gvfs/exec_spaw/5
mike      2199  0.0  0.0  14240   924 pts/0    S+   14:48   0:00 grep --color=auto etwork

--> ip -s address
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
    RX: bytes  packets  errors  dropped overrun mcast   
    27162      366      0       0       0       0       
    TX: bytes  packets  errors  dropped carrier collsns 
    27162      366      0       0       0       0       
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 50:e5:50:ef:50:e5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.10.15/24 brd 192.168.10.255 scope global enp2s0
       valid_lft forever preferred_lft forever
    inet6 fe80::baeb:fe80:baeb:fe80/64 scope link 
       valid_lft forever preferred_lft forever
    RX: bytes  packets  errors  dropped overrun mcast   
    202692     2922     0       0       0       14      
    TX: bytes  packets  errors  dropped carrier collsns 
    301999     3902     0       0       0       0       
```

Nothing in there has shown me a direction to solving the problem so I installed Lubuntu 16.04.3 and have been able to update software and launch Firefox. Thus I installed inxi and produced this output:

```
--> inxi -Fxzplc0
System:    Host: raven Kernel: 4.10.0-30-generic x86_64 (64 bit gcc: 5.4.0) Desktop: LXDE (Openbox 3.6.1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Gigabyte Tecohnology product: H61M-DS2
           Mobo: INTEL model: H61M-DS2 v: x.x Bios: American Megatrends v: F4 date: 12/21/2011
CPU:       Dual core Intel Pentium G630 (-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10775
           clock speeds: max: 2700 MHz 1: 1599 MHz 2: 1599 MHz
Graphics:  Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Display Server: X.org 1.19.3 drivers: (unloaded: fbdev,vesa)
           Resolution: N/A Advanced Data: N/A for root
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.10.0-30-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 02:00.0
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 1000.2GB (17.7% used)
           ID-1: /dev/sda model: Samsung_SSD_840 size: 500.1GB temp: 0C
           ID-2: /dev/sdb model: WDC_WD5000AAKX size: 500.1GB temp: 40C
Partition: ID-1: / size: 20G used: 3.9G (22%) fs: ext4 dev: /dev/sda3 label: Raven
           ID-2: /home size: 9.5G used: 37M (1%) fs: ext4 dev: /dev/sda7 label: Curlew
           ID-3: /media/Avocet size: 455G used: 158G (37%) fs: ext4 dev: /dev/sdb1 label: Avocet
           ID-4: swap-1 size: 4.18GB used: 0.00GB (0%) fs: swap dev: /dev/sdb5 label: N/A
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 143 Uptime: 2 min Memory: 219.4/3844.1MB Init: systemd runlevel: 5 Gcc sys: N/A
           Client: Unknown : sudo inxi: 2.2.35
```

I then re-ran the nine trouble-shooting commands above and three produced results different from Lubuntu 17.04:

```
--> dpkg -l network-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name            Version                Architecture Description
+++-===============-======================-============-=========================================================
ii  network-manager 1.2.6-0ubuntu0.16.04.1 amd64        network management framework (daemon and userspace tools)

--> cat /var/log/syslog | grep etwork | tail -n 10
Aug  5 20:10:24 raven systemd[1]: Reached target Network is Online.
Aug  5 20:10:24 raven whoopsie[1002]: [20:10:24] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
Aug  5 20:10:24 raven whoopsie[1002]: [20:10:24] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
Aug  5 20:10:24 raven whoopsie[1002]: [20:10:24] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
Aug  5 20:10:26 raven NetworkManager[584]: <info>  [1501989026.4947] manager: WiFi hardware radio set enabled
Aug  5 20:10:26 raven NetworkManager[584]: <info>  [1501989026.4948] manager: WWAN hardware radio set enabled
Aug  5 20:11:10 raven ureadahead[230]: ureadahead:network: Ignored relative path
Aug  5 20:11:10 raven ureadahead[230]: ureadahead:NetworkManager_new.795: Ignored relative path
Aug  5 20:11:10 raven ureadahead[230]: ureadahead:NetworkManager: Ignored relative path
Aug  5 20:11:10 raven ureadahead[230]: message repeated 2 times: [ ureadahead:NetworkManager: Ignored relative path]

--> ps aux | grep etwork
root       584  0.0  0.4 455500 16552 ?        Ssl  20:10   0:00 /usr/sbin/NetworkManager --no-daemon
nobody     793  0.0  0.1  52868  4208 ?        S    20:10   0:00 /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-file=/var/run/NetworkManager/dnsmasq.pid --listen-address=127.0.1.1 --cache-size=0 --conf-file=/dev/null --proxy-dnssec --enable-dbus=org.freedesktop.NetworkManager.dnsmasq --conf-dir=/etc/NetworkManager/dnsmasq.d
mike      3554  0.0  0.0  14224   928 pts/0    S+   20:31   0:00 grep --color=auto etwork
```

So the question, is there something to fix and use 17.04, or do I just be happy with 16.04.3?

No data has been lost, no bytes have been harmed, and this is close to being an academic exercise.
Mike

---

### Post by praseodym on 2017-08-06
Download these files (somehow) and place them into your /home folder

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.043.02-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.043.02-1_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu1_all.deb)

Installation
```

sudo dpkg -i ~/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot

---

### Post by mik3e2 on 2017-08-06
Thanks for the files, I've downloaded them with Mint and put them in a safe place. Now I need to re-install 17.04. What are they supposed to do? What am i looking for?

Thanks again,
Mike

---

### Post by mik3e2 on 2017-08-09
The fix didn't fix the problem so I'm sticking with the previous version.

Mike

---

### Post by praseodym on 2017-08-12
Try the newer version instead:

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.044.02-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.044.02-1_all.deb)

---

