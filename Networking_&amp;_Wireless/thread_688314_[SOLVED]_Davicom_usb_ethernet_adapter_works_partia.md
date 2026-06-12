---
title: "[SOLVED] Davicom usb ethernet adapter works partially"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by claudio4j on 2008-02-05
Hi folks, I am having some issues related to the use of a usb ethernet adapter, its a davicom.
The linux is gutsy (kubuntu) with the latest updates applied. Kernel version 2.6.22-14-generic

See below the specifications and settings.

What I found weird, some websites connect to, but others sites doesn't connect, the firefox, displays at status bar "waiting data" forever. Websites such as google.com works fine, but many others I try doesn't work (facebook, sun.com, microsoft.com, ubuntuforums.com)
Currently I have eth0 (usb ethernet) and eth1 (wireless). eth1 works fine.

I saw at ifconfig, there are a lot of dropped and errors at RX transmissions. (see far below, detailed information)

          RX packets:3501 errors:542 dropped:170 overruns:138 frame:659

I will do some debug with wireshark.

But if you need some more info, don't be afraid to ask.

[I see another use have a similar problem]("http://ubuntuforums.org/showpost.php?p=3417238&postcount=65")
[http://ubuntuforums.org/showpost.php?p=3417238&postcount=65](http://ubuntuforums.org/showpost.php?p=3417238&postcount=65)

dmfe and tulipe modules are not loaded
ipv6 is disabled at linux and firefox

Those threads doesn't solve the issue or doesn't apply
[[SOLVED] Davicom DM9601 USB 10/100 Ethernet]("http://ubuntuforums.org/showthread.php?t=483189")
[http://ubuntuforums.org/showthread.php?t=483189](http://ubuntuforums.org/showthread.php?t=483189)

[How to fix problem with Davicom ethernet adapter.]("http://ubuntuforums.org/showthread.php?t=186430")
[http://ubuntuforums.org/showthread.php?t=186430](http://ubuntuforums.org/showthread.php?t=186430)

I can ping DNS servers with good response times.

```
$ cat /etc/resolv.conf
search claudius.com.br
nameserver 192.168.1.1
```

192.168.1.1 is the router device, where it points to the following DNS

DNS 1:  200.167.216.14
DNS 2:  200.167.216.15
```

$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=127 time=3.89 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=127 time=1.72 ms

$ ping 200.167.216.15
PING 200.167.216.15 (200.167.216.15) 56(84) bytes of data.
64 bytes from 200.167.216.15: icmp_seq=1 ttl=252 time=10.1 ms
64 bytes from 200.167.216.15: icmp_seq=2 ttl=252 time=11.5 ms
64 bytes from 200.167.216.15: icmp_seq=3 ttl=252 time=16.6 ms
```

```
$ lshw -C network
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:60:6e:50:43:a0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=dm9601 driverversion=22-Aug-2005 firmware=Davicom DM9601 USB Ethernet ip=192.168.1.10 multicast=yes
```

====================================================

$ lsusb
Bus 003 Device 002: ID 0a46:9601 Davicom Semiconductor, Inc.

```
$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:60:6E:50:43:A0
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3501 errors:542 dropped:170 overruns:138 frame:659
          TX packets:2482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1403464 (1.3 MB)  TX bytes:509632 (497.6 KB)
```

```
$ cat /etc/network/interfaces
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

```
$ route -nv
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
```

====================================================

```
$ lsmod |grep dm9
dm9601                 10624  0
usbnet                 19976  1 dm9601
mii                     6528  2 dm9601,usbnet
usbcore               138632  6 dm9601,usbnet,usbhid,ehci_hcd,uhci_hcd
```
====================================================

```
$ cat /etc/modules
fuse
lp
sbp2
```


==> /var/log/syslog <==
```
Feb  2 18:52:51 panzer kernel: [  175.556000] usb 3-1: new full speed USB device using uhci_hcd and address 3
Feb  2 18:52:51 panzer kernel: [  175.732000] usb 3-1: configuration #1 chosen from 1 choice
Feb  2 18:52:51 panzer kernel: [  175.900000] eth0: register 'dm9601' at usb-0000:00:1d.2-1, Davicom DM9601 USB Ethernet, 00:60:6e:50:43:a0
Feb  2 18:52:51 panzer kernel: [  175.900000] usbcore: registered new interface driver dm9601
Feb  2 18:52:51 panzer kernel: [  175.940000] eth0: link down
Feb  2 18:53:11 panzer kernel: [  195.524000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
```

---

### Post by claudio4j on 2008-02-05
I did some bit of debug with wireshark and see some lost packets

I turned off upnp discovery at the router device and turned of any networking program running at linux, to make it easy to debug.

Then I fired up ssh claudius.com.br and see some lost packets at wireshark

See attached screenshots, really strange.

Anybody have some idea, whats happening ?

Thanks

Claudio

---

### Post by claudio4j on 2008-02-07
After more tests with ssh (no success) and samba shares, I see a similar issue to [1], where I am able to access websites with very small pages and samba shares with small number of files. 

I see a similar issue at linuxquestions.org

1 [http://www.linuxquestions.org/questions/linux-networking-3/a-strange-usb-nic-547397/](http://www.linuxquestions.org/questions/linux-networking-3/a-strange-usb-nic-547397/)

Now its time to take a loot at DM9601.c source file.

Have fun !

Claudio Miranda

---

### Post by claudio4j on 2008-02-07
I have to say that it works now !!!!

Oh Lord, since 3 years ago, I didn't need to compile anything to make basic things (networking) work on linux  (I use and work with linux since 1998).

So, the dm9601 module at linux kernel doesn't works as expected, see my previous comments. 

I downloaded the module from davicom.tw website and compiled and installed it.

[http://www.davicom.com.tw/big5/download/Driver/driver_9601.htm](http://www.davicom.com.tw/big5/download/Driver/driver_9601.htm)

It's a module to 2.6 kernel.

There will be some warning, when run 'make', but no errors, the 

vi /etc/modules
# mode=5 100 m full duplex
options dm9601 mode=5

copy the new dm9601.ko module to kernel modules /lib/modules/2.6.22-14-generic/kernel/drivers/net/usb/dm9601.ko
Please, backup the previous one

Have fun, surfing again....

---

