---
title: "Can't fix my internet in Fiesty"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by jmcd_78 on 2007-07-01
I can't figure out what configuration is bad or file I screwed up, but I can no longer get on the internet. I looked at some other peoples problems with networking and the internet and it didn't help me. I think what I have set up may make it inherently more complicated. I apologize ahead of time for writing a novel.

A little background - I am new to linux. I have been looking at Ubuntu for a while and decided to do a dual boot on my second computer  (it will be a server at some point - when I get better at linux). Linux is hands down better networking. I know from experience with the universities computers (they run both redhat and windows xp).

I have 5 nics in the computer. When I installed ubuntu it assigned eth0, eth1, eth2, eth3, eth4 respectively. I followed what I had found in this forum and around on other sites on the internet to set up a load balanced connection. Somewhere in that process I lost adapter eth3 only to gain adapter eth5, which I never did figure out why,  but everything else at that point was awesome because I was load balancing 3 internet connections (adapter bond0,  round robin, mode 0). I looked into using server 2003 (I can get it through microsofts student alliance with the university) but I think I would have to have at least 4 or 5 of the exact same computers to spare to make it work. I know what I did was working fine because I used iptraf -i all and watched the 3 adapters splitting the load. 

The last thing I was playing with was Firestarter firewall. Afterward things still worked fine, and I could see load balanced network activity. When I started Ubuntu this morning I had no connectivity. I dont understand. I tried restarting all the adapters, restarting the bonded adapter bond0,m even restarting ubuntu. None worked. The system said the device was busy sometimes then later on it would say it was not configured. I couldnt get ifup, ifdown, or mii-tool -r/-R commands to do anything, before they did what you would expect. 

What the gui interface System/Administration/Network option says: eth0, eth1, eth2 are enabled and roaming - its always said this about these adapters. The others, eth4 and eth5, have some 169.254.x.x address.

To clarify my network setup:
eth0, eth1, eth2 - bonded together as bond0 (using ifenslave) connect to internet
eth4 - not connected to anything currently
eth5 - connected to my main computer(runs windows xp) which is not connected to anything else

Are there more configuration files that I need to check? Are there any other tools like ipconfig that I can use to see what is going on? I feel like I have been competing/fighting with some default configuration in Unbuntu and it finally won. I honestly don't know what is going on in my Ubuntu. From all indications I can see, with the tools I know how to use (barely), it seems I should be able to connect to the internet. I even have an ip address issued from DHCP. I thought I might be able to Macgyver myself out of this one, but I haven't had any luck.

Below is the output of some commands and contents of configuration files I edited. I am trying to provide as much information as possible.

[COLOR="Blue"]~$ sudo mii-tool -v
[/COLOR]
eth0: negotiated 100baseTx-FD flow-control, link ok
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

eth1: negotiated 100baseTx-FD flow-control, link ok
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

eth2: negotiated 100baseTx-FD flow-control, link ok
  product info: vendor 00:00:00, model 0 rev 0
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

eth4: negotiated 100baseTx-FD, link ok
  product info: vendor 00:00:20, model 32 rev 1
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  link partner: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

eth5: autonegotiation restarted, no link
  product info: vendor 00:07:49, model 1 rev 1
  basic mode:   autonegotiation enabled
  basic status: autonegotiation restarted, no link
  capabilities: 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

[COLOR="Blue"]~$ ifconfig
[/COLOR]
bond0     Link encap:Ethernet  HWaddr 00:03:B3:48:61:2C  
          inet addr:10.71.0.183  Bcast:10.71.15.255  Mask:255.255.240.0
          inet6 addr: fe80::203:b3ff:fe48:612c/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:42157 (41.1 KiB)  TX bytes:9852 (9.6 KiB)

eth0      Link encap:Ethernet  HWaddr 00:03:B3:48:61:2C  
          inet6 addr: fe80::203:b3ff:fe48:612c/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13209 (12.8 KiB)  TX bytes:2658 (2.5 KiB)
          Interrupt:21 Base address:0xa400 

eth1      Link encap:Ethernet  HWaddr 00:03:B3:48:61:2C  
          inet6 addr: fe80::203:b3ff:fe48:612c/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13439 (13.1 KiB)  TX bytes:2958 (2.8 KiB)
          Interrupt:22 Base address:0x2000 

eth2      Link encap:Ethernet  HWaddr 00:03:B3:48:61:2C  
          inet6 addr: fe80::203:b3ff:fe48:612c/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:111 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15509 (15.1 KiB)  TX bytes:4236 (4.1 KiB)
          Interrupt:23 Base address:0xc00 

eth4      Link encap:Ethernet  HWaddr 00:17:31:7C:A6:9C  
          inet6 addr: fe80::217:31ff:fe7c:a69c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:398 (398.0 b)
          Interrupt:23 Base address:0xe400 

eth5      Link encap:Ethernet  HWaddr 00:18:F8:08:84:0E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xea00 

eth2:avah Link encap:Ethernet  HWaddr 00:03:B3:48:61:2C  
          inet addr:169.254.4.162  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Base address:0xc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212 (212.0 b)  TX bytes:212 (212.0 b)

[COLOR="Blue"]~$ route -n
[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.71.0.0       0.0.0.0         255.255.240.0   U     0      0        0 bond0
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth2
0.0.0.0         10.71.0.1       0.0.0.0         UG    0      0        0 bond0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth2

[COLOR="Blue"]some pinging[/COLOR]

PING 10.71.0.183 (10.71.0.183) 56(84) bytes of data.
64 bytes from 10.71.0.183: icmp_seq=1 ttl=64 time=0.060 ms
64 bytes from 10.71.0.183: icmp_seq=2 ttl=64 time=0.057 ms

--- 10.71.0.183 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.057/0.058/0.060/0.007 ms
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.061 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.061 ms

--- 127.0.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 0.061/0.061/0.061/0.000 ms
PING 64.233.183.103 (64.233.183.103) 56(84) bytes of data.

--- 64.233.183.103 ping statistics ---(<-----this is [www.google.com](www.google.com))
2 packets transmitted, 0 received, 100% packet loss, time 1002ms
ping: sendmsg: Operation not permitted

~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

[COLOR="Red"]/etc/network/interfaces[/COLOR]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface

auto lo
iface lo inet loopback

# NOTE: eth3 mysteriously disappeared - eth5 appeared 6/29/07

#############################################################
# Commented out for NIC bonding - create LB connection 6/28/07
# network interfaces
#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto eth4
#iface eth4 inet dhcp

#auto eth5
#iface eth5 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

#############################################################
# Added for NIC bonding - create LB connection 6/29/07 (3 middle NICs)
iface bond0 inet dhcp
hwaddress ether 00:03:B3:48:61:2C
post-up ifenslave bond0 eth0 eth1 eth2
auto bond0

# Switched connection between independent local networks (MOBO NIC) 

iface eth4 inet static
#address 192.168.1.100
#netmask 255.255.255.0
#network 192.168.1.0
#broadcast 192.168.1.255
#gateway 192.168.1.254
auto eth4

# ICS / Server connection to main computer (bottom NIC)

iface eth5 inet static
#address 10.71.2.50
#netmask 255.255.255.0
#network 10.71.2.0
#broadcast 10.71.2.255
#gateway 10.71.2.254
auto eth5

[COLOR="Red"]/etc/modprobe.d/aliases[/COLOR]

# These are the standard aliases for devices and kernel drivers.
# This file does not need to be modified.
#
# Please file a bug against module-init-tools if a package needs a entry
# in this file.

# network protocols ##########################################################
alias net-pf-1  unix
alias net-pf-2  ipv4
alias net-pf-3  ax25
alias net-pf-4  ipx
alias net-pf-5  appletalk
alias net-pf-6  netrom
alias net-pf-7  bridge
alias net-pf-8  atm
alias net-pf-9  x25
alias net-pf-10 ipv6
alias net-pf-11 rose
alias net-pf-12 decnet
# 13 NETBEUI
alias net-pf-15 af_key
alias net-pf-16 af_netlink
alias net-pf-17 af_packet
# 18 ASH
alias net-pf-19 af_econet
alias net-pf-20 atm
# 22 SNA
alias net-pf-23 irda
alias net-pf-24 pppoe
alias net-pf-25 wanrouter
alias net-pf-26 llc
alias net-pf-31 bluetooth

# executables formats ########################################################
install binfmt-0000 /bin/true
alias binfmt-204 binfmt_aout
alias binfmt-263 binfmt_aout
alias binfmt-264 binfmt_aout
alias binfmt-267 binfmt_aout
alias binfmt-387 binfmt_aout

# block devices ##############################################################
alias block-major-3-*  ide_generic
alias block-major-8-*  sd_mod
alias block-major-9-*  md
alias block-major-11-* sr_mod
alias block-major-22-* ide_generic
alias block-major-33-* ide_generic
alias block-major-34-* ide_generic
alias block-major-37-* ide_tape
alias block-major-44-* ftl
alias block-major-46-* pcd
alias block-major-47-* pf
alias block-major-56-* ide_generic
alias block-major-57-* ide_generic
alias block-major-58-* lvm_mod
alias block-major-88-* ide_generic
alias block-major-89-* ide_generic
alias block-major-90-* ide_generic
alias block-major-91-* ide_generic
alias block-major-93-* nftl
alias block-major-97-* pg

# character devices ##########################################################
alias char-major-9-* st
alias char-major-10-1 psmouse
alias char-major-10-139 openprom
alias char-major-10-157 applicom
alias char-major-10-181 toshiba
alias char-major-10-183 hw_random
alias char-major-10-187 irnet
alias char-major-10-189 ussp
alias char-major-10-250 hci_vhci
alias char-major-13-0  joydev
alias char-major-13-1  joydev
alias char-major-13-2  joydev
alias char-major-13-3  joydev
alias char-major-13-32 mousedev
alias char-major-13-33 mousedev
alias char-major-13-34 mousedev
alias char-major-13-35 mousedev
alias char-major-13-63 mousedev
alias char-major-13-64 evdev
alias char-major-13-65 evdev
alias char-major-13-66 evdev
alias char-major-13-67 evdev
alias char-major-19-* cyclades
alias char-major-20-* cyclades
alias char-major-22-* pcxx
alias char-major-23-* pcxx
alias char-major-27-* ftape
alias char-major-34-* scc
alias char-major-35-* tclmidi
alias char-major-48-* riscom8
alias char-major-49-* riscom8
alias char-major-57-* esp
alias char-major-58-* esp
alias char-major-63-* kdebug
alias char-major-67-* coda
alias char-major-75-* specialix
alias char-major-76-* specialix
alias char-major-81-* videodev
alias char-major-83-* vtx
alias char-major-89-* i2c_dev
alias char-major-90-* mtdchar
alias char-major-96-* pt
alias char-major-97-* pg
alias char-major-107-* 3dfx
alias char-major-109-* lvm_mod
alias char-major-166-* cdc_acm
alias char-major-171-0 raw1394
alias char-major-171-1 video1394
alias char-major-171-2 dv1394
alias char-major-171-3 amdtp
alias char-major-180-* usbcore
alias char-major-195-* nvidia
alias char-major-200-* vxspec
alias char-major-202-* msr
alias char-major-203-* cpuid
alias char-major-206-* osst
alias char-major-208-* ussp
alias char-major-227-* tub3270
#alias char-major-240-* usb-serial
#alias char-major-240-* hsfserial
#alias char-major-241-* hsfserial

# misc #######################################################################
alias xfrm-type-2-4 xfrm4_tunnel
alias xfrm-type-2-50 esp4
alias xfrm-type-2-51 ah4
alias xfrm-type-2-108 ipcomp
alias xfrm-type-10-41 xfrm6_tunnel
alias xfrm-type-10-50 esp6
alias xfrm-type-10-51 ah6
alias xfrm-type-10-108 ipcomp6

alias bt-proto-0 l2cap
alias bt-proto-2 sco
alias bt-proto-3 rfcomm
alias bt-proto-4 bnep
alias bt-proto-5 cmtp
alias bt-proto-6 hidp
alias bt-proto-7 avdtp

alias cipcb0 cipcb
alias cipcb1 cipcb
alias cipcb2 cipcb
alias cipcb3 cipcb
alias dummy0 dummy
alias dummy1 dummy
alias plip0 plip
alias plip1 plip
alias slip0 slip
alias slip1 slip
alias tunl0 ipip
alias gre0 ip_gre

alias usbdevfs usbcore

#############################################################
# Added for NIC bonding - create LB connection 6/28/07
alias bond0 bonding
alias eth0 e100
alias eth1 e100
alias eth2 e100
options bonding mode=0 miimon=100
alias parport_lowlevel parport_pc

[COLOR="Red"]/etc/modprobe.d/arch/i386
[/COLOR]
alias binfmt-0064 binfmt_aout
alias binfmt-332 iBCS

#############################################################
# Added for NIC bonding - create LB connection 6/28/07
alias bond0 bonding
options bonding mode=0 miimon=100 downdelay=200 updelay=200

---

