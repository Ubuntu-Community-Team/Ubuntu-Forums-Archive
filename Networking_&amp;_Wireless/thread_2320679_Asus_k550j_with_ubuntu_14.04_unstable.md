---
title: "Asus k550j with ubuntu 14.04 unstable"
date: 2016-04-16
forum: Networking &amp; Wireless
---

### Post by luis77 on 2016-04-16
Hi.

I own a Asus K550JK-DM013, with ubuntu 14.04 LTS currently unstable.
The wireless connection is very unstable, and often crashes. The only solution I found for such problem is to run "sudo service network-manager restart" to temporarily fix it.

I saw from other posts you'd may require wireless-info-script output, so here it goes 

```


########## wireless info START ##########


Report from: 16 Apr 2016 14:17 WEST +0100


Booted last: 16 Apr 2016 12:41 WEST +0100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: AzureWave Device [1a3b:2161]
	Kernel driver in use: rtl8821ae


04:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
	Kernel driver in use: r8169


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:57b4 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 13d3:3414 IMC Networks 
Bus 001 Device 002: ID 3938:1031  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


asus_nb_wmi            24576  0 
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0 
rtl8821ae             225280  0 
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              741376  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              552960  2 mac80211,rtlwifi
video                  40960  2 i915,asus_wmi
wmi                    20480  2 mxm_wmi,asus_wmi


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
          inet addr:192.168.1.91  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1504170 errors:0 dropped:0 overruns:0 frame:0
          TX packets:832815 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2026319677 (2.0 GB)  TX bytes:180373631 (180.3 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"MEO-9BDD77"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'MEO-9BDD77' [AN10]>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:647   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### network managers ##################


Installed:


	NetworkManager


Running:


root      3170     1  0 12:50 ?        00:00:01 NetworkManager


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


- Device: wlan0  [MEO-9BDD77] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8821ae
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    Vodafone-10C1EE: Infra, <MAC 'Vodafone-10C1EE' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    NOS-1B80:        Infra, <MAC 'NOS-1B80' [AN2]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    DIRECT-AP[TV][LG]42LB5800-ZM: Infra, <MAC 'DIRECT-AP[TV][LG]42LB5800-ZM' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2
    Vodafone-A8D84F: Infra, <MAC 'Vodafone-A8D84F' [AN4]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    ZON-CC60:        Infra, <MAC 'ZON-CC60' [AN5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    henrijosh:       Infra, <MAC 'henrijosh' [AN6]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    MEO-WiFi:        Infra, <MAC 'MEO-WiFi' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN8]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 47
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN9]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 60
    *MEO-9BDD77:     Infra, <MAC 'MEO-9BDD77' [AN10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
    dlink-2373:      Infra, <MAC 'dlink-2373' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    ZON-BC90:        Infra, <MAC 'ZON-BC90' [AN12]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN13]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 47
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN15]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 45
    DrayTek-vilagaia:Infra, <MAC 'DrayTek-vilagaia:Infra, <MAC address>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44' [AN16]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN17]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 40
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN18]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 34
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN19]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27
    NOS-5E80:        Infra, <MAC 'NOS-5E80' [AN20]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    FON_ZON_FREE_INTERNET: Infra, <MAC 'FON_ZON_FREE_INTERNET' [AN21]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 47
    Vodafone-A8D84F: Infra, <MAC 'Vodafone-A8D84F' [AN22]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    ZON-4C70:        Infra, <MAC 'ZON-4C70' [AN23]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    Vodafone-C3E6F4: Infra, <MAC 'Vodafone-C3E6F4' [AN24]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Vodafone-EF5F40: Infra, <MAC 'Vodafone-EF5F40' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    ZON-DC80:        Infra, <MAC 'ZON-DC80' [AN26]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    MEO-24A1D9:      Infra, <MAC 'MEO-24A1D9' [AN27]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Vodafone-9299AF: Infra, <MAC 'Vodafone-9299AF' [AN28]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    ZON-4E90:        Infra, <MAC 'ZON-4E90' [AN29]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Vodafone-07DDDB: Infra, <MAC 'Vodafone-07DDDB' [AN30]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    MEO-WiFi:        Infra, <MAC 'MEO-WiFi' [AN31]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20
    Vodafone-DB6D31: Infra, <MAC 'Vodafone-DB6D31' [AN32]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Vodafone Casa:   Infra, <MAC 'Vodafone Casa' [AN33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WEP


  IPv4 Settings:
    Address:         192.168.1.91
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


[[/etc/NetworkManager/system-connections/MEO-9BDD77]] (600 root)
[connection] id=MEO-9BDD77 | type=802-11-wireless
[802-11-wireless] ssid=MEO-9BDD77 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Lisbon (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


wlan0     Interface doesn't support scanning : Device or resource busy


lo        Interface doesn't support scanning.


##### module infos ######################


[rtl8821ae]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     A376316AC0354FEE740506F
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
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
parm:           int_clear:Set to 0 to disable interrupt clear before set (default 1)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512


[rtlwifi]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     867B4080247A86ABBA59D17
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8821ae]
debug: 0
disable_watchdog: N
fwlps: Y
int_clear: Y
ips: Y
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8821 (rtl8821ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[ 1764.963461] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[ 1764.963467] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[ 1764.963491] bluetooth hci0: Direct firmware load for rtl_bt/rtl8821a_fw.bin failed with error -2
[ 1764.963494] Bluetooth: hci0: Failed to load rtl_bt/rtl8821a_fw.bin
[ 1765.407236] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1765.437547] r8169 0000:04:00.1 eth0: link down
[ 1765.437603] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1768.323735] wlan0: authenticate with <MAC 'MEO-9BDD77' [AN10]>
[ 1768.324129] wlan0: send auth to <MAC 'MEO-9BDD77' [AN10]> (try 1/3)
[ 1768.325654] wlan0: authenticated
[ 1768.326517] wlan0: associate with <MAC 'MEO-9BDD77' [AN10]> (try 1/3)
[ 1768.330076] wlan0: RX AssocResp from <MAC 'MEO-9BDD77' [AN10]> (capab=0x11 status=0 aid=5)
[ 1768.331794] wlan0: associated
[ 1768.331814] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

Any help would be highly appreciated.

---

### Post by fabioepneves on 2016-10-01
I'm having the exact same problem.
My laptop is a Asus K550JX-DM229.
Wireless card is a Realtek 8821AE.
I have tried many different Linux distros and kernels, and they all have the same problem.
I'm stuck with Windows.
Does anyone have a solution?

---

### Post by Hadaka on 2016-10-01
Hello fabioepneves, you have posted on someone's old thread, you cannot mark
the thread SOLVED in the event a solution is found for your wifi driver problem. 
Please start your own thread for better resolution of your issue. Please include
the output of....*Copy and Paste*
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
*Note This command creates a file in YOUR home directory named **wireless-info.txt**. Please copy and paste
the** wireless-info.txt** file to YOUR new thread.
thanks.

---

