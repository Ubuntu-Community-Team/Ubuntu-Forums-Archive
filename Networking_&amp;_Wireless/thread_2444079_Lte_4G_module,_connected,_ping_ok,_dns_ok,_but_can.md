---
title: "Lte 4G module, connected, ping ok, dns ok, but can't browse internet"
date: 2020-05-24
forum: Networking &amp; Wireless
---

### Post by attix84 on 2020-05-24
Hello everyone,
I'm new to this forum but I've been using ubuntu (now Kubuntu) for quite a while, before posting here I made a lot of research but wasn't able to solve my problem, hope someone here can help me getting things to work.

I have this Lenovo T410 notebook, it had an old mpcie GSM module, I decided to replace it with a new 4G one, on Windows 10 as I started it installed and configured right away, I didn't even had to set my provider apn.

Also on Kubuntu it installed and connected right away, a new usb ethernet adapter was created, but I could not browse the web.

In the terminal I can ping a DNS (8.8.8.8), and even a URL ([www.google.com]("http://www.google.com") and any other web address), but if I try to download a file with wget it get stuck.

I changed some settings like "net.ipv4.ip_forward = 1", and also firewall rules but no luck, I now have a fresh install, I don't know much about networks, so I need some help to figure out where is the issue.

Here some info, maybe can be helpful

```

kub@kub-ThinkPad-T410:~$ lsusb
Bus 002 Device 003: ID 1546:1146 U-Blox AG <----This is the modem
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. BCM2045B (BDC-2.1)
Bus 001 Device 003: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse (M-BT58)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

```

kub@kub-ThinkPad-T410:~$ usb-devices
......
T:  Bus=02 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1546 ProdID=1146 Rev=01.00
S:  Manufacturer=u-blox
S:  Product=MODEM-LTE
S:  SerialNumber=000000000100
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#=0x0 Alt= 0 #EPs= 1 Cls=e0(wlcon) Sub=01 Prot=03 Driver=rndis_host
I:  If#=0x1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=rndis_host
I:  If#=0x2 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#=0x3 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

```

```

kub@kub-ThinkPad-T410:~$ ifconfig 
enp0s25: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether f0:de:f1:40:f0:92  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf2600000-f2620000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3054  bytes 327198 (327.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3054  bytes 327198 (327.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

usb0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.100  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::8ccd:eaff:fee5:47b4  prefixlen 64  scopeid 0x20<link>
        ether 8e:cd:ea:e5:47:b4  txqueuelen 1000  (Ethernet)
        RX packets 2540  bytes 1069731 (1.0 MB)
        RX errors 451  dropped 0  overruns 0  frame 450
        TX packets 1991  bytes 724479 (724.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:24:d7:8d:fa:74  txqueuelen 1000  (Ethernet)
        RX packets 38349  bytes 41872300 (41.8 MB)
        RX errors 0  dropped 970  overruns 0  frame 0
        TX packets 30302  bytes 4379753 (4.3 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

```

kub@kub-ThinkPad-T410:~$ ip route list
default via 192.168.1.1 dev usb0 proto dhcp metric 100 
169.254.0.0/16 dev usb0 scope link metric 1000 
192.168.1.0/24 dev usb0 proto kernel scope link src 192.168.1.100 metric 100 


kub@kub-ThinkPad-T410:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    100    0        0 usb0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 usb0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 usb0

```

```

kub@kub-ThinkPad-T410:~$ ping -c 5 www.google.com
PING www.google.com (172.217.21.68) 56(84) bytes of data.
64 bytes from fra07s31-in-f68.1e100.net (172.217.21.68): icmp_seq=1 ttl=53 time=48.6 ms
64 bytes from fra07s31-in-f68.1e100.net (172.217.21.68): icmp_seq=2 ttl=53 time=56.0 ms
64 bytes from fra07s31-in-f68.1e100.net (172.217.21.68): icmp_seq=3 ttl=53 time=64.9 ms
64 bytes from fra07s31-in-f68.1e100.net (172.217.21.68): icmp_seq=4 ttl=53 time=53.7 ms
64 bytes from fra07s31-in-f68.1e100.net (172.217.21.68): icmp_seq=5 ttl=53 time=42.2 ms

--- www.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 42.173/53.094/64.890/7.580 ms

```

```

kub@kub-ThinkPad-T410:~$ wget -O /dev/null http://speedtest.wdc01.softlayer.com/downloads/test10.zip
--2020-05-24 17:34:27--  http://speedtest.wdc01.softlayer.com/downloads/test10.zip
Resolving speedtest.wdc01.softlayer.com (speedtest.wdc01.softlayer.com)... 158.85.230.20, 2607:f0d0:3006:6c::4
Connecting to speedtest.wdc01.softlayer.com (speedtest.wdc01.softlayer.com)|158.85.230.20|:80... connected.
HTTP request sent, awaiting response...

```

---

