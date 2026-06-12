---
title: "Unable to connect to the internet using AR2413"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by netranger on 2008-01-30
Hi

I have setup madwifi on gutsy and all indications tell me everything appears to be running ok and I am connected to my router.  When i check my router it does confirm my wireless is connected and gutsy seems to think so also, but i cannot connect to the internet.  Any help would be greatly appreciated.

Details are below:

$ uname -r
2.6.22-14-generic

$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 6
       bus info: pci@0000:00:06.0
       logical name: wifi0
       version: 01
       serial: 00:c0:a8:bc:67:cd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=svn r3297 latency=96 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:14:0b:00:90:76
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=64 link=no maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=10MB/s

$ ps -ef | grep ath0
dhcp      6717  4896  0 23:23 ?        00:00:00 /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.ath0.leases -pf /var/run/dhclient.ath0.pid -q -e dhc_dbus=31 -d ath0

$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:C0:A8:BC:67:CD  
          inet addr:192.168.38.3  Bcast:192.168.38.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:febc:67cd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:331000 (323.2 KB)  TX bytes:10762 (10.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-C0-A8-BC-67-CD-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:97553 errors:0 dropped:0 overruns:0 frame:2720
          TX packets:2682 errors:10 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:195 
          RX bytes:11197293 (10.6 MB)  TX bytes:136292 (133.0 KB)
          Interrupt:19 

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"SKY61079"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:4D:41:B4:5C   
          Bit Rate:18 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=48/70  Signal level=-38 dBm  Noise level=-86 dBm
          Rx invalid nwid:1  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

$ lspci | grep Atheros
00:06.0 Ethernet controller: Atheros Communications, Inc. AR2413 802.11bg NIC (rev 01)

$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.38.0    *               255.255.255.0   U     0      0        0 ath0
link-local      *               255.255.0.0     U     1000   0        0 ath0
default         192.168.38.1    0.0.0.0         UG    0      0        0 ath0

$ ping bbc.co.uk
ping: unknown host bbc.co.uk

When i query my router it confirms that I am an attached device, however it shows the device name as "UNKNOWN" instead of "lpd-laptop".  The madwifi version i have compiled was the latest on this final push and is tagged "madwifi-ng-r3297-20080129" after being unzipped from the current repository download.

If you need any further information please let me know.  If i bring eth0 back up i can connect no problems.  Any help appreciated, 2 weeks in and either this laptop or myself goes out of the window!

---

