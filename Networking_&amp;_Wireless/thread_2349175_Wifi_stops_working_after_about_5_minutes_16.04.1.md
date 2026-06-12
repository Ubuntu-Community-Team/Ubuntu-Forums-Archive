---
title: "Wifi stops working after about 5 minutes 16.04.1"
date: 2017-01-11
forum: Networking &amp; Wireless
---

### Post by john4 on 2017-01-11
Thank you all in advance.

Bought a Lenovo Ideapad 110 for the new year. I have installed 16.04.1. Everything seems to work except the wifi (ethernet works). After about 5 minutes it stops working. The wifi becomes unresponsive from the menu, and requires a full restart to work again, but to the same results. Everything I've found is for 14.04 and I do not really want to go backwards.

I've been able to update the system and get the wifi script via ethernet.

This was run after a fresh restart with wifi use only.

```


########## wireless info START ##########

Report from: 04 Jan 2017 16:17 PST -0800

Booted last: 04 Jan 2017 00:00 PST -0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
	Kernel driver in use: rtl8821ae

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:3845]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 004: ID 174f:1173 Syntek 
Bus 001 Device 003: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
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

rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              565248  2 mac80211,rtlwifi
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          inet addr:10.1.2.97  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::<IP6 'wlp1s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32393252 (32.3 MB)  TX bytes:1471078 (1.4 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"RANDR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'RANDR' [AN2]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-17 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:10   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.2.1        0.0.0.0         UG    600    0        0 wlp1s0
10.1.0.0        0.0.0.0         255.255.0.0     U     600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       760     1  0 16:11 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     RANDR
GENERAL.CON-UUID:                       9320ee21-c2ab-4d04-a405-f2aa6795b3f9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9320ee21-c2ab-4d04-a405-f2aa6795b3f9 | RANDR
IP4.ADDRESS[1]:                         10.1.2.97/16
IP4.GATEWAY:                            10.1.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.1.2.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1483661481
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.1.2.97
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 10.1.2.1
DHCP4.OPTION[19]:                       broadcast_address = 10.1.255.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 10.1.2.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.0.0
DHCP4.OPTION[25]:                       network_number = 10.1.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 10.1.2.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp1s0' [IF2]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
--                                <MAC '--' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
RANDR                             <MAC 'RANDR' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
RANDR                             <MAC 'RANDR' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
RANDR                             <MAC 'RANDR' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
DIRECT-61-HP DeskJet 3630 series  <MAC 'DIRECT-61-HP DeskJet 3630 series' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no        
randr29                           <MAC 'randr29' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2       no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/RANDR]] (600 root)
[connection] id=RANDR | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=RANDR
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp1s0    Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B9E24DCC76240A48AEEF94E
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A96EBF28EBD4603749D5EC3
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     632F2E9C01BF2AC04D0F40A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[   10.967975] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   10.967980] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   11.221553] rtl8821ae 0000:01:00.0: enabling device (0000 -> 0003)
[   11.242080] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   11.242088] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   11.287096] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.287469] rtlwifi: rtlwifi: wireless switch is on
[   12.519231] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[   26.505138] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[   26.768937] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   27.065284] r8169 0000:02:00.0 enp2s0: link down
[   27.065367] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   28.160604] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   31.200715] wlp1s0: authenticate with <MAC 'RANDR' [AN2]>
[   31.203447] wlp1s0: send auth to <MAC 'RANDR' [AN2]> (try 1/3)
[   31.206468] wlp1s0: authenticated
[   31.208035] wlp1s0: associate with <MAC 'RANDR' [AN2]> (try 1/3)
[   31.212459] wlp1s0: RX AssocResp from <MAC 'RANDR' [AN2]> (capab=0x431 status=0 aid=6)
[   31.213305] wlp1s0: associated
[   31.213354] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

########## wireless info END ############

```

Any and all help is appreciated.

J

---

### Post by chili555 on 2017-01-12
You have a few things going on here that we can address. First, let's turn off power saving in Network Manager. From the terminal:```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```Next, set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, we see this little nightmare:> SSID                              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
<snip>
RANDR                             <MAC 'RANDR' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
RANDR                             <MAC 'RANDR' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
RANDR                             <MAC 'RANDR' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  77      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
<snip>      It is a nightmare for two reasons; first, three SSIDs with the exact same name. I suspect that part of the problem is that your device attempts to roam to another instance of RANDR. I suggest that you bind Network Manager to the preferred instance like this: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

Even better, if you have administrative control over these access points, is to rename them, something like RANDR1, RANDR2, etc.

Further, although we haven't seen a scan, they have all the signs of being set to factory defaults which usually include WPA and WPA2 mixed mode and TKIP.

Again, if you have administrative privileges, WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

After these changes, please report back.

---

### Post by john4 on 2017-01-20
Thank you for the reply. I will give these a try.

Also on the network side I am running a Ubiquiti Unifi network.

John

---

### Post by john4 on 2017-02-14
I apologize for the late response, work got crazy and I was called out of town for a couple weeks.

I ran everything per your response on the laptop. The wifi still goes goes out, but this time I can turn the wifi off and back on, and it will reconnect for a while longer. Then repeat.

I checked my network's wifi settings and the only thing that I changed was moving it to 20 MHz. Everything else was already where you suggested it be.

Here is the new network read out:

```


########## wireless info START ##########

Report from: 14 Feb 2017 17:08 PST -0800

Booted last: 14 Feb 2017 00:00 PST -0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8821AE 802.11ac PCIe Wireless Network Adapter [10ec:8821]
	Subsystem: Lenovo RTL8821AE 802.11ac PCIe Wireless Network Adapter [17aa:a814]
	Kernel driver in use: rtl8821ae

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Lenovo RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [17aa:3845]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 005: ID 174f:1173 Syntek 
Bus 001 Device 004: ID 0bda:0821 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

rtl8821ae             225280  0
btcoexist              53248  1 rtl8821ae
rtl_pci                28672  1 rtl8821ae
rtlwifi                77824  2 rtl_pci,rtl8821ae
mac80211              737280  3 rtl_pci,rtlwifi,rtl8821ae
cfg80211              565248  2 mac80211,rtlwifi
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          inet addr:10.1.2.97  Bcast:10.1.255.255  Mask:255.255.0.0
          inet6 addr: fe80::52cc:d6b6:6343:a396/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1751 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1727407 (1.7 MB)  TX bytes:175916 (175.9 KB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlp1s0    IEEE 802.11abgn  ESSID:"RANDR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'RANDR' [AN1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-17 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.1.2.1        0.0.0.0         UG    600    0        0 wlp1s0
10.1.0.0        0.0.0.0         255.255.0.0     U     600    0        0 wlp1s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp1s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       746     1  0 17:06 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8821AE 802.11ac PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8821ae
GENERAL.DRIVER-VERSION:                 4.4.0-31-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.3/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     RANDR
GENERAL.CON-UUID:                       9320ee21-c2ab-4d04-a405-f2aa6795b3f9
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     72 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9320ee21-c2ab-4d04-a405-f2aa6795b3f9 | RANDR
IP4.ADDRESS[1]:                         10.1.2.97/16
IP4.GATEWAY:                            10.1.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.1.2.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1487207226
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 10.1.2.97
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 10.1.2.1
DHCP4.OPTION[19]:                       broadcast_address = 10.1.255.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 10.1.2.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.0.0
DHCP4.OPTION[25]:                       network_number = 10.1.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 10.1.2.1
IP6.ADDRESS[1]:                         fe80::52cc:d6b6:6343:a396/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:02.4/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                              BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
RANDR                             <MAC 'RANDR' [AN1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
--                                <MAC '--' [AN2]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       no        
RANDR                             <MAC 'RANDR' [AN3]>  Infra  1     2412 MHz  54 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2       no        
RANDR                             <MAC 'RANDR' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
DIRECT-61-HP DeskJet 3630 series  <MAC 'DIRECT-61-HP DeskJet 3630 series' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       no        
randr29                           <MAC 'randr29' [AN6]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2       no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/RANDR]] (600 root)
[connection] id=RANDR | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=RANDR
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US: DFS-FCC
	(2402 - 2472 @ 40), (N/A, 30), (N/A)
	(5170 - 5250 @ 80), (N/A, 17), (N/A)
	(5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
	(5490 - 5730 @ 160), (N/A, 23), (0 ms), DFS
	(5735 - 5835 @ 80), (N/A, 30), (N/A)
	(57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlp1s0    Interface doesn't support scanning : Device or resource busy

##### module infos ######################

[rtl8821ae]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
firmware:       rtlwifi/rtl8821aefw.bin
description:    Realtek 8821ae 802.11ac PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B9E24DCC76240A48AEEF94E
depends:        rtlwifi,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     A96EBF28EBD4603749D5EC3
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/4.4.0-31-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     632F2E9C01BF2AC04D0F40A
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     2FFAEED0245CA1D97FE1E44
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-31-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-31-generic SMP mod_unload modversions 
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

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

##### dmesg #############################

[   13.339444] rtl8821ae 0000:01:00.0: enabling device (0000 -> 0003)
[   13.379500] rtl8821ae: Using firmware rtlwifi/rtl8821aefw.bin
[   13.379509] rtl8821ae: Using firmware rtlwifi/rtl8821aefw_wowlan.bin
[   13.464500] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.464748] rtlwifi: rtlwifi: wireless switch is on
[   13.812680] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000a lmp_ver=06 lmp_subver=8821
[   13.812685] Bluetooth: hci0: rtl: loading rtl_bt/rtl8821a_fw.bin
[   15.088544] rtl8821ae 0000:01:00.0 wlp1s0: renamed from wlan0
[   26.727096] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[   26.985367] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   27.365287] r8169 0000:02:00.0 enp2s0: link down
[   27.365371] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   28.433283] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   31.396125] wlp1s0: authenticate with <MAC 'RANDR' [AN1]>
[   31.399384] wlp1s0: send auth to <MAC 'RANDR' [AN1]> (try 1/3)
[   31.404932] wlp1s0: authenticated
[   31.408170] wlp1s0: associate with <MAC 'RANDR' [AN1]> (try 1/3)
[   31.412785] wlp1s0: RX AssocResp from <MAC 'RANDR' [AN1]> (capab=0x431 status=0 aid=3)
[   31.414372] wlp1s0: associated
[   31.414421] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

########## wireless info END ############

```

Let me know what you think.

Thank you again.

John

---

### Post by chili555 on 2017-02-15
Let's try turning off power saving at the driver level:```
sudo -i
echo "options rtl8821ae ips=0"  >  /etc/modprobe.d/rtl8821ae.conf
exit
```And also in Network Manager:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```After a reboot, let us know if there is any improvement.

---

