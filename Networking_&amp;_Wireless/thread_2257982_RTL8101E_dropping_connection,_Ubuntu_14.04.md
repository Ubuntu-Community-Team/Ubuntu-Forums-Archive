---
title: "RTL8101E dropping connection, Ubuntu 14.04"
date: 2014-12-23
forum: Networking &amp; Wireless
---

### Post by snazzyjazzy on 2014-12-23
Recently upgraded to Ubuntu and had no issues until I returned home for Christmas, have found my wireless connection for my laptop dropping frequently (house recently upgraded to fibre broadband, if that makes any difference). All other devices/laptops in the house work fine. I have run the updates as described in the sticky, but the problem persists. It will either completely disconnect or show a connection but fail to actually load any pages. Any assistance would be greatly appreciated! 

```


########## wireless info START ##########


Report from: 24 Dec 2014 14:44 NZDT +1300


Booted last: 23 Dec 2014 19:01 NZDT +1300


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
	Kernel driver in use: rtl8192ce


03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Toshiba America Info Systems Device [1179:fb37]


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              630653  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  0 


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.69  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fe3a:e0c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:567215 errors:0 dropped:2 overruns:0 frame:0
          TX packets:505975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:703497783 (703.4 MB)  TX bytes:72734335 (72.7 MB)


##### iwconfig ##########################


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"TELECOM-TEWKUT"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'TELECOM-TEWKUT' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=16 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:696   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [TELECOM-TEWKUT] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
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
    *TELECOM-TEWKUT: Infra, <MAC 'TELECOM-TEWKUT' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.69
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


[[/etc/NetworkManager/system-connections/26a Suva Street]] (600 root)
[connection] id=26a Suva Street | type=802-11-wireless
[802-11-wireless] ssid=26a Suva Street | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TELECOM-TEWKUT]] (600 root)
[connection] id=TELECOM-TEWKUT | type=802-11-wireless
[802-11-wireless] ssid=TELECOM-TEWKUT | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/TELECOMA84D37]] (600 root)
[connection] id=TELECOMA84D37 | type=802-11-wireless
[802-11-wireless] ssid=TELECOMA84D37 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Pacific/Auckland (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


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


Channel occupancy:


      1   APs on   Frequency:2.462 GHz (Channel 11)


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TELECOM-TEWKUT' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"TELECOM-TEWKUT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000624dcc7045
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rtl8192ce]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     730FEE1A7696EA37A982482
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[rtl8192c_common]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[18815.840834] wlan0: authenticate with <MAC 'TELECOM-TEWKUT' [AC1]>
[18815.872791] wlan0: send auth to <MAC 'TELECOM-TEWKUT' [AC1]> (try 1/3)
[18815.875688] wlan0: authenticated
[18815.876247] wlan0: associate with <MAC 'TELECOM-TEWKUT' [AC1]> (try 1/3)
[18815.879898] wlan0: RX AssocResp from <MAC 'TELECOM-TEWKUT' [AC1]> (capab=0x411 status=0 aid=5)
[18815.880080] wlan0: associated
[18908.919041] wlan0: deauthenticating from <MAC 'TELECOM-TEWKUT' [AC1]> by local choice (reason=3)
[18911.023554] rtlwifi: wireless switch is on
[18912.365345] rtl8192ce 0000:02:00.0: no hotplug settings from platform
[18913.003622] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[18914.709868] wlan0: authenticate with <MAC 'TELECOM-TEWKUT' [AC1]>
[18914.726129] wlan0: send auth to <MAC 'TELECOM-TEWKUT' [AC1]> (try 1/3)
[18914.727683] wlan0: authenticated
[18914.731036] wlan0: associate with <MAC 'TELECOM-TEWKUT' [AC1]> (try 1/3)
[18914.734559] wlan0: RX AssocResp from <MAC 'TELECOM-TEWKUT' [AC1]> (capab=0x411 status=0 aid=5)
[18914.734736] wlan0: associated
[18914.734765] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############

```

---

### Post by r.stiltskin on 2014-12-24
RTL8101E  is your wired ethernet adapter.  Your issue is with wireless so it's your RTL8188CE wifi adapter that needs attention.  I have no specific knowledge about that card but if you google "rtl8188ce ubuntu 14.04" it brings up a few threads directly dealing with your problem that should be helpful.

---

### Post by snazzyjazzy on 2014-12-24
Apologies, I'm not greatly gifted in the technology department. Will give those threads a read through though, thank you!

---

