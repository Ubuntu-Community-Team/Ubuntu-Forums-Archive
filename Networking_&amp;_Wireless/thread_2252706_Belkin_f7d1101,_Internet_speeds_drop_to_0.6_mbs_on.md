---
title: "Belkin f7d1101, Internet speeds drop to 0.6 mb/s on Ubuntu 14.04.1"
date: 2014-11-13
forum: Networking &amp; Wireless
---

### Post by khuan013 on 2014-11-13
I've been having issues with intermittent connection speeds. My belkin f7d1101 usb device works fine for windows, averaging around 17 mbps. On startup and for a while after I run "sudo service network-manager restart" it works fine on ubuntu as well. But after about 20-30m it drops right back down to .65 mbps.

Does anyone happen know why this happens, or what I can do to fix it? Below is the output from the wireless script.

I'm currently trying to install the r92su driver to see if that helps, but I'm having trouble installing it from [here]("https://github.com/chunkeey/rtl8192su"). The readme says to run make, then make load, but what steps do I need to do after that?
There is no make install in the makefile.

```


########## wireless info START ##########


Report from: 13 Nov 2014 15:54 PST -0800


Booted last: 13 Nov 2014 14:46 PST -0800


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.6-031606-generic #201410150635 SMP Wed Oct 15 10:36:14 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7850]
    Kernel driver in use: r8168


##### lsusb #############################


Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 1b1c:1b07 Corsair 
Bus 003 Device 002: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 003 Device 005: ID 046d:c21d Logitech, Inc. F310 Gamepad [XInput Mode]
Bus 003 Device 004: ID 046d:c245 Logitech, Inc. G400 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


cfg80211              521225  0 
mxm_wmi                13021  0 
wmi                    19379  1 mxm_wmi
r8712u                189931  0 


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
          Interrupt:43 Base address:0xa000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135756 errors:0 dropped:32537 overruns:0 frame:0
          TX packets:85747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169571934 (169.5 MB)  TX bytes:20593818 (20.5 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"MagikarpWifi"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'MagikarpWifi' [AC1]>   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=94/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: wlan0  [MagikarpWifi] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8712u
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    MyCharterWiFi19-2G: Infra, <MAC 'MyCharterWiFi19-2G' [AC3]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 100 WPA2
    MyCharterWiFi62-2G: Infra, <MAC 'MyCharterWiFi62-2G' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Martinez:        Infra, <MAC 'Martinez' [AC7]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 62 WPA2
    2WIRE259:        Infra, <MAC '2WIRE259' [AC4]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
    NETGEAR53:       Infra, <MAC 'NETGEAR53' [AC6]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 56 WPA2
    Free Wifi:       Infra, <MAC 'Free Wifi' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    *MagikarpWifi:   Infra, <MAC 'MagikarpWifi' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 91 WPA2
    HighlyMotivated: Infra, <MAC 'HighlyMotivated' [AN8]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2
    MyCharterWiFif3-2G: Infra, <MAC 'MyCharterWiFif3-2G' [AC5]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA2


  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


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


[[/etc/NetworkManager/system-connections/MagikarpWifi]] (600 root)
[connection] id=MagikarpWifi | type=802-11-wireless
[802-11-wireless] ssid=MagikarpWifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.427 GHz (Channel 4)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'MagikarpWifi' [AC1]>
                    ESSID:"MagikarpWifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC 'MyCharterWiFi62-2G' [AC2]>
                    ESSID:"MyCharterWiFi62-2G"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=88/100  
          Cell 03 - Address: <MAC 'MyCharterWiFi19-2G' [AC3]>
                    ESSID:"MyCharterWiFi19-2G"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.427 GHz (Channel 4)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 04 - Address: <MAC '2WIRE259' [AC4]>
                    ESSID:"2WIRE259"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=58/100  
          Cell 05 - Address: <MAC 'MyCharterWiFif3-2G' [AC5]>
                    ESSID:"MyCharterWiFif3-2G"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2lo        Interface doesn't support scanning.


 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=56/100  
          Cell 06 - Address: <MAC 'NETGEAR53' [AC6]>
                    ESSID:"NETGEAR53"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=47/100  
          Cell 07 - Address: <MAC 'Martinez' [AC7]>
                    ESSID:"Martinez"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=76/100  
          Cell 08 - Address: <MAC 'Free Wifi' [AC8]>
                    ESSID:"Free Wifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2040050f20201000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=56/100  


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.16.6-031606-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.6-031606-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6D:6A:45:E2:F8:86:20:14:BC:04:D3:E1:FA:7C:66:BD:0B:A2:BC:AB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[r8712u]
filename:       /lib/modules/3.16.6-031606-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
srcversion:     9A0BDB5A266844AB0999460
depends:        
staging:        Y
intree:         Y
vermagic:       3.16.6-031606-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6D:6A:45:E2:F8:86:20:14:BC:04:D3:E1:FA:7C:66:BD:0B:A2:BC:AB
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


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


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


##### /etc/modules ######################


lp
rtc
r8712u


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


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/network_drivers.conf]
install r8192s_usb /sbin/modprobe --ignore-install r8192s_usb $CMDLINE_OPTS; /bin/echo "050d 945a" > /sys/bus/usb/drivers/rtl819xU/new_id


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl819xU)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


[/etc/udev/rules.d/network_drivers.rules]
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="945a", RUN+="/sbin/modprobe -qba r8192s_usb"


##### dmesg #############################


[    4.864597] usb 3-4: r8712u: CustomerID = 0x0000
[    4.864599] usb 3-4: r8712u: MAC Address from efuse = <MAC 'wlan0' [IF]>
[    4.864601] usb 3-4: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   11.376993] r8712u 3-4:1.0 wlan0: 1 RCR=0x153f00e
[   11.377512] r8712u 3-4:1.0 wlan0: 2 RCR=0x553f00e
[   11.480771] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   22.457656] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready (repeated 2 times)
[ 3046.361481] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3066.796079] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by khuan013 on 2014-11-15
I tried using wcid instead of the network manager, but still have the same problem.

---

