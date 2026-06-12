---
title: "Wireless connection does not appear in network-manager"
date: 2006-12-04
forum: Networking &amp; Wireless
---

### Post by xoai on 2006-12-04
I have used wireless network before and It had still apeared in network-manager till I unchecked the checkbox in System > Administrator > Networking so when I rebooted, It disapeared >_< I checked by the command
```

sudo ifup wlan0
```

and the result is

```
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

PS: I am running Ubuntu on Macbook

---

### Post by dbott67 on 2006-12-04
**TRY RESTARTING NETWORK**

```
dbott@edgy:~$ sudo/etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          
There is already a pid file/var/run/dhclient.eth0.pidwith pid 3172
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file/var/run/dhclient.eth0.pidwith pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 242774 seconds.
There is already a pid file/var/run/dhclient.eth1.pidwith pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
There is already a pid file/var/run/dhclient.eth2.pidwith pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR?while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file/var/run/dhclient.ath0.pidwith pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
There is already a pid file/var/run/dhclient.wlan0.pidwith pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
                                                                         [ ok ]

```
or use this command
```
dbott@edgy:~$ sudo ifdown eth0 && sudo ifup eth0
There is already a pid file/var/run/dhclient.eth0.pidwith pid 6838
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
There is already a pid file/var/run/dhclient.eth0.pidwith pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:50:ba:c0:a7:55
Sending on   LPF/eth0/00:50:ba:c0:a7:55
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 239212 seconds.
```

If it still doesn't work, can you post the output of the following commands:

```
cat/etc/network/interfaces
```

Here's mine as an example:

```
dbott@dapper:~$ cat/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid bott
wireless-key s:mysecretwepkey
```

This command shows ALL network interfaces on the system (whether enabled or not):

```
ifconfig -a
```

```
dbott@dapper:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:C5:0C:AD:XX
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:438044459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438044459 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1712747473 (1.5 GiB)  TX bytes:1712747473 (1.5 GiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:16:CE:31:88:XX
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ceff:fe31:886f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:738503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:658372626 (627.8 MiB)  TX bytes:64530804 (61.5 MiB)
          Interrupt:169 Memory:dfcfc000-dfd00000
```

This command outputs the network hardware detected:

```
sudo lshw -C network
```

Here's mine for comparison:

```
dbott@dapper:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:16:ce:31:88:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.25 firmware=Broadcom,11/02/2005, 4.10.40.0 ip=192.168.1.105 link=yes multicast=yes wireless=IEEE 802.11b
       resources: iomemory:dfcfc000-dfcfffff irq:169
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:0c:ad:05
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:df9fe000-df9fffff irq:217

```

This command tries to detect wireless access points using each NIC:

```
iwlist scanning
```

```
dbott@dapper:~$ iwlist scanning

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :

Cell 01 - Address: 00:40:05:B2:AF:YY
              ESSID:"bott"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=34/100  Signal level=39/100  Noise level=11/100
              Encryption key:on
              Bit Rate:22 Mb/s

Cell 02 - Address: 00:05:5D:FA:B2:XX
              ESSID</size:small?:"soni"
              Mode:Master
              Frequency:2.437 GHz (Channel 6)
              Quality=24/100  Signal level=27/100  Noise level=12/100
              Encryption key:on
              Bit Rate:54 Mb/s

sit0      Interface doesn't support scanning.
```

This command prints out your routing table:

```
route -n
```

```
dbott@dapper:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

And finally, this command prints out PCI information:

```
lspci
```

```
dbott@dapper:~$ lspci

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 7145
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:03:01.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:03:01.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
?000:03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
[COLOR="Red"]0000:0b:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
[/COLOR]
```

```
dbott@edgy:~$ cat/etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:50:ba:c0:a7:55 arp 1
```

---

### Post by xoai on 2006-12-04
Thank you for reply soon

I restarted my network but it still dispaears in networ-manager. Do I need to reboot?

Here are my results when run your reommended commands

```
cat/etc/network/interfaces
```

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp


iface ath0 inet dhcp
wireless-essid Aqua Wifi Cafe

auto wlan0
iface wlan0 inet dhcp

auto eth0

```

```
ifconfig -a
```

```

eth0      Link encap:Ethernet  HWaddr 00:17:F2:27:82:65  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fe27:8265/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3814 (3.7 KiB)  TX bytes:5040 (4.9 KiB)
          Interrupt:201 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:395714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:395714 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:444946232 (424.3 MiB)  TX bytes:444946232 (424.3 MiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

```
sudo lshw -c network
```

```

  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:27:82:65
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=sky2 driverversion=1.6.1 duplex=full firmware=N/A ip=192.168.1.33 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: iomemory:90100000-90103fff ioport:1000-10ff irq:201
  *-usb
       description: Bluetooth wireless interface
       vendor: Apple Computer, Inc.
       physical id: 1
       bus info: usb@4:1
       version: 19.65
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s


```

```
iwlist scanning
```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

```



```
lspci
```

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Unknown device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

route -n and cat /etc/iftab is normal

---

### Post by dbott67 on 2006-12-04
According to your **/etc/network/interfaces** file, your wireless interface is **ath0** but it is not set to 'auto'.

1. Edit your /etc/network/interfaces file:
```
gksudo gedit /etc/network/interfaces
```

2. Add the following line (in red):
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

[COLOR="Red"]**auto ath0**[/COLOR]
iface ath0 inet dhcp
wireless-essid Aqua Wifi Cafe

auto wlan0
iface wlan0 inet dhcp

auto eth0
```

3. Run the following command to restart network:
```
sudo ifdown ath0 && sudo ifup ath0
```

4. Pray to the gods above! :)

---

### Post by xoai on 2006-12-04
I did as you said but the result is it could not bring up ath0. 

I rebooted to Mac OS and found out the Airport card is not detected. OMG, I thoought I would have to take my Macbook to Apple Care. I removed the battery and tried to remove the airport card but I relized that I dont have enough equipment. When I rebooted second to Ubuntu to tell you my problems, suddenly I see the wireless card is working and now everything is okie :D

anyway thank you very much :D

---

### Post by dbott67 on 2006-12-04
Glad it's working.

The fact that your **/etc/network/interfaces** was missing the 'auto ath0' line just meant that the interface would not be automatically started when the OS booted up.

By adding the line, you told the OS to enable the **ath0** interface everytime the computer starts.

The 2 commands you can use to restart the network (without re-booting) are:
```
sudo/etc/init.d/networking restart
```
or (to specify a specific interface, such as eth0, eth1, ath0, etc.):
```
sudo ifdown ath0 && sudo ifup ath0
```
just replace **ath0** with the appropriate interface.

-Dave

---

### Post by javierfh on 2006-12-06
Hello,

im desperated, im trying to configure my wlan card but there is no way i can make it work.
I have tried several methods from several posts and still nothing.
So would you be so kind to tell me if you see something strange in my logs or ask me to produce you more logs. 
i would really appreciate it..because it seems so messed up. I doesnt seem right to me..and i bet im not that far from getting it right.


Thanks in advance,

Javi


> 

javier@laptoplinux:~$ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 6034
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:30:b4:00:00:00
Sending on   LPF/eth1/00:30:b4:00:00:00
Sending on   Socket/fallback
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Timer expired
SIOCSIFFLAGS: Timer expired
Listening on LPF/eth1/00:30:b4:00:00:00
Sending on   LPF/eth1/00:30:b4:00:00:00
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ ok ]
javier@laptoplinux:~$ 




> 

javier@laptoplinux:~$ sudo ifdown eth0 && sudo ifup eth0
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
javier@laptoplinux:~$ 

javier@laptoplinux:~$ sudo ifdown wlan0 && sudo ifup wlan0
ifdown: interface wlan0 not configured
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.
javier@laptoplinux:~$ 




Here i add the content of /etc/network/interfaces , to be honest seems that the commands at the end..get automatically writen by some process i guess or some of the commands and well to be honest i dont know anymore which one it is the wlan, because eth1 keeps appearing new, no matter if i comment these lines out.

> 

javier@laptoplinux:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

#iface eth0 inet dhcp

#iface eth1 inet dhcp
#wireless-essid FRHOC
#wireless-key s:XXXXXXXX

auto wlan0
iface wlan0 inet dhcp
wireless-essid FRHOC
wireless-key XXXXXXXX




#auto eth1
#auto wlan0

#iface eth0 inet dhcp

#iface eth1 inet dhcp
#wireless-essid FRHOC
#wireless-key XXXXXXXX


iface eth1 inet dhcp
wireless-essid FRHOC
wireless-key XXXXXXXX

auto eth1






> 

javier@laptoplinux:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:02:A5:9A:F9:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:30:B4:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 

lo        Link encap:Local Loopback  
          LOOPBACK  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

javier@laptoplinux:~$ 





> 

javier@laptoplinux:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 41
       serial: 00:02:a5:9a:f9:50
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
       resources: iomemory:d0200000-d0200fff ioport:3000-303f irq:9
  *-network DISABLED
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@03:00.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 multicast=yes wireless=NOT READY!
       resources: iomemory:24000000-24001fff irq:10





> 

javier@laptoplinux:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
sit0      Interface doesn't support scanning.

javier@laptoplinux:~$ 





> 

javier@laptoplinux:~$ route -n
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
javier@laptoplinux:~$ 




> 

javier@laptoplinux:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: d8000000-dfffffff

00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01) (prog-if 00 [UHCI])
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: bus master, medium devsel, latency 0, IRQ 10
        I/O ports at 1860 [size=32]

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=06, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 20000000-21ffffff

00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 1800 [size=16]
        Memory at 22000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 009c
        Flags: medium devsel, IRQ 5
        I/O ports at 1820 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 005c
        Flags: bus master, medium devsel, latency 0, IRQ 5
        I/O ports at 1c00 [size=256]
        I/O ports at 1880 [size=64]

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY (prog-if 00 [VGA])
        Subsystem: Compaq Computer Corporation Unknown device b11b
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 2000 [size=256]
        Memory at d0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at d0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:04.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device 8d89
        Flags: medium devsel, IRQ 255
        Memory at d0210000 (32-bit, non-prefetchable) [disabled] [size=64K]
        I/O ports at 3040 [disabled] [size=8]
        Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Compaq Computer Corporation Unknown device b1b1
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at d0201000 (32-bit, non-prefetchable) [size=2K]
        Memory at d0204000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
        Subsystem: Compaq Computer Corporation Unknown device b103
        Flags: bus master, medium devsel, latency 168, IRQ 10
        Memory at d0202000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 24000000-25fff000
        I/O window 0: 00003400-000034ff
        I/O window 1: 00003800-000038ff
        16-bit legacy interface ports at 0001

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
        Subsystem: Compaq Computer Corporation Unknown device 0093
        Flags: bus master, medium devsel, latency 66, IRQ 9
        Memory at d0200000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
        Subsystem: Accton Technology Corporation SMC2835W V3 EU Wireless Cardbus Adapter
        Flags: bus master, medium devsel, latency 80, IRQ 10
        Memory at 24000000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>






> 

javier@laptoplinux:~$ cat /etc/iftab
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:02:a5:9a:f9:50 arp 1
javier@laptoplinux:~$ 




---

### Post by woopud on 2006-12-06
I'm having the same problem as the user of the second post, hereby my output:

Bert

```
woopud@woopud-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 4495
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:b0:47:92:2e
Sending on   LPF/eth0/00:0f:b0:47:92:2e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:b0:47:92:2e
Sending on   LPF/eth0/00:0f:b0:47:92:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.5 -- renewal in 41222 seconds.
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
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
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
                                                                         [ ok ]
woopud@woopud-laptop:~$ sudo ifdown eth0 && sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5326
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:b0:47:92:2e
Sending on   LPF/eth0/00:0f:b0:47:92:2e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:0f:b0:47:92:2e
Sending on   LPF/eth0/00:0f:b0:47:92:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.0.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.0.1
bound to 192.168.0.5 -- renewal in 37285 seconds.
woopud@woopud-laptop:~$ cat/etc/network/interfaces
bash: cat/etc/network/interfaces: No such file or directory
woopud@woopud-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:47:92:2E  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe47:922e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1864995 (1.7 MiB)  TX bytes:207883 (203.0 KiB)
          Interrupt:185 Base address:0x800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

woopud@woopud-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:47:92:2e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.0.5 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:7000-70ff iomemory:e0108800-e01088ff irq:185
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       resources: iomemory:e0104000-e0105fff irq:217
woopud@woopud-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

woopud@woopud-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
woopud@woopud-laptop:~$ gksudo gedit /etc/network/interfaces

(gedit:5747): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
woopud@woopud-laptop:~$ 

```

---

### Post by dbott67 on 2006-12-06
Hi Javi,

From what I can tell reading your output is that you have 2 interfaces: etho (wired) and eth1 (wireless):
```
javier@laptoplinux:~$ ifconfig -a
**[COLOR="Red"]eth0[/COLOR]** Link encap:Ethernet HWaddr 00:02:A5:9A:F9:50
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

**[COLOR="Red"]eth1[/COLOR]** Link encap:Ethernet HWaddr 00:30:B4:00:00:00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 
```

The other thing I notice is the "NOT READY" status at the end of the **sudo lshw -C network** output.

```
javier@laptoplinux:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@02:08.0
logical name: eth0
version: 41
serial: 00:02:a5:9a:f9:50
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
resources: iomemory:d0200000-d0200fff ioport:3000-303f irq:9
*-network DISABLED
description: Wireless interface
product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
vendor: Intersil Corporation
physical id: 1
bus info: pci@03:00.0
logical name: eth1
version: 01
serial: 00:30:b4:00:00:00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=prism54[/COLOR] multicast=yes [B][COLOR="Red"]wireless=NOT READY!
[/COLOR][/B]resources: iomemory:24000000-24001fff irq:10
```

I take it that you are running Ubuntu on a laptop (javier@laptoplinux).  Many laptops have some sort of button or toggle that you must activate in order to tunr on the wireless capabilities (for example, my Dell 6400 requires FN+F2, while others have a dedicated button or switch).  The associated icon normally looks like a radio tower or similar.  Make sure that the switch is in the ON position.

Here's a few examples:
[IMG]http://dellresell.com/Ebay%20Content/Online%20Content/Laptop%20Parts%20Images/wireless-icon.gif[/IMG] or [IMG]http://images.google.com/images?q=tbn:3d8MVKZixP-wFM:http://supcontent.gateway.com/support.gateway.com/s/Mobile/Gateway/M520/WirelessIcon.gif[/IMG]

[IMG]http://static.flickr.com/69/185533480_9b489d074b_m.jpg[/IMG]

You can also remove the following from your /etc/network/interfaces file:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid FRHOC
wireless-key XXXXXXXX
```
As your wireless interface is eth1, not wlan0.

-Dave

---

### Post by javierfh on 2006-12-07
Hi Dave,

thanks for your interest and suggestions. 
Im right now at work :D (i live in europe so we have the time difference), but i will try your suggestions when i arrive home today.

I was wondering also about that eth1 since, it keeps appearing automatically in the interfaces file, i guess that some of the methods i tried did some kind update in that file. Also some of these made some mapping to wlan0. But as i said, to me sounds so messed up, so maybe keeping it simple will help it to work.

About the button you mentioned to enable the wireless, i understand what you mean, in my ThinkPad T60 at work, I have that kind of key, but i assume that it is because the wireless card and bluetooth both are integrated inside the laptop. The one that i have at home is a PCMCIA. So i guess that you dont need to enable it or disable it, it is as easy as remove the card, while in the ones that it is integrated you cant do it, so there has to be a mean to do it.

In fact the same card works when i boot with windows XP without doing anything.

I will try to change these things and i can post again hopping that you can help me to advance little bit more :)

Thanks again,

Javi

---

### Post by javierfh on 2006-12-07
> **dbott67 said:**
> Hi Javi,

From what I can tell reading your output is that you have 2 interfaces: etho (wired) and eth1 (wireless):
```
javier@laptoplinux:~$ ifconfig -a
**[COLOR="Red"]eth0[/COLOR]** Link encap:Ethernet HWaddr 00:02:A5:9A:F9:50
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

**[COLOR="Red"]eth1[/COLOR]** Link encap:Ethernet HWaddr 00:30:B4:00:00:00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
Interrupt:10 
```

The other thing I notice is the "NOT READY" status at the end of the **sudo lshw -C network** output.

```
javier@laptoplinux:~$ sudo lshw -C network
*-network
description: Ethernet interface
product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@02:08.0
logical name: eth0
version: 41
serial: 00:02:a5:9a:f9:50
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=no multicast=yes port=MII speed=10MB/s
resources: iomemory:d0200000-d0200fff ioport:3000-303f irq:9
*-network DISABLED
description: Wireless interface
product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
vendor: Intersil Corporation
physical id: 1
bus info: pci@03:00.0
logical name: eth1
version: 01
serial: 00:30:b4:00:00:00
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=prism54[/COLOR] multicast=yes [B][COLOR="Red"]wireless=NOT READY!
[/COLOR][/B]resources: iomemory:24000000-24001fff irq:10
```

I take it that you are running Ubuntu on a laptop (javier@laptoplinux).  Many laptops have some sort of button or toggle that you must activate in order to tunr on the wireless capabilities (for example, my Dell 6400 requires FN+F2, while others have a dedicated button or switch).  The associated icon normally looks like a radio tower or similar.  Make sure that the switch is in the ON position.

Here's a few examples:
[IMG]http://dellresell.com/Ebay%20Content/Online%20Content/Laptop%20Parts%20Images/wireless-icon.gif[/IMG] or [IMG]http://images.google.com/images?q=tbn:3d8MVKZixP-wFM:http://supcontent.gateway.com/support.gateway.com/s/Mobile/Gateway/M520/WirelessIcon.gif[/IMG]

[IMG]http://static.flickr.com/69/185533480_9b489d074b_m.jpg[/IMG]

You can also remove the following from your /etc/network/interfaces file:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid FRHOC
wireless-key XXXXXXXX
```
As your wireless interface is eth1, not wlan0.

-Dave

Hi Dave,

i have tried several things...cleaning the interface file and still cant make it work.
I followed that [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) from the scratch and well...everything seems kind of ok..except one step where i need to check some logs.

I dont know if this is a problem or not.


> 

javier@laptoplinux:~$ sudo modprobe ndiswrapper
javier@laptoplinux:~$ tail /var/log/messages
Dec  7 20:30:57 localhost gconfd (javier-4506): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec  7 20:30:57 localhost gconfd (javier-4506): Resolved address "xml:readwrite:/home/javier/.gconf" to a writable configuration source at position 1
Dec  7 20:30:57 localhost gconfd (javier-4506): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Dec  7 20:30:57 localhost gconfd (javier-4506): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Dec  7 20:30:57 localhost gconfd (javier-4506): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Dec  7 20:31:00 localhost kernel: [17179784.808000] NET: Registered protocol family 10
Dec  7 20:31:00 localhost kernel: [17179784.808000] lo: Disabled Privacy Extensions
Dec  7 20:31:00 localhost kernel: [17179784.808000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec  7 20:31:00 localhost kernel: [17179784.808000] IPv6 over IPv4 tunneling driver
Dec  7 20:31:06 localhost gconfd (javier-4506): Resolved address "xml:readwrite:/home/javier/.gconf" to a writable configuration source at position 0




And then when trying to get it up.. this is what i get.

> 

javier@laptoplinux:~$ sudo ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 4445
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:30:b4:00:00:00
Sending on   LPF/eth1/00:30:b4:00:00:00
Sending on   Socket/fallback
javier@laptoplinux:~$ sudo ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFFLAGS: Timer expired
SIOCSIFFLAGS: Timer expired
Listening on LPF/eth1/00:30:b4:00:00:00
Sending on   LPF/eth1/00:30:b4:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.




And again...and i guess thats the key.. the "wireless=NOT READY" thingy, i really dont have any clue how can i activate that...it just works if i restart in windows...without a glitch.

> 

 *-network DISABLED
       description: Wireless interface
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@03:00.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 multicast=yes wireless=NOT READY!
       resources: iomemory:24000000-24001fff irq:10




Any idea how to force it?
I would really appreciate whatever help you can provide me.

Javi

---

### Post by dbott67 on 2006-12-07
Are you using WPA?

I found a thread [here]("http://www.linuxforums.org/forum/linux-networking/51257-wpa-wpa_supplicant-problems-ubuntu.html") where someone had the same "wireless=NOT READY!" error message and they were using WPA (they also had the prism54 driver).

Try disabling all encryption (WEP or WPA) on the router and try to connect.  From there, try using some of the commands noted above (ifconfig -a, ifdown/ifup, iwlist scanning, etc.) and see what kind of output you get.

-Dave

---

### Post by javierfh on 2006-12-07
> **dbott67 said:**
> Are you using WPA?

I found a thread [here]("http://www.linuxforums.org/forum/linux-networking/51257-wpa-wpa_supplicant-problems-ubuntu.html") where someone had the same "wireless=NOT READY!" error message and they were using WPA (they also had the prism54 driver).

Try disabling all encryption (WEP or WPA) on the router and try to connect.  From there, try using some of the commands noted above (ifconfig -a, ifdown/ifup, iwlist scanning, etc.) and see what kind of output you get.

-Dave

Hi Dave,

i am afraid that it is the case, that i use wep, and to be honest dont even know how to disable these things in the router. I got the connection from the work and the router it is already preconfigured.

In fact i was thinking to check in the forums or in google that "Wireless not ready" error message.

But funny thing is that i cant even start the card. I would expect at least to see lights and when trying to connect, then get error if not properly configured, but so far, cant even get to the point of scanning networks around. I was trying with my phone (has wlan as well) if i could see some wlan around, but ...i dont see any public ones. I was hoping that i can try to scan or to try to connect to some public or not protected instead of mine to see if i can make the card working. But no luck in there  either.

Thanks a lot for your interest.

Javi

---

### Post by dbott67 on 2006-12-07
The only other things that come to mind at the moment are:
- try switching PCMCIA slots (if possible)
- borrow a different PC wifi card just to test to see if it works (it will help eliminate if it's the card or the PCMCIA bus, or the OS, or the driver...)

-Dave

---

### Post by javierfh on 2006-12-08
> **dbott67 said:**
> The only other things that come to mind at the moment are:
- try switching PCMCIA slots (if possible)
- borrow a different PC wifi card just to test to see if it works (it will help eliminate if it's the card or the PCMCIA bus, or the OS, or the driver...)

-Dave

Hi Dave,

might be the PCMCIA slots that are not switched on in linux, but the funny thing is that the exact setup, without touching anywhere..works perfectly in windows xp. 
In other words, if i restart the machine and boot in windows xp it will just work without touching a thing.
So i guess, that this solves your second point to try to figure out if the pcmcia bus is faulty. I guess that last two variables here are still open, the OS or the driver.

I have to continue investigating :D
I will let you know if i ever succeed :D

Thanks,

Javi

---

### Post by dbott67 on 2006-12-08
Hi Javi,

My thought about switching the PCMCIA slots was actually just about moving the wifi card from slot A to slot B (if your laptop has two slots).

You might also want to try this:

1. Remove the card
2. Run the following command from a terminal:
```
sudo /etc/init.d/dbus restart
```
3. Re-insert the card & see if the lights come on.

-Dave

---

### Post by aDOT on 2006-12-26
Dear Javi,
I have the same problems.
Did you find the solution? I can not find any solution that should not use winXP drivers like next
[http://patrick.vande-walle.eu/software/intersil-isl3886-linux/](http://patrick.vande-walle.eu/software/intersil-isl3886-linux/)
regards,
A.

---

### Post by afeickert on 2007-01-08
To whom it may concern:

I am running a Broadcom 4311 card on my Dell Inspiron E1505 and have the same problem... my Networking prefs recognize my card, but network-manager does not.

Whenever I run 'iwlist eth1 scan' as a standard user, it shows no results. BUT, when I run 'sudo eth1 scan' (now as root, obviously), I get several scan results.

I already checked /etc/network/interfaces and all is well, and my laptop's wireless light is on.

Any advice anyone can give?

---

