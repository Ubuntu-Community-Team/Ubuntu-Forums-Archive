---
title: "WIFI stops working after a few minutes of use in 14.04"
date: 2015-03-18
forum: Networking &amp; Wireless
---

### Post by Linc_mc on 2015-03-18
Hey Guys,

     I recently installed Ultimate Edition 4.2 Gamers built on Ubuntu 14.04 LTS last week. Before I had a chance to explore the system properly I came across the following problem. I would be extremely grateful for any help from you guys! 

     When I turn on wifi-radar and connect to my wireless network (only source of internet on my desktop) it takes a few moments to detect and connect. The strange thing is that even after it connects wifi-radar continually states that it is "Acquiring IP Address". Then, after a few seconds to a few minutes it suddenly stops working. The connection icon still indicates "connected" and it looks like I'm connected (correct ESSID etc.), however no sites can be accessed on Firefox. If I then disconnect from my network and reconnect it will work for another few moments and fail again. WiFi works no problem under Windows 7 with one exception, and that is when I first start Windows I have to unplug the network adaptor and put it back to get wifi working, but this only occurs when I switch from UE to Windows.

     My Linux experience is pretty limited, as I have tried it out for a few weeks a couple of times over the years. However, I did install the driver for the network adaptor (which is a Netgear WNDA3100 usb). Also I did manage to download and run the wireless-script after many tries (details below). 

     Many apologies that the details are a little fudged, it is just that I am working on very little sleep. I have to write it from Windows, as in Linux by the time I ran the terminal and a few commands my internet is out! But I can provide specific details once I know what to look for. If anyone has any ideas as to what the problems may be or suggestions on how to fix it they would be greatly appreciated.


Thanks in advance,
LJ




```
                         

########## wireless info START ########## 

last: /var/log/wtmp: No such file or directory Perhaps this file was removed by the operator to
prevent logging last info. Report from: 16 Mar 2015 20:03 PDT -0700 

Booted last: 16 Mar 2015 00:00 PDT -0700 

Script from: 20 Sep 2014 23:04 UTC +0000 

##### release ########################### 

Distributor ID:    Ultimate_Edition Description:    Ultimate Edition 4.2.1 Gamers LTS Release:    4.2.1 Codename:    trusty 

##### kernel ############################ 

Linux 3.13.0-38-generic #65-Ubuntu SMP Thu Oct 9
11:36:50 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux 

Parameters: ro, quiet, splash, nomdmonddf,
nomdmonisw, vt.handoff=7 

##### desktop ########################### 

MATE 

##### lspci ############################# 

08:00.0 Ethernet controller [0200]: Realtek
Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit
Ethernet Controller [10ec:8168] (rev 06)     Subsystem: ASUSTeK Computer Inc. P8P67 and
other motherboards [1043:8432]     Kernel driver in use: r8169 

##### lsusb ############################# 

Bus 002 Device 007: ID 04e8:6860 Samsung
Electronics Co., Ltd GT-I9100 Phone [Galaxy S II], GT-I9300 Phone
[Galaxy S III], GT-P7500 [Galaxy Tab 10.1] Bus 002 Device 006: ID 093a:2521 Pixart Imaging,
Inc. 
Bus 002 Device 008: ID 0846:9011 NetGear, Inc.
WNDA3100v2 802.11abgn [Broadcom BCM4323] Bus 002 Device 004: ID 045e:003c Microsoft Corp.
SideWinder Joystick Bus 002 Device 003: ID 0e6f:011f Logic3 
Bus 002 Device 002: ID 8087:0024 Intel Corp.
Integrated Rate Matching Hub Bus 002 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 004 Device 001: ID 1d6b:0003 Linux
Foundation 3.0 root hub Bus 003 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub Bus 001 Device 002: ID 8087:0024 Intel Corp.
Integrated Rate Matching Hub Bus 001 Device 001: ID 1d6b:0002 Linux
Foundation 2.0 root hub 

##### PCMCIA card info ################## 

'pccardctl' is not installed (package
"pcmciautils"). 

##### rfkill ############################ 

./wireless_script: line 176: rfkill: command not
found 

##### lsmod ############################# 

cfg80211              484040  0 
ndiswrapper           283985  0 
mxm_wmi                13021  1 nouveau eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi sparse_keymap          13948  1 asus_wmi video                  19476  2 nouveau,asus_wmi wmi                    19177  3
mxm_wmi,nouveau,asus_wmi 

##### interfaces ######################## 

auto lo iface lo inet loopback auto eth0 iface eth0 inet dhcp 

##### ifconfig ########################## 

eth0      Link encap:Ethernet  HWaddr <MAC
'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500 
Metric:1           RX packets:0 errors:0 dropped:0
overruns:0 frame:0           TX packets:0 errors:0 dropped:0
overruns:0 carrier:0           collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wlan0     Link encap:Ethernet  HWaddr <MAC
'wlan0' [IF]>  
          inet addr:192.168.0.100 
Bcast:192.168.0.255  Mask:255.255.255.0           inet6 addr:
fe80::22e5:2aff:fe3c:fac0/64 Scope:Link           UP BROADCAST RUNNING MULTICAST 
MTU:1500  Metric:1           RX packets:66 errors:0 dropped:0
overruns:0 frame:0           TX packets:112 errors:0 dropped:0
overruns:0 carrier:0           collisions:0 txqueuelen:1000 
          RX bytes:24772 (24.7 KB)  TX
bytes:15826 (15.8 KB) 

##### iwconfig ########################## 

eth0      no wireless extensions. 

lo        no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:"Moonbeam-WIFI"
 
          Mode:Managed  Frequency:2.432 GHz 
Access Point: <MAC 'Moonbeam-WIFI' [AC1]>   
          Bit Rate=52 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B  
          Power Management:off           Link Quality:0  Signal level:0  Noise
level:0           Rx invalid nwid:0  Rx invalid crypt:0 
Rx invalid frag:0           Tx excessive retries:0  Invalid misc:0
  Missed beacon:0 

##### route ############################# 

Kernel IP routing table Destination     Gateway         Genmask        
Flags Metric Ref    Use Iface 0.0.0.0         192.168.0.1     0.0.0.0        
UG    0      0        0 wlan0 192.168.0.0     0.0.0.0         255.255.255.0  
U     9      0        0 wlan0 

##### resolv.conf ####################### 

nameserver 127.0.1.1 nameserver 127.0.1.1 search columbus.rr.com nameserver 127.0.1.1 search columbus.rr.com nameserver 127.0.1.1 search columbus.rr.com nameserver 127.0.1.1 search columbus.rr.com nameserver 127.0.1.1 search columbus.rr.com nameserver 127.0.1.1 search columbus.rr.com nameserver 127.0.1.1 nameserver 209.18.47.61 nameserver 209.18.47.62 nameserver 0.0.0.0 

##### nm-tool ########################### 

NetworkManager Tool 

State: connected (global) 

- Device: wlan0  [Moonbeam-WIFI]
-----------------------------------------------   Type:              802.11 WiFi   Driver:            ndiswrapper   State:             connected   Default:           yes   HW Address:        <MAC 'wlan0' [IF]> 

  Capabilities:     Speed:           52 Mb/s 

  Wireless Properties     WEP Encryption:  yes     WPA Encryption:  yes     WPA2 Encryption: yes 

  Wireless Access Points (* = current AP)     WiFiRSU_8770a:   Infra, <MAC
'WiFiRSU_8770a' [AC4]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 60
WPA2     Hawknest:        Infra, <MAC 'Hawknest'
[AC2]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2     Linksys00103:    Infra, <MAC
'Linksys00103' [AC3]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 30
WPA WPA2     MaxxAutosPlus:   Infra, <MAC
'MaxxAutosPlus' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20
WPA2     SETUP:           Ad-Hoc, <MAC 'SETUP'
[AC5]>, Freq 2462 MHz, Rate 11 Mb/s, Strength 72     *Moonbeam-WIFI:  Infra, <MAC
'Moonbeam-WIFI' [AC1]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 0 

  IPv4 Settings:     Address:         192.168.0.100     Prefix:          24 (255.255.255.0)     Gateway:         192.168.0.1 

    DNS:             192.168.0.1 

- Device: eth0
-----------------------------------------------------------------   Type:              Wired   Driver:            r8169   State:             unavailable   Default:           no   HW Address:        <MAC 'eth0' [IF]> 

  Capabilities:     Carrier Detect:  yes 

  Wired Properties     Carrier:         off 

##### NetworkManager.state ############## 

[main] NetworkingEnabled=true WirelessEnabled=true WWANEnabled=true WimaxEnabled=true 

##### NetworkManager.conf ############### 

[main]     plugins=ifupdown,keyfile,ofono     dns=dnsmasq 

    [ifupdown]     managed=true 

##### NetworkManager profiles ########### 

[[/etc/NetworkManager/system-connections/Moonbeam-WIFI]]
(600 root) [connection] id=Moonbeam-WIFI |
type=802-11-wireless [802-11-wireless] ssid=Moonbeam-WIFI |
mac-address=<MAC 'wlan0' [IF]> [ipv6] method=auto [ipv4] method=auto 

##### iw reg get ######################## 

Region: America/Los_Angeles (based on set time
zone) 

country 00:     (2402 - 2472 @ 40), (3, 20)     (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS     (2474 - 2494 @ 20), (3, 20), NO-OFDM,
PASSIVE-SCAN, NO-IBSS     (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS     (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN,
NO-IBSS 

##### iwlist channels ################### 

eth0      no frequency information. 

lo        no frequency information. 

wlan0     14 channels in total; available
frequencies :           Channel 01 : 2.412 GHz           Channel 02 : 2.417 GHz           Channel 03 : 2.422 GHz           Channel 04 : 2.427 GHz           Channel 05 : 2.432 GHz           Channel 06 : 2.437 GHz           Channel 07 : 2.442 GHz           Channel 08 : 2.447 GHz           Channel 09 : 2.452 GHz           Channel 10 : 2.457 GHz           Channel 11 : 2.462 GHz           Channel 12 : 2.467 GHz           Channel 13 : 2.472 GHz           Channel 14 : 2.484 GHz           Current Frequency:2.432 GHz (Channel
5) 

##### iwlist scan ####################### 

Channel occupancy: 

      2   APs on   Frequency:2.412 GHz (Channel
1)       2   APs on   Frequency:2.432 GHz (Channel
5)       2   APs on   Frequency:2.457 GHz (Channel
10)       1   APs on   Frequency:2.462 GHz (Channel
11) 

eth0      Interface doesn't support scanning. 

lo        Interface doesn't support scanning. 

wlan0     Scan completed :           Cell 01 - Address: <MAC
'Moonbeam-WIFI' [AC1]>                     ESSID:"Moonbeam-WIFI"                     Protocol:IEEE 802.11g                     Mode:Master                     Frequency:2.432 GHz (Channel
5)                     Quality:50/100  Signal
level:-64 dBm  Noise level:-96 dBm                     Encryption key:off                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 6 Mb/s; 9 Mb/s                               11 Mb/s; 12 Mb/s;
18 Mb/s                     Extra:bcn_int=100                     Extra:atim=0           Cell 02 - Address: <MAC 'Hawknest'
[AC2]>                     ESSID:"Hawknest"                     Protocol:IEEE 802.11g                     Mode:Master                     Frequency:2.432 GHz (Channel
5)                     Quality:42/100  Signal
level:-69 dBm  Noise level:-96 dBm                     Encryption key:on                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 18 Mb/s                               24 Mb/s; 36 Mb/s;
54 Mb/s                     Extra:bcn_int=100                     Extra:atim=0                     IE: IEEE 802.11i/WPA2
Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) :
CCMP TKIP                         Authentication Suites
(1) : PSK                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) :
CCMP TKIP                         Authentication Suites
(1) : PSK           Cell 03 - Address: <MAC
'Linksys00103' [AC3]>                     ESSID:"Linksys00103"                     Protocol:IEEE 802.11g                     Mode:Master                     Frequency:2.457 GHz (Channel
10)                     Quality:21/100  Signal
level:-82 dBm  Noise level:-96 dBm                     Encryption key:on                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 9 Mb/s                               18 Mb/s; 36 Mb/s;
54 Mb/s                     Extra:bcn_int=100                     Extra:atim=0                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (1) :
TKIP                         Authentication Suites
(1) : PSK                     IE: IEEE 802.11i/WPA2
Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (1) :
CCMP                         Authentication Suites
(1) : PSK           Cell 04 - Address: <MAC
'WiFiRSU_8770a' [AC4]>                     ESSID:"WiFiRSU_8770a"                     Protocol:IEEE 802.11g                     Mode:Master                     Frequency:2.457 GHz (Channel
10)                     Quality:53/100  Signal
level:-62 dBm  Noise level:-96 dBm                     Encryption key:on                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 9 Mb/s                               18 Mb/s; 36 Mb/s;
54 Mb/s                     Extra:bcn_int=100                     Extra:atim=0                     IE: IEEE 802.11i/WPA2
Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) :
CCMP                         Authentication Suites
(1) : PSK           Cell 05 - Address: <MAC 'SETUP'
[AC5]>                     ESSID:"SETUP"                     Protocol:IEEE 802.11b                     Mode:Ad-Hoc                     Frequency:2.462 GHz (Channel
11)                     Quality:23/100  Signal
level:-81 dBm  Noise level:-96 dBm                     Encryption key:off                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s                     Extra:bcn_int=10                     Extra:atim=0           Cell 06 - Address: <MAC 'Maxx Autos
Plus Netgear' [AC6]>                     ESSID:"Maxx Autos Plus
Netgear"                     Protocol:IEEE 802.11g                     Mode:Master                     Frequency:2.412 GHz (Channel
1)                     Quality:25/100  Signal
level:-80 dBm  Noise level:-96 dBm                     Encryption key:on                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 18 Mb/s                               24 Mb/s; 36 Mb/s;
54 Mb/s                     Extra:bcn_int=200                     Extra:atim=0                     IE: IEEE 802.11i/WPA2
Version 1                         Group Cipher : CCMP                         Pairwise Ciphers (1) :
CCMP                         Authentication Suites
(1) : PSK           Cell 07 - Address: <MAC 'MAXX AUTOS
PLUS GUEST' [AC7]>                     ESSID:"MAXX AUTOS PLUS
GUEST"                     Protocol:IEEE 802.11g                     Mode:Master                     Frequency:2.412 GHz (Channel
1)                     Quality:25/100  Signal
level:-80 dBm  Noise level:-96 dBm                     Encryption key:on                     Bit Rates:1 Mb/s; 2 Mb/s;
5.5 Mb/s; 11 Mb/s; 18 Mb/s                               24 Mb/s; 36 Mb/s;
54 Mb/s                     Extra:bcn_int=200                     Extra:atim=0                     IE: IEEE 802.11i/WPA2
Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) :
CCMP TKIP                         Authentication Suites
(1) : PSK                     IE: WPA Version 1                         Group Cipher : TKIP                         Pairwise Ciphers (2) :
CCMP TKIP                         Authentication Suites
(1) : PSK 

##### module infos ###################### 

[cfg80211] filename:      
/lib/modules/3.13.0-38-generic/kernel/net/wireless/cfg80211.ko description:    wireless configuration support license:        GPL author:         Johannes Berg srcversion:     C2478077E22138832B71659 depends:        
intree:         Y vermagic:       3.13.0-38-generic SMP mod_unload
modversions 
signer:         Magrathea: Glacier signing key sig_key:       
2A:DE:ED:EA:6C:BA:0B:95:A6:22:22:40:71:1F:49:C8:72:07:BB:F6 sig_hashalgo:   sha512 parm:           ieee80211_regdom:IEEE 802.11
regulatory domain code (charp) parm:          
cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band
(bool) 

[ndiswrapper] filename:      
/lib/modules/3.13.0-38-generic/updates/ndiswrapper.ko license:        GPL version:        1.59 description:    NDIS wrapper driver author:         ndiswrapper team
<ndiswrapper-general@lists.sourceforge.net> srcversion:     DC1EFD919FDF2DB80D424C6 depends:        
vermagic:       3.13.0-38-generic SMP mod_unload
modversions 
parm:           if_name:Network interface name
or template (default: wlan%d) (charp) parm:           proc_uid:The uid of the files
created in /proc (default: 0). (int) parm:           proc_gid:The gid of the files
created in /proc (default: 0). (int) parm:           debug:debug level (int) parm:           hangcheck_interval:The interval,
in seconds, for checking if driver is hung. (default: 0) (int) parm:           utils_version:Compatible version
of utils (read only: 1.9) (charp) 

##### module parameters ################# 

[cfg80211] cfg80211_disable_40mhz_24ghz: N ieee80211_regdom: 00 

grep: /sys/module/ndiswrapper/parameters/debug:
Permission denied grep:
/sys/module/ndiswrapper/parameters/hangcheck_interval: Permission
denied grep:
/sys/module/ndiswrapper/parameters/if_name: Permission denied grep:
/sys/module/ndiswrapper/parameters/proc_gid: Permission denied grep:
/sys/module/ndiswrapper/parameters/proc_uid: Permission denied grep:
/sys/module/ndiswrapper/parameters/utils_version: Permission denied [ndiswrapper] 

##### /etc/modules ###################### 

lp rtc 

##### modprobe options ################## 

[/etc/modprobe.d/blacklist-ath_pci.conf] blacklist ath_pci 

[/etc/modprobe.d/blacklist-bcm43.conf] blacklist b43 blacklist b43legacy blacklist ssb blacklist bcm43xx blacklist brcm80211 blacklist brcmfmac blacklist brcmsmac blacklist bcma 

[/etc/modprobe.d/blacklist.conf] blacklist evbug blacklist usbmouse blacklist usbkbd blacklist eepro100 blacklist de4x5 blacklist eth1394 blacklist snd_intel8x0m blacklist snd_aw2 blacklist i2c_i801 blacklist prism54 blacklist bcm43xx blacklist garmin_gps blacklist asus_acpi blacklist snd_pcsp blacklist pcspkr blacklist amd76x_edac 

[/etc/modprobe.d/blacklist-rare-network.conf] alias net-pf-3 off alias net-pf-6 off alias net-pf-9 off alias net-pf-11 off alias net-pf-12 off alias net-pf-19 off alias net-pf-21 off alias net-pf-36 off 

[/etc/modprobe.d/broadcom-sta-common.conf] blacklist b43 blacklist b43legacy blacklist b44 blacklist bcma blacklist brcm80211 blacklist brcmsmac blacklist ssb install wl /sbin/modprobe --ignore-install wl
$CMDLINE_OPTS 

[/etc/modprobe.d/iwlwifi.conf] remove iwlwifi \ (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e
^iwlwifi | xargs /sbin/rmmod) \ && /sbin/modprobe -r mac80211 

[/etc/modprobe.d/mlx4.conf] softdep mlx4_core post: mlx4_en 

[/etc/modprobe.d/ndiswrapper.conf] alias usb:v050Dp6050d*dc*dsc*dp*ic*isc*ip*
ndiswrapper alias usb:v050Dp615Ad*dc*dsc*dp*ic*isc*ip*
ndiswrapper alias usb:v050Dp825Cd*dc*dsc*dp*ic*isc*ip*
ndiswrapper alias usb:v0846p9011d*dc*dsc*dp*ic*isc*ip*
ndiswrapper alias usb:v0846p9020d*dc*dsc*dp*ic*isc*ip*
ndiswrapper 

[/etc/modprobe.d/oss-compat.conf] softdep snd-pcm post: snd-pcm-oss softdep snd-mixer post: snd-mixer-oss softdep snd-seq post: snd-seq-midi snd-seq-oss 

[/etc/modprobe.d/qemu-system-x86.conf] options kvm_intel nested=1 

##### rc.local ########################## 

exit 0 

##### pm-utils ########################## 

##### udev rules ######################## 

[/etc/udev/rules.d/70-persistent-net.rules] # PCI device 0x10ec:0x8168 (r8169) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="eth*", NAME="eth0" # USB device 0x:0x (ndiswrapper) SUBSYSTEM=="net", ACTION=="add",
DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>",
ATTR{dev_id}=="0x0", ATTR{type}=="1",
KERNEL=="wlan*", NAME="wlan0" 

##### dmesg ############################# 

[   18.398627] ndiswrapper: driver bcmn43xx64
(,08/26/2009, 5.10.79.30) loaded [   18.935189] wlan0: ethernet device <MAC
'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e,
NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf [   18.937169] wlan0: encryption modes
supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA,
WPA2, WPA2-PSK [  318.651531] IPv6: ADDRCONF(NETDEV_UP): wlan0:
link is not ready (repeated 2 times) [  326.190591] IPv6: ADDRCONF(NETDEV_CHANGE):
wlan0: link becomes ready [  649.977428] ndiswrapper
(iw_get_network_type:361): getting network type failed: C001000C [  650.001732] ndiswrapper: device wlan0 removed [  660.274993] ndiswrapper: driver bcmn43xx64
(,08/26/2009, 5.10.79.30) loaded [  660.822483] wlan0: ethernet device <MAC
'wlan0' [IF]> using NDIS driver: bcmn43xx64, version: 0x50a4f1e,
NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9011.F.conf [  660.824957] wlan0: encryption modes
supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA,
WPA2, WPA2-PSK [  660.846035] IPv6: ADDRCONF(NETDEV_UP): wlan0:
link is not ready (repeated 2 times) [  671.387087] IPv6: ADDRCONF(NETDEV_CHANGE):
wlan0: link becomes ready 

########## wireless info END ############ 

 
```

---

### Post by praseodym on 2015-03-18
Tried this driver:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

Additionally, change to b/g mode only in your router.

---

### Post by Linc_mc on 2015-03-18
> **praseodym said:**
> Tried this driver:

[http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/37/11/2955302-Broadcom_bcm43xx_USB_32_64bit_v3.tar.gz)

Additionally, change to b/g mode only in your router.




The driver you suggested is the same one as I am currently using. 

Changing to b/g mode appears to have done the trick as I have been connected for about 45 minutes no problem. YAY!!!

Now I just need to figure out how to enable ubuntu to work with WPA/WPA2 encryption so that I can get my network secured.

Thanks for the help

LJ

---

### Post by praseodym on 2015-03-20
I strongly recommend pure WPA2-AES (CCMP)

---

