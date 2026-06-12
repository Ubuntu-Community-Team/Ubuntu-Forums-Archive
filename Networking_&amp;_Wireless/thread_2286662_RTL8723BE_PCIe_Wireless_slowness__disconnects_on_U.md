---
title: "RTL8723BE PCIe Wireless slowness / disconnects on Ubuntu 14.10 x64"
date: 2015-07-13
forum: Networking &amp; Wireless
---

### Post by byhoratiss on 2015-07-13
Hi everyone,


I've posted before another problem regarding my wifi connection: [http://ubuntuforums.org/showthread.php?t=2286312](http://ubuntuforums.org/showthread.php?t=2286312).
When I use the solution provided by @praseodym started working, but I experienced some connection issues & slowness.


So I googled a bit and found some interesting updated drivers (or that was what I thought).
I'm quite sure that something went wrong when I followed this "guide" ([https://github.com/lwfinger/rtlwifi_new/issues/18#issuecomment-71635275](https://github.com/lwfinger/rtlwifi_new/issues/18#issuecomment-71635275)), because I cannot make my bluetooth work. But that is another issue.


The thing is that now is almost impossible to web-browse because of the slowness and doing "ssh" tasks are a living nightmare.


Can any of you help me with this?
Thank you!


This is the wireless-script output:


```

########## wireless info START ##########


Report from: 13 Jul 2015 19:47 ART -0300


Booted last: 11 Jul 2015 23:03 ART -0300


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic


##### kernel ############################


Linux 3.16.0-43-generic #58-Ubuntu SMP Fri Jun 19 11:04:02 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:b729]
	Kernel driver in use: rtl8723be


03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: CLEVO/KAPOK Computer Device [1558:5494]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 012: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120
Bus 002 Device 003: ID 04f2:b43b Chicony Electronics Co., Ltd 
Bus 002 Device 011: ID 0bda:b002 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8723be             139131  0 
btcoexist             183652  1 rtl8723be
rtl_pci                39724  1 rtl8723be
rtlwifi               125447  3 btcoexist,rtl_pci,rtl8723be
mac80211              660651  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              510218  2 mac80211,rtlwifi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104102  8 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1718408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1411152 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1787066325 (1.7 GB)  TX bytes:256331010 (256.3 MB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.9  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5627:1eff:fe94:2be7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:668046 errors:0 dropped:1 overruns:0 frame:0
          TX packets:340388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:444191191 (444.1 MB)  TX bytes:67797228 (67.7 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Tissera"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC 'Tissera' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       940     1  0 Jul11 ?        00:00:05 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0  [Tissera] -----------------------------------------------------
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
    ax951:           Infra, <MAC 'ax951' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    VALE:            Infra, <MAC 'VALE' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA
    *Tissera:        Infra, <MAC 'Tissera' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 62 WPA2


  IPv4 Settings:
    Address:         192.168.0.9
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             200.42.4.204
    DNS:             200.49.130.41


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


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


[[/etc/NetworkManager/system-connections/Tissera]] (600 root)
[connection] id=Tissera | type=802-11-wireless
[802-11-wireless] ssid=Tissera | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AndroidAP]] (600 root)
[connection] id=AndroidAP | type=802-11-wireless
[802-11-wireless] ssid=AndroidAP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WiFi-Arnet-Hesiel]] (600 root)
[connection] id=WiFi-Arnet-Hesiel | type=802-11-wireless
[802-11-wireless] ssid=WiFi-Arnet-Hesiel | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/PyP]] (600 root)
[connection] id=PyP | type=802-11-wireless
[802-11-wireless] ssid=PyP | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/patricia]] (600 root)
[connection] id=patricia | type=802-11-wireless
[802-11-wireless] ssid=patricia | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Argentina/Buenos_Aires (based on set time zone)


country KR: DFS-UNSET
	(2402 - 2482 @ 20), (N/A, 20)
	(5170 - 5250 @ 20), (3, 20)
	(5250 - 5330 @ 20), (3, 20), DFS
	(5490 - 5630 @ 20), (3, 30), DFS
	(5735 - 5815 @ 20), (3, 30)


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
          Current Frequency:2.442 GHz (Channel 7)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Tissera' [AC1]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"Tissera"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000009f785cd548
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ax951' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"ax951"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000803ced643d
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'VALE' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"VALE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002705e1cd96
                    Extra: Last beacon: 13880ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8723be]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     1A35907BCCEF84FE28F988D
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
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
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     50149A68C0A3A531EFD566D
depends:        mac80211,rtlwifi
vermagic:       3.16.0-43-generic SMP mod_unload modversions 


[rtlwifi]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C521E75F9EA649617E3EDDD
depends:        mac80211,cfg80211
vermagic:       3.16.0-43-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B5:AA:FA:DF:28:7B:39:3A:FB:5E:BD:08:7C:4B:E9:35:FE:8A:57:64
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B5:AA:FA:DF:28:7B:39:3A:FB:5E:BD:08:7C:4B:E9:35:FE:8A:57:64
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
swenc: Y
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


[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008172sv0000E020sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008172sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00000315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001139sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001629sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000169Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000016B3sd000010CFbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001786sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001A39sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002057sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002078sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002481sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002A57sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003824sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003874sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007185sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007611sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008130sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008131sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008175sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd0000185Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000818Asd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008194sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008197sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008205sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008206sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008207sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008208sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008209sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008210sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008211sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008212sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008213sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008214sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008215sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008216sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008217sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008218sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008219sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008220sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008221sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008222sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008230sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008231sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000824Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008297sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000084B5sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000085E5sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000874Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009174sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009175sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009196sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009197sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009205sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008177sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001178sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007622sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007622sd00007392bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv000084B6sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv000085E3sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000179sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000183sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000187sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000188sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000190sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000193sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00000195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001238sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012A8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012B8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012C8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv000012D8sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000197Dsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001D38sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00001F38sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv00008180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv0000E08Asd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008179sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000001Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000002Bsd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000818Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv0000819Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000818Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008191sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00000186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00008293sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv00009293sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008193sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000725sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000726sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000727sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000728sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000729sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000730sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000731sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000732sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000733sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00000734sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00002114sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv00008723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008723sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008724sv00008724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008724sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Asv0000872Asd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Asv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Bsv0000872Bsd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000872Bsv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv00008753sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008753sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv000020EFsd0000148Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv00008812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A811sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A812sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv0000A813sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008812sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00002161sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Bsd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000216Csd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv000085B4sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv00008821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A801sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A802sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A803sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A804sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv0000A821sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008821sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002159sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000215Asd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002165sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv000021FDsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv00002231sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B001sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B723sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B724sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B725sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B726sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B727sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B728sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B729sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B730sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B731sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B732sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B733sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B734sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B735sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B736sd000017AAbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B737sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000B738sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E089sd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv0000E08Dsd0000105Bbc*sc*i* ndiswrapper
alias pci:v000010ECd0000B723sv*sd*bc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv000030A1sd000017AAbc*sc*i* ndiswrapper
alias pci:v0000168Cd0000002Bsv*sd*bc*sc*i* ndiswrapper


[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be swenc=1 fwlps=0 ips=0


##### rc.local ##########################


/etc/init.d/bluetooth stop


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[44490.141209] rtlwifi: wireless switch is on
[44491.867869] rtk_btusb: get_firmware start
[44491.867874] rtk_btusb: get_firmware done
[44496.318614] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[44498.398927] wlan0: authenticate with <MAC 'Tissera' [AC1]>
[44498.410939] wlan0: send auth to <MAC 'Tissera' [AC1]> (try 1/3)
[44498.414321] wlan0: authenticated
[44498.417129] wlan0: associate with <MAC 'Tissera' [AC1]> (try 1/3)
[44498.421392] wlan0: RX AssocResp from <MAC 'Tissera' [AC1]> (capab=0x431 status=0 aid=3)
[44498.422187] wlan0: associated
[44498.422194] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by Bucky Ball on 2015-07-13
Off topic but just a note: 14.10 is out of support on July 23, 2015. About nine days. Have you thought about upgrading to 15.04 (supported until January 2016) or installing 14.04 LTS (supported until 2019)? If not, the time is now. Good luck. :)

---

### Post by byhoratiss on 2015-07-13
Yes, but I wanted to stay with that version. In my desktop I updated to 15.04, and the wifi was gone. Had to reinstall everything to 14.04.2 and is working ok.

Now I don't exactly know what is wrong with my notebook, now even the usb mouse stopped working, and of course I don't have neither LAN or WAN.
Seems that I need to reinstall everything again, and is tedious.
Starting to hate this.
:(

---

### Post by Bucky Ball on 2015-07-14
By all means, stay with 14.10, at your own risk. You will have no security updates or any other updates after the EOL date. See [HERE]("https://lists.ubuntu.com/archives/ubuntu-announce/2015-July/000197.html"). I'd stick with 14.04 LTS if all is working. 

Good luck.

---

### Post by byhoratiss on 2015-07-14
I would love to update, but now I dont have wired or wireless internet connection on my laptop.
I mixed up all my drivers, or something worse.

Your solution seems to be "simple": update & GL & HF.

Could you help me to get at least my wired connection back to life ?

---

### Post by jeremy31 on 2015-07-14
Things might work again if you remove that ndiswrapper driver

---

### Post by byhoratiss on 2015-07-14
Don't know how to do it, but thanks anyway.

I installed Xubuntu, works just fine, as a clean Ubuntu install, but both can't get my bluetooth start working, but thats another issue, not wifi :D.

Thanks, solved by "reinstall os".

---

### Post by jeremy31 on 2015-07-14
Search the forum for posts by Pilot6 as he has posted instructions for his PPA that will get the bluetooth going along with more recent wifi module

---

### Post by byhoratiss on 2015-07-14
Thank you for the tip @jeremy31.
Now I have wireless & bluetooth working just fine!

---

### Post by byhoratiss on 2015-07-14
Another problem that I faced was that I could pair the device, but not to "stream" music to it.

I'm using Xubuntu 14.04.2 with the hibrid Realtek RTL8723BE PCIe Wireless Network Adapter.

So I finally did this to solve all problems:

1. Install Pilot6 drivers:
```

sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8723au-bt-dkms rtlwifi-new-dkms linux-firmware

```

2. Install "pulseaudio-module-bluetooth"
```

sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover

```

And bluetooth is working, and wireless connection problems (slowness & disconnection) are gone.

---

