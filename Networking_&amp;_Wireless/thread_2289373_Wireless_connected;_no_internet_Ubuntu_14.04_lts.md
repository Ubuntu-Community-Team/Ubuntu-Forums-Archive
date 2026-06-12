---
title: "Wireless connected; no internet Ubuntu 14.04 lts"
date: 2015-08-03
forum: Networking &amp; Wireless
---

### Post by ryan172 on 2015-08-03
Hello everyone. Linux noob here.

Some background: I switched to a different router and the wired connection works fine. However, when using wifi I can connect to the router but can't get any internet. My previous router used WPA2 however, the one I switched to uses WPA. I have tried updating/upgrading but no luck.

I have searched these forums and it seems many people have this problem but can be specific in terms of the problem? It might be a duplicate but I'm not too sure. I have downloaded and run the wireless script. The results are below.

```

########## wireless info START ##########

Report from: 03 Aug 2015 09:38 PDT -0700

Booted last: 03 Aug 2015 09:25 PDT -0700

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-45-generic #60~14.04.1-Ubuntu SMP Fri Jul 24 21:16:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
    Kernel driver in use: e1000e

05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178]
    Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 004: ID 1bcf:0005 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 2516:0020  
Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

eeepc_wmi              13151  0 
asus_wmi               24094  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
rtl8192ce              53516  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                64255  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              652777  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              498458  2 mac80211,rtlwifi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
mxm_wmi                13021  1 nouveau
video                  20128  2 nouveau,asus_wmi
wmi                    19193  3 mxm_wmi,nouveau,asus_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66165 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33343 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95413890 (95.4 MB)  TX bytes:2852771 (2.8 MB)
          Interrupt:20 Memory:f7200000-f7220000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:474 errors:0 dropped:0 overruns:0 frame:0
          TX packets:519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:103756 (103.7 KB)  TX bytes:66311 (66.3 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"shimwire"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'shimwire' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search oc.cox.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       712     1  0 09:25 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [shimwire] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    La Plata:        Infra, <MAC 'La Plata' [AN1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 26 WPA2
    ATT5453:         Infra, <MAC 'ATT5453' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 97 WPA2
    87cc97:          Infra, <MAC '87cc97' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    SHABAKEH:        Infra, <MAC 'SHABAKEH' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    NETGEAR-Guest:   Infra, <MAC 'NETGEAR-Guest' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2
    JHAVERI:         Infra, <MAC 'JHAVERI' [AC8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26 WPA2
    DDW365.45F465-2.4G: Infra, <MAC 'DDW365.45F465-2.4G' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 26 WPA WPA2
    SHABAKEH-guest:  Infra, <MAC 'SHABAKEH-guest' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26
    Chromecast0522:  Infra, <MAC 'Chromecast0522' [AC6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 26
    *shimwire:       Infra, <MAC 'shimwire' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 82 WPA

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11

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

no-auto-default=<MAC address>,<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/shimwire]] (600 root)
[connection] id=shimwire | type=802-11-wireless
[802-11-wireless] ssid=shimwire | mac-address=<MAC 'wlan0' [IF]>
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
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'shimwire' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"shimwire"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000acdddfaff
                    Extra: Last beacon: 60ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '87cc97' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"87cc97"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000981773d4e1
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SHABAKEH' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"SHABAKEH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007d6eba70f
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'SHABAKEH-guest' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"SHABAKEH-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000007d6ebc23e
                    Extra: Last beacon: 60ms ago
          Cell 05 - Address: <MAC 'DDW365.45F465-2.4G' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"DDW365.45F465-2.4G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fb437ab38
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Chromecast0522' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:off
                    ESSID:"Chromecast0522"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000490408bd0
                    Extra: Last beacon: 60ms ago
          Cell 07 - Address: <MAC 'NETGEAR-Guest' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=6400000244210ab1
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'JHAVERI' [AC8]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"JHAVERI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000024420faa0
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'salsa5' [AC9]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"salsa5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002cbdb0183d7
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     BE372FB24A1F38A5218DAA0
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
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

[rtl8192c_common]
filename:       /lib/modules/3.16.0-45-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A279C50E29ED7F277EAF738
depends:        
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

[rtl8192ce]
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
# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   42.543551] wlan0: Connection to AP <MAC 'shimwire' [AC1]> lost
[   43.842954] wlan0: authenticate with <MAC 'shimwire' [AC1]>
[   43.862843] wlan0: send auth to <MAC 'shimwire' [AC1]> (try 1/3)
[   43.864402] wlan0: authenticated
[   43.864476] rtl8192ce 0000:05:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   43.864478] rtl8192ce 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   43.864479] rtl8192ce 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   43.866669] wlan0: associate with <MAC 'shimwire' [AC1]> (try 1/3)
[   43.873537] wlan0: RX AssocResp from <MAC 'shimwire' [AC1]> (capab=0x411 status=0 aid=5)
[   43.873631] wlan0: associated
[  200.889764] wlan0: deauthenticating from <MAC 'shimwire' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  201.782881] wlan0: authenticate with <MAC 'shimwire' [AC1]>
[  201.803025] wlan0: send auth to <MAC 'shimwire' [AC1]> (try 1/3)
[  201.811426] wlan0: authenticated
[  201.811524] rtl8192ce 0000:05:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  201.811527] rtl8192ce 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  201.811528] rtl8192ce 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  201.814451] wlan0: associate with <MAC 'shimwire' [AC1]> (try 1/3)
[  201.820671] wlan0: RX AssocResp from <MAC 'shimwire' [AC1]> (capab=0x411 status=0 aid=5)
[  201.820770] wlan0: associated
[  214.162238] wlan0: deauthenticating from <MAC 'shimwire' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  220.122340] wlan0: authenticate with <MAC 'shimwire' [AC1]>
[  220.465185] wlan0: send auth to <MAC 'shimwire' [AC1]> (try 1/3)
[  220.466698] wlan0: authenticated
[  220.466775] rtl8192ce 0000:05:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  220.466777] rtl8192ce 0000:05:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  220.466778] rtl8192ce 0000:05:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  220.468451] wlan0: associate with <MAC 'shimwire' [AC1]> (try 1/3)
[  220.474229] wlan0: RX AssocResp from <MAC 'shimwire' [AC1]> (capab=0x411 status=0 aid=5)
[  220.474324] wlan0: associated

########## wireless info END ############


```

I would appreciate any help!

Thanks again

---

### Post by prshah on 2015-08-03
it looks to me that your DNS servers are not set correctly. Usually, this is picked up from your router (as is the IP address).

In your current setting, the DNS server is set to 127.0.1.1 (see file /etc/resolv.conf) - that doesn't seem correct, unless you have an esoteric setup of some kind.

Usually, it SHOULD be the same as your gateway (192.168.1.1), or public DNS's such as 208.67.222.222 (...220.220) or 8.8.8.8 (...4.4).

However, you cannot change the /etc/resolv.conf by hand; change the DNS either in your router or in connection settings (click the wireless icon, and choose "edit connections")

You're able to connect to the router fine, WPA2/WPA is not the issue.

Please post back if you need more information, or if the problem continues.

---

### Post by ryan172 on 2015-08-03
Thank you for the response! I do not have any special setups. When going into edit connections > IPv4 Settings, what settings would I be adding/changing? I'm not sure if this is correct but I have tried adding the gateway address (192.168.1.1) into "Additional DNS servers" and tried pinging 8.8.8.8 but still no luck. Could you take me through the steps to troubleshoot?

Thanks again!

---

### Post by ryan172 on 2015-08-04
Problem fixed. Needed to update/install realtek driver. Solution was in this thread: [http://ubuntuforums.org/showthread.php?t=2282079](http://ubuntuforums.org/showthread.php?t=2282079)

---

