---
title: "WEP Connected - no dhcp"
date: 2007-10-09
forum: Networking &amp; Wireless
---

### Post by McHenry on 2007-10-09
I have a wireless connection that appears to connect to my router but beyond that no IP is assigned etc. Can anyone suggest what I have done wrong here ?

Thanks in advance...


maint@mythbox:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

iface wlan0 inet dhcp
wireless-essid ******
wireless-mode managed
wireless-key ******************************* open
# address 192.168.1.5
# netmask 255.255.255.0
# gateway 192.168.1.10
# network 192.168.1.0
# broadcast 192.168.1.255
auto wlan0
maint@mythbox:~$





maint@mythbox:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:13:72:0D:0C:3C
inet addr:192.168.1.12 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::213:72ff:fe0d:c3c/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:23550 errors:0 dropped:0 overruns:0 frame:0
TX packets:12752 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:33644659 (32.0 MiB) TX bytes:992018 (968.7 KiB)
Base address:0xcce0 Memory:fe3e0000-fe400000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:94 errors:0 dropped:0 overruns:0 frame:0
TX packets:94 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:412517 (402.8 KiB) TX bytes:412517 (402.8 KiB)

wlan0 Link encap:Ethernet HWaddr 00:0F:B5:D7:E4:57
inet6 addr: fe80::20f:b5ff:fed7:e457/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 b) TX bytes:5112 (4.9 KiB)

wmaster0 Link encap:UNSPEC HWaddr 00-0F-B5-D7-E4-57-00-00-00-00-00-0* 0-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)

maint@mythbox:~$






maint@mythbox:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 IEEE 802.11g Frequency:2.442 GHz
RTS thr:off Fragment thr=2346 B

wlan0 IEEE 802.11g ESSID:"******"
Mode:Managed Frequency:2.442 GHz Access Point: 00:04:ED:42:54:C7
RTS thr:off Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

maint@mythbox:~$





maint@mythbox:~$ sudo dhclient wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [www.isc.org/sw/dhcp](www.isc.org/sw/dhcp)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0f:b5:d7:e4:57
Sending on LPF/wlan0/00:0f:b5:d7:e4:57
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
maint@mythbox:~$

---

### Post by kevdog on 2007-10-09
see if you can get a connection manually just to troubleshoot network manager
[http://ubuntuforums.org/showthread.php?t=571194](http://ubuntuforums.org/showthread.php?t=571194)

---

### Post by McHenry on 2007-10-09
I have updated the driver to use ndiswrapper and all i can see appears fine but still doesn't get an IP ?

maint@mythbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:0D:0C:3C  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe0d:c3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1570 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:158364 (154.6 KiB)  TX bytes:222211 (217.0 KiB)
          Base address:0xcce0 Memory:fe3e0000-fe400000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:0F:B5:D7:E4:57  
          inet6 addr: fe80::20f:b5ff:fed7:e457/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20363 (19.8 KiB)  TX bytes:12620 (12.3 KiB)

maint@mythbox:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"******"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:04:ED:42:54:C7   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr=2346 B   Fragment thr=2400 B   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

maint@mythbox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:04:ED:42:54:C7
                    ESSID:"******"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

maint@mythbox:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 01
       serial: 00:13:72:0d:0c:3c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.4-1 ip=192.168.1.12 latency=0 multicast=yes
       resources: iomemory:fe3e0000-fe3fffff iomemory:fe400000-fe7fffff ioport:cce0-ccff irq:17
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:b5:d7:e4:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper driverversion=1.38 firmware=NETGEAR Inc.,3/16/2006,5.1213.0 multicast=yes wireless=IEEE 802.11g
maint@mythbox:~$

---

### Post by kevdog on 2007-10-09
Can you post lspci -nn??  And what about updating ndiswrapper to the 1.49 version.  1.38 is really old, and although it works in most cases, sometimes it doesnt!

---

### Post by McHenry on 2007-10-09
the ndiswrapper version is the synaptic standard:
sudo apt-get install ndiswrapper-utils-1.9



maint@mythbox:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770]
00:01.0 PCI bridge [0604]: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port [8086:2771]
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 [8086:27e0] (rev 01)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 [8086:27e2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge [8086:27b0] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controller AHCI [8086:27c1] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV380 [Radeon X600 (PCIE)] [1002:5b62]
01:00.1 Display controller [0380]: ATI Technologies Inc RV380 [Radeon X600] [1002:5b72]
04:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a] (rev 01)
05:04.0 Multimedia video controller [0400]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [14f1:8800] (rev 05)
05:04.2 Multimedia controller [0480]: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] [14f1:8802] (rev 05)
maint@mythbox:~$

---

### Post by kevdog on 2007-10-09
In the lspci -nn output -- where is your wireless card??? Was it plugged on turned on when you typed this command.

---

### Post by McHenry on 2007-10-09
it's a usb adapter sorry:

maint@mythbox:~$ lsusb
Bus 005 Device 007: ID 0fe9:db51 DVICO 
Bus 005 Device 004: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 413c:2003 Dell Computer Corp. 
Bus 004 Device 001: ID 0000:0000  
maint@mythbox:~$

---

### Post by McHenry on 2007-10-09
I also found the following which relates to my adapter on the ndiswrapper website:

#
Card: Netgear WG111v2 802.11g Wireless USB2.0 Adapter
    *
      usbid: 0846:6a00
    *
      Distro-specific: FEDORA CORE 5 (4K kernel stack size), Ndiswrapper 1.33
    *
      Driver: Netgear windows driver Version: Netgear, Inc.,3/16/2006, 5.1213.06.0316 downloadable from Netgear site (wg111v2_1_3_0 , winme driver)
    *
      Other: WEP work properly

And it now has an IP address !!


WOW IT WORKS !!!!!!!!!!!!!!!!!!!!!!!!!!

I had used the Win98 inf not the winME inf file...

I removed the old one using ndiswrapper -r and then installed the new one with ndiswrapper -i

When I reboot will it remain or do I need to issue another command to make it permanent ?

---

### Post by kevdog on 2007-10-09
No, its permanent until you remove the driver.

---

