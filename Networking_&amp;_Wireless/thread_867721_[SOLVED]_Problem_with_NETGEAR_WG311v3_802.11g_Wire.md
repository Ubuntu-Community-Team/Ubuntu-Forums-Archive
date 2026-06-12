---
title: "[SOLVED] Problem with NETGEAR WG311v3 802.11g Wireless PCI Adapter"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by ivikas on 2008-07-23
Hello all,

i have a NETGEAR WG311v3 802.11g Wireless PCI Adapter.And after referring from various post, i managed to install the driver using ndiswrapper.I  have done this solely   using internet resources and i got connected to internet using ubuntu 8.04 LTS.This is what i have done.


NETGEAR WG311v3 802.11g Wireless PCI Adapter(SOLVED)

Ubuntu Version:8.04 LTS Desktop

Ndiswrapper 
ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
ndiswrapper-common_1.50-1ubuntu1_all.deb

Driver Selected
NETGEAR WG311v3 windows XP driver

----------------------------------------------------------------
Now Installed all above like this:

root@-desktop:~# ndiswrapper -h
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card

root@-desktop:~# cd WG311v3\ V1.0/Driver/Windows\ 
Windows 2000/ Windows 98/   Windows ME/   Windows XP/   

root@-desktop:~# cd WG311v3\ V1.0/Driver/Windows\ XP/

root@-desktop:~/WG311v3 V1.0/Driver/Windows XP# ls
WG311v3.cat  WG311v3.INF  WG311v3.sys  WG311v3XP.sys

root@-desktop:~/WG311v3 V1.0/Driver/Windows XP# ndiswrapper -i WG311v3.INF 
installing wg311v3 ...

root@-desktop:~/WG311v3 V1.0/Driver/Windows 2000# ndiswrapper -l
[COLOR="Red"]wg311v3 : driver installed
	device (11AB:1FAA) present
[/COLOR]

root@-desktop:~/WG311v3 V1.0/Driver/Windows 2000# 

[COLOR="Red"]Ifconfig Output[/COLOR]

~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:d1:7a:20:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x20c0 Memory:50300000-50320000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1564 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1564 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81408 (79.5 KB)  TX bytes:81408 (79.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:2c:dc:f9  
          inet6 addr: fe80::21b:2fff:fe2c:dcf9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:53 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:175187 (171.0 KB)  TX bytes:21676 (21.1 KB)
          Interrupt:23 Memory:50000000-50010000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:2f:2c:dc:f9  
          inet addr:169.254.9.75  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:23 Memory:50000000-50010000 


[COLOR="Red"]IWconfig Output[/COLOR]

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"NETWORKID"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:60:B3:35:35:B2   
          Bit Rate=36 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

-----------------------------------------------------------------
[COLOR="Red"]DMESG OUTPUT[/COLOR]

dmesg tail

[ 3596.049468] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3596.090635] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[ 3596.090770] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 22 (level, low) -> IRQ 23
[ 3596.091253] ndiswrapper: using IRQ 23
[ 3596.350638] wlan0: ethernet device 00:1b:2f:2c:dc:f9 using NDIS driver: wg311v3, version: 0x3000036, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:1FAA.5.conf
[ 3596.350655] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 3596.350706] usbcore: registered new interface driver ndiswrapper
[ 3598.160184] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3669.993980] heci: schedule work the heci_bh_handler failed error=0
[ 3706.520318] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3710.071802] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3713.736498] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3713.761670] NET: Registered protocol family 17
[ 3720.250853] wlan0: no IPv6 routers present
[ 3736.942182] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3821.691214] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3825.348107] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3829.103139] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3831.842907] wlan0: no IPv6 routers present
[ 3848.210321] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3915.549491] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3915.686031] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3919.408591] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3923.300312] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3930.492619] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3946.648901] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3946.661021] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3948.569758] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3950.477270] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3972.252215] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3975.932720] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 3980.717887] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3990.743111] wlan0: no IPv6 routers present
[ 4000.479652] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4336.055711] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4336.084399] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4337.971601] ADDRCONF(NETDEV_UP): eth0: link is not ready
[COLOR="Red"][ 4344.546600] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready[/COLOR]
[ 4345.818271] heci: schedule work the heci_bh_handler failed error=0
[ 4355.287810] wlan0: no IPv6 routers present
[ 4362.633610] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4645.748388] heci: schedule work the heci_bh_handler failed error=0
----------------------------------------------------------------

After this i installed a a gui for ndiswrapper and installed winXP driver with it and i got connected to internet.

This is the GUI package

ndisgtk_0.7.2-1ubuntu1_i386.deb


Finally from  System->Administration->Network configure your wirless network.



ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.189.104) 56(84) bytes of data.
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=1 ttl=243 time=146 ms
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=2 ttl=246 time=112 ms
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=3 ttl=243 time=143 ms
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=4 ttl=243 time=282 ms
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=6 ttl=246 time=426 ms
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=7 ttl=243 time=419 ms
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=8 ttl=243 time=371 ms
64 bytes from hk-in-f104.google.com (64.233.189.104): icmp_seq=9 ttl=246 time=326 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 8002ms
rtt min/avg/max/mdev = 112.337/278.530/426.836/120.386 ms

---

### Post by superprash2003 on 2008-07-23
try this.. go to system->admin->network and go to wireless connection (wlan0) properties.. and enter the SSID and other details manually.. also try entering the ip address manually and then see if you are able to connect.. the problem is that you arent getting an ip.. your drivers seem to be fine

---

