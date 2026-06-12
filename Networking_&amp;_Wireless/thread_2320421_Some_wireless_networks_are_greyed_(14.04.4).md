---
title: "Some wireless networks are greyed (14.04.4)"
date: 2016-04-13
forum: Networking &amp; Wireless
---

### Post by danielsender on 2016-04-13
I was trying a few PCI wifi adapters on my legacy HP pavilion and all of them are giving me troubles. For example I installed the driver for a belkin with the airgo agn100 chipset without any problems using the diswrapper utility. However when it lists the available wireless networks most of them appear greyed out, just a few ATTxxx seem to be available to connect (not accesible by me). This does not happen with another laptop with an internal wireless card. Googling around it seems similar to bug #952126. I wonder if anybody experienced the same thing with newer distributions.

Thanks in advance.

Daniel

---

### Post by danielsender on 2016-04-14
bump

One more thing: I entered the name of my wireless network after clicking on "unlisted networks (or something like that)", it prompts me for a password and after waiting for a moment comes back asking me for the password again.

---

### Post by danielsender on 2016-04-15
bump^2

---

### Post by Bucky Ball on 2016-04-16
Please run the wirelessinfo script in my signature at the bottom of this post. Post the output back here between code tags thanks (see the green link in my sig).

Please confirm which card you want to get working and we'll work on that rather than half a dozen, which can only get confusing. Whichever you choose to use, make sure it is plugged in (and preferably the ethernet cable is unplugged) when you run the wirelessinfo script.

---

### Post by danielsender on 2016-04-16
I wasn't sure that I could enclose a binary file (.gz) between code delimiters, so I uncompressed it.
```
########## wireless info START ##########


Report from: 16 Apr 2016 19:56 PDT -0700


Booted last: 16 Apr 2016 19:34 PDT -0700


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:41 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME Flashback (Metacity) (from ~/.dmrc)


##### lspci #############################


00:10.0 Ethernet controller [0200]: Accton Technology Corporation EN-1216 Ethernet Adapter [1113:1216] (rev 11)
    Subsystem: Accton Technology Corporation EN2242 10/100 Ethernet Mini-PCI Card [1113:2242]
    Kernel driver in use: tulip


02:00.0 Ethernet controller [0200]: Airgo Networks, Inc. AGN100 802.11 a/b/g True MIMO Wireless Card [17cb:0001] (rev 01)
    Subsystem: Linksys Device [1737:0037]
    Kernel driver in use: ndiswrapper


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


##### lsmod #############################


cfg80211              417586  0 
ndiswrapper           192915  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.25  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:206379 (206.3 KB)  TX bytes:89667 (89.6 KB)


ham0      Link encap:Ethernet  HWaddr <MAC 'ham0' [IF]>  
          inet addr:25.131.216.163  Bcast:25.255.255.255  Mask:255.0.0.0
          inet6 addr: 2620:9b::1983:d8a3/96 Scope:Global
          inet6 addr: fe80::<IP6 'ham0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1404  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:18907 (18.9 KB)


wlan5     Link encap:Ethernet  HWaddr <MAC 'wlan5' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:28000000-28080000 


##### iwconfig ##########################


lo        no wireless extensions.


ham0      no wireless extensions.


eth0      no wireless extensions.


wlan5     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:108 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
25.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 ham0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       769     1  0 19:34 ?        00:00:05 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Ethernet connection 1] ----------------------------------------
  Type:              Wired
  Driver:            tulip
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.2.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4


- Device: wlan5 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan5' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes


  Wireless Access Points 
    discepolo:       Infra, <MAC 'discepolo' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA2
    gardel:          Infra, <MAC 'gardel' [AC2]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 100 WPA2
    bach:            Infra, <MAC 'bach' [AC3]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA2
    vivaldi:         Infra, <MAC 'vivaldi' [AC5]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 100 WPA2
    ATT824:          Infra, <MAC 'ATT824' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Mike's place:    Infra, <MAC 'Mike's place' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    ELIJAH's Wi-Fi Network: Infra, <MAC 'ELIJAH's Wi-Fi Network' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2


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


[[/etc/NetworkManager/system-connections/belkin.4f4 1]] (600 root)
[connection] id=belkin.4f4 1 | type=802-11-wireless
[802-11-wireless] ssid=belkin.4f4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/vivaldi_5g]] (600 root)
[connection] id=vivaldi_5g | type=802-11-wireless
[802-11-wireless] ssid=vivaldi_5g | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Actiontec]] (600 root)
[connection] id=Actiontec | type=802-11-wireless
[802-11-wireless] ssid=Actiontec | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Motel 6]] (600 root)
[connection] id=Motel 6 | type=802-11-wireless
[802-11-wireless] ssid=Motel 6 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/xfinitywifi 1]] (600 root)
[connection] id=xfinitywifi 1 | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/madhouse]] (600 root)
[connection] id=madhouse | type=802-11-wireless
[802-11-wireless] ssid=madhouse | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/madhouse_5G]] (600 root)
[connection] id=madhouse_5G | type=802-11-wireless
[802-11-wireless] ssid=madhouse_5G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Cindy's Wi-Fi Network]] (600 root)
[connection] id=Cindy's Wi-Fi Network | type=802-11-wireless
[802-11-wireless] ssid=Cindy's Wi-Fi Network | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/vivaldi]] (600 root)
[connection] id=vivaldi | type=802-11-wireless
[802-11-wireless] ssid=vivaldi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/vivaldi 3]] (600 root)
[connection] id=vivaldi 3 | type=802-11-wireless
[802-11-wireless] ssid=vivaldi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/vivaldi 4]] (600 root)
[connection] id=vivaldi 4 | type=802-11-wireless
[802-11-wireless] ssid=vivaldi | mac-address=<MAC 'wlan5' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/earthpal]] (600 root)
[connection] id=earthpal | type=802-11-wireless
[802-11-wireless] ssid=earthpal | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/2WIRE728]] (600 root)
[connection] id=2WIRE728 | type=802-11-wireless
[802-11-wireless] ssid=2WIRE728 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/belkin.4f4]] (600 root)
[connection] id=belkin.4f4 | type=802-11-wireless
[802-11-wireless] ssid=belkin.4f4 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/vivaldi 1]] (600 root)
[connection] id=vivaldi 1 | type=802-11-wireless
[802-11-wireless] ssid=vivaldi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/lukaboy]] (600 root)
[connection] id=lukaboy | type=802-11-wireless
[802-11-wireless] ssid=lukaboy | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/gardel]] (600 root)
[connection] id=gardel | type=802-11-wireless
[802-11-wireless] ssid=gardel | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/xfinitywifi]] (600 root)
[connection] id=xfinitywifi | type=802-11-wireless
[802-11-wireless] ssid=xfinitywifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/ATT824]] (600 root)
[connection] id=ATT824 | type=802-11-wireless
[802-11-wireless] ssid=ATT824 | mac-address=<MAC 'wlan5' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/madhouse_5g]] (600 root)
[connection] id=madhouse_5g | type=802-11-wireless
[802-11-wireless] ssid=madhouse_5g | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/vivaldi 2]] (600 root)
[connection] id=vivaldi 2 | type=802-11-wireless
[802-11-wireless] ssid=vivaldi | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/grieg]] (600 root)
[connection] id=grieg | type=802-11-wireless
[802-11-wireless] ssid=grieg | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/lukaboy 1]] (600 root)
[connection] id=lukaboy 1 | type=802-11-wireless
[802-11-wireless] ssid=lukaboy | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


ham0      no frequency information.


eth0      no frequency information.


wlan5     14 channels in total; available frequencies :
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
          Current Channel:0


##### iwlist scan #######################


lo        Interface doesn't support scanning.


ham0      Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.442 GHz (Channel 7)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlan5     Scan completed :
          Cell 01 - Address: <MAC 'discepolo' [AC1]>
                    ESSID:"discepolo"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:100/100  Signal level:100/154  Noise level:160/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'gardel' [AC2]>
                    ESSID:"gardel"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:100/100  Signal level:100/154  Noise level:160/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'bach' [AC3]>
                    ESSID:"bach"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:100/100  Signal level:100/154  Noise level:160/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'ATT824' [AC4]>
                    ESSID:"ATT824"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:70/154  Noise level:160/154
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
          Cell 05 - Address: <MAC 'vivaldi' [AC5]>
                    ESSID:"vivaldi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality:100/100  Signal level:100/154  Noise level:160/154
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-85-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-85-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        78:68:14:66:CC:B0:7A:DA:85:CC:07:B4:2F:F6:E3:82:2D:04:58:22
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ndiswrapper]
filename:       /lib/modules/3.13.0-85-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     C101C962263FFF26465A483
depends:        
vermagic:       3.13.0-85-generic SMP mod_unload modversions 686 
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


lp
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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1113:0x1216 (tulip)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0013 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x168c:0x001a (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
# PCMCIA device 0x0002:0x0156 (orinoco_cs)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x168c:0x001a (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan4"
# PCMCIA device 0x000a:0x015f (airo_cs)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x17cb:0x0001 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan5' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan5"


##### dmesg #############################


[   42.774756] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e529bd
[   42.779121] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0b67000
[   42.783491] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdbd33000
[   42.787855] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdb6a5276
[   42.792101] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e52ae1
[   42.796454] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0ed68c9
[   46.747696] ndiswrapper (NdisWriteErrorLogEntry:188): log: C000138A, count: 8, return_address: e0e56ffa
[   46.752563] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x6e6b6e55
[   46.757241] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x206e776f
[   46.761837] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20536f51
[   46.766221] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x69746341
[   46.770599] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x32206e6f
[   46.774977] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x6c282037
[   46.779267] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x32206e65
[   46.783717] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xa2935
[   46.788148] ndiswrapper (NdisWriteErrorLogEntry:188): log: C000138A, count: 8, return_address: e0e56ffa
[   46.792658] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x706d7544
[   46.797369] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20676e69
[   46.801941] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x62203532
[   46.806366] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x73657479
[   46.810699] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x206e6920
[   46.815159] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x74736f68
[   46.819646] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x64726f20
[   46.824112] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xa7265
[   46.828506] ndiswrapper (NdisWriteErrorLogEntry:188): log: C000138A, count: 8, return_address: e0e56ffa
[   46.833256] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x66206231
[   46.838040] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30302066
[   46.842494] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20303020
[   46.846957] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30203030
[   46.851446] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30302030
[   46.855931] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20303020
[   46.860329] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e5000a
[   46.864831] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0ed6917
[   46.869344] ndiswrapper (NdisWriteErrorLogEntry:188): log: C000138A, count: 8, return_address: e0e56ffa
[   46.874115] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30203030
[   46.878816] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30302030
[   46.883449] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20303020
[   46.887930] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30203030
[   46.892260] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30302031
[   46.896628] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20303020
[   46.901076] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e5000a
[   46.905537] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0ed68f5
[   46.909915] ndiswrapper (NdisWriteErrorLogEntry:188): log: C000138A, count: 8, return_address: e0e56ffa
[   46.914647] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30203030
[   46.919398] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30302030
[   46.923966] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20303020
[   46.928324] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30203030
[   46.932735] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x30302030
[   46.937147] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x20303020
[   46.941542] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e5000a
[   46.945847] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0ed68f5
[   46.950244] ndiswrapper (NdisWriteErrorLogEntry:188): log: C000138A, count: 8, return_address: e0e56ffa
[   46.954905] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0x206433
[   46.959409] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdbe26604
[   46.963936] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e529bd
[   46.968328] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0b67000
[   46.972699] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdb1e9f00
[   46.977007] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdbe2665a
[   46.981373] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e52ae1
[   46.985758] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0ed68f5
[   46.990139] ndiswrapper (NdisWriteErrorLogEntry:188): log: C000138A, count: 8, return_address: e0e56ffa
[   46.994715] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdbd3000a
[   46.999385] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdb6a5484
[   47.003917] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e529bd
[   47.008298] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0b67000
[   47.012586] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdbd33000
[   47.016952] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xdb6a54b6
[   47.021330] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0e52ae1
[   47.025561] ndiswrapper (NdisWriteErrorLogEntry:191): code: 0xe0ed68c9
[   48.049723] IPv6: ADDRCONF(NETDEV_UP): wlan5: link is not ready (repeated 2 times)
[   51.153783] tulip 0000:00:10.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972117)
[   51.153815] net eth0: Setting full-duplex based on MII#1 link partner capability of 45e1


########## wireless info END ############

```

Thanks.

---

### Post by danielsender on 2016-04-18
Any ideas?

I noticed that some lines within the output of the script say "Permission Denied", should I re-run the script as root, or that information is not relevant?

---

### Post by danielsender on 2016-04-19
(bump)^3

---

### Post by danielsender on 2016-04-20
(bump)^4

---

### Post by danielsender on 2016-04-22
(bump)^5

---

### Post by jeremy31 on 2016-04-22
I would take the lack of activity to indicate that solutions can't be found.  You will likely have better results using an Intel or Atheros wifi card as anything I have had that needed ndiswrapper has had issues

---

