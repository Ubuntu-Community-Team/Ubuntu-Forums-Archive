---
title: "Disconnected from network"
date: 2015-07-03
forum: Networking &amp; Wireless
---

### Post by cowboy.bebop on 2015-07-03
The first time I installed Ubuntu I configured it and it worked flawlessly. Then it gave me this issue. So I reinstalled and again it worked flawlessly. Now after 3 days it's doing it again. I removed my connection and set up the wireless again by typing in the wireless password and still nothing. Now for some reason when I restart my router, I am able to connect, which really gets me cause my other devices (ipad, android tablet, iphone and android phone) all work flawlessly without issues. I really don't feel like reinstalling ubuntu just to get it to work again. I also checked additional drivers, but it comes up blank. Also I am literally 2-3 meters from the router.

See screenshot of error at top right.

My output text if useful ;)
```


#lsmod

Module                  Size  Used by
nls_iso8859_1          12713  0 
uas                    27255  0 
usb_storage            66545  1 uas
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
dm_crypt               23216  0 
asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
snd_hda_codec_hdmi     47548  1 
snd_hda_codec_realtek    77514  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
snd_hda_intel          30469  3 
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              17698  1 snd_hda_codec
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
kvm_intel             143590  0 
kvm                   452047  1 kvm_intel
arc4                   12608  2 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  487 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  246 ghash_clmulni_intel,aesni_intel,ablk_helper
ath9k                 137283  0 
ath9k_common           25638  1 ath9k
joydev                 17393  0 
ath9k_hw              446521  2 ath9k_common,ath9k
serio_raw              13483  0 
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652777  1 ath9k
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lpc_ich                21093  0 
snd_timer              29562  2 snd_pcm,snd_seq
snd                    79468  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              15047  2 snd,snd_hda_codec
mei_me                 19696  0 
mei                    87875  1 mei_me
shpchp                 37047  0 
mac_hid                13227  0 
parport_pc             32741  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
i915                  906106  3 
ahci                   34062  2 
i2c_algo_bit           13413  1 i915
drm_kms_helper         61574  1 i915
psmouse               106722  0 
libahci                32424  1 ahci
drm                   311018  5 i915,drm_kms_helper
atl1c                  46101  0 
wmi                    19193  1 asus_wmi
video                  20128  2 i915,asus_wmi

#rfkill list all

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no

#lspci

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)


```
[http://i.imgur.com/3rWOG6B.png](http://i.imgur.com/3rWOG6B.png)

---

### Post by cowboy.bebop on 2015-07-04
zero replies =\?

---

### Post by gordintoronto on 2015-07-05
What version of Ubuntu? Brand and model of your laptop? Router? SSID? (Oddly, the SSID can be an issue in Linux.)

Atheros wireless is generally well supported, so your problem is unexpected.

---

### Post by wildmanne39 on 2015-07-05
Please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth.
Thanks

---

### Post by cowboy.bebop on 2015-07-07
> **gordintoronto said:**
> What version of Ubuntu? Brand and model of your laptop? Router? SSID? (Oddly, the SSID can be an issue in Linux.)

Atheros wireless is generally well supported, so your problem is unexpected.

Make: Asus
Model: K53E
SSID: Bat-Cave
Linux bebop 3.16.0-41-generic #57~14.0.4.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

# Wireless_Script Output

```


########## wireless info START ##########

Report from: 07 Jul 2015 13:45 EDT -0400

Booted last: 07 Jul 2015 13:31 EDT -0400

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.16.0-41-generic #57~14.04.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /home/cowboy/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 004: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 13d3:5710 IMC Networks UVC VGA Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
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

asus_nb_wmi            21128  0 
asus_wmi               24094  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
ath9k                 137283  0 
ath9k_common           25638  1 ath9k
ath9k_hw              446521  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              652777  1 ath9k
cfg80211              494362  4 ath,ath9k_common,ath9k,mac80211
wmi                    19193  1 asus_wmi
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
          inet6 addr: fe80::208:caff:fe22:1a3c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:459 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:129963 (129.9 KB)  TX bytes:29653 (29.6 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    HP-Print-AC-Deskjet 3510 series: Infra, <MAC 'HP-Print-AC-Deskjet 3510 series' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 87 WPA2
    homenet1:        Infra, <MAC 'homenet1' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    closet-freak:    Infra, <MAC 'closet-freak' [AN3]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2
    Bat-Cave:        Infra, <MAC 'Bat-Cave' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

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

[[/etc/NetworkManager/system-connections/Bat-Cave-cda1b24f-137a-4478-9508-02ad84d3816c]] (600 root)
[connection] id=Bat-Cave | type=802-11-wireless
[802-11-wireless] ssid=Bat-Cave | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

[[/etc/NetworkManager/system-connections/Bat-Cave]] (644 root)
[connection] id=Bat-Cave | type=802-11-wireless
[802-11-wireless] ssid=Bat-Cave
[ipv4] method=auto
[ipv6] method=ignore

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

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Bat-Cave' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-31 dBm  
                    Encryption key:on
                    ESSID:"Bat-Cave"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000046a3120b
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'HP-Print-AC-Deskjet 3510 series' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-AC-Deskjet 3510 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000006d36954485
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'homenet1' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"homenet1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000853b767f51c
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) :lo        Interface doesn't support scanning.

 CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5C1878F185424DB0329389D
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)

[ath9k_common]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     265A5990B1258ECC29235FC
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     0D1161FC3B202FBE214F25D
depends:        ath
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.16.0-41-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     376BFDE8E6207B0AAA6339B
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0

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

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  602.163778] wlan0: deauthenticating from <MAC 'Bat-Cave' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  605.005853] wlan0: authenticate with <MAC 'Bat-Cave' [AC1]>
[  605.022740] wlan0: send auth to <MAC 'Bat-Cave' [AC1]> (try 1/3)
[  605.024417] wlan0: authenticated
[  605.024582] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  605.025674] wlan0: associate with <MAC 'Bat-Cave' [AC1]> (try 1/3)
[  605.028411] wlan0: RX AssocResp from <MAC 'Bat-Cave' [AC1]> (capab=0x431 status=0 aid=6)
[  605.028482] wlan0: associated
[  605.031733] ath: EEPROM regdomain: 0x8348
[  605.031737] ath: EEPROM indicates we should expect a country code
[  605.031739] ath: doing EEPROM country->regdmn map search
[  605.031741] ath: country maps to regdmn code: 0x3a
[  605.031743] ath: Country alpha2 being used: US
[  605.031744] ath: Regpair used: 0x3a
[  605.031746] ath: regdomain 0x8348 dynamically updated by country IE
[  650.216920] wlan0: deauthenticating from <MAC 'Bat-Cave' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  653.051187] wlan0: authenticate with <MAC 'Bat-Cave' [AC1]>
[  653.068116] wlan0: send auth to <MAC 'Bat-Cave' [AC1]> (try 1/3)
[  653.075390] wlan0: authenticated
[  653.075514] ath9k 0000:02:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[  653.076552] wlan0: associate with <MAC 'Bat-Cave' [AC1]> (try 1/3)
[  653.092606] wlan0: RX AssocResp from <MAC 'Bat-Cave' [AC1]> (capab=0x431 status=0 aid=6)
[  653.092696] wlan0: associated
[  653.094565] ath: EEPROM regdomain: 0x8348
[  653.094568] ath: EEPROM indicates we should expect a country code
[  653.094569] ath: doing EEPROM country->regdmn map search
[  653.094570] ath: country maps to regdmn code: 0x3a
[  653.094572] ath: Country alpha2 being used: US
[  653.094572] ath: Regpair used: 0x3a
[  653.094574] ath: regdomain 0x8348 dynamically updated by country IE
[  698.271208] wlan0: deauthenticating from <MAC 'Bat-Cave' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############



```

# Router Wireless Setup

[[img]http://i.imgur.com/cdSDYjBm.png[/img]](http://imgur.com/cdSDYjB)

---

### Post by gordintoronto on 2015-07-08
It looks like you have interference on channel 6. Have a look at this article:
[https://www.maketecheasier.com/find-best-wifi-channel/](https://www.maketecheasier.com/find-best-wifi-channel/)

Install wifi radar and try to find a channel with less clutter.

I would also change the ssid to batcave, but that is probably not going to help.

---

### Post by cowboy.bebop on 2015-07-08
> **gordintoronto said:**
> It looks like you have interference on channel 6. Have a look at this article:
[https://www.maketecheasier.com/find-best-wifi-channel/](https://www.maketecheasier.com/find-best-wifi-channel/)

Install wifi radar and try to find a channel with less clutter.

I would also change the ssid to batcave, but that is probably not going to help.

If you don't mind me asking, how did you determine this, I would really like know, this did not resolve the issues after I adjusted the channels, the same issues still applies.

---

### Post by gordintoronto on 2015-07-09
How often does the problem happen? Does it reconnect?

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)

This is also odd:
Linux bebop 3.16.0-41-generic #57~14.0.4.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by cowboy.bebop on 2015-07-10
> **gordintoronto said:**
> How often does the problem happen? Does it reconnect?

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.437 GHz (Channel 6)

This is also odd:
Linux bebop 3.16.0-41-generic #57~14.0.4.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

If I turn my laptop on, it will not connect. At this point I restart my router and everything works. But the moment I turn my laptop off and turn it back on, I cannot connect. I then restart my router and everything works fine again. The network manager does not appear to obtain the routers gateway IP, everything appears blank, no ip; netmask or gateway which is really weird. As I said before, all other devices on my network between my wifes iphone, ipad and laptop work, both my android devices and my PC is hardwired.

What is odd about the uname -a?

I ran inSSIDer from my android and the channels did not appear to overlap, the only AP's that overlapped in channels, was my HP printer which was on channel 6 and my Router, the PS3 is on channel 6. Well no longer, this is after I was asked to change channels.

[[img]http://i.imgur.com/G1TVff8t.png[/img]](http://imgur.com/G1TVff8)

---

### Post by cowboy.bebop on 2015-07-11
So I did a default on my router, configured all devices. Since then I have been able to connect, concrete. If it happens again I will just resort to wpa_supplicant which seemed to nail it every time.

---

