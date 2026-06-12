---
title: "Asus X200M (RTL8188EE) wireless connection drops after minutes of use"
date: 2015-08-08
forum: Networking &amp; Wireless
---

### Post by Jim_D on 2015-08-08
Hi, 

I have a new Asus X200M (called k200ma in the store) with a Realtek RTL8188EE wireless adapter and a fresh install of Ubuntu 14.04.2 from the live USB, with all updates installed as of Aug 7 2015.  It dual boots Windows 8.1 and Ubuntu 14.04.2, and I haven't had any trouble with the wireless on Windows 8.1 but Ubuntu will drop the connection after just minutes of use.  Ubuntu starts just fine and connects automatically to our house's network with the password I previously entered  (Linksys WRT54GL with WPA2).  But I get just a few minutes of being connected (14 minutes when I tested it this morning) before it loses the connection.  Its attempts to re-connect automatically all fail, and my attempts to reconnect by choosing my network from the wireless icon's menu all fail.  Only on restarting the laptop will it connect again.

I'm thinking of checking things on the router side (making sure firmware is upgraded, trying a new router), but many other wireless devices in our house connect to the router just fine (Asus eeepc 1005HA with Panda WirelessN USB adapter, two kindle fires, two ipod touches, etc.)

If there's anything software-related I can do on the laptop side, though (changing configuration, getting a different or newer driver) that would be great.  I'm trying to get this laptop set up to give to my wife for her birthday next week, so I'm hoping there's a solution if I just spend enough time on it.

I ran the wireless-info script twice, once at boot after connection was successful, and once after the connection was lost and the laptop made unsuccessful attempts to automatically reconnect.  When it's trying to reconnect, the place where dmesg/syslog looks different is at the point where it's saying "wlan0: associate with ... try 1/3" and instead of a "wlan0: RX AssocResp" it goes through 2 more tries until it says "wlan0: association with ... timed out".

If anyone has any ideas of things to try or check, please let me know, I'd really appreciate it!  I'm trying to avoid having to give the laptop to my wife and tell her to forget about Ubuntu and use Windows instead.

Thanks,
Jim

wireless-info at boot with successful connection:

```

########## wireless info START ##########

Report from: 08 Aug 2015 07:14 EDT -0400

Booted last: 08 Aug 2015 07:04 EDT -0400

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

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: AzureWave Device [1a3b:1d38]
    Kernel driver in use: rtl8188ee

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 04f2:b409 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0457:1028 Silicon Integrated Systems Corp. 
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

rtl8188ee              85387  0 
rtl_pci                26690  1 rtl8188ee
rtlwifi                64255  2 rtl_pci,rtl8188ee
mac80211              652777  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              498458  2 mac80211,rtlwifi
asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
wmi                    19193  1 asus_wmi
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
video                  20128  2 i915,asus_wmi

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
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4387 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4528739 (4.5 MB)  TX bytes:487706 (487.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"happyhut"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'happyhut' [AC1]>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1211   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       711     1  0 07:04 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

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

- Device: wlan0  [happyhut] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *happyhut:       Infra, <MAC 'happyhut' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    HOME-E5A2:       Infra, <MAC 'HOME-E5A2' [AN2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             71.243.0.12
    DNS:             68.237.161.12

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

[[/etc/NetworkManager/system-connections/happyhut]] (600 root)
[connection] id=happyhut | type=802-11-wireless
[802-11-wireless] ssid=happyhut | mac-address=<MAC 'wlan0' [IF]>
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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'happyhut' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"happyhut"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000087bd2edc1
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

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

[   12.055781] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   12.328117] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.328463] rtlwifi: wireless switch is on
[   17.273660] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.248911] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   19.268695] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[   19.270585] wlan0: authenticated
[   19.270771] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   19.270776] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   19.272534] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[   19.276479] wlan0: RX AssocResp from <MAC 'happyhut' [AC1]> (capab=0x411 status=0 aid=4)
[   19.276607] wlan0: associated
[   19.276622] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   19.306923] wlan0: deauthenticating from <MAC 'happyhut' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   19.317178] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   19.327281] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[   19.329176] wlan0: authenticated
[   19.329409] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   19.329414] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   19.332417] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[   19.334524] wlan0: RX AssocResp from <MAC 'happyhut' [AC1]> (capab=0x411 status=0 aid=4)
[   19.334637] wlan0: associated

########## wireless info END ############

```

wireless-info after dropped connection:

```

########## wireless info START ##########

Report from: 08 Aug 2015 07:20 EDT -0400

Booted last: 08 Aug 2015 07:04 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

(no change)

##### kernel ############################

(no change)

##### desktop ###########################

(no change)

##### lspci #############################

(no change)

##### lsusb #############################

(no change)

##### PCMCIA card info ##################

##### rfkill ############################

(no change)

##### lsmod #############################

(no change)

##### interfaces ########################

(no change)

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4547443 (4.5 MB)  TX bytes:495795 (495.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

(no change)

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

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

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    happyhut:        Infra, <MAC 'happyhut' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2

##### NetworkManager.state ##############

(no change)

##### NetworkManager.conf ###############

(no change)

##### NetworkManager profiles ###########

(no change)

##### iw reg get ########################

(no change)

##### iwlist channels ###################

(no change)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'happyhut' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"happyhut"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008917bcca7
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

(no change)

##### module parameters #################

(no change)

##### /etc/modules ######################

(no change)

##### modprobe options ##################

(no change)

##### rc.local ##########################

(no change)

##### pm-utils ##########################

##### udev rules ########################

(no change)

##### dmesg #############################

[  844.879639] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[  844.983718] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 3/3)
[  845.087796] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[  846.438592] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  846.457444] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  846.459099] wlan0: authenticated
[  846.459666] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  846.459687] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  846.461318] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  846.564962] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  846.669082] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  846.773191] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  848.624480] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  848.643598] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  848.646670] wlan0: authenticated
[  848.647237] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  848.647253] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  848.650796] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  848.754554] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  848.858697] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  848.962930] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  861.850976] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  861.861242] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  861.965445] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[  861.971418] wlan0: authenticated
[  861.971684] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  861.971691] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  861.973429] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  862.077429] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  862.181870] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  862.285714] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  873.152621] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  873.171356] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  873.274716] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[  873.379007] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 3/3)
[  873.381472] wlan0: authenticated
[  873.382255] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  873.382276] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  873.383361] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  873.486863] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  873.590857] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  873.694899] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  886.895424] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  886.905797] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  887.010037] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[  887.014063] wlan0: authenticated
[  887.014301] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  887.014307] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  887.017951] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  887.122165] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  887.226230] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  887.330368] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  898.192931] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  898.211730] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  898.315087] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[  898.419225] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 3/3)
[  898.424940] wlan0: authenticated
[  898.425749] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  898.425771] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  898.427147] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  898.531253] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  898.635397] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  898.739385] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  911.887772] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  911.898094] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  912.006381] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[  912.011968] wlan0: authenticated
[  912.012719] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  912.012740] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  912.014293] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  912.118515] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  912.222562] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  912.326614] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  923.193305] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  923.212084] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  923.217297] wlan0: authenticated
[  923.218013] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  923.218035] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  923.219365] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  923.323587] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  923.427695] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  923.531761] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  936.927001] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  936.938386] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  936.942960] wlan0: authenticated
[  936.943472] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  936.943487] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  936.946281] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  937.050720] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  937.154823] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  937.258921] wlan0: association with <MAC 'happyhut' [AC1]> timed out
[  948.132672] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  948.147810] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[  948.153117] wlan0: authenticated
[  948.153685] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  948.153700] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  948.155847] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[  948.259850] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[  948.363929] wlan0: associate with <MAC 'happyhut' [AC1]> (try 3/3)
[  948.468015] wlan0: association with <MAC 'happyhut' [AC1]> timed out

########## wireless info END ############

```

---

### Post by Jim_D on 2015-08-09
My Asus wireless behavior is slightly different after one change I've made today.  I upgraded my router's (WRT54GL) firmware to the latest released this year, and now:
- The wireless connection stays up longer.  In one case, I had it for 3 hours before it dropped.  Later it was 1 hour before it dropped.
- I can use the wireless icon to select my network and successfully connect again.  Before the firmware upgrade, I was unable to connect at all after a failure until I rebooted the laptop.
- Different messages are logged to dmesg when it fails to connect.  Rather than seeing the "association with ... timeout" message, I see a "CLASS3_FRAME_FROM_NONASSOC_STA" message as the first indication something is happening to the wireless.

I'd still definitely like to eliminate the connection drops if possible.  If anyone can help me understand why the connection is being dropped, and whether there's anything else I can do, I'd appreciate it.

dmesg after the connection is dropped, with the upgraded router firmware in place:

```

[   23.874357] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[   23.877984] wlan0: authenticated
[   23.878187] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   23.878191] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   23.880315] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[   23.882592] wlan0: RX AssocResp from <MAC 'happyhut' [AC1]> (capab=0x411 status=0 aid=1)
[   23.882708] wlan0: associated
[   55.111191] wlan0: Connection to AP <MAC 'happyhut' [AC1]> lost
[   56.269263] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   56.288863] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[   56.290486] wlan0: authenticated
[   56.290693] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   56.290698] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   56.292589] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[   56.294742] wlan0: RX AssocResp from <MAC 'happyhut' [AC1]> (capab=0x411 status=0 aid=1)
[   56.294866] wlan0: associated
[ 3346.472056] wlan0: deauthenticated from <MAC 'happyhut' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 3346.493811] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[ 3346.505318] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[ 3346.507042] wlan0: authenticated
[ 3346.507700] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3346.507721] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3346.511579] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[ 3346.615879] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[ 3346.619104] wlan0: RX AssocResp from <MAC 'happyhut' [AC1]> (capab=0x411 status=0 aid=1)
[ 3346.619289] wlan0: associated
[ 3965.837931] wlan0: deauthenticated from <MAC 'happyhut' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 3965.861056] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[ 3965.871387] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[ 3965.875672] wlan0: authenticated
[ 3965.876685] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 3965.876707] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 3965.879601] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[ 3965.888366] wlan0: RX AssocResp from <MAC 'happyhut' [AC1]> (capab=0x411 status=0 aid=1)
[ 3965.888554] wlan0: associated
[ 8510.971277] wlan0: deauthenticated from <MAC 'happyhut' [AC1]> (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
[ 8510.999612] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[ 8511.010065] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 1/3)
[ 8511.113641] wlan0: send auth to <MAC 'happyhut' [AC1]> (try 2/3)
[ 8511.116982] wlan0: authenticated
[ 8511.118337] rtl8188ee 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 8511.118360] rtl8188ee 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 8511.121717] wlan0: associate with <MAC 'happyhut' [AC1]> (try 1/3)
[ 8511.225513] wlan0: associate with <MAC 'happyhut' [AC1]> (try 2/3)
[ 8511.228273] wlan0: RX AssocResp from <MAC 'happyhut' [AC1]> (capab=0x411 status=0 aid=1)
[ 8511.228453] wlan0: associated
[ 8519.224900] wlan0: deauthenticated from <MAC 'happyhut' [AC1]> (Reason: 15=4WAY_HANDSHAKE_TIMEOUT)

```

Thanks in advance for any help!

Jim

---

### Post by Jim_D on 2015-08-09
I was looking at similar "wlan0: deauthenticated from ... (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)" messages reported by [**[COLOR=#000000]sam_baker2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1842448") for his RTL8188CE card at [http://ubuntuforums.org/showthread.php?t=2269696](http://ubuntuforums.org/showthread.php?t=2269696), and wondering whether the same driver update could work for my laptop and RTL8188EE card (getting the latest rtlwifi from the "Realtek wireless" PPA [https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+packages](https://launchpad.net/~hanipouspilot/+archive/ubuntu/rtlwifi/+packages)).

I notice different Realtek cards seem to have different modules, e.g. rtl8188ee.  Are the modules for all Realtek cards included in "rtlwifi"?

Is there a way to tell what the root cause of the CLASS3_FRAME_FROM_NONASSOC_STA messages is and whether the driver update is likely to fix it?

Thanks in advance,
Jim

---

### Post by Jim_D on 2015-08-10
I did try installing rtlwifi-new-dkms from the "Realtek wireless" PPA [https://launchpad.net/~hanipouspilot...wifi/+packages]("https://launchpad.net/%7Ehanipouspilot/+archive/ubuntu/rtlwifi/+packages"), which was a successful install on top of the 3.19.0-25 kernel I'd installed to resolve a touchpad problem (needed focaltech-dkms), but after rebooting I never got a successful connection.

Is rtlwifi-new-dkms compatible with the 3.19.0-25 kernel?

This is wireless-info after my boot with rtlwiki-new-dkms:

```


########## wireless info START ##########

Report from: 10 Aug 2015 08:07 EDT -0400

Booted last: 10 Aug 2015 08:03 EDT -0400

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

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: AzureWave Device [1a3b:1d38]
    Kernel driver in use: rtl8188ee

03:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 04f2:b409 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0457:1028 Silicon Integrated Systems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

asus_nb_wmi            24576  0 
asus_wmi               24576  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
rtl8188ee             139264  0 
rtl_pci                40960  1 rtl8188ee
rtlwifi               122880  2 rtl_pci,rtl8188ee
mac80211              708608  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              524288  2 mac80211,rtlwifi
wmi                    20480  1 asus_wmi
snd_soc_rt5640         94208  0 
snd_soc_rl6231         16384  1 snd_soc_rt5640
snd_soc_core          196608  2 snd_soc_rt5640,snd_soc_sst_mfld_platform
snd_pcm               106496  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_sst_mfld_platform,snd_hda_controller,snd_pcm_dmaengine
video                  20480  2 i915,asus_wmi

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
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       689     1  0 08:03 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

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

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    happyhut:        Infra, <MAC 'happyhut' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA2

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

[[/etc/NetworkManager/system-connections/happyhut]] (600 root)
[connection] id=happyhut | type=802-11-wireless
[802-11-wireless] ssid=happyhut | mac-address=<MAC 'wlan0' [IF]>
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'happyhut' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"happyhut"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023b349d42f
                    Extra: Last beacon: 488ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8188ee]
filename:       /lib/modules/3.19.0-25-generic/updates/dkms/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     03570C4CF6642B828D51436
depends:        rtlwifi,rtl_pci,mac80211
vermagic:       3.19.0-25-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl_pci]
filename:       /lib/modules/3.19.0-25-generic/updates/dkms/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     50149A68C0A3A531EFD566D
depends:        mac80211,rtlwifi
vermagic:       3.19.0-25-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.19.0-25-generic/updates/dkms/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AA292FEB01DFF0A9680EAA5
depends:        mac80211,cfg80211
vermagic:       3.19.0-25-generic SMP mod_unload modversions 

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

[rtl8188ee]
debug: 1
disable_watchdog: N
fwlps: N
ips: N
msi: Y
swenc: N
swlps: N

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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

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

[   18.090330] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.299230] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   19.309324] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   19.511906] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   19.716301] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   19.920022] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   20.998331] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   21.013563] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   21.217211] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   21.421374] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   21.625417] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   23.111771] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   23.131376] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   23.334934] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   23.539387] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   23.743560] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   25.709981] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   25.729651] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   25.933372] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   26.137205] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   26.341822] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   38.295368] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   38.321907] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   38.523326] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   38.727762] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   38.931861] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   48.073887] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   48.084512] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   48.287237] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   48.491323] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   48.695469] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   59.673417] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   59.693029] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   59.897066] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   60.101123] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   60.305258] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   76.102355] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   76.120075] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   76.322020] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   76.526168] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   76.730616] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[   87.717711] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[   87.736678] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[   87.939462] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[   88.143656] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[   88.347869] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[  104.153604] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  104.169520] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[  104.372860] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[  104.577005] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[  104.781166] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out
[  115.777762] wlan0: authenticate with <MAC 'happyhut' [AC1]>
[  115.789457] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 1/3)
[  115.990578] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 2/3)
[  116.194310] wlan0: direct probe to <MAC 'happyhut' [AC1]> (try 3/3)
[  116.398866] wlan0: authentication with <MAC 'happyhut' [AC1]> timed out

########## wireless info END ############

```

Is there anything else I should be doing with the rtlwifi-new-dkms package?  Is it the right package for my kernel and wireless adapter?

Thanks,
Jim

---

### Post by Jim_D on 2015-08-10
After installing just "rtlwifi-new-dkms" from the ppa:hanipouspilot/rtlwifi PPA, and getting the immediate authentication timeout messages and connection failure I posted about above, I went back and installed again along with linux-firmware, as it shows in [http://ubuntuforums.org/showthread.php?t=2283759:](http://ubuntuforums.org/showthread.php?t=2283759:)

sudo apt-get install rtlwifi-new-dkms linux-firmware

I could see that this time linux-firmware was updated (from 1.127 to 1.144 or something like that).  But the resulting behavior was the same, wireless logs immediate authentication timeout messages and fails to connect.  It looks the same as the last wireless-info.txt I posted above.

I'm not sure what I'm missing or how to get more information.  I think I might switch back to the 3.16 kernel I originally had with Ubuntu 14.04 and try installing the PPA rtlwifi-new-dkms and linux-firmware on top of that.  Right now I was trying to get rtlwifi-new-dkms to work on top of the 3.19 kernel I installed to get the focaltech-dkms PPA package for touchpad support.  I don't know if there's any kind of order I should worry about there, or if they're all meant to work together.

---

### Post by Jim_D on 2015-08-11
Doing "sudo apt-get install rtlwifi-new-dkms linux-firmware" from the 3.16 kernel seems to build the rtlwifi-new-dkms driver into the 3.16 kernel,but booting the 3.16 kernel with rtlwifi-new gives the same behavior as with 3.19, immediate authentication timeout.  I added the debug=5 module parameter to rtl8188ee to see if the extra messages would help understand what was going on.  Here's syslog when wifi times out authenticating:

```

Aug 11 00:10:38 magooch NetworkManager[856]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Aug 11 00:10:38 magooch kernel: [  852.991820] rtl8188ee:rtl88e_phy_sw_chnl_callback():<0-0> 
Aug 11 00:10:38 magooch kernel: [  852.991830] rtl8188ee:rtl88e_phy_sw_chnl():<0-0> sw_chnl_inprogress false schdule workitem current channel 6
Aug 11 00:10:38 magooch kernel: [  852.991837] rtl8188ee:rtl88ee_set_hw_reg():<0-0> HW_VAR_SLOT_TIME 14
Aug 11 00:10:38 magooch kernel: [  852.991856] rtl8188ee:rtl88e_phy_set_bw_mode_callback():<0-0> Switch to 20MHz bandwidth
Aug 11 00:10:38 magooch kernel: [  852.991867] rtl8188ee:rtl88e_phy_set_bb_reg():<0-0> regaddr(0x800), bitmask(0x1), data(0x0)
Aug 11 00:10:38 magooch kernel: [  852.991877] rtl8188ee:rtl88e_phy_set_bb_reg():<0-0> regaddr(0x800), bitmask(0x1), data(0x83040000)
Aug 11 00:10:38 magooch kernel: [  852.991883] rtl8188ee:rtl88e_phy_set_bb_reg():<0-0> regaddr(0x900), bitmask(0x1), data(0x0)
Aug 11 00:10:38 magooch kernel: [  852.991893] rtl8188ee:rtl88e_phy_set_bb_reg():<0-0> regaddr(0x900), bitmask(0x1), data(0x0)
Aug 11 00:10:38 magooch kernel: [  852.991900] rtl8188ee:rtl88e_phy_set_rf_reg():<0-0> regaddr(0x18), bitmask(0xfffff), data(0xc06), rfpath(0x0)
Aug 11 00:10:38 magooch kernel: [  852.991906] rtl8188ee:rtl88e_phy_set_bb_reg():<0-0> regaddr(0x840), bitmask(0xffffffff), data(0x1800c06)
Aug 11 00:10:38 magooch kernel: [  852.991914] rtl8188ee:rtl88e_phy_set_bb_reg():<0-0> regaddr(0x840), bitmask(0xffffffff), data(0x1800c06)
Aug 11 00:10:38 magooch kernel: [  852.991921] rtl8188ee:_rtl88e_phy_rf_serial_write():<0-0> RFW-0 Addr[0x840]=0x1800c06
Aug 11 00:10:38 magooch kernel: [  852.991927] rtl8188ee:rtl88e_phy_set_rf_reg():<0-0> regaddr(0x18), bitmask(0xfffff), data(0xc06), rfpath(0x0)
Aug 11 00:10:38 magooch kernel: [  852.991932] rtl8188ee:rtl88e_phy_set_bw_mode_callback():<0-0> 
Aug 11 00:10:38 magooch kernel: [  852.992069] rtlwifi:rtl_op_bss_info_changed():<0-0> bssid: 68:7f:74:1b:67:30
Aug 11 00:10:38 magooch kernel: [  852.992178] wlan0: direct probe to 68:7f:74:1b:67:30 (try 1/3)
Aug 11 00:10:38 magooch kernel: [  852.992206] rtl8188ee:rtl88ee_tx_fill_desc():<200-1> 
Aug 11 00:10:38 magooch kernel: [  852.992236] rtl_pci:_rtl_pci_interrupt():<10000-1> Manage ok interrupt!
Aug 11 00:10:38 magooch kernel: [  852.992244] rtl_pci:_rtl_pci_tx_isr():<10000-1> new ring->idx:93,free: skb_queue_len:0, free: seq:3520
Aug 11 00:10:39 magooch kernel: [  853.078806] rtl_pci:_rtl_pci_interrupt():<10000-1> Rx ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.078853] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> regaddr(0x824), bitmask(0x200)
Aug 11 00:10:39 magooch kernel: [  853.078870] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> BBR MASK=0x200 Addr[0x824]=0xa1390204
Aug 11 00:10:39 magooch kernel: [  853.181144] rtl_pci:_rtl_pci_interrupt():<10000-1> Rx ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.181185] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> regaddr(0x824), bitmask(0x200)
Aug 11 00:10:39 magooch kernel: [  853.181193] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> BBR MASK=0x200 Addr[0x824]=0xa1390204
Aug 11 00:10:39 magooch kernel: [  853.194440] wlan0: direct probe to 68:7f:74:1b:67:30 (try 2/3)
Aug 11 00:10:39 magooch kernel: [  853.194491] rtl8188ee:rtl88ee_tx_fill_desc():<200-1> 
Aug 11 00:10:39 magooch kernel: [  853.194535] rtl_pci:_rtl_pci_interrupt():<10000-1> Manage ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.194559] rtl_pci:_rtl_pci_tx_isr():<10000-1> new ring->idx:94,free: skb_queue_len:0, free: seq:3536
Aug 11 00:10:39 magooch kernel: [  853.283629] rtl_pci:_rtl_pci_interrupt():<10000-1> Rx ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.283677] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> regaddr(0x824), bitmask(0x200)
Aug 11 00:10:39 magooch kernel: [  853.283695] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> BBR MASK=0x200 Addr[0x824]=0xa1390204
Aug 11 00:10:39 magooch kernel: [  853.386138] rtl_pci:_rtl_pci_interrupt():<10000-1> Rx ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.386184] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> regaddr(0x824), bitmask(0x200)
Aug 11 00:10:39 magooch kernel: [  853.386202] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> BBR MASK=0x200 Addr[0x824]=0xa1390204
Aug 11 00:10:39 magooch kernel: [  853.398515] wlan0: direct probe to 68:7f:74:1b:67:30 (try 3/3)
Aug 11 00:10:39 magooch kernel: [  853.398575] rtl8188ee:rtl88ee_tx_fill_desc():<200-1> 
Aug 11 00:10:39 magooch kernel: [  853.398616] rtl_pci:_rtl_pci_interrupt():<10000-1> Manage ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.398632] rtl_pci:_rtl_pci_tx_isr():<10000-1> new ring->idx:95,free: skb_queue_len:0, free: seq:3552
Aug 11 00:10:39 magooch kernel: [  853.488639] rtl_pci:_rtl_pci_interrupt():<10000-1> Rx ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.488686] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> regaddr(0x824), bitmask(0x200)
Aug 11 00:10:39 magooch kernel: [  853.488704] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> BBR MASK=0x200 Addr[0x824]=0xa1390204
Aug 11 00:10:39 magooch kernel: [  853.591048] rtl_pci:_rtl_pci_interrupt():<10000-1> Rx ok interrupt!
Aug 11 00:10:39 magooch kernel: [  853.591098] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> regaddr(0x824), bitmask(0x200)
Aug 11 00:10:39 magooch kernel: [  853.591113] rtl8188ee:rtl88e_phy_query_bb_reg():<10000-1> BBR MASK=0x200 Addr[0x824]=0xa1390204
Aug 11 00:10:39 magooch kernel: [  853.602593] wlan0: authentication with 68:7f:74:1b:67:30 timed out

```

I'm not really sure what the debug messages mean, though.

I'm still having better behavior from the stock 3.16.0-45 kernel and the stock 3.19.0-25, than from rtlwifi-new-dkms, I just have the connection dropped after a while (hour or so), which I'd still like to solve.

If anyone can help me troubleshoot what's going on with rtlwifi-new-dkms, I'd really appreciate the help.

Thanks,
Jim

---

### Post by Jim_D on 2015-08-13
Hi,

I tried switching out my router as a solution to the connection issues I had, and it worked.  Old router was a 2010 Linksys WRT54GL running latest Linksys firmware from July 2015.  New router is a TP-LINK TL-WR841N.  They were both configured with the same security - WPA2 personal with AES encryption.  I've tested the wireless connection over the course of 6 hours without losing the connection, unlike with the WRT54GL where I would usually lose the connection within an hour or so.  Both the stock 14.04 3.16.0-45 kernel, and the 3.19 kernel I installed to resolve touchpad issues with focaltech-dkms, seem to work fine with the router with no issues.  Unless something terrible happens with the TP-LINK, I'm probably done with the Linksys and troubleshooting the problems I had with its network.

Thanks,
Jim

---

