---
title: "YoutubeVideos Turns Wifi off. Ubuntu 14.04."
date: 2014-09-26
forum: Networking &amp; Wireless
---

### Post by inspiral2 on 2014-09-26
[FONT=arial]To be Specific: it seems as though overloaded internet traffic turns it off, 
whenever a youtube video was clicked or something was being downloaded; e.g. earlier when [/FONT]"[FONT=Ubuntu Mono][COLOR=#000000]sudo apt-get dist-upgrade" was executed, N300 USB adapter Wna3100, had to be plugged off and on as it;
[/COLOR][/FONT][SIZE=2][COLOR=#000000]-Connected
-Downloaded few more %
[/COLOR]-Wifi wave live and yet frozen% with internet not working ( on the command box)[/SIZE]
[CENTER]=Thus it had to be unplugged and ON it went until all was downloaded and nothing fixed.[/CENTER]

Here is the wireless-info.txt (~) -Gedit:
```


########## wireless info START ##########


Report from: 26 Sep 2014 23:18 BST +0100


Booted last: 26 Sep 2014 23:14 BST +0100


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7641]
    Kernel driver in use: r8169


##### lsusb #############################


Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c534 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
Bus 001 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              521225  0 
ndiswrapper           283985  0 
wmi                    19379  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::4e60:deff:fe6e:fa36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:433 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:152219 (152.2 KB)  TX bytes:50503 (50.5 KB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"SKYFDDDE"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'SKYFDDDE' [AC1]>   
          Bit Rate=117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:71/100  Signal level:-50 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:4532   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search Home


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [SKYFDDDE] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           117 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    SKY5CA82:        Infra, <MAC 'SKY5CA82' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    *SKYFDDDE:       Infra, <MAC 'SKYFDDDE' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 71 WPA2


  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/SKYFDDDE]] (600 root)
[connection] id=SKYFDDDE | type=802-11-wireless
[802-11-wireless] ssid=SKYFDDDE | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'SKYFDDDE' [AC1]>
                    ESSID:"SKYFDDDE"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:75/100  Signal level:-48 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SKY5CA82' [AC2]>
                    ESSID:"SKY5CA82"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.16.0-031600-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D86AFD97E7F71C59777C05F
depends:        
intree:         Y
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        22:1A:AC:02:5E:17:C8:E7:6D:81:97:A5:3A:A7:65:A4:61:7A:E7:DC
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.16.0-031600-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.16.0-031600-generic SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]


##### /etc/modules ######################


fuse
lp
sbp2
ndiswrapper


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper
alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip* ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[   32.288087] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.621430] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  180.421571] ndiswrapper: device wlan0 removed
[  182.897059] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[  183.295855] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001477e000, 16000, 4
[  183.295859] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014781e80, 16000, 5
[  183.295861] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014785d00, 16000, 5
[  183.295863] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014789b80, 16000, 5
[  183.295865] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001478da00, 16000, 5
[  183.295867] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014791880, 16000, 5
[  183.295869] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014795700, 16000, 5
[  183.295871] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014799580, 16000, 5
[  183.295872] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001479d400, 16000, 5
[  183.295874] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147a1280, 16000, 5
[  183.295875] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147a5100, 16000, 4
[  183.295877] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147a8f80, 16000, 5
[  183.295879] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147ace00, 16000, 5
[  183.295880] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147b0c80, 16000, 5
[  183.295882] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147b4b00, 16000, 5
[  183.295884] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147b8980, 16000, 5
[  183.295885] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147bc800, 16000, 5
[  183.295887] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147c0680, 16000, 5
[  183.295888] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147c4500, 16000, 5
[  183.295890] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147c8380, 16000, 5
[  183.295891] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147cc200, 16000, 5
[  183.295893] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147d0080, 16000, 4
[  183.295895] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147d3f00, 16000, 5
[  183.295896] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147d7d80, 16000, 5
[  183.295898] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147dbc00, 16000, 5
[  183.295900] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147dfa80, 16000, 5
[  183.295901] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147e3900, 16000, 5
[  183.295903] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147e7780, 16000, 5
[  183.295905] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147eb600, 16000, 5
[  183.295906] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147ef480, 16000, 5
[  183.295908] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147f3300, 16000, 5
[  183.295909] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147f7180, 16000, 4
[  183.295911] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147fb000, 16000, 4
[  183.295913] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900147fee80, 16000, 5
[  183.295927] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014802d00, 16000, 5
[  183.295928] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014806b80, 16000, 5
[  183.295930] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001480aa00, 16000, 5
[  183.295939] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001480e880, 16000, 5
[  183.295945] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014812700, 16000, 5
[  183.295952] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014816580, 16000, 5
[  183.295958] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001481a400, 16000, 5
[  183.295965] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001481e280, 16000, 5
[  183.295971] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014822100, 16000, 4
[  183.295978] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014825f80, 16000, 5
[  183.295985] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014829e00, 16000, 5
[  183.295990] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001482dc80, 16000, 5
[  183.295994] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014831b00, 16000, 5
[  183.295995] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014835980, 16000, 5
[  183.295997] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90014839800, 16000, 5
[  183.295999] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9001483d680, 16000, 5
[  183.310878] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[  183.590261] wlan0: ethernet device <MAC 'wlan0' [IF]> using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[  183.596410] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[  183.613682] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  204.513574] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```
[FONT=arial]NewNoob on Ubuntu- obviously.
 Your help would be greatly appreciated, even though it'll only be by me (For no one else seems to be having this problem) 

A challenge Shearlocks to logic it out.
Hello, Please and Thank You.

---------------------------------

[/FONT]On recent searches of the web this was found



[FONT=arial]
> 
[/FONT]> Mint 15 is working pretty well so far aside from my previously mentioned issues with the wireless card in my laptop. Problems ranged from high dropped packet rates to disconnects to the truly bizarre, such as inability to ping the wireless access point it&#8217;s connected to yet being able to ping the other machines it&#8217;s connected to through that access point. Since that is also the default gateway, that means it loses any connectivity to the outside world.


After a web search, the solution appears to be _disabling hardware encryption_. The wireless chip is apparently overloaded trying to do the encryption as well as everything else it has to do, which makes sense because it would normally go horribly wrong when starting Firefox, which hits the Internet to download a number of web pages when restoring the old configuration.


To do this, create a file /etc/modprobe.d/rtl8192se.conf and put the following line in it:


options rtl8192se swenc=1


This forces software encryption, which appears to be an insignificant overhead on an i5 CPU. Since enabling this I&#8217;ve run for a few hours with no problems, but I&#8217;ll update this if I do.
[FONT=arial]
[/FONT][FONT=arial]
[/FONT]http://blog.edwardmgrant.com/?p=1410
by Edward.M.Grant

the problem being it's a solution for; Mint 15 not ubuntu 14.04 and Realtek not netgear but the main problem is overheating I think.
also I haven't a clue as to what it's instructing, where is wna3100 file located? This "/etc/modprobe.d/rtl8192se.conf"
if you know then please do the honours.

---

### Post by inspiral2 on 2014-09-27
>Bumpus formus {to the topus}< no solution found yet! you who know their ubuntu please try, thank you.

---

### Post by inspiral2 on 2014-09-27
Possibly, it's the usb card at fault, I've had it for about a year or more and occasionally it behaved the same on past OS Windows. 

Meh.

---

### Post by jeremy31 on 2014-09-27
> **inspiral2 said:**
> Possibly, it's the usb card at fault, I've had it for about a year or more and occasionally it behaved the same on past OS Windows. 

Meh.

It could be that the fault might be with the USB card but ndiswrapper is the only option with no linux drivers being available.  I have the same card and I tried to make it work better than what it does and found no solutions.  I do have an older USB card that works nice but it has no wireless-N capability.  If you find one cheap, it might be worth trying, Linksys WUSB54GSC

---

### Post by inspiral2 on 2014-09-27
> **jeremy31 said:**
> It could be that the fault might be with the USB card but ndiswrapper is the only option with no linux drivers being available.  I have the same card and I tried to make it work better than what it does and found no solutions.  I do have an older USB card that works nice but it has no wireless-N capability.  If you find one cheap, it might be worth trying, Linksys WUSB54GSC


I shall get a new wefe dongle tomorrow and test the theory, if wrong, this thread will persist on pissing ubuntu fourm N&W until satisfactory climax.


```
No but really | though youtube matters little or non-at-all
{simple not-a-lotta-image <learn coding>websites works} 
And it being the main reason for changing to linux
I care not.
```

All aside,
Thank you for the reply, Jeremy possibly 31

---

