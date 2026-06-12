---
title: "Cannot connect using WPA-PSK"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by toddhd on 2007-02-26
I am running a "clean" install of Ubuntu 6.10. This PC connects fine while running Mandriva, so I know my hardware is Linux compatible and setup properly. I replaced Mandriva with Ubuntu, but can't seem to get the network running at all. Here is a copy of my 'interfaces' file:
=================
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
wpa-driver wext
wpa-conf managed
wpa-ssid SeaburyDesign
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk <my hex key>

auto wlan0
iface wlan0 inet dhcp
==================
I tried changing the wpa-driver to madwifi, and changed the wpa-pairwise and group to CCMP, but no difference. I also created a /etc/wpa_supplicant.conf file with my hex key and SSID info. I followed all the troubleshooting  guides and just can't seem to get things working. Here is all the info I think to muster, maybe it will help? 

I should also note that an interface called wifi0 shows up. I'm not sure what that is, but it's the only one that shows packets coming/going. There is no IP address or anything however. I also tried to install network manager, but for some reason the install fails, and it says something like'Network manager cannot be installed on your computer type (i386)'. 

Any help would be greatly appreciated, my PC is pretty useless without an internet connection.

==============================
todd@basement:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: c
       bus info: pci@00:0c.0
       logical name: wifi0
       version: 01
       serial: 00:0f:3d:ea:0e:50
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.2) multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f7e00000-f7e0ffff irq:193
todd@basement:~$ lspci -v | grep Ethernet
00:0c.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
todd@basement:~$ sudo lspci -n
00:00.0 0600: 1106:3188 (rev 01)
00:01.0 0604: 1106:b188
00:07.0 0c00: 1106:3044 (rev 80)
00:0c.0 0200: 168c:0013 (rev 01)
00:0f.0 0104: 1106:3149 (rev 80)
00:0f.1 0101: 1106:0571 (rev 06)
00:10.0 0c03: 1106:3038 (rev 81)
00:10.1 0c03: 1106:3038 (rev 81)
00:10.2 0c03: 1106:3038 (rev 81)
00:10.3 0c03: 1106:3038 (rev 81)
00:10.4 0c03: 1106:3104 (rev 86)
00:11.0 0601: 1106:3227
00:11.5 0401: 1106:3059 (rev 60)
00:11.6 0780: 1106:3068 (rev 80)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:00.0 0300: 10de:0343 (rev a1)
todd@basement:~$ lsmod | grep ath
ath_pci               100000  0 
ath_rate_sample        16512  1 ath_pci
wlan                  207580  4 wlan_scan_sta,ath_pci,ath_rate_sample
ath_hal               192976  3 ath_pci,ath_rate_sample
todd@basement:~$ sudo iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
todd@basement:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:0F:3D:EA:0E:50  
          inet6 addr: fe80::20f:3dff:feea:e50/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:178 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13636 (13.3 KiB)  TX bytes:13636 (13.3 KiB)

wifi0     Link encap:UNSPEC  HWaddr 00-0F-3D-EA-0E-50-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5620 errors:0 dropped:0 overruns:0 frame:23
          TX packets:12168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:564680 (551.4 KiB)  TX bytes:559728 (546.6 KiB)
          Interrupt:193 Memory:f8aa0000-f8ab0000 

todd@basement:~$ sudo iwlist ath0 scan
ath0      Scan completed :
          Cell 01 - Address: 00:15:05:EE:44:EE
                    ESSID:"SeaburyDesign"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/94  Signal level=-69 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK

---

### Post by wieman01 on 2007-02-26
Can you connect to unsecured networks?

"madwifi" is definitely the right wpa-driver for your card.

---

### Post by toddhd on 2007-02-27
I don't know why that didn't work the first time I tried it , but now using madwifi as the driver seems to do the trick, everything else is the same as I have it listed here. Thanks for the help!

---

