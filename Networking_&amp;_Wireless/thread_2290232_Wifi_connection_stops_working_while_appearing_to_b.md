---
title: "Wifi connection stops working while appearing to be still connected"
date: 2015-08-10
forum: Networking &amp; Wireless
---

### Post by kmumu on 2015-08-10
The issue of my wifi connection dropping out while appearing to still be connected isn't a new issue to me, when I had Ubuntu 14.04 LTS installed the issue appeared and I solved it but I can no longer find the solution I used before. I installed Ubuntu 14.04 Gnome onto my Pc and the wifi issue had popped up again. Below is the the result of the wireless check code found in the sticky on "Before posting in Networking & Wireless."

I really need help with this.

```

########## wireless info START ##########

Report from: 10 Aug 2015 19:48 SAST +0200

Booted last: 10 Aug 2015 17:57 SAST +0200

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:16:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM-3 Gigabit Network Connection [8086:10de] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:3034]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 002: ID 0bda:8178 Realtek Semiconductor Corp. RTL8192CU 802.11n WLAN Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04d9:a06b Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192cu              69632  0 
rtl_usb                20480  1 rtl8192cu
rtl8192c_common        53248  1 rtl8192cu
rtlwifi                73728  3 rtl_usb,rtl8192c_common,rtl8192cu
mac80211              708608  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              524288  2 mac80211,rtlwifi
hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
wmi                    20480  1 hp_wmi

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
          Interrupt:19 Memory:f0500000-f0520000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:153720 errors:0 dropped:0 overruns:0 frame:0
          TX packets:106561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:193674332 (193.6 MB)  TX bytes:11995288 (11.9 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Twifi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Twifi' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.2        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       703     1  0 17:57 ?        00:00:02 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Twifi] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192cu
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
    *Twifi:          Infra, <MAC 'Twifi' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2

  IPv4 Settings:
    Address:         10.0.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.2

    DNS:             10.0.0.2

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
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

[[/etc/NetworkManager/system-connections/Twifi]] (600 root)
[connection] id=Twifi | type=802-11-wireless
[802-11-wireless] ssid=Twifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Johannesburg (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Twifi' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"Twifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004f59a828f
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192cu]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     3E8327A34276F37FFE5A6A8
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_usb]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
description:    USB basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     814A6FB8DBFFB696F45B316
depends:        rtlwifi,mac80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512

[rtl8192c_common]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     134BAE300AAF914967D6C6C
depends:        rtlwifi
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     35016235A31CEB1854418E1
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B23264F074A7D27F8B691A2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        6A:AA:11:D1:8C:2D:3A:40:B1:B4:DB:E5:BF:8A:D6:56:DD:F5:18:38
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192cu]
debug: 0
swenc: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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
options iwlwifi 11n_disable=1 wd_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x10de (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 6069.444501] rtl8192cu: MAC auto ON okay!
[ 6069.480397] rtl8192cu: Tx queue select: 0x05
[ 6069.878588] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6071.316638] wlan0: authenticate with <MAC 'Twifi' [AC1]>
[ 6071.328624] wlan0: send auth to <MAC 'Twifi' [AC1]> (try 1/3)
[ 6071.330658] wlan0: authenticated
[ 6071.332049] wlan0: associate with <MAC 'Twifi' [AC1]> (try 1/3)
[ 6071.363433] wlan0: RX AssocResp from <MAC 'Twifi' [AC1]> (capab=0x411 status=0 aid=1)
[ 6071.364417] wlan0: associated
[ 6071.364468] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6071.397931] wlan0: deauthenticating from <MAC 'Twifi' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 6071.410653] wlan0: authenticate with <MAC 'Twifi' [AC1]>
[ 6071.422253] wlan0: send auth to <MAC 'Twifi' [AC1]> (try 1/3)
[ 6071.424286] wlan0: authenticated
[ 6071.428045] wlan0: associate with <MAC 'Twifi' [AC1]> (try 1/3)
[ 6071.433903] wlan0: RX AssocResp from <MAC 'Twifi' [AC1]> (capab=0x411 status=0 aid=1)
[ 6071.434654] wlan0: associated
[ 6387.763791] wlan0: deauthenticating from <MAC 'Twifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6391.348531] rtl8192cu: MAC auto ON okay!
[ 6391.384299] rtl8192cu: Tx queue select: 0x05
[ 6391.779786] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6393.212605] wlan0: authenticate with <MAC 'Twifi' [AC1]>
[ 6393.224890] wlan0: send auth to <MAC 'Twifi' [AC1]> (try 1/3)
[ 6393.230310] wlan0: authenticated
[ 6393.232035] wlan0: associate with <MAC 'Twifi' [AC1]> (try 1/3)
[ 6393.243827] wlan0: RX AssocResp from <MAC 'Twifi' [AC1]> (capab=0x411 status=0 aid=1)
[ 6393.244705] wlan0: associated
[ 6393.244756] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6393.270241] wlan0: deauthenticating from <MAC 'Twifi' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 6393.282520] wlan0: authenticate with <MAC 'Twifi' [AC1]>
[ 6393.293800] wlan0: send auth to <MAC 'Twifi' [AC1]> (try 1/3)
[ 6393.306204] wlan0: authenticated
[ 6393.308051] wlan0: associate with <MAC 'Twifi' [AC1]> (try 1/3)
[ 6393.322078] wlan0: RX AssocResp from <MAC 'Twifi' [AC1]> (capab=0x411 status=0 aid=1)
[ 6393.322820] wlan0: associated
[ 6666.389622] wlan0: deauthenticating from <MAC 'Twifi' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 6668.674744] rtl8192cu: MAC auto ON okay!
[ 6668.708376] rtl8192cu: Tx queue select: 0x05
[ 6669.099416] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6670.564647] wlan0: authenticate with <MAC 'Twifi' [AC1]>
[ 6670.577236] wlan0: send auth to <MAC 'Twifi' [AC1]> (try 1/3)
[ 6670.580527] wlan0: authenticated
[ 6670.584040] wlan0: associate with <MAC 'Twifi' [AC1]> (try 1/3)
[ 6670.608785] wlan0: RX AssocResp from <MAC 'Twifi' [AC1]> (capab=0x411 status=0 aid=1)
[ 6670.609531] wlan0: associated
[ 6670.609584] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6670.630153] wlan0: deauthenticating from <MAC 'Twifi' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 6670.642682] wlan0: authenticate with <MAC 'Twifi' [AC1]>
[ 6670.653854] wlan0: send auth to <MAC 'Twifi' [AC1]> (try 1/3)
[ 6670.664157] wlan0: authenticated
[ 6670.668032] wlan0: associate with <MAC 'Twifi' [AC1]> (try 1/3)
[ 6670.672768] wlan0: RX AssocResp from <MAC 'Twifi' [AC1]> (capab=0x411 status=0 aid=1)
[ 6670.673644] wlan0: associated

########## wireless info END ############


```

---

### Post by Hadaka on 2015-08-10
Hi please open a terminal and do..
```
sudo apt-get update
sudo iw reg set ZA
sudo sed -i 's/^REG.*=$/&ZA/' /etc/default/crda
```
and here is a link for your driver...
[https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)
good luck to you.

---

### Post by kmumu on 2015-08-10
You're scholar and a gentleman Hadaka, thank you very much for your amazing help. Will mark as [SOLVED] seeing as the wifi device is acting like it did with the previous solution.

---

### Post by Hadaka on 2015-08-10
Excellent ! glad that worked for you.

---

