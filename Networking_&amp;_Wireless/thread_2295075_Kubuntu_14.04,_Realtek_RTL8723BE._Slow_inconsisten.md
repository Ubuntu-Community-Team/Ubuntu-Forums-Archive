---
title: "Kubuntu 14.04, Realtek RTL8723BE. Slow inconsistent downloads and streaming."
date: 2015-09-15
forum: Networking &amp; Wireless
---

### Post by bill90 on 2015-09-15
Additional info: 
I installed the driver from [http://github.com/lwfinger/rtlwifi_new](http://github.com/lwfinger/rtlwifi_new)

Streaming and downloading begin fine. After a few minutes the download speed slows and becomes erratic. The network becomes unusable by everyone connected to the network. A speed test on dslreports.com gives me an F for bufferbloat. My service provider is xfinity with 150Mbps/10Mbps speed. I can achieve close to those speeds using windows 7.

I really appreciate any help with this matter.

```

########## wireless info START ##########

Report from: 15 Sep 2015 20:15 EDT -0400

Booted last: 15 Sep 2015 19:06 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-49-generic #65~14.04.1-Ubuntu SMP Wed Sep 9 10:03:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

KDE Plasma Workspace

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:380a]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Device [17aa:b736]
    Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 5986:055d Acer, Inc 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             139298  0 
btcoexist             183378  1 rtl8723be
rtl_pci                39740  1 rtl8723be
rtlwifi               101788  3 btcoexist,rtl_pci,rtl8723be
mac80211              652777  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              498458  2 mac80211,rtlwifi
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

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
          inet addr:192.168.1.129  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:128793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:144743663 (144.7 MB)  TX bytes:48129204 (48.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Bills_Brothel"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'Bills_Brothel' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-18 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search hsd1.ma.comcast.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       812     1  0 19:06 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Bills_Brothel] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    xfinitywifi:     Infra, <MAC 'xfinitywifi' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    HOME-B102:       Infra, <MAC 'HOME-B102' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    *Bills_Brothel:  Infra, <MAC 'Bills_Brothel' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.129
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Bills_Brothel-91226109-3573-469f-b321-230bb6272cb1]] (600 root)
[connection] id=Bills_Brothel | type=802-11-wireless
[802-11-wireless] ssid=Bills_Brothel | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-B102]] (600 root)
[connection] id=HOME-B102 | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=HOME-B102 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Linksys35829]] (600 root)
[connection] id=Linksys35829 | type=802-11-wireless | permissions=user:bill:;
[802-11-wireless] ssid=Linksys35829 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Bills_Brothel]] (600 root)
[connection] id=Bills_Brothel | type=802-11-wireless
[802-11-wireless] ssid=Bills_Brothel | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.452 GHz (Channel 9)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.452 GHz (Channel 9)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Bills_Brothel' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"Bills_Brothel"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000029ce53de57
                    Extra: Last beacon: 156ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HOME-B102' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"HOME-B102"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000192e71db859
                    Extra: Last beacon: 4044ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000192e7223c49
                    Extra: Last beacon: 3748ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000192e71dc70c
                    Extra: Last beacon: 3748ms ago

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/3.16.0-49-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         PageHe    <page_he@realsil.com.cn>
srcversion:     1A35907BCCEF84FE28F988D
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
parm:           swlps:bool
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
parm:           ips:using no link power save (default 1 is open)
 (bool)
parm:           fwlps:using linked fw control power save (default 1 is open)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.16.0-49-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1BFD9F9E9693CB93908149A
depends:        mac80211,rtlwifi
vermagic:       3.16.0-49-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.16.0-49-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BD8B6223C32D4A4F23648DA
depends:        mac80211,cfg80211
vermagic:       3.16.0-49-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.16.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5375B0354B6CF7C84FC1934
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-49-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        ED:CF:BF:81:5A:6E:CA:BE:5C:35:0D:4A:AF:8A:8B:80:AE:A6:16:B6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: N
ips: N
msi: N
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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N ips=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[    7.551452] wlan0: associate with <MAC 'Bills_Brothel' [AC1]> (try 1/3)
[    7.575714] wlan0: RX AssocResp from <MAC 'Bills_Brothel' [AC1]> (capab=0x411 status=0 aid=3)
[    7.575991] wlan0: associated
[    7.576016] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  139.910438] wlan0: deauthenticating from <MAC 'Bills_Brothel' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  143.996613] wlan0: authenticate with <MAC 'HOME-B102' [AC2]>
[  144.017985] wlan0: send auth to <MAC 'HOME-B102' [AC2]> (try 1/3)
[  144.020237] wlan0: authenticated
[  144.023455] wlan0: associate with <MAC 'HOME-B102' [AC2]> (try 1/3)
[  144.040142] wlan0: RX AssocResp from <MAC 'HOME-B102' [AC2]> (capab=0x411 status=0 aid=3)
[  144.040734] wlan0: associated
[  144.286926] wlan0: deauthenticating from <MAC 'HOME-B102' [AC2]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  144.298839] wlan0: authenticate with <MAC 'HOME-B102' [AC2]>
[  144.309734] wlan0: send auth to <MAC 'HOME-B102' [AC2]> (try 1/3)
[  144.311916] wlan0: authenticated
[  144.315710] wlan0: associate with <MAC 'HOME-B102' [AC2]> (try 1/3)
[  144.332463] wlan0: RX AssocResp from <MAC 'HOME-B102' [AC2]> (capab=0x411 status=0 aid=3)
[  144.333462] wlan0: associated
[  447.474731] wlan0: deauthenticating from <MAC 'HOME-B102' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  449.961210] wlan0: authenticate with <MAC 'Bills_Brothel' [AC1]>
[  449.972109] wlan0: send auth to <MAC 'Bills_Brothel' [AC1]> (try 1/3)
[  449.994974] wlan0: authenticated
[  449.996048] wlan0: associate with <MAC 'Bills_Brothel' [AC1]> (try 1/3)
[  450.020121] wlan0: RX AssocResp from <MAC 'Bills_Brothel' [AC1]> (capab=0x411 status=0 aid=3)
[  450.020717] wlan0: associated

########## wireless info END ############

 
```

---

### Post by chili555 on 2015-09-16
Please see Jeremy31's answer here: [http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/](http://askubuntu.com/questions/590414/wifi-problems-with-rtl8723be-in-ubuntu-14-04/)

---

