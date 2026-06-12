---
title: "Unstable WIFI and a warning"
date: 2014-12-28
forum: Networking &amp; Wireless
---

### Post by mbkwp on 2014-12-28
Howdy. Sorry to do this one more time, but one would think a proper remedy would be in order.  I used 13. on an older machine, installed 14.04 and it fried the WiFi. So now into a new machine and it is still unstable. I have been chasing for 5 days and nothing. I have gone to all the "solved" sites and it seems to be non eventful.
The 14.04 wiped the new machine on install but no worries. I heard horror stories on Windows 8.1 and they seem to do it injustice, it was much worse.

So any new ideas?

---

### Post by kerry_s on 2014-12-29
Specs ?
when you say unstable, what exactly is unstable ? is it just the popup crash reports, cause you can turn those off. they don't effect the system.
i went from 14.10 ubuntu mate, unity->14.04.1 ubuntu mate, gnome->12.04 elementary os and finally got something stable as a rock.
but, my machine is old, pieced together from several broken computers. it's a atom 330 1.6ghz x4, 2gb ram maxed out. everything just works now, my wifi stopped dropping out(i ordered a new 1 from amazon cause i thought it was braking), network printer works like a champ, etc...

just keep trying you'll find your fit.

---

### Post by chili555 on 2014-12-29
> **mbkwp said:**
> Howdy. Sorry to do this one more time, but one would think a proper remedy would be in order.  I used 13. on an older machine, installed 14.04 and it fried the WiFi. So now into a new machine and it is still unstable. I have been chasing for 5 days and nothing. I have gone to all the "solved" sites and it seems to be non eventful.
The 14.04 wiped the new machine on install but no worries. I heard horror stories on Windows 8.1 and they seem to do it injustice, it was much worse.

So any new ideas?There is no possible way we could have the slightest idea since you've given us no information to work with. Please see: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by mbkwp on 2014-12-29
I tried your sticky but the command would not run. This came up after trying the linked post. I do not know what I'm looking at or for, so maybe this will make since to you.

Thanks




########## wireless info START ##########


Report from: 29 Dec 2014 09:41 CST -0600


Booted last: 29 Dec 2014 09:14 CST -0600


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.17.0-031700-generic #201410060605 SMP Mon Oct 6 10:07:09 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:2213]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 064e:9302 Suyin Corp. 
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8188ee              95951  0 
rtl_pci                27306  1 rtl8188ee
rtlwifi                69157  2 rtl_pci,rtl8188ee
mac80211              696913  3 rtl_pci,rtlwifi,rtl8188ee
cfg80211              514757  2 mac80211,rtlwifi
hp_wmi                 14017  0 
sparse_keymap          13890  1 hp_wmi
wmi                    19379  1 hp_wmi


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
          inet addr:192.168.3.3  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::3ab1:dbff:fe0c:bfa4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6617 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5306337 (5.3 MB)  TX bytes:1239336 (1.2 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"belkin.3846"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC 'belkin.3846' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:178   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    0      0        0 wlan0
192.168.3.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search Belkin


##### nm-tool ###########################


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


- Device: wlan0  [belkin.3846] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
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
    CenturyLink0877: Infra, <MAC 'CenturyLink0877' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 8 WPA WPA2
    *belkin.3846:    Infra, <MAC 'belkin.3846' [AC1]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    HP-Print-4E-ENVY 4500 series: Infra, <MAC 'HP-Print-4E-ENVY 4500 series' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4


  IPv4 Settings:
    Address:         192.168.3.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.3.1


    DNS:             192.168.3.1


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


[[/etc/NetworkManager/system-connections/HP-Print-4E-ENVY 4500 series]] (600 root)
[connection] id=HP-Print-4E-ENVY 4500 series | type=802-11-wireless
[802-11-wireless] ssid=HP-Print-4E-ENVY 4500 series | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CenturyLink0877]] (600 root)
[connection] id=CenturyLink0877 | type=802-11-wireless
[802-11-wireless] ssid=CenturyLink0877 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/belkin.3846]] (600 root)
[connection] id=belkin.3846 | type=802-11-wireless
[802-11-wireless] ssid=belkin.3846 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: America/Chicago (based on set time zone)


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
          Current Frequency:2.422 GHz (Channel 3)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'belkin.3846' [AC1]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=4 dBm  
                    Encryption key:on
                    ESSID:"belkin.3846"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001183adaf6b
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'CenturyLink0877' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=4 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink0877"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000789c53114f
                    Extra: Last beacon: 1576ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
     lo        Interface doesn't support scanning.


                   Authentication Suites (1) : PSK


##### module infos ######################


[rtl8188ee]
filename:       /lib/modules/3.17.0-031700-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     1DE3D42A2169AD8F52BB699
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.17.0-031700-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        66:75:FB:01:47:2A:1F:12:08:1E:AF:42:B9:6D:17:94:46:AF:C5:78
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
filename:       /lib/modules/3.17.0-031700-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     2261FF61AE88330FD4ABB71
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.17.0-031700-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        66:75:FB:01:47:2A:1F:12:08:1E:AF:42:B9:6D:17:94:46:AF:C5:78
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/3.17.0-031700-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     6105E22C048121BA62ED173
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.17.0-031700-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        66:75:FB:01:47:2A:1F:12:08:1E:AF:42:B9:6D:17:94:46:AF:C5:78
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.17.0-031700-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     50BFD5A22F2717F72E28E1A
depends:        cfg80211
intree:         Y
vermagic:       3.17.0-031700-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        66:75:FB:01:47:2A:1F:12:08:1E:AF:42:B9:6D:17:94:46:AF:C5:78
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.17.0-031700-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A189C096E57D9F63A205933
depends:        
intree:         Y
vermagic:       3.17.0-031700-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        66:75:FB:01:47:2A:1F:12:08:1E:AF:42:B9:6D:17:94:46:AF:C5:78
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8188ee]
debug: 0
fwlps: Y
ips: Y
msi: Y
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
blacklist rtl8192cu


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


[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee msi=1


[/etc/modprobe.d/rtl8192ce.conf]
options rtl8192ce swenc=1 ips=0


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


[   35.088048] wlan0: deauthenticating from <MAC 'belkin.3846' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   35.122734] wlan0: authenticate with <MAC 'belkin.3846' [AC1]>
[   35.132853] wlan0: send auth to <MAC 'belkin.3846' [AC1]> (try 1/3)
[   35.135857] wlan0: authenticated
[   35.139046] wlan0: associate with <MAC 'belkin.3846' [AC1]> (try 1/3)
[   35.142761] wlan0: RX AssocResp from <MAC 'belkin.3846' [AC1]> (capab=0x411 status=0 aid=1)
[   35.142896] wlan0: associated
[   68.732351] wlan0: Connection to AP <MAC 'belkin.3846' [AC1]> lost
[   69.926722] wlan0: authenticate with <MAC 'belkin.3846' [AC1]>
[   69.945827] wlan0: send auth to <MAC 'belkin.3846' [AC1]> (try 1/3)
[   69.947680] wlan0: authenticated
[   69.949717] wlan0: associate with <MAC 'belkin.3846' [AC1]> (try 1/3)
[   69.954208] wlan0: RX AssocResp from <MAC 'belkin.3846' [AC1]> (capab=0x411 status=0 aid=1)
[   69.954334] wlan0: associated
[  356.800275] wlan0: deauthenticating from <MAC 'belkin.3846' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  361.866194] wlan0: authenticate with <MAC 'belkin.3846' [AC1]>
[  361.885284] wlan0: send auth to <MAC 'belkin.3846' [AC1]> (try 1/3)
[  361.887047] wlan0: authenticated
[  361.892783] wlan0: associate with <MAC 'belkin.3846' [AC1]> (try 1/3)
[  361.897296] wlan0: RX AssocResp from <MAC 'belkin.3846' [AC1]> (capab=0x411 status=0 aid=1)
[  361.897439] wlan0: associated
[  361.913302] wlan0: deauthenticating from <MAC 'belkin.3846' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  361.948200] wlan0: authenticate with <MAC 'belkin.3846' [AC1]>
[  361.958334] wlan0: send auth to <MAC 'belkin.3846' [AC1]> (try 1/3)
[  361.959832] wlan0: authenticated
[  361.961138] wlan0: associate with <MAC 'belkin.3846' [AC1]> (try 1/3)
[  361.965672] wlan0: RX AssocResp from <MAC 'belkin.3846' [AC1]> (capab=0x411 status=0 aid=1)
[  361.965799] wlan0: associated
[  371.055399] wlan0: Connection to AP <MAC 'belkin.3846' [AC1]> lost
[  372.229180] wlan0: authenticate with <MAC 'belkin.3846' [AC1]>
[  372.248558] wlan0: send auth to <MAC 'belkin.3846' [AC1]> (try 1/3)
[  372.250099] wlan0: authenticated
[  372.252103] wlan0: associate with <MAC 'belkin.3846' [AC1]> (try 1/3)
[  372.256011] wlan0: RX AssocResp from <MAC 'belkin.3846' [AC1]> (capab=0x411 status=0 aid=1)
[  372.256144] wlan0: associated
[  401.476160] wlan0: Connection to AP <MAC 'belkin.3846' [AC1]> lost
[  402.679165] wlan0: authenticate with <MAC 'belkin.3846' [AC1]>
[  402.698691] wlan0: send auth to <MAC 'belkin.3846' [AC1]> (try 1/3)
[  402.700322] wlan0: authenticated
[  402.703307] wlan0: associate with <MAC 'belkin.3846' [AC1]> (try 1/3)
[  402.707534] wlan0: RX AssocResp from <MAC 'belkin.3846' [AC1]> (capab=0x411 status=0 aid=1)
[  402.707660] wlan0: associated


########## wireless info END ############

---

### Post by chili555 on 2014-12-29
Ahhhh! Wonderful! We see that you have a working wireless device and driver, rtl8188ee and that is drops. If we may assume that the access point to which you are connected, belkin.3846, is yours or that you have administrative privileges, then there are some things we'd suggest. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo modprobe -r rtl8188ee
sudo modprobe rtl8188ee swenc=1 ips=0 fwlps=0
```If it helps, we'll write one quick file and make it permanent.

---

### Post by mbkwp on 2014-12-29
You are fantastic. \\:D/ I already had the IPv6 set to ignore, but never knew I could or even wanted to change the settings in the router. The internet is great for how to do that one. It has always worked in the past and even Ubuntu offerings "just worked". It is faster and seems to be hanging on for now, we'll see if it lasts but is better now than ever. Sorry, I'm no where close to a computer type person.
It seems there isn't anything close to a one size fits all fix for this but it seems that I found the right person for the job. I'll be hanging on to the Ubuntu for a while longer it seems. I'm happy enough with that.
Thank You.

---

### Post by chili555 on 2014-12-29
Glad it's working, at least for now. Please let us know how it goes. The searchers with the same device will appreciate it.

---

### Post by mbkwp on 2014-12-29
It has been over an hour and still up and running. It would have dropped out a dozen times by now before. I couldn't figure out how to change off the WPA/WPA2 setting but it seems to be a moot point right now, the others were just stumbling through the menu, but hey it didn't work right anyway and there were clear instructions that even I could follow to reset to factory defaults.
For folks in the United States, the country code is US, and yes I assume it needs to be capitalized, so replace the IS with US.
As for the last instructions, I didn't need them. I hope if this helps anyone that all the chasing was worth it. I just wish I could have stumbled on this before springing for a new machine, but the other one was over ten years old and had been helped along by a friend during the time. He finally just said to stop being a tight wad and get a modern machine. LOL
Happy New Year to all.

---

