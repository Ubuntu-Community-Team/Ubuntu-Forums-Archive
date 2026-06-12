---
title: "Installation of USB WLAN adapter AWUS036ACH difficulties"
date: 2018-08-31
forum: Networking &amp; Wireless
---

### Post by zardaxt on 2018-08-31
Hey Everyone,

I have problems installing the driver for the device **AWUS036ACH**.

I tried to use the driver from: [https://github.com/aircrack-ng/rtl8812au](https://github.com/aircrack-ng/rtl8812au)

So I follow the instructions 

```

sudo apt-get install build-essential
sudo apt-get install bc

```

works. But when I try to install the linux-headers with

```

sudo apt-get install linux-headers-`uname -r`

```

I get:

```

kolai@nikolai:~/Desktop/Kernel$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-4.18.5-041805-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-4.18.5-041805-generic' has no installation candidate

```

When I try to install the driver with 

```
sudo ./dkms-install.sh
```

it fails and the logs say:

```

DKMS make.log for rtl8812au-5.1.5 for kernel 4.18.5-041805-generic (x86_64)
Fr 31. Aug 14:28:27 CEST 2018
make -j 4 ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.5-041805-generic/build M=/var/lib/dkms/rtl8812au/5.1.5/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.5-041805-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target 'Makefile'.  Stop.
make[1]: Leaving directory '/usr/src/linux-headers-4.18.5-041805-generic'
Makefile:1918: recipe for target 'modules' failed
make: *** [modules] Error 2



```


I installed the latest kernel 4.18.5 a week ago [FONT=SFMono-Regular]from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).[/FONT]

[FONT=SFMono-Regular]I downloaded the necessary files and I try to reinstall the headers which fails for me:


[/FONT]```


nikolai@nikolai:~/Desktop/Kernel$ ll
total 53548
drwxrwxr-x 2 nikolai nikolai     4096 Aug 31 14:24 ./
drwxr-x--- 7 nikolai nikolai     4096 Aug 27 01:38 ../
-rw-rw-r-- 1 nikolai nikolai  1123928 Aug 27 01:14 linux-headers-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb
-rw-rw-r-- 1 nikolai nikolai  8157428 Aug 27 01:14 linux-image-unsigned-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb
-rw-rw-r-- 1 nikolai nikolai 45519844 Aug 27 01:14 linux-modules-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb
nikolai@nikolai:~/Desktop/Kernel$ sudo dpkg -i linux-headers-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb 
Selecting previously unselected package linux-headers-4.18.5-041805-generic.
(Reading database ... 468825 files and directories currently installed.)
Preparing to unpack linux-headers-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb ...
Unpacking linux-headers-4.18.5-041805-generic (4.18.5-041805.201808241320) ...
dpkg: dependency problems prevent configuration of linux-headers-4.18.5-041805-generic:
 linux-headers-4.18.5-041805-generic depends on linux-headers-4.18.5-041805; however:
  Package linux-headers-4.18.5-041805 is not installed.


dpkg: error processing package linux-headers-4.18.5-041805-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-4.18.5-041805-generic



```[FONT=SFMono-Regular]


This is circular reasoning for me and I don't get it:
[/FONT]```

dpkg: dependency problems prevent configuration of linux-headers-4.18.5-041805-generic:
 linux-headers-4.18.5-041805-generic depends on linux-headers-4.18.5-041805; however:
  Package linux-headers-4.18.5-041805 is not installed.

```


[FONT=SFMono-Regular]What should I do next?[/FONT]

Here is the outpout of wireless-info script: [https://paste.ubuntu.com/p/JMYMkDCJQw/](https://paste.ubuntu.com/p/JMYMkDCJQw/)

---

### Post by chili555 on 2018-08-31
It may help to try to install them both simultaneously with a * wildcard: ```
sudo dpkg -i linux-headers*.deb
```

---

### Post by zardaxt on 2018-08-31
Many thanks!

I needed to install both the files 
```

linux-headers-4.18.5-041805_4.18.5-041805.201808241320_all.deb 
linux-headers-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb 

```

I thought that the file linux-headers-4.18.5-041805_4.18.5-041805.201808241320**_all**.deb was a additional file that included all three kernel files: headers, image and modules. This was my thought mistake.

Installation was successful:
```

nikolai@nikolai:~/Desktop/Kernel$ sudo dpkg -i linux-headers-4.18.5-041805_4.18.5-041805.201808241320_all.deb 
Selecting previously unselected package linux-headers-4.18.5-041805.
(Reading database ... 480254 files and directories currently installed.)
Preparing to unpack linux-headers-4.18.5-041805_4.18.5-041805.201808241320_all.deb ...
Unpacking linux-headers-4.18.5-041805 (4.18.5-041805.201808241320) ...
Setting up linux-headers-4.18.5-041805 (4.18.5-041805.201808241320) ...
nikolai@nikolai:~/Desktop/Kernel$ sudo dpkg -i linux-headers-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb 
(Reading database ... 497189 files and directories currently installed.)
Preparing to unpack linux-headers-4.18.5-041805-generic_4.18.5-041805.201808241320_amd64.deb ...
Unpacking linux-headers-4.18.5-041805-generic (4.18.5-041805.201808241320) over (4.18.5-041805.201808241320) ...
Setting up linux-headers-4.18.5-041805-generic (4.18.5-041805.201808241320) ...
/etc/kernel/header_postinst.d/dkms:
Secure Boot not enabled on this system.

```

Then also the installation of the driver worked as the logfile ```
/var/lib/dkms/rtl8812au/kernel-4.18.5-041805-generic-x86_64/log/make.log
``` proves:
```

nikolai@nikolai:~$ cat /var/lib/dkms/rtl8812au/kernel-4.18.5-041805-generic-x86_64/log/make.log 
DKMS make.log for rtl8812au-5.1.5 for kernel 4.18.5-041805-generic (x86_64)
Fr 31. Aug 15:08:18 CEST 2018
make -j 4 ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.18.5-041805-generic/build M=/var/lib/dkms/rtl8812au/5.1.5/build  modules
make[1]: Entering directory '/usr/src/linux-headers-4.18.5-041805-generic'
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_cmd.o
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_security.o
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_debug.o
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_io.o
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_ioctl_query.o
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_ioctl_set.o
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_ieee80211.o
[...]
  CC [M]  /var/lib/dkms/rtl8812au/5.1.5/build/core/rtw_mp.o
  LD [M]  /var/lib/dkms/rtl8812au/5.1.5/build/8814au.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /var/lib/dkms/rtl8812au/5.1.5/build/8814au.mod.o
  LD [M]  /var/lib/dkms/rtl8812au/5.1.5/build/8814au.ko
make[1]: Leaving directory '/usr/src/linux-headers-4.18.5-041805-generic'

```

Output of nmcli
```

nikolai@nikolai:~$ nmcli
wlx{{MAC ADDRESS}}: connected to TC-3C110 1
        "Realtek 802.11n NIC"
        wifi (8812au), 00:C0:XXXXXXXX, hw, mtu 1500
        ip6 default
        inet6 2a02:2450:102e:79:2982:607b:d711:fcf0/64
        inet6 2a02:2450:102e:79:e80a:9c31:529f:4449/64
        inet6 fe80::eafa:30ee:e16f:c31a/64
        route6 2a02:2450:102e:79::/64
        route6 ::/0
        route6 ff00::/8
        route6 fe80::/64
        route6 fe80::/64
        route6 2a02:2450:102e:79::/64



```


I can now use both network devices, the USB WLAN adapter and my built-in laptop wireless card. However it seems that the built in wlan device does a slightly better job, but I need to experiment now anyways.

ifconfig outpout
```

wlx{{MAC ADDRESS}}: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.6  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::eafa:30ee:e16f:c31a  prefixlen 64  scopeid 0x20<link>
        inet6 2a02:2450:102e:79:e80a:9c31:529f:4449  prefixlen 64  scopeid 0x0<global>
        inet6 2a02:2450:102e:79:2982:607b:d711:fcf0  prefixlen 64  scopeid 0x0<global>
        ether {{MAC ADDRESS}}  txqueuelen 1000  (Ethernet)
        RX packets 2272  bytes 2403371 (2.4 MB)
        RX errors 0  dropped 3  overruns 0  frame 0
        TX packets 3379  bytes 466935 (466.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

---

