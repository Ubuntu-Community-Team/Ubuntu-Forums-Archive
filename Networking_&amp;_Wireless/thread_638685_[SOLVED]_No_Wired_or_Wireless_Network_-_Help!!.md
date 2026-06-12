---
title: "[SOLVED] No Wired or Wireless Network - Help!!"
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by mulerobba on 2007-12-12
I am first time user of linux.  

I just built a PC and decided to put Xubuntu 7.10 on it

My motherboard is Gigabyte GA-945GCM-S2L.  It has integrated gigabit LAN onboard.  The LAN is Realtek 8111C.

I am unable to connec to a wired or wireless network. The ethernet card and/or the wireless adapter are detected but no connection being made.

Can anyone help?

---

### Post by akmgg on 2007-12-12
I am having the same issue.  I had to reinstall Ubuntu after a hard drive problem.  I installed the new version and now my networking does not work.  It worked before. I have tried disabling IPv6 like suggested and that does not help. My router shows the PC connected and has assigned an IP address, but when I pull up the network connection on the PC, either wired or the wireless one, all of the addresses are 0.0.0.0.  I am stumped.

---

### Post by mulerobba on 2007-12-12
Some more information

# ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:1D:7D:34:63:46  
          inet6 addr: fe80::21d:7dff:fe34:6346/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967279 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:1D:7D:34:63:46  
          inet addr:169.254.4.158  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)


# dhclient
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:7d:34:63:46
Sending on   LPF/eth0/00:1d:7d:34:63:46
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


# cat /etc/network/interfaces

auto lo

iface lo inet loopback


#iface wlan0 inet dhcp
#wireless-key s:5DFCDD30C3
#wireless-essid Thumper

#auto wlan0

auto eth0
iface eth0 inet dhcp
netmask 255.255.255.0
gateway 192.168.1.1



# ethtool eth0
Settings for eth0:
        Supported ports: [ FIBRE ]
        Supported link modes:   1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: FIBRE
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: pumbg
        Current message level: 0x00000033 (51)
        Link detected: yes

# lsmod | grep 8169
r8169                  32260  0 

# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                        
There is already a pid file /var/run/dhclient.eth0.pid with pid 5046
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:7d:34:63:46
Sending on   LPF/eth0/00:1d:7d:34:63:46
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1d:7d:34:63:46
Sending on   LPF/eth0/00:1d:7d:34:63:46
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


# lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)

---

### Post by mulerobba on 2007-12-12
By the way I have also updated to the latest driver from Realtek for linux 2.6.x and 2.4.x for RTL8111C

---

### Post by mulerobba on 2007-12-12
bump

---

### Post by mulerobba on 2007-12-13
Solved,

Went down to the computer store and got me a D-link DGE-530T.  Works right of the box.

Hooray!!!

---

