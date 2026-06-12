---
title: "[SOLVED] Destination Host Unreachable problem using rtl8139"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by hypochronic on 2008-07-09
Hey all,

I've been having the weirdest networking problems, and after 2 days of trying to fix it, I've come here.

Symptoms:
During the install of Ubuntu Server 8.04.1, DHCP failed. I told it to skip and manually configured it later. Since DHCP didn't work, I tried using a static IP address, but that didn't change anything. Whenever I tried to ping the default gateway (192.168.1.1) ping gave the error message "Destination Host Unreachable."

The strange thing is that when I tried using tcpdump to see if I was sending any packets, I managed to catch a lot of traffic from my network, but not any packets from the ubuntu computer.

Here are the details of the computer and it's configuration:

OS: Ubuntu Server edition, v. 8.04.1
Kernel: Linux ubuntu 2.6.24-19-generic
nic: Realtek RTL8139 10/100 chipset (I think the card was actually made by TP-Link)

I originally tried a Davicom DM9009, but it had the same problem. That was why I switched to the Realtek; to see if changing the nic would make a difference. Unfortunately, it hasn't.

lspci:> 
00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C586/A/B PCI-to-ISA [Apollo VP] (rev 47)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 02)
00:07.3 Host bridge: VIA Technologies, Inc. VT82C586B ACPI (rev 10)
**00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**
00:0a.0 VGA compatible controller: Trident Microsystems 3DImage 9750 (rev f3)

lsmod:
> Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
usb_storage            73664  1 
libusual               19108  1 usb_storage
ipv6                  267780  25 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
lp                     12324  0 
loop                   18948  0 
evdev                  13056  0 
ns558                   5632  0 
gameport               16008  2 ns558
af_packet              23812  2 
parport_pc             36260  1 
serio_raw               7940  0 
parport                37832  2 lp,parport_pc
psmouse                40336  0 
via_agp                11136  1 
shpchp                 34452  0 
agpgart                34760  1 via_agp
i2c_via                 5124  0 
pci_hotplug            30880  1 shpchp
i2c_algo_bit            7300  1 i2c_via
pcspkr                  4224  0 
i2c_core               24832  2 i2c_via,i2c_algo_bit
ext3                  136712  1 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sg                     36880  0 
sr_mod                 17956  0 
sd_mod                 30720  5 
cdrom                  37408  1 sr_mod
pata_via               13316  2 
ata_generic             8324  0 
pata_acpi               8320  0 
8139cp                 24704  0 
uhci_hcd               27024  0 
floppy                 59588  0 
libata                159344  3 pata_via,ata_generic,pata_acpi
8139too                27520  0 
mii                     6400  2 8139cp,8139too
usbcore               146028  4 usb_storage,libusual,uhci_hcd
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 


ethtool -i eth0:
> driver: 8139too
version: 0.9.28
firmware-version: 
bus-info: 0000:00:09.0

/etc/network/interfaces:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
#	address 192.168.1.10
#	netmask 255.255.255.0
#	network 192.168.1.0
#	broadcast 192.168.1.255
#	gateway 192.168.1.1
#	# dns-* options are implemented by the resolvconf package, if installed
#	dns-nameservers 192.168.1.1
#	dns-search WORKGROUP

ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:19:e0:25:f4:a5  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:e0ff:fe25:f4a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1345535 (1.2 MB)  TX bytes:49794 (48.6 KB)
          Interrupt:10 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:595 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:290909 (284.0 KB)  TX bytes:290909 (284.0 KB)

dmesg | grep "eth\|8139":
> [   39.353928] 8139too Fast Ethernet driver 0.9.28
[   39.356023] eth0: RealTek RTL8139 at 0xe800, 00:19:e0:25:f4:a5, IRQ 10
[   39.356047] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   40.126784] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   43.652036] Driver 'sd' needs updating - please use bus_type methods
[   43.653803]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   71.530269] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  108.289688] eth0: no IPv6 routers present

route -n :
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


dhclient:
> There is already a pid file /var/run/dhclient.pid with pid 13242
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:19:e0:25:f4:a5
Sending on   LPF/eth0/00:19:e0:25:f4:a5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

ip link:
> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:19:e0:25:f4:a5 brd ff:ff:ff:ff:ff:ff

iptables -L: 
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

ping -c 3 192.168.1.1
> PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.10 icmp_seq=1 Destination Host Unreachable
From 192.168.1.10 icmp_seq=2 Destination Host Unreachable
From 192.168.1.10 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms
, pipe 3


several lines from tcpdump:
> 
15:20:54.302615 IP 192.168.1.102.56120 > 192.168.1.103.63331: P 1553:1802(249) ack 2792 win 16425
15:20:54.303633 IP 192.168.1.103.63331 > 192.168.1.102.56120: . ack 1802 win 256
15:20:54.320393 IP 83.89.18.194.3822 > 192.168.1.104.31055: P 383:400(17) ack 366461 win 65535
15:20:54.347431 IP 83.89.18.194.3822 > 192.168.1.104.31055: . ack 369381 win 65535
15:20:54.355464 IP 192.168.1.103.63331 > 192.168.1.102.56120: P 2792:2851(59) ack 1802 win 256
15:20:54.356446 IP 192.168.1.102.56120 > 192.168.1.103.63331: P 1802:2095(293) ack 2851 win 16410
15:20:54.408321 IP 83.89.18.194.3822 > 192.168.1.104.31055: . ack 372301 win 65535
15:20:54.423261 IP 192.168.1.103.63331 > 192.168.1.102.56120: P 2851:2984(133) ack 2095 win 255
15:20:54.423279 IP 192.168.1.103.63331 > 192.168.1.102.56120: P 2984:3101(117) ack 2095 win 255
15:20:54.423385 IP 192.168.1.102.56120 > 192.168.1.103.63331: . ack 3101 win 16347
15:20:54.423762 IP 192.168.1.102.56120 > 192.168.1.103.63331: R 2095:2095(0) ack 3101 win 0
15:20:54.477534 IP 83.89.18.194.3822 > 192.168.1.104.31055: . ack 375221 win 65535
15:20:54.558873 IP 83.89.18.194.3822 > 192.168.1.104.31055: . ack 378141 win 65535
15:20:54.604660 IP 83.89.18.194.3822 > 192.168.1.104.31055: . ack 381061 win 65535

Network layout:
The ubuntu box is connected to an 8 port switch, which has two other vista boxes connected to it. It also has a line to a Linksys wrt54g wireless router, which is acting as the default gateway, and is connected to a few more computers and a cable modem.

Is there any important information that I forgot?

Basically, I can receive packets (the RX byte count goes up rather regularly, and I can capture packets from other computers on my network with tcpdump) but I can't send them. When I tried to capture my own ping packets with tcpdump, nothing showed up.

Any ideas on how to fix this, so that I can connect to my lan and get DHCP?

I've tried a lot of stuff already. I haven't really tried the various combinations of kernel arguments, such as pci=noacpi, acpi=off, etc. because I'm not sure what they do, and which ones would fix my problem.

Thanks!

---

### Post by hypochronic on 2008-07-09
Well, it turns out that the problem was a faulty switch. Sorry to bother everyone. Kind of weird though, that the nic could receive traffic, but not send it on the broken ports.

---

### Post by soliton1 on 2009-06-04
I have just run into EXACTLY the same problem installing 9.04 - DHCP failed during installation so I went with static IP. Now I can ping the server but any attempt from the server to ping anything results in "Destination Host Unreachable". I tried changing ports on my switch but no luck. Any other suggestions?

---

