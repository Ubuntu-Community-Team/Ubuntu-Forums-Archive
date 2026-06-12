---
title: "Lubuntu 16.10, Atheros QCA9565 / AR9565 drops and reconnect continuously"
date: 2016-12-16
forum: Networking &amp; Wireless
---

### Post by dagmeow on 2016-12-16
Hi guys

I have some problems with my Acer Cloudbook, while surfing the web (especially watching video stream like twitch or youtube) the connection keeps drops then reconnect automatically, i'm in the same room as the wifi source, others PC are working correctly.
I have the same problem with Lubuntu 14.04, 16.04 and 16.10, from kernel 4.4 to 4.8, 4.9rc7 also (never tried 4.9 stable btw).

My modem/router is a Technicolor TG582n, edited to WPA2-PSK (AES mode i believe) cause i see other protocols can cause problems.
Wireless Network Adapter: Qualcomm Atheros QCA9565 / AR9565.
Using ath9k driver and NetworkManager.

I tried setting my region with "iw reg set", editing "/etc/default/crda", setting the "nohwcrypt=1" option to the driver, blacklisting "acer_wmi"... Nothing changed.
I'm using some kernel parameters "edd=off noapic modprobe.blacklist=pinctrl_cherryview" cause i need those to boot up every linux os on my machine as documented here [https://wiki.archlinux.org/index.php/Acer_Cloudbook](https://wiki.archlinux.org/index.php/Acer_Cloudbook)

Here's the wifi-info script:
```


########## wireless info START ##########


Report from: 16 Dec 2016 17:07 CET +0100


Booted last: 16 Dec 2016 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety


##### kernel ############################


Linux 4.8.0-30-generic #32-Ubuntu SMP Fri Dec 2 03:43:27 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, edd=off, noapic, modprobe.blacklist=pinctrl_cherryview, quiet, splash, vt.handoff=7


##### desktop ###########################


Lubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0803]
    Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 007: ID 04ca:3014 Lite-On Technology Corp. 
Bus 001 Device 003: ID 064e:9404 Suyin Corp. 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
ath9k                 147456  0
ath9k_common           36864  1 ath9k
ath9k_hw              475136  2 ath9k,ath9k_common
ath                    32768  3 ath9k_hw,ath9k,ath9k_common
mac80211              757760  1 ath9k
cfg80211              581632  4 mac80211,ath9k,ath,ath9k_common
ath3k                  20480  0
snd_soc_rt5670        126976  0
snd_soc_rl6231         16384  1 snd_soc_rt5670
snd_soc_core          233472  2 snd_soc_rt5670,snd_soc_sst_mfld_platform
bluetooth             552960  29 btrtl,hci_uart,btintel,btqca,bnep,btbcm,ath3k,btusb
snd_pcm               110592  8 snd_hda_intel,snd_hda_codec,snd_soc_rt5670,snd_pcm_dmaengine,snd_hda_core,snd_hda_codec_hdmi,snd_soc_sst_mfld_platform,snd_soc_core
wmi                    16384  1 acer_wmi
video                  40960  2 acer_wmi,i915


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 703  bytes 61847 (61.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 703  bytes 61847 (61.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.76  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::caff:28ff:fe01:3915  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 125293  bytes 176782532 (176.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 72158  bytes 7887245 (7.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:"Meow"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Meow' [AN1]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-18 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:126   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlp2s0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp2s0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       551     1  0 Dec15 ?        00:00:19 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA9565 / AR9565 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       wlp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Meow
GENERAL.CON-UUID:                       34dd7077-e287-46bc-b6b4-20a0f1818bb0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     65 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   34dd7077-e287-46bc-b6b4-20a0f1818bb0 | Meow
IP4.ADDRESS[1]:                         192.168.1.76/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             8.8.8.8
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1481989119
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.1.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.1.76
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = lan
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 86400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.1.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.254
IP6.ADDRESS[1]:                         fe80::caff:28ff:fe01:3915/64
IP6.GATEWAY:                            


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
Meow               <MAC 'Meow' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2         yes     * 
Vodafone-25701038  <MAC 'Vodafone-25701038' [AN2]>  Infra  7     2442 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1         no        
Vodafone-WiFi      <MAC 'Vodafone-WiFi' [AN3]>  Infra  7     2442 MHz  54 Mbit/s  30      &#9602;___  --           no        
FASTWEB-1-A55C8B   <MAC 'FASTWEB-1-A55C8B' [AN4]>  Infra  1     2412 MHz  54 Mbit/s  22      &#9602;___  WPA2         no        
WOW FI - FASTWEB   <MAC 'WOW FI - FASTWEB' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  19      &#9602;___  WPA2 802.1X  no        
Vodafone-30588644  <MAC 'Vodafone-30588644' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  17      &#9602;___  WPA2         no        
Alice-38803333     <MAC 'Alice-38803333' [AN7]>  Infra  6     2437 MHz  54 Mbit/s  14      &#9602;___  WPA1 WPA2    no        


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


[[/etc/NetworkManager/system-connections/Meow]] (600 root)
[connection] id=Meow | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Meow
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Rome (based on set time zone)


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


wlp2s0    13 channels in total; available frequencies :
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


wlp2s0    Interface doesn't support scanning : Device or resource busy


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     7DD7AE5764B41812C31660E
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     C1094862B67773C0C7822B7
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D15742225CC828FEB319976
depends:        ath
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.8.0-30-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     BDE5CB0CC0A980B65D19934
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.8.0-30-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F170FED576AF12B070D2E69
depends:        
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ath3k]
filename:       /lib/modules/4.8.0-30-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     822A166EB22C0577CB2ED55
depends:        bluetooth
intree:         Y
vermagic:       4.8.0-30-generic SMP mod_unload modversions 


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[ 2702.826071] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 2/3)
[ 2702.879461] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 3/3)
[ 2702.948728] wlp2s0: authentication with <MAC 'Meow' [AN1]> timed out
[ 2704.426806] wlp2s0: authenticate with <MAC 'Meow' [AN1]>
[ 2704.443556] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 1/3)
[ 2704.446189] wlp2s0: authenticated
[ 2704.449146] wlp2s0: associate with <MAC 'Meow' [AN1]> (try 1/3)
[ 2704.453152] wlp2s0: RX AssocResp from <MAC 'Meow' [AN1]> (capab=0x411 status=0 aid=6)
[ 2704.453323] wlp2s0: associated
[ 2813.758836] wlp2s0: authenticate with <MAC 'Meow' [AN1]>
[ 2813.777014] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 1/3)
[ 2813.839448] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 2/3)
[ 2813.903894] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 3/3)
[ 2813.960926] wlp2s0: authentication with <MAC 'Meow' [AN1]> timed out
[ 2821.385868] wlp2s0: authenticate with <MAC 'Meow' [AN1]>
[ 2821.401858] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 1/3)
[ 2821.406207] wlp2s0: authenticated
[ 2821.411560] wlp2s0: associate with <MAC 'Meow' [AN1]> (try 1/3)
[ 2821.415386] wlp2s0: RX AssocResp from <MAC 'Meow' [AN1]> (capab=0x411 status=0 aid=6)
[ 2821.415546] wlp2s0: associated
[14408.778790] wlp2s0: authenticate with <MAC 'Meow' [AN1]>
[14408.794273] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 1/3)
[14408.796885] wlp2s0: authenticated
[14408.805568] wlp2s0: associate with <MAC 'Meow' [AN1]> (try 1/3)
[14408.809477] wlp2s0: RX AssocResp from <MAC 'Meow' [AN1]> (capab=0x411 status=0 aid=6)
[14408.809690] wlp2s0: associated
[16354.714004] wlp2s0: authenticate with <MAC 'Meow' [AN1]>
[16354.741256] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 1/3)
[16354.775325] wlp2s0: authenticated
[16354.777369] wlp2s0: associate with <MAC 'Meow' [AN1]> (try 1/3)
[16354.783012] wlp2s0: RX AssocResp from <MAC 'Meow' [AN1]> (capab=0x411 status=0 aid=6)
[16354.783268] wlp2s0: associated
[25810.735230] wlp2s0: deauthenticating from <MAC 'Meow' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[25811.495240] ath: phy0: ASPM enabled: 0x42
[25812.467780] usb 1-5: device firmware changed
[25812.687213] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[25814.713774] wlp2s0: authenticate with <MAC 'Meow' [AN1]>
[25814.726846] wlp2s0: send auth to <MAC 'Meow' [AN1]> (try 1/3)
[25814.729153] wlp2s0: authenticated
[25814.731524] wlp2s0: associate with <MAC 'Meow' [AN1]> (try 1/3)
[25814.735263] wlp2s0: RX AssocResp from <MAC 'Meow' [AN1]> (capab=0x411 status=0 aid=9)
[25814.735474] wlp2s0: associated
[25814.735743] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready


########## wireless info END ############



```

Have a nice day everyone!
(if you have a better thread title please let me know!)

---

