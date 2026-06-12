---
title: "No joy connecting ethernet to my Dell G5 with a Killer E2400 NIC"
date: 2020-08-13
forum: Networking &amp; Wireless
---

### Post by livelyc on 2020-08-13
Hello everyone,

I'm running Ubuntu 20.04 (Linux only) on my Dell G5.  I can't connect using the Killer E2400 built in Ethernet adapter.  I have a professionally certified gigabit connection to my router. I have browsed several support threads related to this Ethernet adapter, but they all seem to be aimed at far older releases.  I'm honestly shocked that by 2020,  people are still having issues with this,  but I digress.  

[SIZE=4]_**The NIC functions as it should when booted from a Live Image of Ubuntu 20.04.1 on a thumb drive.**_[/SIZE]

I have verified that the NIC is enabled in the BIOS,
I added "iomms=soft" to grub,
I created /etc/udev/rules.d/99-alx.rules file and added:
```
ACTION=="add", ATTRS{idVendor}=="1969", ATTRS{idProduct}=="e0a1",  RUN+="/sbin/modprobe alx" RUN+="/bin/sh -c 'echo 1969 e0a1 >  /sys/bus/pci/drivers/alx/new_id'"
```

output of ifconfig
```
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 797  bytes 106296 (106.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 797  bytes 106296 (106.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp0s20f3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.42.193  netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 fe80::b6fe:ff13:19a8:4473  prefixlen 64  scopeid 0x20<link>
        ether a0:51:0b:62:03:bd  txqueuelen 1000  (Ethernet)
        RX packets 2162  bytes 1438735 (1.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1551  bytes 263544 (263.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

Output of lsmod | grep alx
```
alx                    49152  0
mdio                   16384  1 alx
```

Output of dmesg | grep alx
```
[    0.984440] alx 0000:3c:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [d8:d0:90:42:8a:2b]
[    1.014802] alx 0000:3c:00.0 enp60s0: renamed from eth0
```

I'm now at a loss, someone assist?  I will post any information requested.

---

### Post by chili555 on 2020-08-13
Please show us:

```
lspci -nnk | grep 0200 -A3
dmesg | grep -e alx -e enp
dmesg | grep 3c:00
```From both the working live USB session and the not-working HDD install.

> I created /etc/udev/rules.d/99-alx.rules fileWhy is this needed? The default alx driver covers your device:

```
$ modinfo alx | grep E0A1
alias:          pci:v0000[COLOR="#FF0000"]1969[/COLOR]d0000[COLOR="#FF0000"]E0A1[/COLOR]sv*sd*bc*sc*i*
```

---

