---
title: "Network problems after motherboard replacement"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by brnd on 2008-02-07
Hi,

As an ubuntu-newbie I ran into problems with my network connection after the replacement of my motherboard (the old one seemed to cause random restarts, but that's another story). At startup the network information (System -> Administration -> Network) was gone so I manually entered my IP adres, subnet mask, and gateway. Then everything worked fine... for about half a minute. After that no connectivity (internet browser, ssh, local pings all don't work).

I browsed through the ubuntu fora before posting this message and encountered some related problems due to MAC-address changes. With this information I modified the "/etc/udev/rules.d/70-persistent-net.rules" and "/etc/network/interfaces" files (see below).

Presently the situation is that my connection is fine directly after a network restart (sudo /etc/init.d/networking restart) for about half a minute, and then it stalls again. I am running Ubuntu 7.10 (gutsy gibbon). Included below is the output of 

/var/log/syslog
dmesg
/etc/udev/rules.d/70-persistent-net.rules
/etc/network/interfaces
ifconfig
route

Any help is much appreciated!

Bernard



/var/log/syslog (from network restart to network stalling)
-----------------------------------------------------------
Feb  7 17:57:27 physth03 avahi-daemon[5369]: Interface eth0.IPv4 no longer relevant for mDNS.
Feb  7 17:57:27 physth03 avahi-daemon[5369]: Leaving mDNS multicast group on interface eth0.IPv4 with address 164.15.124.65.
Feb  7 17:57:27 physth03 avahi-daemon[5369]: Withdrawing address record for fe80::215:f2ff:fe0d:3d6 on eth0.
Feb  7 17:57:27 physth03 avahi-daemon[5369]: Withdrawing address record for 164.15.124.65 on eth0.
Feb  7 17:57:27 physth03 avahi-daemon[5369]: Joining mDNS multicast group on interface eth0.IPv4 with address 164.15.124.65.
Feb  7 17:57:27 physth03 avahi-daemon[5369]: New relevant interface eth0.IPv4 for mDNS.
Feb  7 17:57:27 physth03 avahi-daemon[5369]: Registering new address record for 164.15.124.65 on eth0.IPv4.
Feb  7 17:57:27 physth03 kernel: [ 5756.219482] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
Feb  7 17:57:28 physth03 ntpdate[19829]: the NTP socket is in use, exiting
Feb  7 17:57:28 physth03 avahi-daemon[5369]: Registering new address record for fe80::215:f2ff:fe0d:3d6 on eth0.*.
Feb  7 17:57:37 physth03 kernel: [ 5766.337869] eth0: no IPv6 routers present
Feb  7 17:58:06 physth03 kernel: [ 5795.409391] Inbound IN=eth0 OUT= MAC=00:15:f2:0d:03:d6:00:0e:c0:29:92:0c:08:00 SRC=62.69.179.208 DST=164.15.124.65 LEN=1500 TOS=0x00 PREC=0x00 TTL=55 ID=35751 PROTO=TCP SPT=80 DPT=59579 WINDOW=22112 RES=0x00 ACK URGP=0 


dmesg (last two lines are from network restart to network stalling)
-----------------------------------------------------------
[ 6180.848093] Inbound IN=eth0 OUT= MAC=00:15:f2:0d:03:d6:00:0e:c0:29:92:0c:08:00 SRC=62.69.179.213 DST=164.15.124.65 LEN=40 TOS=0x00 PREC=0x00 TTL=54 ID=61392 PROTO=TCP SPT=80 DPT=35670 WINDOW=8192 RES=0x00 ACK URGP=0 
[ 6226.863754] e100: eth0: e100_watchdog: link up, 10Mbps, half-duplex
[ 6237.349941] eth0: no IPv6 routers present


/etc/udev/rules.d/70-persistent-net.rules
-----------------------------------------------------------
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Commented out by me
# PCI device 0x8086:0x1064 (e100)
# SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:11:d8:2b:ce:18", NAME="eth0"

# Commented out by me
# PCI device 0x8086:0x1064 (e100)
# SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:15:f2:0d:03:d6", NAME="eth1"

# Changed eth1 -> eth0 here
# PCI device 0x8086:0x1064 (e100)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:15:f2:0d:03:d6", NAME="eth0"


/etc/network/interfaces
-----------------------------------------------------------
auto lo
iface lo inet loopback

iface eth0 inet static
address 164.15.124.65
netmask 255.255.255.0
gateway 164.15.124.254

auto eth0

# Commented out by me
# iface eth1 inet static
# address 164.15.124.65
# netmask 255.255.255.0
# gateway 165.15.124.254

# auto eth1


ifconfig
-----------------------------------------------------------
eth0      Link encap:Ethernet  HWaddr 00:15:F2:0D:03:D6  
          inet addr:164.15.124.65  Bcast:164.15.124.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe0d:3d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:321 txqueuelen:1000 
          RX bytes:943069 (920.9 KB)  TX bytes:155623 (151.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25961 (25.3 KB)  TX bytes:25961 (25.3 KB)



route (after network restart)
-----------------------------------------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
164.15.124.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         gate-1242N4.113 0.0.0.0         UG    100    0        0 eth0


route (when stalled)
-----------------------------------------------------------
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
164.15.124.0    *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         164.15.124.254  0.0.0.0         UG    100    0        0 eth0

---

### Post by brnd on 2008-02-11
Hi,

Just a quick follow-up to let you know that it turned out to be a hardware problem... I (re)installed ubuntu and openSUSE but the problem persisted. A new motherboard did solve the problem.

Cheers,

Bernard

---

