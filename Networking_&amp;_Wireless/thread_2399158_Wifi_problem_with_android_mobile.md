---
title: "Wifi problem with android mobile"
date: 2018-08-22
forum: Networking &amp; Wireless
---

### Post by GirishSharma on 2018-08-22
```

girish@gk:~$ uname -a
Linux gk 4.15.0-32-generic #35-Ubuntu SMP Fri Aug 10 17:58:07 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

I am facing very strange issue. After searching google, I am writing here. I am running ubuntu 18.04 and using internet from my mobile's hotspot by a usb wifi receiver. It sometime detects wifi and remains active for 5-6 minutes and than randomly disconnects and sometime it do not detects wifi. I have followed this link ([https://askubuntu.com/questions/457061/ralink-mt7601u-148f7601-wi-fi-adapter-installation](https://askubuntu.com/questions/457061/ralink-mt7601u-148f7601-wi-fi-adapter-installation)) too but it ended some Linux error 2 :

```

girish@gk:~/mt7601usta/src$ make
make -C tools
make[1]: Entering directory '/home/girish/mt7601usta/src/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory '/home/girish/mt7601usta/src/tools'
/home/girish/mt7601usta/src/tools/bin2h
cp -f os/linux/Makefile.6 /home/girish/mt7601usta/src/os/linux/Makefile
make -C /lib/modules/4.15.0-32-generic/build SUBDIRS=/home/girish/mt7601usta/src/os/linux modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-32-generic'
Makefile:976: "Cannot use CONFIG_STACK_VALIDATION=y, please install libelf-dev, libelf-devel or elfutils-libelf-devel"
  CC [M]  /home/girish/mt7601usta/src/os/linux/../../os/linux/rt_linux.o
/home/girish/mt7601usta/src/os/linux/../../os/linux/rt_linux.c: In function ‘__RTMP_OS_Init_Timer’:
/home/girish/mt7601usta/src/os/linux/../../os/linux/rt_linux.c:120:3: error: implicit declaration of function ‘init_timer’; did you mean ‘init_timers’? [-Werror=implicit-function-declaration]
   init_timer(pTimer);
   ^~~~~~~~~~
   init_timers
/home/girish/mt7601usta/src/os/linux/../../os/linux/rt_linux.c:121:9: error: ‘OS_NDIS_MINIPORT_TIMER {aka struct timer_list}’ has no member named ‘data’
   pTimer->data = (unsigned long)data;
         ^~
/home/girish/mt7601usta/src/os/linux/../../os/linux/rt_linux.c:122:20: error: assignment from incompatible pointer type [-Werror=incompatible-pointer-types]
   pTimer->function = function;
                    ^
cc1: some warnings being treated as errors
scripts/Makefile.build:332: recipe for target '/home/girish/mt7601usta/src/os/linux/../../os/linux/rt_linux.o' failed
make[2]: *** [/home/girish/mt7601usta/src/os/linux/../../os/linux/rt_linux.o] Error 1
Makefile:1552: recipe for target '_module_/home/girish/mt7601usta/src/os/linux' failed
make[1]: *** [_module_/home/girish/mt7601usta/src/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-32-generic'
Makefile:418: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
girish@gk:~/mt7601usta/src$ 

```

This is my further info :

```

girish@gk:~$ uname -a
Linux gk 4.15.0-32-generic #35-Ubuntu SMP Fri Aug 10 17:58:07 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
girish@gk:~$ lsusb
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 13ba:0018 PCPlay Barcode PCP-BCG4209
Bus 003 Device 002: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
girish@gk:~$ ifconfig
enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 60:45:cb:a3:6f:8f  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xf7100000-f7120000  


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 465  bytes 37918 (37.9 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 465  bytes 37918 (37.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlx00e12900f694: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.43.233  netmask 255.255.255.0  broadcast 192.168.43.255
        inet6 fe80::d1a:d6b3:cf4e:85a  prefixlen 64  scopeid 0x20<link>
        ether 00:e1:29:00:f6:94  txqueuelen 1000  (Ethernet)
        RX packets 3  bytes 637 (637.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 221  bytes 18293 (18.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


girish@gk:~$

```

---

