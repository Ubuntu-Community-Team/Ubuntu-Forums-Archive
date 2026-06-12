---
title: "Wireless connection does not appear in network-manager"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by jpbennett on 2006-12-06
I just upgraded from dapper to edgy and my wireless connection disappeared from network-manager. I had wireless working in dapper using ndiswrapper. I saw a [related posting]("http://www.ubuntuforums.org/showthread.php?t=312543&highlight=wireless+no+such+device"), but the recommended solutions didn't work for me.

Here are some diagnostics that might help someone troubleshoot.

```
judy@barbaloot:~$ sudo ifup wlan0
Password:
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
```

```
judy@barbaloot:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4329
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:14:22:97:04:2d
Sending on   LPF/eth0/00:14:22:97:04:2d
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.0.1.1 port 67
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:14:22:97:04:2d
Sending on   LPF/eth0/00:14:22:97:04:2d
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPOFFER from 10.0.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 10.0.1.1
bound to 10.0.1.4 -- renewal in 39600 seconds.

```

```
judy@barbaloot:~$ cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid hal9001

auto eth0
iface eth0 inet dhcp

```

```
judy@barbaloot:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:22:97:04:2D  
          inet addr:10.0.1.4  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe97:42d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2208 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2050 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1950471 (1.8 MiB)  TX bytes:274803 (268.3 KiB)
          Interrupt:217 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

```
judy@barbaloot:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:97:04:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=1.00 duplex=full ip=10.0.1.4 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:dfbfc000-dfbfdfff irq:217
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       resources: iomemory:dfbfe000-dfbfffff irq:10

```

```
judy@barbaloot:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```

```
judy@barbaloot:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by gitargr8 on 2006-12-06
Are you sure wlan0 is configured correctly with ndiswrapper? It isn't showing up when you run ifconfig -a. Post the results of the following: 
```

modprobe -l | grep bcm
ndiswrapper -l

```

I know on my machine, I had to disable the default wifi driver by adding it to the blacklist file, install ndiswrapper, and install the correct driver for my card. Then I was able to use the card.

Hope that helps,
~Ryan

---

### Post by jpbennett on 2006-12-06
Well, I checked and it is in the blacklist file. Just to be sure, I rebooted, undid and repeated the ndiswrapper install. Here are some more clues.

```
judy@barbaloot:~$ sudo modprobe ndiswrapper
Password:
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

```
judy@barbaloot:~$ modprobe -l | grep bcm
/lib/modules/2.6.17-10-386/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko
/lib/modules/2.6.17-10-386/kernel/drivers/media/dvb/frontends/bcm3510.ko
/lib/modules/2.6.17-10-386/kernel/drivers/bluetooth/bcm203x.ko

```

```
judy@barbaloot:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  driver present, hardware present 

```

---

### Post by gitargr8 on 2006-12-06
Its strange that you get an error when you do modprobe ndiswrapper. Perhaps you can try reinstalling ndiwrapper itself? If that doesn't work, though, I'm not sure what else to do instead of reinstalling the OS. 

Also, you've made sure that bcm43xx.ko is in the blacklist file? 

~Ryan

---

### Post by jpbennett on 2006-12-07
Aaah, that was it. The blacklist file had "bcm43xx". I changed it to "bcm43xx.ko" and now the wireless card appears in network manager. It isn't connecting to the network yet, but that's a different problem. Thanks for your help.

---

