---
title: "Installed Ubuntu but no wifi! Tried everything."
date: 2017-04-15
forum: Networking &amp; Wireless
---

### Post by techsupport-hotmail on 2017-04-15
Help! I've done a fresh install of Ubuntu on a notebook but I got no net connection. The icon at the top right tells me I'm connected and it's the correct password for my wifi but I can't log in to nothing or use anything that requires a net connection. Any ideas? Please keep things simple as I'm fairly new to Ubuntu.
Thanks.

---

### Post by howefield on 2017-04-15
Thread moved to the "*Networking & Wireless*" forum for a better fit.

---

### Post by wildmanne39 on 2017-04-15
Click on the wireless script in my signature and follow the directions for running it and posting the link created to pastebin here, which is where the file will be posted.

---

### Post by techsupport-hotmail on 2017-04-15
Thanks for the info but this notebook don't have anything to be able to connect to a wired connection. Any other ideas I can try? Feels like a losing battle

---

### Post by wildmanne39 on 2017-04-15
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.

If you look on the page where the wireless script is there is a link to directions to run it without an internet connection but the commands above should work too.
Thank you

---

### Post by techsupport-hotmail on 2017-04-15
Thanks for getting back to me. I'm unsure how I can paste any results on here because I cannot get no internet on the notebook which Ubuntu is on as I'm having to post these messages via my mobile phone.

---

### Post by wildmanne39 on 2017-04-15
My fault, I was not clear enough, if you have internet access on another computer copy the output from the commands to a flash drive, then use the other computer to post the output here, or you may be able to use your cell phone to tether an internet connection on your ubuntu computer, which I have done before and the run the wireless script and post the results to pastebin as the directions say to on the wireless script page.
Thanks

---

### Post by techsupport-hotmail on 2017-04-16
Here's pastebin  that you asked for. 
```
########## wireless info START ##########

Report from: 16 Apr 2017 10:38 BST +0100

Booted last: 16 Apr 2017 00:00 BST +0100

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 17.04
Release:	17.04
Codename:	zesty

##### kernel ############################

Linux 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]
	Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 002: ID 05c8:036e Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl8723be              90112  0
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                73728  2 rtl_pci,rtl8723be
mac80211              782336  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              602112  2 mac80211,rtlwifi
snd_soc_rt5645        147456  0
snd_soc_rt5640        118784  0
snd_soc_rl6231         16384  2 snd_soc_rt5640,snd_soc_rt5645
snd_soc_core          233472  3 snd_soc_rt5640,snd_soc_rt5645,snd_soc_sst_mfld_platform
snd_pcm               102400  9 snd_hda_intel,snd_hda_codec,snd_pcm_dmaengine,snd_hda_core,snd_soc_rt5640,snd_hda_codec_hdmi,snd_soc_rt5645,snd_soc_sst_mfld_platform,snd_soc_core
wmi                    16384  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF1]> brd <MAC address>
    inet 192.168.43.181/24 brd 192.168.43.255 scope global dynamic wlp1s0
       valid_lft 3381sec preferred_lft 3381sec
    inet6 fe80::6220:63db:8f2a:3374/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:"AndroidHotspot3999"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'AndroidHotspot3999' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-8 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

##### route #############################

default via 192.168.43.1 dev wlp1s0 proto static metric 600 
169.254.0.0/16 dev wlp1s0 scope link metric 1000 
192.168.43.0/24 dev wlp1s0 proto kernel scope link src 192.168.43.181 metric 600 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

	NetworkManager

Running:

root      2073     1  0 10:13 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8723BE PCIe Wireless Network Adapter
GENERAL.DRIVER:                         rtl8723be
GENERAL.DRIVER-VERSION:                 4.10.0-19-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF1]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     AndroidHotspot3999
GENERAL.CON-UUID:                       b0aad1ce-2ede-406e-9ebc-37db43bc5c63
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/7
GENERAL.METERED:                        yes (guessed)
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   b0aad1ce-2ede-406e-9ebc-37db43bc5c63 | AndroidHotspot3999
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   5db9f132-2d03-4fb8-b0dd-a92eb80ef748 | VodafoneConnect01823618
IP4.ADDRESS[1]:                         192.168.43.181/24
IP4.GATEWAY:                            192.168.43.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.43.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.43.1
DHCP4.OPTION[5]:                        ip_address = 192.168.43.181
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.43.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.43.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.43.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1492338865
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = john-HP-Stream-Notebook-PC-11
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.43.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.43.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::6220:63db:8f2a:3374/64
IP6.GATEWAY:                            

SSID                     BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
VodafoneConnect01823618  <MAC 'VodafoneConnect01823618' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
AndroidHotspot3999       <MAC 'AndroidHotspot3999' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2       yes     * 
VM159673-2G              <MAC 'VM159673-2G' [AC4]>  Infra  6     2437 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
SKY742AF                 <MAC 'SKY742AF' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2       no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=0

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/AndroidHotspot3999]] (600 root)
[connection] id=AndroidHotspot3999 | type=wifi | permissions=user:john:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=AndroidHotspot3999
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VFD 1400]] (600 root)
[connection] id=VFD 1400 | type=wifi | permissions=user:john:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=VFD 1400
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/VodafoneConnect01823618]] (600 root)
[connection] id=VodafoneConnect01823618 | type=wifi | permissions=user:john:;
[wifi] mac-address=<MAC 'wlp1s0' [IF1]> | mac-address-blacklist= | ssid=VodafoneConnect01823618
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

global
country 00: DFS-UNSET
	(2402 - 2472 @ 40), (N/A, 20), (N/A)
	(2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
	(5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
	(5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
	(5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

wlp1s0    13 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'AndroidHotspot3999' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-12 dBm  
                    Encryption key:on
                    ESSID:"AndroidHotspot3999"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000f1571c4
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SKY742AF' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"SKY742AF"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000004fb69158f95
                    Extra: Last beacon: 4400ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'VodafoneConnect01823618' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"VodafoneConnect01823618"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000174eeaebe16
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'VM159673-2G' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"VM159673-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000595d60e4
                    Extra: Last beacon: 8160ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     8A4042E8F447BFEE8F45BA5
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
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
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)
parm:           ant_sel:Set to 1 or 2 to force antenna number (default 0)
 (int)

[rtl8723_common]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     B06F4AE01E9561133D82E7E
depends:        
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 

[rtl_pci]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B93F82B28F7945C22514E4D
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 

[rtlwifi]
filename:       /lib/modules/4.10.0-19-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     884DE3F31278351A45DA409
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6FCDB39CB1DCCA0C9A450B2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0ADFC23D0B6BCD6916160E7
depends:        
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
ant_sel: 0
debug: 0
disable_watchdog: N
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

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   22.917740] wlp1s0: authenticate with <MAC 'VodafoneConnect01823618' [AC3]>
[   22.949922] wlp1s0: send auth to <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[   22.952543] wlp1s0: authenticated
[   22.957342] wlp1s0: associate with <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[   22.961598] wlp1s0: RX AssocResp from <MAC 'VodafoneConnect01823618' [AC3]> (capab=0x411 status=0 aid=2)
[   22.962185] wlp1s0: associated
[   22.962261] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  150.125970] wlp1s0: deauthenticating from <MAC 'VodafoneConnect01823618' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  150.575652] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[  152.622563] wlp1s0: authenticate with <MAC 'VodafoneConnect01823618' [AC3]>
[  152.644843] wlp1s0: send auth to <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[  152.647479] wlp1s0: authenticated
[  152.649359] wlp1s0: associate with <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[  152.654426] wlp1s0: RX AssocResp from <MAC 'VodafoneConnect01823618' [AC3]> (capab=0x411 status=0 aid=2)
[  152.655368] wlp1s0: associated
[  152.655439] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  424.235014] wlp1s0: deauthenticating from <MAC 'VodafoneConnect01823618' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  445.781596] wlp1s0: authenticate with <MAC 'AndroidHotspot3999' [AC1]>
[  445.802401] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[  445.805374] wlp1s0: authenticated
[  445.808994] wlp1s0: associate with <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[  445.813514] wlp1s0: RX AssocResp from <MAC 'AndroidHotspot3999' [AC1]> (capab=0x411 status=0 aid=1)
[  445.814458] wlp1s0: associated
[  473.096078] wlp1s0: deauthenticating from <MAC 'AndroidHotspot3999' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  500.429244] wlp1s0: authenticate with <MAC 'AndroidHotspot3999' [AC1]>
[  500.445572] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[  500.449299] wlp1s0: authenticated
[  500.453104] wlp1s0: associate with <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[  500.457617] wlp1s0: RX AssocResp from <MAC 'AndroidHotspot3999' [AC1]> (capab=0x411 status=0 aid=1)
[  500.458211] wlp1s0: associated
[  546.059602] wlp1s0: deauthenticating from <MAC 'AndroidHotspot3999' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  547.031220] wlp1s0: authenticate with <MAC 'VodafoneConnect01823618' [AC3]>
[  547.053159] wlp1s0: send auth to <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[  547.055968] wlp1s0: authenticated
[  547.060995] wlp1s0: associate with <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[  547.065655] wlp1s0: RX AssocResp from <MAC 'VodafoneConnect01823618' [AC3]> (capab=0x411 status=0 aid=2)
[  547.066256] wlp1s0: associated
[ 1232.154557] wlp1s0: deauthenticating from <MAC 'VodafoneConnect01823618' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1258.377476] wlp1s0: authenticate with <MAC 'AndroidHotspot3999' [AC1]>
[ 1258.392870] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[ 1258.395957] wlp1s0: authenticated
[ 1258.401578] wlp1s0: associate with <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[ 1258.406488] wlp1s0: RX AssocResp from <MAC 'AndroidHotspot3999' [AC1]> (capab=0x411 status=0 aid=1)
[ 1258.407082] wlp1s0: associated
[ 1304.069612] wlp1s0: deauthenticating from <MAC 'AndroidHotspot3999' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1305.061206] wlp1s0: authenticate with <MAC 'VodafoneConnect01823618' [AC3]>
[ 1305.077813] wlp1s0: send auth to <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[ 1305.081899] wlp1s0: authenticated
[ 1305.085565] wlp1s0: associate with <MAC 'VodafoneConnect01823618' [AC3]> (try 1/3)
[ 1305.090081] wlp1s0: RX AssocResp from <MAC 'VodafoneConnect01823618' [AC3]> (capab=0x411 status=0 aid=2)
[ 1305.091413] wlp1s0: associated
[ 1316.162124] wlp1s0: deauthenticating from <MAC 'VodafoneConnect01823618' [AC3]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1317.141162] wlp1s0: authenticate with <MAC 'AndroidHotspot3999' [AC1]>
[ 1317.157607] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[ 1317.161331] wlp1s0: authenticated
[ 1317.169208] wlp1s0: associate with <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[ 1317.173877] wlp1s0: RX AssocResp from <MAC 'AndroidHotspot3999' [AC1]> (capab=0x411 status=0 aid=1)
[ 1317.174473] wlp1s0: associated
[ 1344.469315] wlp1s0: deauthenticated from <MAC 'AndroidHotspot3999' [AC1]> (Reason: 3=DEAUTH_LEAVING)
[ 1345.574431] wlp1s0: authenticate with <MAC 'AndroidHotspot3999' [AC1]>
[ 1345.594936] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[ 1345.697473] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 2/3)
[ 1345.801486] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 3/3)
[ 1345.905074] wlp1s0: authentication with <MAC 'AndroidHotspot3999' [AC1]> timed out
[ 1359.965465] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[ 1394.259389] wlp1s0: authenticate with <MAC 'AndroidHotspot3999' [AC1]>
[ 1394.280020] wlp1s0: send auth to <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[ 1394.283043] wlp1s0: authenticated
[ 1394.285073] wlp1s0: associate with <MAC 'AndroidHotspot3999' [AC1]> (try 1/3)
[ 1394.290044] wlp1s0: RX AssocResp from <MAC 'AndroidHotspot3999' [AC1]> (capab=0x411 status=0 aid=1)
[ 1394.291339] wlp1s0: associated
[ 1394.291421] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

########## wireless info END ############
```

---

### Post by wildmanne39 on 2017-04-16
Let's set your settings in network manager to match the screenshots:
Then restart network manager:
```
sudo systemctl restart NetworkManager.service
```
or just reboot.

There are a few other things we can change but I would like to do the above first since this is a new release so we can isolate the issues a little better.
Thanks

---

### Post by techsupport-hotmail on 2017-04-16
Hi. I've typed that in terminal and wifi went off and then back on but nothing still. It shows that my router is there and connected but still unable to get any webpage or the Amazon icon on the desktop. 
I noticed in your last message it says attached thumbnails but I can't see nothing.

---

### Post by wildmanne39 on 2017-04-16
That is strange the thumbnails are their and that is where the settings are that need changed to make it work. 

Let's do it another way, do you see them now? if so change the settings, then restart network manager.
[ATTACH=CONFIG]274583[/ATTACH][ATTACH=CONFIG]274584[/ATTACH]
Thanks

---

### Post by techsupport-hotmail on 2017-04-16
Thank you!! It works! Your fantastic for putting up with me because I'm new. Problem I got now is that it's slow. Done a speed test on router and I'm getting 69 meg but I can't even run a webcam because it says my connection slow. Not sure if it's related tho.

---

### Post by wildmanne39 on 2017-04-16
It is another issue related to the driver I believe that can probably be solved, but to keep this clear for searchers that are having trouble with internet with 17.04 please use thread tools at the top of the page to mark this thread solved then start a new thread on this issue and post the wireless script info there.
Thanks

---

### Post by techsupport-hotmail on 2017-04-16
Thank you for all your help. Very much appreciated for all you have done.

---

### Post by wildmanne39 on 2017-04-16
Your very welcome!

---

