---
title: "No WIFI on Asus X455L Ubuntu 1704 (fresh install)"
date: 2017-06-11
forum: Networking &amp; Wireless
---

### Post by cantervilotis on 2017-06-11
Hi everyone. I am not able to start de wifi, the ethernet connection works perfect, but i cant see any of the wifi networks. In the same laptop i have installed windows and it works ok.


Maybe this info could be usefull

```
root@user-X455LJ:~# exec sudo -i
root@user-X455LJ:~# ifconfig -a
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.53  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::ecd7:c00d:ccc0:930b  prefixlen 64  scopeid 0x20<link>
        ether 9c:5c:8e:3b:64:01  txqueuelen 1000  (Ethernet)
        RX packets 27054  bytes 29462937 (29.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 27367  bytes 2567778 (2.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Bucle local)
        RX packets 359  bytes 26223 (26.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 359  bytes 26223 (26.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@user-X455LJ:~# ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.53  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::ecd7:c00d:ccc0:930b  prefixlen 64  scopeid 0x20<link>
        ether 9c:5c:8e:3b:64:01  txqueuelen 1000  (Ethernet)
        RX packets 27054  bytes 29462937 (29.4 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 27367  bytes 2567778 (2.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Bucle local)
        RX packets 359  bytes 26223 (26.2 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 359  bytes 26223 (26.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

root@user-X455LJ:~# iwconfig
lo        no wireless extensions.

enp2s0    no wireless extensions.

root@user-X455LJ:~# lspci
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:04.0 Signal processing controller: Intel Corporation Broadwell-U Processor Thermal Subsystem (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Broadcom Limited BCM43142 802.11b/g/n (rev 01)
04:00.0 3D controller: NVIDIA Corporation GK208M [GeForce 920M] (rev a1)
root@user-X455LJ:~# lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 005: ID 04ca:2006 Lite-On Technology Corp. Broadcom BCM43142A0 Bluetooth Device
Bus 001 Device 002: ID 04f2:b483 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@user-X455LJ:~# inxi -N

```


thank you for your help!

---

### Post by wildmanne39 on 2017-06-11
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by wildmanne39 on 2017-06-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by cantervilotis on 2017-06-11
Hi again, it worked with this

> sudo apt-get install bcmwl-kernel-source broadcom-sta-common broadcom-sta-source

SOLVED!!!

---

