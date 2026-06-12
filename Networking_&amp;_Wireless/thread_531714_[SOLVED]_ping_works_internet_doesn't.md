---
title: "[SOLVED] ping works internet doesn't"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by tonytux on 2007-08-21
my connection was working well, until I decided to install some irc server stuff.  Now I can only "ping" internally, to my router or wife's XP laptop, but I cannot access my router through FF anymore, update my system, or anything else network/internet related. I've completely removed the IRC server pkgs and attemted to go through steps to get my box back on-line, to no avail.  When I try to "sudo /etc/init.d/networking restart" I get "postconf: fatal: open /etc/postfix/main.cf: No such file or directory exists" I've "sudo ifcongif eth1 up" to my hearts content, and stil no luck.  All I know is that my wifes XP connects with no problem and my Feisty seems to be stuck on it's self.  Is there a command like "dpkg-reconfig xorg" for net interfaces.

---

### Post by Brandon.Viking on 2007-08-21
Sounds like the server package may have messed with your network settings. dhclient is the cmd line tool to renew DHCP address if you use that on the internal network. ip route list will display routing table on the linux host.
It should look similar to the "route print" on the windows box.
Verify firewall rules arent blocking everything on the linux box ... sudo iptables -L will show you your current rules. if its all allow thats not the issue.

THere are a number of other things to check but more descriptions of whats actually happening might help.

Other thing that may be an issue if the IP addresses are all correct is the /etc/resolv.conf file for DNS resolution. 
nameservers may need to be manually corrected to be similar to the other machine.

Good luck debugging it

Brandon.

---

### Post by tonytux on 2007-08-21
I use a static address so that I can forward ports to my box, BT and such.  
ip route list outputed 
"192.168.1.0/24 dev eth2 proto kernel scope link src 192.168.1.100 
169.254.0.0/16 dev eth2 scope link metric 1000
default va 192.168.1.1 dev eth2"
now before all this I used eth2 which is a Network everywhere on my PCI, my eth1 is an integrated realtek nic which never worked properly.  while i as trying to get my box up and running I noticed my Network Everywhere is now at eth1. And I don't know what ever happened to eth0, so I just ignored it, cause my net interface worked at that point.

---

### Post by tonytux on 2007-08-21
poking around I saw that this info might help others hel me so:
 here's the last few lines of my hwinfo
```
65: None 00.0: 10700 Loopback
  [Created at net.119]
  Unique ID: ZsBS.GQNx7L4uPNA
  SysFS ID: /class/net/lo
  Hardware Class: network interface
  Model: "Loopback network interface"
  Device File: lo
  Config Status: cfg=new, avail=yes, need=no, active=unknown

66: None 02.0: 10701 Ethernet
  [Created at net.119]
  UDI: /org/freedesktop/Hal/devices/net_00_40_2b_46_1a_1e
  Unique ID: pDke.ndpeucax6V1
  Parent ID: mY_N.51ftycRYkf4
  SysFS ID: /class/net/eth2
  SysFS Device Link: /devices/pci0000:00/0000:00:1e.0/0000:02:02.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "8139too"
  Driver Modules: "8139too"
  Device File: eth2
  HW Address: 00:40:2b:46:1a:1e
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #24 (Ethernet controller)

67: None 01.0: 10701 Ethernet
  [Created at net.119]
  UDI: /org/freedesktop/Hal/devices/net_00_18_f8_09_20_fd
  Unique ID: L2Ua.ndpeucax6V1
  Parent ID: JNkJ.EpgkC3S71D2
  SysFS ID: /class/net/eth1
  SysFS Device Link: /devices/pci0000:00/0000:00:1e.0/0000:02:0b.0
  Hardware Class: network interface
  Model: "Ethernet network interface"
  Driver: "tulip"
  Driver Modules: "tulip"
  Device File: eth1
  HW Address: 00:18:f8:09:20:fd
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (Ethernet controller)

```
my ifconfig -a
```
eth1      Link encap:Ethernet  HWaddr 00:18:F8:09:20:FD  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f8ff:fe09:20fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:325 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72409 (70.7 KiB)  TX bytes:18467 (18.0 KiB)
          Interrupt:19 Base address:0x2400 

eth2      Link encap:Ethernet  HWaddr 00:40:2B:46:1A:1E  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:113586 (110.9 KiB)  TX bytes:113586 (110.9 KiB)


```
my lspci
```
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Trigem Computer Inc. Unknown device 3189
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at 2000 [size=256]
	Memory at e8100000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2

02:0b.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
	Subsystem: ADMtek Unknown device 0570
	Flags: bus master, fast Back2Back, medium devsel, latency 64, IRQ 19
	I/O ports at 2400 [size=256]
	Memory at e8100400 (32-bit, non-prefetchable) [size=1K]
	[virtual] Expansion ROM at 20000000 [disabled] [size=128K]
	Capabilities: [c0] Power Management version 2


```
my lshw -C
```
  *-network:0
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth2
       version: 10
       serial: 00:40:2b:46:1a:1e
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half ip=192.168.1.100 latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: ioport:2000-20ff iomemory:e8100000-e81000ff irq:20
  *-network:1
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: ADMtek
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth1
       version: 11
       serial: 00:18:f8:09:20:fd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 ip=192.168.1.100 latency=64 maxlatency=128 mingnt=64 multicast=yes
       resources: ioport:2400-24ff iomemory:e8100400-e81007ff irq:19

```
netstat -r
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     *               255.255.255.0   U         0 0          0 eth2
192.168.1.0     *               255.255.255.0   U         0 0          0 eth1
169.254.0.0     *               255.255.0.0     U         0 0          0 eth2
default         192.168.1.1     0.0.0.0         UG        0 0          0 eth2

```
and my sysctl.conf
```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

```

it's probably too much but I just need it fixed..

---

### Post by tonytux on 2007-09-03
simple fix for this I feel so stupid.  One of the packages must have messed over my iptables.  Found the answer here [http://ubuntuforums.org/showthread.php?t=540784&highlight=iptables]("http://http://ubuntuforums.org/showthread.php?t=540784&highlight=iptables"). So... solved.

---

