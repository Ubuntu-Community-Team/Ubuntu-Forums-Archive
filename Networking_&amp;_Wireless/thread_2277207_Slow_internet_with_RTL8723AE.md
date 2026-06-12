---
title: "Slow internet with RTL8723AE"
date: 2015-05-07
forum: Networking &amp; Wireless
---

### Post by themaninthehat on 2015-05-07
Hi,

I have been trying to configure my wifi card, and I found a few threads on this, but somehow the things I've tried haven't worked (these include compiling drivers from several repositories and trying them). I tried to find the definitive RTL8723AE thread, but couldn't find it. Any help would be very appreciated.

Symptoms are: I can connect to Wifi, but the internet is rather slow (~60 kb/s, instead of 5 mb/s I get on a Windows box).

Here is the output of the wireless script.

```

########## wireless info START ##########

Report from: 07 May 2015 08:31 CDT -0500

Booted last: 07 May 2015 08:28 CDT -0500

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-52-generic #86-Ubuntu SMP Mon May 4 04:32:59 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, persistent, splash, quiet

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
	Subsystem: AzureWave Device [1a3b:2114]
	Kernel driver in use: rtl8723ae

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 13d3:3394 IMC Networks 
Bus 002 Device 004: ID 1241:1603 Belkin Keyboard
Bus 002 Device 003: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 002 Device 002: ID 1f6f:1000 Aliph 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8723ae              81882  0 
rtl8723_common         23361  1 rtl8723ae
rtl_pci                26690  1 rtl8723ae
rtlwifi                63475  2 rtl_pci,rtl8723ae
mac80211              630669  3 rtl_pci,rtlwifi,rtl8723ae
cfg80211              484040  2 mac80211,rtlwifi

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
          inet addr:192.168.1.212  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::260a:64ff:fe9c:a237/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5278 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3051893 (3.0 MB)  TX bytes:887464 (887.4 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"INFINITUM79BA"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'INFINITUM79BA' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:33   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

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

- Device: wlan0  [INFINITUM79BA] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
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
    *INFINITUM79BA:  Infra, <MAC 'INFINITUM79BA' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.212
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

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

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/INFINITUM79BA]] (600 root)
[connection] id=INFINITUM79BA | type=802-11-wireless
[802-11-wireless] ssid=INFINITUM79BA | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Mexico_City (based on set time zone)

country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.452 GHz (Channel 9)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'INFINITUM79BA' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"INFINITUM79BA"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000066d572307
                    Extra: Last beacon: 76ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'IGA2' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"IGA2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000040aa1b9176
                    Extra: Last beacon: 4632ms ago

##### module infos ######################

[rtl8723ae]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723fw_B.bin
firmware:       rtlwifi/rtl8723fw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     618CBEE84D8321009FAA0B0
depends:        rtlwifi,rtl8723-common,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl8723_common]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     D1807280DBDC9B8A7EBDAB7
depends:        
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-52-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-52-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-52-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-52-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        19:81:BC:91:6F:FC:00:59:92:31:EC:56:30:E6:66:E0:25:6F:D6:F1
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723ae]
debug: 0
fwlps: Y
ips: Y
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

coretemp

coretemp

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (MOSCHIP usb-ethernet driver)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[    4.574710] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    5.589826] wlan0: authenticate with <MAC 'INFINITUM79BA' [AC1]>
[    5.606074] wlan0: send auth to <MAC 'INFINITUM79BA' [AC1]> (try 1/3)
[    5.607610] wlan0: authenticated
[    5.608863] wlan0: associate with <MAC 'INFINITUM79BA' [AC1]> (try 1/3)
[    5.619024] wlan0: RX AssocResp from <MAC 'INFINITUM79BA' [AC1]> (capab=0x31 status=0 aid=4)
[    5.619274] wlan0: associated
[    5.619315] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  152.091171] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=78.47.202.122 DST=192.168.1.212 LEN=70 TOS=0x00 PREC=0x00 TTL=49 ID=54418 DF PROTO=TCP SPT=443 DPT=41397 WINDOW=114 RES=0x00 ACK PSH URGP=0 
[  156.250829] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=74.125.227.31 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=58 ID=23724 PROTO=TCP SPT=443 DPT=35903 WINDOW=0 RES=0x00 RST URGP=0 
[  156.318398] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=173.194.77.84 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=50 ID=49432 PROTO=TCP SPT=443 DPT=45517 WINDOW=0 RES=0x00 RST URGP=0 
[  157.266035] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=173.194.77.84 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=50 ID=49453 PROTO=TCP SPT=443 DPT=45517 WINDOW=0 RES=0x00 RST URGP=0 
[  157.277110] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=173.194.77.84 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=50 ID=26287 PROTO=TCP SPT=443 DPT=45506 WINDOW=0 RES=0x00 RST URGP=0 
[  157.393902] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=74.125.227.3 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=58 ID=22617 PROTO=TCP SPT=443 DPT=41085 WINDOW=0 RES=0x00 RST URGP=0 
[  158.632122] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=74.125.227.36 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=58 ID=25609 PROTO=TCP SPT=443 DPT=48329 WINDOW=0 RES=0x00 RST URGP=0 
[  158.642518] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=74.125.227.1 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=58 ID=1387 PROTO=TCP SPT=443 DPT=60637 WINDOW=0 RES=0x00 RST URGP=0 
[  158.644323] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=74.125.227.36 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=58 ID=25610 PROTO=TCP SPT=443 DPT=48329 WINDOW=0 RES=0x00 RST URGP=0 
[  158.680474] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=74.125.227.31 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=58 ID=25073 PROTO=TCP SPT=443 DPT=35903 WINDOW=0 RES=0x00 RST URGP=0 
[  158.702149] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=74.125.227.0 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=58 ID=43812 PROTO=TCP SPT=443 DPT=47735 WINDOW=0 RES=0x00 RST URGP=0 
[  172.222761] wlan0: deauthenticated from <MAC 'INFINITUM79BA' [AC1]> (Reason: 2)
[  173.317773] wlan0: authenticate with <MAC 'INFINITUM79BA' [AC1]>
[  173.349840] wlan0: send auth to <MAC 'INFINITUM79BA' [AC1]> (try 1/3)
[  173.351278] wlan0: authenticated
[  173.353359] wlan0: associate with <MAC 'INFINITUM79BA' [AC1]> (try 1/3)
[  173.364073] wlan0: RX AssocResp from <MAC 'INFINITUM79BA' [AC1]> (capab=0x31 status=0 aid=4)
[  173.364343] wlan0: associated
[  182.626375] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC 'wlan0' [IF]>:<MAC 'INFINITUM79BA' [AC1]>:08:00 SRC=173.194.77.189 DST=192.168.1.212 LEN=40 TOS=0x10 PREC=0x60 TTL=50 ID=23145 PROTO=TCP SPT=443 DPT=49737 WINDOW=0 RES=0x00 RST URGP=0 
[  205.257598] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=192.168.1.212 DST=224.0.0.1 LEN=140 TOS=0x00 PREC=0x00 TTL=1 ID=47590 DF PROTO=UDP SPT=4448 DPT=4448 LEN=120 

########## wireless info END ############

```

Thanks a lot in advance!!

---

### Post by themaninthehat on 2015-05-08
I forgot to say that the machine in question is a Gigabyte Brix GB-BXi5-4200 (rev. 1.0).

---

