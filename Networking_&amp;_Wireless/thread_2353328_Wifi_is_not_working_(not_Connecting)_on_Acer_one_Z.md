---
title: "Wifi is not working (not Connecting) on Acer one Z1402-32F2  on Ubunto 16.10"
date: 2017-02-20
forum: Networking &amp; Wireless
---

### Post by odel on 2017-02-20
Okay im new to Ubuntu. My wifi is not working so I follow this : [https://forums.linuxmint.com/viewtopic.php?t=208434](https://forums.linuxmint.com/viewtopic.php?t=208434) and installed the driver but it did work. Then I boot my computer using 14.4 LTS. Then wifi worked , but in 16.10 (which I am using) wifi is not working. Can anyone help me , 

Driver I found from mint forum : 
 
[https://github.com/lwfinger/rtl8723bu](https://github.com/lwfinger/rtl8723bu)

My hardware :: 

```
Bus 002 Device 002: ID 0bda:b720 Realtek Semiconductor Corp. 


CPU:       Dual core Intel Core i3-5005U (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 7981
           clock speeds: max: 1900 MHz 1: 1900 MHz 2: 1899 MHz 3: 1900 MHz
           4: 1899 MHz
Graphics:  Card: Intel HD Graphics 5500 bus-ID: 00:02.0
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2)
           GLX Version: 3.0 Mesa 12.0.3 Direct Rendering: Yes
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Broadwell-U Audio Controller
           driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.8.0-37-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
```

Thank you :D

---

### Post by wildmanne39 on 2017-02-20
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by odel on 2017-02-22
Sorry I tried to paste the code here but it is to large  (276928 lines)  and also in Ubuntu Pastebin but I couldn't. So I uploaded the text file  to Google Drive. The link is below.
[https://drive.google.com/file/d/0B7xGWjXyxh6Ha3R0YVFJWllxUms/view?usp=sharing](https://drive.google.com/file/d/0B7xGWjXyxh6Ha3R0YVFJWllxUms/view?usp=sharing)

Thank you.

---

### Post by wildmanne39 on 2017-02-22
I am not sure what happened but when I clicked on the link the file did not display properly and it crashed my browser and that has never happened in the last ten years.

Please put it here:
[http://pastebin.com/](http://pastebin.com/)
You should not have any problems doing so because I use that site all the time.
Thanks

---

### Post by jeremy31 on 2017-02-22
Hi wildmanne39
It seems that odel has a bunch of source code in the /etc/pm directory.  Here is a cleaned up version
```
########## wireless info START ##########

Report from: 22 Feb 2017 16:15 EST -0500

Booted last: 22 Feb 2017 00:00 EST -0500

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.10
Release:	16.10
Codename:	yakkety

##### kernel ############################

Linux 4.8.0-39-generic #42-Ubuntu SMP Mon Feb 20 11:47:27 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
	Subsystem: Device [1d05:1011]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 5986:065e Acer, Inc 
Bus 002 Device 003: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 002: ID 0bda:b720 Realtek Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

snd_soc_rt5640        118784  0
rtl8xxxu              126976  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
mac80211              757760  1 rtl8xxxu
snd_soc_core          233472  2 snd_soc_ssm4567,snd_soc_rt5640
cfg80211              581632  1 mac80211
snd_pcm               110592  7 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_core
wmi                    16384  0

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.2.100  netmask 255.255.255.0  broadcast 192.168.2.255
        inet6 fe80::e43:cf8d:977a:5b91  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 21622  bytes 19136385 (19.1 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16587  bytes 2610784 (2.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 25389  bytes 1767615 (1.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 25389  bytes 1767615 (1.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx7cc7095a7e46: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1  bytes 135 (135.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1  bytes 155 (155.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0f1  no wireless extensions.

wlx7cc7095a7e46  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 enp2s0f1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0f1
192.168.2.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0f1

##### resolv.conf #######################

nameserver 127.0.1.1
search home

##### network managers ##################

Installed:

	NetworkManager

Running:

root       992     1  0 14:38 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0f1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:02:00.1/net/enp2s0f1
GENERAL.IP-IFACE:                       enp2s0f1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6ed690d7-cf0a-3f53-bc02-f682010ac555
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6ed690d7-cf0a-3f53-bc02-f682010ac555 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.2.100/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
IP4.DNS[2]:                             208.67.222.222
IP4.DNS[3]:                             208.67.220.220
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.2.1
DHCP4.OPTION[5]:                        ip_address = 192.168.2.100
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.2.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        time_offset = 0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_rebinding_time = 529200
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.2.1
DHCP4.OPTION[17]:                       dhcp_renewal_time = 302400
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       domain_name = home
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       expiry = 1488397096
DHCP4.OPTION[22]:                       host_name = punsith-One-Z1402
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[27]:                       network_number = 192.168.2.0
DHCP4.OPTION[28]:                       requested_domain_search = 1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       ntp_servers = 192.168.2.1
DHCP4.OPTION[31]:                       dhcp_lease_time = 604800
DHCP4.OPTION[32]:                       requested_host_name = 1
DHCP4.OPTION[33]:                       next_server = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::e43:cf8d:977a:5b91/64
IP6.GATEWAY:                            
IP6.DNS[1]:                             2620:0:ccc::2
IP6.DNS[2]:                             2620:0:ccd::2

GENERAL.DEVICE:                         wlx7cc7095a7e46
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek
GENERAL.PRODUCT:                        802.11n WLAN Adapter
GENERAL.DRIVER:                         rtl8xxxu
GENERAL.DRIVER-VERSION:                 4.8.0-39-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb2/2-1/2-1:1.2/net/wlx7cc7095a7e46
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3e001401-c299-4326-8855-fe6ff664e7fc | e46f1399e165

SSID          BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
e46f1399e165  <MAC 'e46f1399e165' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA2      no        

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

[[/etc/NetworkManager/system-connections/NETGEAR73]] (600 root)
[connection] id=NETGEAR73 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR73
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/e46f1399e165]] (600 root)
[connection] id=e46f1399e165 | type=wifi | permissions=user:punsith:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=e46f1399e165
[ipv4] method=disabled
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FireHotspot]] (600 root)
[connection] id=FireHotspot | type=wifi | permissions=user:punsith:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=FireHotspot
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/NETGEAR96]] (600 root)
[connection] id=NETGEAR96 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=NETGEAR96
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

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

lo        no frequency information.

enp2s0f1  no frequency information.

wlx7cc7095a7e46  14 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

enp2s0f1  Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlx7cc7095a7e46  Scan completed :
          Cell 01 - Address: <MAC 'e46f1399e165' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"e46f1399e165"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000113cb9d06e
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8xxxu]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     59F02B6CF781E1985E0D1CE
depends:        mac80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)

[mac80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

grep: /sys/module/rtl8xxxu/parameters/debug: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_pages: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_aggregation: Permission denied
grep: /sys/module/rtl8xxxu/parameters/dma_agg_timeout: Permission denied
grep: /sys/module/rtl8xxxu/parameters/ht40_2g: Permission denied
[rtl8xxxu]

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory
##### udev rules ########################

##### dmesg #############################

[   19.379157] usb 2-1: rtl8xxxu: Loading firmware rtlwifi/rtl8723bu_nic.bin
[   20.439584] Bluetooth: hci0: rtl: examining hci_ver=06 hci_rev=000b lmp_ver=06 lmp_subver=8723
[   20.439587] Bluetooth: hci0: rtl: loading rtl_bt/rtl8723b_fw.bin
[   21.876442] rtl8xxxu 2-1:1.2 wlx7cc7095a7e46: renamed from wlan0
[   40.393958] IPv6: ADDRCONF(NETDEV_UP): wlx7cc7095a7e46: link is not ready (repeated 3 times)
[ 4713.796002] wlx7cc7095a7e46: authenticate with <MAC 'e46f1399e165' [AC1]>
[ 4713.799688] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4714.003742] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 2/3)
[ 4714.207709] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 3/3)
[ 4714.209205] wlx7cc7095a7e46: authenticated
[ 4714.211709] wlx7cc7095a7e46: associate with <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4714.415718] wlx7cc7095a7e46: associate with <MAC 'e46f1399e165' [AC1]> (try 2/3)
[ 4714.619796] wlx7cc7095a7e46: associate with <MAC 'e46f1399e165' [AC1]> (try 3/3)
[ 4714.823782] wlx7cc7095a7e46: association with <MAC 'e46f1399e165' [AC1]> timed out
[ 4716.008343] wlx7cc7095a7e46: authenticate with <MAC 'e46f1399e165' [AC1]>
[ 4716.013222] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4716.219871] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 2/3)
[ 4716.423929] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 3/3)
[ 4716.635916] wlx7cc7095a7e46: authentication with <MAC 'e46f1399e165' [AC1]> timed out
[ 4718.212428] wlx7cc7095a7e46: authenticate with <MAC 'e46f1399e165' [AC1]>
[ 4718.216226] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4718.217644] wlx7cc7095a7e46: authenticated
[ 4718.220046] wlx7cc7095a7e46: associate with <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4718.424686] wlx7cc7095a7e46: associate with <MAC 'e46f1399e165' [AC1]> (try 2/3)
[ 4718.628057] wlx7cc7095a7e46: associate with <MAC 'e46f1399e165' [AC1]> (try 3/3)
[ 4718.832127] wlx7cc7095a7e46: association with <MAC 'e46f1399e165' [AC1]> timed out
[ 4720.916631] wlx7cc7095a7e46: authenticate with <MAC 'e46f1399e165' [AC1]>
[ 4720.920459] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4721.124305] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 2/3)
[ 4721.328308] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 3/3)
[ 4721.532345] wlx7cc7095a7e46: authentication with <MAC 'e46f1399e165' [AC1]> timed out
[ 4733.661737] wlx7cc7095a7e46: authenticate with <MAC 'e46f1399e165' [AC1]>
[ 4733.665886] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4733.869413] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 2/3)
[ 4734.073452] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 3/3)
[ 4734.277505] wlx7cc7095a7e46: authentication with <MAC 'e46f1399e165' [AC1]> timed out
[ 4749.531289] wlx7cc7095a7e46: authenticate with <MAC 'e46f1399e165' [AC1]>
[ 4749.535695] wlx7cc7095a7e46: send auth to <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4749.541661] wlx7cc7095a7e46: authenticated
[ 4749.542739] wlx7cc7095a7e46: associate with <MAC 'e46f1399e165' [AC1]> (try 1/3)
[ 4749.549746] wlx7cc7095a7e46: RX AssocResp from <MAC 'e46f1399e165' [AC1]> (capab=0x411 status=0 aid=3)
[ 4749.550293] usb 2-1: rtl8xxxu_bss_info_changed: HT supported
[ 4749.550819] wlx7cc7095a7e46: associated
[ 4749.550867] IPv6: ADDRCONF(NETDEV_CHANGE): wlx7cc7095a7e46: link becomes ready
[ 4749.551251] usb 2-1: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_START
[ 4759.556812] wlx7cc7095a7e46: deauthenticating from <MAC 'e46f1399e165' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4759.556885] usb 2-1: rtl8xxxu_ampdu_action: IEEE80211_AMPDU_RX_STOP
[ 4766.930641] IPv6: ADDRCONF(NETDEV_UP): wlx7cc7095a7e46: link is not ready

########## wireless info END ############
```

---

### Post by odel on 2017-02-22
Thank you for the replay but  [http://pastebin.com/](http://pastebin.com/) asked for a pro version to because text is to large. But  [**[COLOR=#C61919][B]jeremy31**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1924242") cleaned up the code ( thank you[ jeremy31 ) . ]("https://ubuntuforums.org/member.php?u=1924242")

---

### Post by odel on 2017-02-22
Thank you very much :D  [**[COLOR=#C61919][B]jeremy31**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1924242")

---

### Post by wildmanne39 on 2017-02-22
I am researching this device but it may take sometime, a lot of distractions at the moment.

---

### Post by odel on 2017-02-22
Thank you very much [**[COLOR=#C61919][B]wildmanne39**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=508533") :D :D

---

### Post by wildmanne39 on 2017-02-22
Please do:
```
echo "blacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then:
```
git clone https://github.com/lwfinger/rtl8723bu.git
cd rtl8723bu
make
sudo make install
sudo modprobe -v 8723bu
```
Watch for errors, warning are okay.

Thanks Jeremy31!:)

---

### Post by odel on 2017-02-22
[  						 							]("https://ubuntuforums.org/member.php?u=1924242")[**[COLOR=#C61919][B]jeremy31**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1924242") and  [URL="https://ubuntuforums.org/member.php?u=508533"][B][COLOR=#C61919][B]wildmanne39 
.
[/B][/COLOR][/B][/URL]Thank you it worked without errors Wifi and BT broth are working now.
Wifi adaper is showing twice but it is doesn't matter. Thank you again for help and your time.

---

### Post by wildmanne39 on 2017-02-22
Your welcome!
Enjoy!

---

### Post by wildmanne39 on 2017-02-22
When the kernel is upgraded you will have to recompile the driver:
```
cd rtl8723bu
make clean
make
sudo make install
sudo modprobe -v 8723bu
```

---

### Post by odel on 2017-05-13
Thanks again I just use it :):)

---

