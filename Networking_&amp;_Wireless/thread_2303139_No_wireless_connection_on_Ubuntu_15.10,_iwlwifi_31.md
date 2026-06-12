---
title: "No wireless connection on Ubuntu 15.10, iwlwifi 3160"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by dorin4 on 2015-11-16
Hello! I have installed Ubuntu 15.10 on my HP Pavilion x360 laptop, and I have noticed that since from the very beginning I didn't have internet connection. The wired connection works fine. I have installed 14.04 and 15.04 before, I could get it work after many random commands already forgot by me. I just know that the last one was: 
```
sudo tee /etc/modprobe.d/iwlwifi-opt.conf <<< "11n_disable=1"
```. I have tried to install different firmware versions by pasting them in /lib/firmware, even pasting 12 as 15 and so on, but without any results. I ran the wireless-info script, here is the output:
```

########## wireless info START ##########

Report from: 16 Nov 2015 20:12 EET +0200

Booted last: 16 Nov 2015 00:00 EET +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.10
Release:    15.10
Codename:    wily

##### kernel ############################

Linux 4.2.0-18-generic #22-Ubuntu SMP Fri Nov 6 18:25:50 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:806e]
    Kernel driver in use: r8169

08:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8070]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 003 Device 002: ID 8087:8001 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0483:91d1 STMicroelectronics 
Bus 001 Device 004: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 001 Device 003: ID 04f3:20a4 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 8087:07dc Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                294912  0
mac80211              733184  1 iwlmvm
hp_wmi                 16384  0
snd_soc_rt5640        114688  0
snd_soc_rl6231         16384  1 snd_soc_rt5640
acer_wmi               20480  0
snd_soc_core          196608  1 snd_soc_rt5640
sparse_keymap          16384  2 acer_wmi,hp_wmi
snd_pcm               102400  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_pcm_dmaengine,snd_hda_core
iwlwifi               200704  1 iwlmvm
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
wmi                    20480  2 acer_wmi,hp_wmi
video                  36864  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp7s0    Link encap:Ethernet  HWaddr <MAC 'enp7s0' [IF]>  
          inet addr:192.168.8.1  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'enp7s0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5627 (5.6 KB)  TX bytes:12323 (12.3 KB)

wlp8s0    Link encap:Ethernet  HWaddr <MAC 'wlp8s0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp7s0    no wireless extensions.

lo        no wireless extensions.

wlp8s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.8.254   0.0.0.0         UG    100    0        0 enp7s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp7s0
192.168.8.0     0.0.0.0         255.255.255.0   U     100    0        0 enp7s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       642     1  0 20:10 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp7s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101E/RTL8102E PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp7s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:07:00.0/net/enp7s0
GENERAL.IP-IFACE:                       enp7s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       949fc85e-3aea-47c9-b9fb-76e6e59f21ba
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   949fc85e-3aea-47c9-b9fb-76e6e59f21ba | Wired connection 1
IP4.ADDRESS[1]:                         192.168.8.1/24
IP4.GATEWAY:                            192.168.8.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             168.95.1.1
DHCP4.OPTION[1]:                        requested_ntp_servers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        expiry = 1447701057
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.8.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 3600
DHCP4.OPTION[14]:                       routers = 192.168.8.254
DHCP4.OPTION[15]:                       ip_address = 192.168.8.1
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_netbios_scope = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       domain_name_servers = 168.95.1.1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_routers = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       dhcp_message_type = 5
DHCP4.OPTION[25]:                       network_number = 192.168.8.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.8.254
IP6.ADDRESS[1]:                         fe80::<IP6 'enp7s0' [IF]>/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp8s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 3160 (Dual Band Wireless AC 3160)
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.2.0-18-generic
GENERAL.FIRMWARE-VERSION:               15.227938.0
GENERAL.HWADDR:                         <MAC 'wlp8s0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:08:00.0/net/wlp8s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

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

[[/etc/NetworkManager/system-connections/dlink]] (600 root)
[connection] id=dlink | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp8s0' [IF]> | mac-address-blacklist= | ssid=dlink
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Chisinau (based on set time zone)

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

enp7s0    no frequency information.

lo        no frequency information.

wlp8s0    32 channels in total; available frequencies :
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

##### iwlist scan #######################

wlp8s0    Interface doesn't support scanning : Network is down

enp7s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-18-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D59CBA6E05CEA656524E14B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        93:AD:27:02:12:25:CE:1B:B4:86:5E:4B:AB:1E:2B:6A:5F:09:94:29
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-18-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C9DB66EC5B332CC610F266D
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        93:AD:27:02:12:25:CE:1B:B4:86:5E:4B:AB:1E:2B:6A:5F:09:94:29
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-18-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-IWL3160_UCODE_API_OK.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     75057B888CB98F986AD50C3
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        93:AD:27:02:12:25:CE:1B:B4:86:5E:4B:AB:1E:2B:6A:5F:09:94:29
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-18-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     1F1A25B2E9C847110BD9ED9
depends:        
intree:         Y
vermagic:       4.2.0-18-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        93:AD:27:02:12:25:CE:1B:B4:86:5E:4B:AB:1E:2B:6A:5F:09:94:29
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 1
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi 11n_disable=1

[/etc/modprobe.d/iwlwifi-opt.conf]
11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

grep: /etc/udev/rules.d/*net*.rules: No such file or directory

##### dmesg #############################

[   10.735064] iwlwifi 0000:08:00.0: Unsupported splx structure
[   11.164772] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.7.10-fw-1.0.1.2d.d.bseq
[   11.257096] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   11.734572] iwlwifi 0000:08:00.0: loaded firmware version 15.227938.0 op_mode iwlmvm
[   12.443812] iwlwifi 0000:08:00.0: Detected Intel(R) Dual Band Wireless AC 3160, REV=0x164
[   12.444301] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[   12.600293] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[   12.636299] iwlwifi 0000:08:00.0 wlp8s0: renamed from wlan0
[   23.470079] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready
[   23.471445] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[   23.556466] r8169 0000:07:00.0 enp7s0: link down (repeated 2 times)
[   23.556536] IPv6: ADDRCONF(NETDEV_UP): enp7s0: link is not ready
[   25.218228] r8169 0000:07:00.0 enp7s0: link up
[   25.218236] IPv6: ADDRCONF(NETDEV_CHANGE): enp7s0: link becomes ready
[   33.823857] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   33.963572] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready (repeated 2 times)
[   74.607859] iwlwifi 0000:08:00.0: L1 Enabled - LTR Enabled (repeated 4 times)
[   74.740993] IPv6: ADDRCONF(NETDEV_UP): wlp8s0: link is not ready (repeated 2 times)

########## wireless info END ############


```

Many thanks in advance for any attempt to help!

---

### Post by praseodym on 2015-11-16
Acer modules on HP machines won't work ;)
```

sudo rmmod acer_wmi
sudo rfkill unblock all
rfkill list
iwconfig
```

---

### Post by dorin4 on 2015-11-16
I have run the above commands, at first it wasn't working, I wanted to put here the output of the wireless-info command again, and, after running it, it WORKED! But after rebooting I had to run again the wireless-info command to make it work. Is there any way to make it stable? Thank you very much, you helped me a lot already!

---

### Post by praseodym on 2015-11-16
Run then
```

echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot

---

### Post by dorin4 on 2015-11-17
Thanks again, everything worked!

---

