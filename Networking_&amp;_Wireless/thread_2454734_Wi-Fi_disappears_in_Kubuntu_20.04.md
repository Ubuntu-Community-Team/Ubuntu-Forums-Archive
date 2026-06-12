---
title: "Wi-Fi disappears in Kubuntu 20.04"
date: 2020-12-04
forum: Networking &amp; Wireless
---

### Post by kunzhut on 2020-12-04
Hello! I have a problem that makes me crazy. I'm a newbie in Linux world, erased Win10, relocated on Kubuntu and I have permanent problem: in unpredictable periods of time Wi-Fi is dropped down, any clicks on Wi-Fi icon don't show the list of networks around and only reboot can help. My wife has another laptop on Win10, she is connected to the same Wi-Fi point and everything is well — it's not the router problem.

KDE Plasma Version: 5.18.5
KDE Frameworks Version: 5.68.0
Qt Version: 5.12.8
Kernel Version: 5.4.0-56-generic

What I've tried:

1. Reinstall drivers for Qualcomm Atheros QCA9377 from Github

2. Reinstall of all Ubuntu packages &#8594;

```
sudo apt-get clean
paste below into reinstall_all.sh
\#\!/bin/bash   
for pkg in `dpkg --get-selections | awk '{print $1}' | egrep -v '(dpkg|apt|mysql|mythtv)'` ; do apt-get -y --force-yes install --reinstall $pkg ; done
sudo chown root:root reinstall_all.sh
sudo chmod 755 reinstall_all.sh
sudo ./reinstall_all.sh

```

3. **sudo apt-get install --reinstall bcmwl-kernel-source**

but I have the same bug, help me, please.

SecureBoot is disabled

**sudo service network-manager restart **doesn't work

**[FONT=monospace][COLOR=#000000]sudo lshw -C network[/COLOR][/FONT]**[FONT=monospace] shows: 
[/FONT]&#8203;```
-network                  
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 10
       serial: 54:e1:ad:c1:72:f2
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000b
t-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multi
cast=yes port=MII
       resources: irq:18 ioport:c000(size=256) memory:f4204000-f4204fff memory:f4200000-f4203fff
  *-network
       description: Wireless interface
       product: QCA9377 802.11ac Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 31
       serial: d4:6a:6a:df:05:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=5.4.0-56-generic firmware=WLAN.TF.2.1-00021-QCARMSWP-1 ip=
192.168.50.57 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:132 memory:f4000000-f41fffff
```

**nmcli device show wlp5s0 | grep IP4.DNS **shows:
```
IP4.DNS[1]:                             8.8.8.8
```

**ifconfig** s[FONT=monospace][COLOR=#000000]hows:[/COLOR]
[/FONT]```
enp4s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 54:e1:ad:c1:72:f2  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2014  bytes 149738 (149.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2014  bytes 149738 (149.7 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.50.57  netmask 255.255.255.0  broadcast 192.168.50.255
        inet6 fe80::c5b:e24:ce0d:5122  prefixlen 64  scopeid 0x20<link>
        ether d4:6a:6a:df:05:13  txqueuelen 1000  (Ethernet)
        RX packets 66135  bytes 60494402 (60.4 MB)
        RX errors 0  dropped 1271  overruns 0  frame 0
        TX packets 35370  bytes 6700045 (6.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```[FONT=monospace]
[/FONT]

---

