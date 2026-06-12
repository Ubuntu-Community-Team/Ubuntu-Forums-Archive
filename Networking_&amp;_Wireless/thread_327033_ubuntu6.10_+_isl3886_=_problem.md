---
title: "ubuntu6.10 + isl3886 = problem"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by aDOT on 2006-12-28
Dear friends,

I faced problem that was discussed a lot of time in many forums, but none solutions works for me.
- I installed Ubuntu6.10
- wifi isl3886 pci
- I blacklisted buildin firmware
- I installed ndiswrapper + wixXP
- i added ndiswrapper in /etc/modules
after this I reboot the machine that results in

 [I]root@andrew-laptop:/home/andrew# dmesg | grep wlan
[17179585.876000] wlan0: vendor: 'PRISM 802.11g Adapter (3886)'
[17179585.876000] wlan0: ethernet device 00:90:4b:d2:ee:f7 using NDIS driver prisma00, 1260:3886:1260:0000.5.conf
[17179585.876000] wlan0: encryption modes supported: WEP; TKIP with WPA; AES/CCMP with WPA
[17179585.884000] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
**[17182406.008000] ADDRCONF(NETDEV_UP): eth1: link is not ready**[/I]


[I]root@andrew-laptop:/home/andrew# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:03:0D:2A:B9:B8  
          inet addr:192.168.1.122  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:dff:fe2a:b9b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2596 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1604273 (1.5 MiB)  TX bytes:375062 (366.2 KiB)
          Interrupt:217 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:90:4B:D2:EE:F7  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:dfffe000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3601 (3.5 KiB)  TX bytes:3601 (3.5 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/I]


iwconfig 

[I]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Encryption key:1234-5678-AB   Security mode:restricted
          Power Management max timeout:0us  mode:All packets received
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
[/I]

[I]root@andrew-laptop:/home/andrew# iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:17:9A:D4:D9:CE
                    ESSID:"wifi"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-40 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=25[/I]


[I]root@andrew-laptop:/dev# more /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.122
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.5
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid wifi
wireless-key 12345678ab[/I]


what do i need to do????

Please HELP!!!](*,)

---

