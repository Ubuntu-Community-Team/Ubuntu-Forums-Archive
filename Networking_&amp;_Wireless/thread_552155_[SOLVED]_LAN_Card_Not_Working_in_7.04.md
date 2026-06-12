---
title: "[SOLVED] LAN Card Not Working in 7.04"
date: 2007-09-16
forum: Networking &amp; Wireless
---

### Post by omariqbalnaru on 2007-09-16
I connect to the internet using a 10mbps HALF DUPLEX LAN connection. If I change the settings to 100mbps or Automatic even in windows, I cannot connect to the network. Now I cannot connect to my LAN  in 7.04. So, please help...

---

### Post by noob12 on 2007-09-16
Try this command.  This assumes your interface is called eth0 which is the most likely.

```

sudo ifdown eth0
sudo ethtool -s eth0 speed 10 duplex half autoneg off
sudo ifup eth0

```

See if this works for you.  If this works you can set it to occur automatically by adding a new line
```

pre-up ethtool -s eth0 speed 10 duplex half autoneg off

```
*immediately after* the **iface eth0** line in the file **/etc/network/interfaces**.

---

### Post by omariqbalnaru on 2007-09-17
This is what I got in the terminal:

naru@ubuntu:~$ sudo ifdown eth0 RTNETLINK answers: No such process There is already a pid file /var/run/dhclient.eth0.pid with pid 7262 
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/Listening](http://www.isc.org/sw/dhcp/Listening) on LPF/eth0/4c:00:10:38:39:46
Sending on   LPF/eth0/4c:00:10:38:39:46
Sending on   Socket/fallback
naru@ubuntu:~$ sudo ethtool -s eth0 speed 10 duplex half autoneg off
naru@ubuntu:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Listening on LPF/eth0/4c:00:10:38:39:46
Sending on   LPF/eth0/4c:00:10:38:39:46
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by omariqbalnaru on 2007-09-17
Anybody, please help...

---

### Post by noob12 on 2007-09-17
Can you provide some information about which card and driver you are using?

This will tell us:
```

lspci -nn

sudo lshw -C network

```

Also, after you run the commands, can you check the status of the ethernet connection by typing
```

sudo ethtool eth0

```

In Windows, are you assigning an address statically or are you getting an address "automatically" from DHCP?  If you do not know, you can post the output of **ipconfig /all** and **route print** commands run on the Windows box.

---

### Post by omariqbalnaru on 2007-09-17
naru@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub 

Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P PCI to AGP Controller [8086:2571] 

(rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI 

Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI 

Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI 

Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI 

Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI 

Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge 

[8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller 

[8086:24db] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801EB (ICH5) SATA Controller [8086:24d1] 

(rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller 

[8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 

Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AQ [Radeon 9600] 

[1002:4151]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AQ [Radeon 9600] (Secondary) 

[1002:4171]
02:04.0 Communication controller [0780]: Apache Micro Peripherals Inc Unknown device 

[141a:1035] (rev 89)
02:05.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ 

[10ec:8139] (rev 10)

naru@ubuntu:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@02:05.0
       logical name: eth0
       version: 10
       serial: 4c:00:10:38:39:46
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 

100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 

duplex=full latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b800-b8ff iomemory:ff9efc00-ff9efcff irq:20

naru@ubuntu:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: no

In Windows, my address is automatically assigned by DHCP...

---

### Post by noob12 on 2007-09-17
See the **link detected: no** in the **ethtool** output?   That means the driver thinks the link is down.  Since your link is probably connected, you may have the issue described here:  [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448) 

Try that.  It has been reported by two other users to work for 8139 cards as well.

---

### Post by omariqbalnaru on 2007-09-18
Thanks alot! It is now working smoothly... Actually I am a Computer Sciences student and have to do an Operating Systems assignment using Linux...

---

### Post by noob12 on 2007-09-18
Great!  Please mark the thread solved and good luck.

---

