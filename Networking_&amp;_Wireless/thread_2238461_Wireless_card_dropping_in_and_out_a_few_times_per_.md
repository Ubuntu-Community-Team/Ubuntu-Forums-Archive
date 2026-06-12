---
title: "Wireless card dropping in and out a few times per second"
date: 2014-08-08
forum: Networking &amp; Wireless
---

### Post by Ryan_Akers on 2014-08-08
Hi All, 

I installed Ubuntu 14.04 for the first foray into Linux a couple of weeks back. 
So far it's going well, exept that I can't get my wireless card to work. 
I have found lots of topics on using this card AWUS036H, however none of them seem to have an answer that works for me. 
An interesting thing to note is that when I click on the network icon I can see the wired connection stable, but the wireless section of the drop down flickers on and off. This is also shown in lsusb whereby it shows the connected device only occasionally if I run the command a few times in a row. 

I appreciate any help I can get. 

Thanks

Ryan

The output of the wireless script provided here is:


```
########## wireless info START ##########

Report from: 08 Aug 2014 16:02 EST +1000

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
    Kernel driver in use: e1000e

##### lsusb #####

Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 1c4f:0032 SiGma Micro 
Bus 003 Device 003: ID 046d:c626 Logitech, Inc. 3Dconnexion Space Navigator 3D Mouse
Bus 003 Device 036: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 003 Device 006: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 003 Device 005: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

30: phy30: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

rtl8187                64909  0 
mac80211              630653  1 rtl8187
cfg80211              484040  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
video                  19476  1 asus_wmi
wmi                    19177  2 mxm_wmi,asus_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1241746 (1.2 MB)  TX bytes:183403 (183.4 KB)
          Interrupt:20 Memory:f7f00000-f7f20000 

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8187
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

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

##### iwlist scan #####

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : No such device

##### module infos #####

[rtl8187]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andrea.merello@gmail.com>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     A707FEC6B464A70F7A04C69
alias:          usb:v1737p0073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p8187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6232d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D1pABE6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1371p9401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v114Bp0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0029d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p000Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0pCA02d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p4260d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p6A00d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p6100d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p010Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0769p11F2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8198d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8189d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8187d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp705Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p171Dd*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,eeprom_93cx6,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512

##### module parameters #####

##### /etc/modules #####

lp
rtc

##### blacklists #####

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
blacklist rt2800lib
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb

##### udev rules #####

# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rndis_host)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[    0.796451] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.962143] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.873890] type=1400 audit(1407477679.603:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
[    1.874238] type=1400 audit(1407477679.603:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=548 comm="apparmor_parser"
[    2.409089] ieee80211 phy0: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[    2.416920] rtl8187: Customer ID is 0xFF
[    2.417250] rtl8187: wireless switch is on
[    4.233153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.119928] ieee80211 phy1: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[    5.127389] rtl8187: Customer ID is 0xFF
[    5.127652] rtl8187: wireless switch is on
[    6.944169] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    8.976374] ieee80211 phy2: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[    8.984943] rtl8187: Customer ID is 0xFF
[    8.985244] rtl8187: wireless switch is on
[   10.810716] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.990108] ieee80211 phy3: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   23.997565] rtl8187: Customer ID is 0xFF
[   23.997828] rtl8187: wireless switch is on
[   25.813336] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.708412] ieee80211 phy4: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   26.715959] rtl8187: Customer ID is 0xFF
[   26.716225] rtl8187: wireless switch is on
[   28.539736] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.417176] ieee80211 phy5: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   29.424698] rtl8187: Customer ID is 0xFF
[   29.424963] rtl8187: wireless switch is on
[   31.249379] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.899216] ieee80211 phy6: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   31.906700] rtl8187: Customer ID is 0xFF
[   31.906964] rtl8187: wireless switch is on
[   33.727224] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   34.380841] ieee80211 phy7: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   34.388315] rtl8187: Customer ID is 0xFF
[   34.388577] rtl8187: wireless switch is on
[   36.213072] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   36.883084] ieee80211 phy8: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   36.890562] rtl8187: Customer ID is 0xFF
[   36.890832] rtl8187: wireless switch is on
[   38.702936] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   39.373462] ieee80211 phy9: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   39.380930] rtl8187: Customer ID is 0xFF
[   39.381194] rtl8187: wireless switch is on
[   41.200811] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.862390] ieee80211 phy10: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   41.869854] rtl8187: Customer ID is 0xFF
[   41.870117] rtl8187: wireless switch is on
[   43.686625] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.353165] ieee80211 phy11: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   44.360752] rtl8187: Customer ID is 0xFF
[   44.361031] rtl8187: wireless switch is on
[   46.180399] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   46.862013] ieee80211 phy12: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   46.869778] rtl8187: Customer ID is 0xFF
[   46.870042] rtl8187: wireless switch is on
[   48.694326] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.377082] ieee80211 phy13: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   49.384569] rtl8187: Customer ID is 0xFF
[   49.384835] rtl8187: wireless switch is on
[   51.200172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.858840] ieee80211 phy14: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   51.866423] rtl8187: Customer ID is 0xFF
[   51.866689] rtl8187: wireless switch is on
[   53.690029] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   54.588366] ieee80211 phy15: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   54.595886] rtl8187: Customer ID is 0xFF
[   54.596156] rtl8187: wireless switch is on
[   56.415666] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.069425] ieee80211 phy16: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   57.076900] rtl8187: Customer ID is 0xFF
[   57.077169] rtl8187: wireless switch is on
[   58.889540] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   59.524548] ieee80211 phy17: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   59.532031] rtl8187: Customer ID is 0xFF
[   59.532296] rtl8187: wireless switch is on
[   61.347330] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   62.012933] ieee80211 phy18: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   62.020435] rtl8187: Customer ID is 0xFF
[   62.020702] rtl8187: wireless switch is on
[   63.845495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   64.751884] ieee80211 phy19: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   64.759377] rtl8187: Customer ID is 0xFF
[   64.759667] rtl8187: wireless switch is on
[   66.615154] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   67.290698] ieee80211 phy20: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   67.298316] rtl8187: Customer ID is 0xFF
[   67.298609] rtl8187: wireless switch is on
[   69.140996] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.800315] ieee80211 phy21: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   69.807978] rtl8187: Customer ID is 0xFF
[   69.808263] rtl8187: wireless switch is on
[   71.642808] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   72.527195] ieee80211 phy22: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   72.535440] rtl8187: Customer ID is 0xFF
[   72.535828] rtl8187: wireless switch is on
[   74.368227] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.237416] ieee80211 phy23: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   75.244882] rtl8187: Customer ID is 0xFF
[   75.245145] rtl8187: wireless switch is on
[   77.086006] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   77.747463] ieee80211 phy24: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   77.754953] rtl8187: Customer ID is 0xFF
[   77.755216] rtl8187: wireless switch is on
[   79.595969] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   80.480845] ieee80211 phy25: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   80.489118] rtl8187: Customer ID is 0xFF
[   80.489504] rtl8187: wireless switch is on
[   82.337395] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   83.002937] ieee80211 phy26: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   83.011159] rtl8187: Customer ID is 0xFF
[   83.011546] rtl8187: wireless switch is on
[   84.831194] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   85.516757] ieee80211 phy27: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   85.524221] rtl8187: Customer ID is 0xFF
[   85.524484] rtl8187: wireless switch is on
[   87.365002] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   88.258146] ieee80211 phy28: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   88.266797] rtl8187: Customer ID is 0xFF
[   88.267258] rtl8187: wireless switch is on
[   90.110837] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   90.771507] ieee80211 phy29: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   90.779680] rtl8187: Customer ID is 0xFF
[   90.780059] rtl8187: wireless switch is on
[   92.640708] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   93.324268] ieee80211 phy30: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   93.331734] rtl8187: Customer ID is 0xFF
[   93.331999] rtl8187: wireless switch is on
[   95.186383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   96.063850] ieee80211 phy31: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   96.071323] rtl8187: Customer ID is 0xFF
[   96.071592] rtl8187: wireless switch is on
[   97.924022] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   98.805021] ieee80211 phy32: hwaddr <MAC addr wlan0>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[   98.812655] rtl8187: Customer ID is 0xFF
[   98.812980] rtl8187: wireless switch is on
[  100.673651] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############
```

---

### Post by Ryan_Akers on 2014-08-09
Turns out it was a **** USB cable. So many hours wasted....

---

