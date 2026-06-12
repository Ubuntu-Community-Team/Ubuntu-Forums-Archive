---
title: "Wifi stopped connecting to net but still downloads torrents"
date: 2015-08-06
forum: Networking &amp; Wireless
---

### Post by roquet2 on 2015-08-06
I'm on xubuntu 14.04 on a an Asus x200ma. Wifi suddenly stopped connecting to the web but still downloads torrents. I can't ping google in Terminal. Wireless was never perfect - sometimes dropping packets - but worked ok most of the time. Now I can't get any web pages at all.

What could be causing this? Below I've put the results of "wireless info START" run with the LAN cable in.

Thanks for you help.

```

########## wireless info START ##########

Report from: 06 Aug 2015 19:40 JST +0900

Booted last: 06 Aug 2015 19:18 JST +0900

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: AzureWave Device [1a3b:1d38]
    Kernel driver in use: rtl8188ee

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 04f2:b424 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
rtl8188ee              85387  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                64255  2 rtl_pci,rtl8188ee
mac80211              652777  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              498458  2 mac80211,rtlwifi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
wmi                    19193  1 asus_wmi
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
video                  20128  2 i915,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 240f:6a:2ae6:1:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 240f:6a:2ae6:1:606a:f1b9:4cc8:b702/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4286 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5611 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1624183 (1.6 MB)  TX bytes:1471626 (1.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 240f:6a:2ae6:1:6dea:6629:1c86:1740/64 Scope:Global
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          inet6 addr: 240f:6a:2ae6:1:<IP6 'wlan0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:787806 (787.8 KB)  TX bytes:245394 (245.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"aterm-fde8fe-g"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: <MAC 'aterm-fde8fe-g' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:771   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       761     1  0 19:18 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

  IPv6 Settings:
    Address:         240f:6a:2ae6:1:606a:f1b9:4cc8:b702
    Prefix:          64
    Gateway:         ::

    Address:         240f:6a:2ae6:1:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         ::

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         ::

    DNS:             2001:268:fd07:4::1
    DNS:             2001:268:fd08:4::1

- Device: wlan0  [aterm-fde8fe-g] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           150 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    aterm-fde8fe-gw: Infra, <MAC 'aterm-fde8fe-gw' [AC2]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 77 WEP
    *aterm-fde8fe-g: Infra, <MAC 'aterm-fde8fe-g' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    0024A5C799FC-3:  Infra, <MAC '0024A5C799FC-3' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WEP

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/aterm-fde8fe-g]] (600 root)
[connection] id=aterm-fde8fe-g | type=802-11-wireless
[802-11-wireless] ssid=aterm-fde8fe-g | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Asia/Tokyo (based on set time zone)

country JP:
    (2402 - 2482 @ 40), (N/A, 20)
    (2474 - 2494 @ 20), (N/A, 20), NO-OFDM
    (4910 - 4990 @ 40), (N/A, 23)
    (5030 - 5090 @ 40), (N/A, 23)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 23), DFS

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
          Current Frequency:2.457 GHz (Channel 10)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.457 GHz (Channel 10)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'aterm-fde8fe-g' [AC1]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"aterm-fde8fe-g"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000c614bc20a13
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'aterm-fde8fe-gw' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"aterm-fde8fe-gw"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000c614bc15980
                    Extra: Last beacon: 196ms ago

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     83E9F79B1C7C341263B448E
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D48679749A6B8B822E391CA
depends:        
intree:         Y
vermagic:       3.16.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C1:A3:1E:DB:9F:C4:C6:4E:2D:95:A7:FF:18:A6:73:D1:8C:AB:15:A6
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8188ee]
debug: 0
fwlps: Y
ips: Y
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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.598868] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.599222] rtlwifi: wireless switch is on
[   16.176903] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.023789] wlan0: authenticate with <MAC 'aterm-fde8fe-g' [AC1]>
[   18.043347] wlan0: send auth to <MAC 'aterm-fde8fe-g' [AC1]> (try 1/3)
[   18.045366] wlan0: authenticated
[   18.047430] wlan0: associate with <MAC 'aterm-fde8fe-g' [AC1]> (try 1/3)
[   18.051161] wlan0: RX AssocResp from <MAC 'aterm-fde8fe-g' [AC1]> (capab=0x431 status=0 aid=1)
[   18.051278] wlan0: associated
[   18.051316] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   18.179977] wlan0: deauthenticating from <MAC 'aterm-fde8fe-g' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   18.190340] wlan0: authenticate with <MAC 'aterm-fde8fe-g' [AC1]>
[   18.200467] wlan0: send auth to <MAC 'aterm-fde8fe-g' [AC1]> (try 1/3)
[   18.202431] wlan0: authenticated
[   18.203504] wlan0: associate with <MAC 'aterm-fde8fe-g' [AC1]> (try 1/3)
[   18.207207] wlan0: RX AssocResp from <MAC 'aterm-fde8fe-g' [AC1]> (capab=0x431 status=0 aid=1)
[   18.207321] wlan0: associated

########## wireless info END ############
```

---

### Post by roquet2 on 2015-08-08
I fixed the issue of not being able to get internet pages by reinstalling resolveconf in Terminal:
```
sudo apt-get remove --purge resolvconf && sudo apt-get install --reinstall resolvconf 
sudo dpkg-reconfigure resolvconf
```and rebooting.

From this post: [http://ubuntuforums.org/showthread.php?t=2282079](http://ubuntuforums.org/showthread.php?t=2282079)

---

