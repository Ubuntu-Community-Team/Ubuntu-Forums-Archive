---
title: "RTL8191SU super slow internet, Ubuntu 14.04"
date: 2014-08-06
forum: Networking &amp; Wireless
---

### Post by potts.matthewj on 2014-08-06
I changed over to Ubuntu from Windows 7 a few months ago and LOVE it.  However a week or so ago, there was an update and since then my wireless has been super slow, averaging about .4mbps :'( I have been digging through forum after forum trying anything and everything to fix the issue and I am at a loss. I don't normally post on forums of any type but I don't know what else to do.  Chances are I probably screwed something up in my system from all the attempts of trying to fix this thing... but everything else seems to still be running fine. Maybe I have multiple drivers installed and they are causing the issue? I honestly have no clue and I don't know a ton about this OS yet... I'm not even convinced that I am even using the RTL8191SU adapter!  any help is greatly appreciated! Thanks in advance!!

Here is what I got from running the wireless script i see everyone posting about:
```



########## wireless info START ##########


Report from: 06 Aug 2014 01:08 EDT -0400


Script from: 04 Aug 2014 18:47 UTC +0000


##### release #####


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel #####


Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop #####


Ubuntu


##### lspci #####


0a:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8168


##### lsusb #####


Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 013 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 012 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 002: ID 04f9:0045 Brother Industries, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 001 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 002: ID 0c45:6300 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c041 Logitech, Inc. G5 Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


##### lsmod #####


eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
video                  19476  1 asus_wmi
mxm_wmi                13021  0 
r8712u                184158  0 
wmi                    19177  2 mxm_wmi,asus_wmi


##### interfaces #####


auto lo
iface lo inet loopback


##### ifconfig #####


eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:98 Base address:0xc000 


wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:ae31:cc4f:0:21a:efff:fe1f:cd75/64 Scope:Global
          inet6 addr: fe80::21a:efff:fe1f:cd75/64 Scope:Link
          inet6 addr: 2002:ae31:cc4f:0:986f:5dd6:44ad:d0ee/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4546 errors:0 dropped:12269 overruns:0 frame:0
          TX packets:5140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2503828 (2.5 MB)  TX bytes:956503 (956.5 KB)


##### iwconfig #####


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"NotYours"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=48/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1
search hsd1.pa.comcast.net


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [NotYours] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan0>


  Capabilities:
    Speed:           150 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    HOME-007D:       Infra, <MAC addr HOME-007D>, Freq 2462 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2
    She_Sneaks_Out_The_Window: Infra, <MAC addr She_Sneaks_Out_The_Window>, Freq 2422 MHz, Rate 54 Mb/s, Strength 46 WPA WPA2
    The Markel Network: Infra, <MAC addr beajohn>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA2
    beajohn:         Infra, <MAC addr WeGoHard>, Freq 2417 MHz, Rate 54 Mb/s, Strength 7 WPA2
    WeGoHard:        Infra, <MAC addr NotYours-guest>, Freq 2422 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    NotYours-guest:  Infra, <MAC addr NotYours>, Freq 2412 MHz, Rate 54 Mb/s, Strength 58
    *NotYours:       Infra, <MAC address>, Freq 2412 MHz, Rate 54 Mb/s, Strength 93 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.115
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             75.75.76.76
    DNS:             75.75.75.75
    DNS:             192.168.1.1


  IPv6 Settings:
    Address:         2002:ae31:cc4f:0:986f:5dd6:44ad:d0ee
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe00:dca


    Address:         2002:ae31:cc4f:0:21a:efff:fe1f:cd75
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe00:dca


    Address:         fe80::21a:efff:fe1f:cd75
    Prefix:          64
    Gateway:         fe80::c2c1:c0ff:fe00:dca


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #####


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC address>
                    ESSID:"NotYours"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC addr NotYours>
                    ESSID:"NotYours-guest"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Signal level=57/100  
          Cell 03 - Address: <MAC addr She_Sneaks_Out_The_Window>
                    ESSID:"She_Sneaks_Out_The_Window"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd180050f20101000050f20401000050f20401000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 04 - Address: <MAC addr HOME-007D>
                    ESSID:"HOME-007D"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=73/100  


##### module infos #####


[r8712u]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     5A7B13CC2FA1D2F4B5820F9
alias:          usb:v0409p02B6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7622d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp845Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8174d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3325d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3341d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3339d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF5d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04F2pAFF2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0064d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0049d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0058d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p4901d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED18d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0015d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7612d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3303d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3309d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3336d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3335d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3334d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3333d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3342d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3311d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0EB0p9061d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8192d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CABd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v25D4p4CA1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p646Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0752d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp5077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0154d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0063d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0059d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0045d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0057d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0167d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE034d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0016d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9603d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7611d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3306d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp11F1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1791d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1786d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDApC512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8713d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8173d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*in*
depends:        
staging:        Y
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


##### module parameters #####


[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0


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


[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


[/etc/modprobe.d/r8168-dkms.conf]
blacklist r8169


##### udev rules #####


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[    3.259892] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[    3.261161] r8712u: Staging version
[    3.261176] r8712u: register rtl8712_netdev_ops to netdev_ops
[    3.261180] usb 2-2: r8712u: USB_SPEED_HIGH with 4 endpoints
[    3.262027] usb 2-2: r8712u: Boot from EFUSE: Autoload OK
[    3.307162] type=1400 audit(1407301581.086:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=560 comm="apparmor_parser"
[    3.307511] type=1400 audit(1407301581.086:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=560 comm="apparmor_parser"
[    3.815708] usb 2-2: r8712u: CustomerID = 0x0000
[    3.815713] usb 2-2: r8712u: MAC Address from efuse = <MAC addr wlan0>
[    3.815715] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[    4.543962] r8712u 2-2:1.0 wlan0: 1 RCR=0x153f00e
[    4.544768] r8712u 2-2:1.0 wlan0: 2 RCR=0x553f00e
[    4.651744] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.959459] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.377171] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   15.385994] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address>, seq = 0, tid = 0
[   22.900192] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC address>, seq = 0, tid = 5


########## wireless info END ############

```

---

### Post by potts.matthewj on 2014-08-10
Does anyone have any suggestions?

---

### Post by potts.matthewj on 2014-08-28
Update: After being frustrated beyond belief, I tried a different USB port... and it worked!! but only for a week. It is now back to the same slow wifi speeds again... I am at a loss

---

