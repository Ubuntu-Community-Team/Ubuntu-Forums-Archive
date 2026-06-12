---
title: "Can not connect to wireless"
date: 2017-07-15
forum: Networking &amp; Wireless
---

### Post by Dan_Bowser on 2017-07-15
Hello,

I have been unable to connect to the wifi of an Arris modem/router. I can see the network on the network interface I can select it, input a password and the GUI will indicate that the computer is connecting to the wifi, but after 20 seconds or so I recive a notification that I have been disconnected from the network. I ran through the troubleshooting list on the support website.

lshw -C network output:

```
description: Wireless interface
       product: Wireless 8260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 3a
       serial: 06:1b:b6:98:3f:20
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-26-generic firmware=21.302800.0 latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:330 memory:df300000-df301fff
```

I have a AC 8260 M.2 for my wireless connection which does not appear to require drivers. (I am using ubuntu 17.04 presently)

rfkill list output:

```
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

I have an active connection to the same router through a wired connection, but without this wire I still can not connect via wifi. There are multiple, 6 or so, devices currently connect to the same router/modem via wifi at the moment, and I have triple checked that the password is correct. To me it looks like there is no problem with either the hardware or the software and I still can not connect so I don't know what to do now.

---

### Post by BenginM on 2017-07-15
Salutations!

[SIZE=3][FONT=arial narrow]I see:

configuration: broadcast=yes driver=iwlwifi driverversion=4.10.0-26-generic firmware=21.302800
 
please #see the my comments regarding the 8260 with the iwlwifi driver loaded with a broken firmware:
[/FONT][/SIZE]

[https://ubuntuforums.org/showthread.php?t=2366041](https://ubuntuforums.org/showthread.php?t=2366041)
[https://ubuntuforums.org/showthread.php?t=2365398](https://ubuntuforums.org/showthread.php?t=2365398)

[SIZE=3][FONT=arial narrow]So, in short load and try firmware 22 :

cd /lib/firmware
sudo wget [https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8000C-22.ucode](https://git.kernel.org/cgit/linux/kernel/git/iwlwifi/linux-firmware.git/plain/iwlwifi-8000C-22.ucode)


Also, please run the [wireless script]("https://ubuntuforums.org/showthread.php?t=370108") and paste the result here using [CODE] tag .
[/FONT][/SIZE]

---

### Post by Dan_Bowser on 2017-07-15
OK, I put the 8000c-22 file in /lib/firmware.

Here is the scripts output:


```
########## wireless info START ##########

Report from: 15 Jul 2017 10:29 EDT -0400

Booted last: 15 Jul 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: Intel Corporation Ethernet Connection (2) I219-V [8086:0000]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Wireless 8260 [8086:1010]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 05e3:0617 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 004: ID 046d:c30f Logitech, Inc. Logicool HID-Compliant Keyboard (106 key)
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
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

mxm_wmi                16384  0
iwlmvm                368640  0
mac80211              782336  1 iwlmvm
iwlwifi               229376  1 iwlmvm
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
wmi                    16384  1 mxm_wmi

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
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.0.8/24 brd 192.168.0.255 scope global dynamic enp0s31f6
       valid_lft 1204181sec preferred_lft 1204181sec
    inet6 fe80::afb1:c6e1:7b32:4e79/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

enp0s31f6  no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.0.1 dev enp0s31f6 proto static metric 100 
169.254.0.0/16 dev enp0s31f6 scope link metric 1000 
192.168.0.0/24 dev enp0s31f6 proto kernel scope link src 192.168.0.8 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       850     1  0 08:54 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       d4684a8a-6244-38e2-80eb-ac1679f1b18d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d4684a8a-6244-38e2-80eb-ac1679f1b18d | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.8/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             64.233.217.2
IP4.DNS[2]:                             64.233.217.3
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1501333176
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 1209600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.8
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 64.233.217.2 64.233.217.3
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::afb1:c6e1:7b32:4e79/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.10.0-26-generic
GENERAL.FIRMWARE-VERSION:               21.302800.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
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
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   28d8a04b-069b-44e1-b348-b9d68f162a97 | WOW!2917

SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
WOW!2917  <MAC 'WOW!2917' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
dlink     <MAC 'dlink' [AC1]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  --        no        

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

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WOW!2917]] (600 root)
[connection] id=WOW!2917 | type=wifi | permissions=user:daniel:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WOW!2917
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

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

phy#0 (self-managed)
country 00: DFS-UNSET
    (2402 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
    (5170 - 5250 @ 80), (6, 22), (N/A), NO-OUTDOOR, AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5490 - 5730 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5735 - 5815 @ 80), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5815 - 5835 @ 20), (6, 22), (N/A), AUTO-BW, IR-CONCURRENT, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ, PASSIVE-SCAN

##### iwlist channels ###################

lo        no frequency information.

enp0s31f6  no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

enp0s31f6  Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'dlink' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c4e9f6181
                    Extra: Last beacon: 420ms ago
          Cell 02 - Address: <MAC 'WOW!2917' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"WOW!2917"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c4b18415b
                    Extra: Last beacon: 560ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     5B2ECBB7295933FCC472061
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.10.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
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
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-26.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-26.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-26.ucode
firmware:       iwlwifi-8000C-26.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--26.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--26.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--26.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--26.ucode
srcversion:     F8F4E503BE16838CB3C1ADC
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.10.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

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

[   29.615540] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[   29.685965] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[   29.735360] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[   29.793974] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[   36.826930] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[   36.834717] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[   36.886770] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[   36.958025] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[   37.007491] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[   54.009908] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[   78.770917] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[   78.777913] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[   78.847999] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[   78.905154] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[   78.973642] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[   83.482462] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[   83.490560] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[   83.556016] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[   83.615451] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[   83.673484] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[   95.486580] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[   95.493742] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[   95.557080] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[   95.617312] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[   95.680466] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[  104.009443] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[  128.477369] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[  128.484375] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[  128.537664] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[  128.593539] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[  128.640102] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[  147.997131] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[  148.004135] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[  148.044970] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[  148.118148] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[  148.183377] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[  154.007816] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[  232.544648] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[  232.551462] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[  232.615347] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[  232.664739] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[  232.731308] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[  249.430646] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[  249.437826] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[  249.508476] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[  249.561814] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[  249.613614] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[  254.010247] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  302.835438] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  302.835511] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
[  563.306711] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[  571.439309] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[  571.446318] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[  571.509743] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[  571.584893] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[  571.658233] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[  588.363979] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[  588.371003] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[  588.448291] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[  588.530618] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[  588.587367] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[  596.012782] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 5 times)
[ 1503.157918] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[ 1503.165071] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[ 1503.229214] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[ 1503.292121] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[ 1503.355109] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[ 1520.068240] wlp2s0: authenticate with <MAC 'WOW!2917' [AC2]>
[ 1520.075424] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 1/3)
[ 1520.136473] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 2/3)
[ 1520.204547] wlp2s0: send auth to <MAC 'WOW!2917' [AC2]> (try 3/3)
[ 1520.263663] wlp2s0: authentication with <MAC 'WOW!2917' [AC2]> timed out
[ 1525.021120] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 15 times)

########## wireless info END ############
```

---

### Post by BenginM on 2017-07-15
[SIZE=3][FONT=arial narrow]Ok.looking at the script output ... the kernel is still loading 21

GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.10.0-26-generic
GENERAL.FIRMWARE-VERSION:               21.302800.0

did you reboot! if not , then reboot and to check the loaded firmware run:

$ dmesg | grep iwlwifi[/FONT][/SIZE]

---

### Post by Dan_Bowser on 2017-07-15
I just rebooted now, I had forgotten before, and here is the output of sudo dmesg | grep iwlwifi:

```
[    4.002479] iwlwifi 0000:02:00.0: enabling device (0000 -> 0002)
[    4.004034] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-26.ucode failed with error -2
[    4.004225] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-25.ucode failed with error -2
[    4.004582] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-24.ucode failed with error -2
[    4.004782] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-8000C-23.ucode failed with error -2
[    4.010595] iwlwifi 0000:02:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[    4.025986] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    4.028022] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    4.028635] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    4.425720] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    5.069477] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    5.069753] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    5.195465] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    5.195725] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    5.305415] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    5.306029] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    5.431423] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled
[    5.431671] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled

```

So the firmware looks correct now.

I still can not connect to the router via the wifi connection though.

---

### Post by Hadaka on 2017-07-15
Hi, please re-set your bios to default, then edit wifi connections
*If there are multiple  " WOW!2917 " connections, delete them all
and add back in.
*The wireless diagnostic report shows..
```
 #*wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:**[COLOR=#ff0000]on[/COLOR]**
```
To correct please COPY and paste..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```

*Country code unset causes drops and no connects.
```
##### iw reg get ########################
Region: America/Toronto (based on set time zone)
country **[COLOR=#ff0000]00[/COLOR]**: DFS-**[COLOR=#ff0000]UNSET[/COLOR]**
```
To correct please COPY and paste..
```
sudo iw reg set CA
sudo sed -i 's/=.*/=CA/' /etc/default/crda
```
The access point definition has 3 possible problems..
```
*#Cell 02 - Address: <MAC 'WOW**[COLOR=#ff0000]![/COLOR]**2917' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=**[COLOR=#ff0000]27/70[/COLOR]**  Signal level=-83 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : **[COLOR=#ff0000]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : **[COLOR=#ff0000]TKIP[/COLOR]** CCMP
```
1..The exclamation ! in the ssid may be seen as a command by Ubuntu
2..Signal quality..27..is very weak
3..Ubuntu and Dr. chili555 hate TKIP and it does cause drops and no connects.
To correct please..
```
Access your router and change ssid..as an experiment to something simple.
Check your antenna connections for corrosion and that they are tight and connected
Change to wpa2 aes ccmp NO TKIP
```
Remove wired connection and any usb 
Boot and test wireless
Thanks.

---

### Post by Dan_Bowser on 2017-07-15
OK,

I had to actually install the antenna lines. Then I ran the two scripts you gave me, and fiddled with the router settings. I can now connect to the wifi.

---

### Post by Dan_Bowser on 2017-07-15
This connection to the wifi is useless. It just hangs on connecting without ever completing the action of connecting to the google search page.

Do I start a new question or continue this one?

---

### Post by Hadaka on 2017-07-15
Sounds like there is some progress being made, and a possible 
DNS problem, first ..we need some additional information.
Please post the type..make of your computer..as in HP,Dell,ASUS..etc
also please run and post a new wireless-info ,so we can see if any new
problems have happened....we re getting there...
thanks.

---

### Post by Dan_Bowser on 2017-07-15
Here's the wireless script output:

```

########## wireless info START ##########

Report from: 15 Jul 2017 17:47 EDT -0400

Booted last: 15 Jul 2017 00:00 EDT -0400

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-26-generic #30-Ubuntu SMP Tue Jun 27 09:30:12 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I219-V [8086:15b8]
    Subsystem: Intel Corporation Ethernet Connection (2) I219-V [8086:0000]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Wireless 8260 [8086:24f3] (rev 3a)
    Subsystem: Intel Corporation Wireless 8260 [8086:1010]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 05e3:0617 Genesys Logic, Inc. 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:0a2b Intel Corp. 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 004: ID 046d:c30f Logitech, Inc. Logicool HID-Compliant Keyboard (106 key)
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

mxm_wmi                16384  0
iwlmvm                368640  0
mac80211              782336  1 iwlmvm
iwlwifi               229376  1 iwlmvm
cfg80211              602112  3 iwlmvm,iwlwifi,mac80211
wmi                    16384  1 mxm_wmi

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
2: enp0s31f6: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp0s31f6' [IF1]> brd <MAC address>
    inet 192.168.0.8/24 brd 192.168.0.255 scope global dynamic enp0s31f6
       valid_lft 1206614sec preferred_lft 1206614sec
    inet6 fe80::afb1:c6e1:7b32:4e79/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp0s31f6  no wireless extensions.

lo        no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.0.1 dev enp0s31f6 proto static metric 100 
169.254.0.0/16 dev enp0s31f6 scope link metric 1000 
192.168.0.0/24 dev enp0s31f6 proto kernel scope link src 192.168.0.8 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       837     1  0 16:42 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s31f6
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ethernet Connection (2) I219-V
GENERAL.DRIVER:                         e1000e
GENERAL.DRIVER-VERSION:                 3.2.6-k
GENERAL.FIRMWARE-VERSION:               0.2-4
GENERAL.HWADDR:                         <MAC 'enp0s31f6' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1f.6/net/enp0s31f6
GENERAL.IP-IFACE:                       enp0s31f6
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       d4684a8a-6244-38e2-80eb-ac1679f1b18d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/6
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d4684a8a-6244-38e2-80eb-ac1679f1b18d | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.8/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             64.233.217.2
IP4.DNS[2]:                             64.233.217.3
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1501361835
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 1209600
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.8
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       routers = 192.168.0.1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 64.233.217.2 64.233.217.3
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::afb1:c6e1:7b32:4e79/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Wireless 8260
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.10.0-26-generic
GENERAL.FIRMWARE-VERSION:               22.391740.0
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         39 (Device disconnected by user or client)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    no
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
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   1c1e62a8-d29f-45ed-86f4-792174ec9712 | WOW!2917

SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
DIRECT-roku-81B81E  <MAC 'DIRECT-roku-81B81E' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2      no        
BHNTG1682GDACB      <MAC 'BHNTG1682GDACB' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2      no        
ATT3eD9rQa          <MAC 'ATT3eD9rQa' [AN3]>  Infra  5     2432 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
ARRIS-ABCF          <MAC 'ARRIS-ABCF' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
dlink               <MAC 'dlink' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  --        no        
WOW!2917            <MAC 'WOW!2917' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
BHNTG1682GC092      <MAC 'BHNTG1682GC092' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
ATT8LNV3DD          <MAC 'ATT8LNV3DD' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        

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

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/WOW!2917]] (600 root)
[connection] id=WOW!2917 | type=wifi | permissions=user:daniel:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=WOW!2917
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Toronto (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 20), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (6, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (6, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

phy#0 (self-managed)
country US: DFS-UNSET
    (2402 - 2482 @ 40), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-80MHZ, NO-160MHZ
    (5170 - 5250 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
    (5250 - 5330 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5490 - 5730 @ 80), (6, 22), (0 ms), DFS, AUTO-BW, NO-HT40PLUS, NO-160MHZ, PASSIVE-SCAN
    (5735 - 5815 @ 80), (6, 22), (N/A), AUTO-BW, NO-HT40PLUS, NO-160MHZ
    (5815 - 5835 @ 20), (6, 22), (N/A), AUTO-BW, NO-HT40MINUS, NO-HT40PLUS, NO-80MHZ, NO-160MHZ

##### iwlist channels ###################

enp0s31f6  no frequency information.

lo        no frequency information.

wlp2s0    32 channels in total; available frequencies :
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

enp0s31f6  Interface doesn't support scanning.

wlp2s0    Interface doesn't support scanning : Device or resource busy

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     5B2ECBB7295933FCC472061
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.10.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     309C9ACED540FCAA1DE7422
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.10.0-26-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
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
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-26.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-26.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-26.ucode
firmware:       iwlwifi-8000C-26.ucode
firmware:       iwlwifi-9000-pu-a0-lc-a0--26.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--26.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--26.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--26.ucode
srcversion:     F8F4E503BE16838CB3C1ADC
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.10.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D77C8F93375950F3BA95B16
depends:        
intree:         Y
vermagic:       4.10.0-26-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
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
11n_disable: 0
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

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

[    3.742631] iwlwifi 0000:02:00.0: loaded firmware version 22.391740.0 op_mode iwlmvm
[    3.755490] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 8260, REV=0x208
[    3.757302] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[    3.884285] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.055380] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[    4.578807] IPv6: ADDRCONF(NETDEV_UP): enp0s31f6: link is not ready (repeated 2 times)
[    4.769686] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    4.771380] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled (repeated 4 times)
[    5.071638] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[    5.107394] iwlwifi 0000:02:00.0: L1 Disabled - LTR Enabled (repeated 4 times)
[    5.312457] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 3 times)
[   58.994860] wlp2s0: authenticate with <MAC 'WOW!2917' [AN6]>
[   59.004650] wlp2s0: send auth to <MAC 'WOW!2917' [AN6]> (try 1/3)
[   59.011367] wlp2s0: authenticated
[   59.015480] wlp2s0: associate with <MAC 'WOW!2917' [AN6]> (try 1/3)
[   59.029875] wlp2s0: RX AssocResp from <MAC 'WOW!2917' [AN6]> (capab=0x411 status=0 aid=2)
[   59.032014] wlp2s0: associated
[   59.032080] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  402.981288] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  402.981348] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s31f6: link becomes ready
[  476.667235] e1000e: enp0s31f6 NIC Link is Down
[  486.425203] wlp2s0: deauthenticating from <MAC 'WOW!2917' [AN6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  486.439112] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  491.947670] wlp2s0: authenticate with <MAC 'WOW!2917' [AN6]>
[  491.954836] wlp2s0: send auth to <MAC 'WOW!2917' [AN6]> (try 1/3)
[  491.956507] wlp2s0: authenticated
[  491.959500] wlp2s0: associate with <MAC 'WOW!2917' [AN6]> (try 1/3)
[  491.975295] wlp2s0: RX AssocResp from <MAC 'WOW!2917' [AN6]> (capab=0x411 status=0 aid=2)
[  491.977484] wlp2s0: associated
[  491.977517] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  725.134396] e1000e: enp0s31f6 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[  742.749677] wlp2s0: deauthenticating from <MAC 'WOW!2917' [AN6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  742.761600] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 2 times)
[  842.136628] wlp2s0: authenticate with <MAC 'WOW!2917' [AN6]>
[  842.142987] wlp2s0: send auth to <MAC 'WOW!2917' [AN6]> (try 1/3)
[  842.149002] wlp2s0: authenticated
[  842.149745] wlp2s0: associate with <MAC 'WOW!2917' [AN6]> (try 1/3)
[  842.171046] wlp2s0: RX AssocResp from <MAC 'WOW!2917' [AN6]> (capab=0x411 status=0 aid=1)
[  842.172905] wlp2s0: associated
[  842.172974] IPv6: ADDRCONF(NETDEV_CHANGE): wlp2s0: link becomes ready
[  891.341191] wlp2s0: deauthenticating from <MAC 'WOW!2917' [AN6]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  891.355586] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready (repeated 10 times)

########## wireless info END ############


```

I built the computer myself earlier this week. It has a z270 chipset. I can give you more information about it but I'm not sure what is helpful.

---

### Post by Hadaka on 2017-07-15
Hi, the country code failed to set, please copy
and paste..
```
sudo iw reg set CA
sudo sed -i 's/=.*/=CA/' /etc/default/crda
```
then do..
```
echo "options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
you also still have the issue with the ssid name..you dont have to leave it changed..but please do so
to see if indeed the " ! " in the name is causing a problem.
You state "I built the computer myself earlier this week. It has a z270 chipset."
Some of the new chip sets have "issues" with the intel drivers..please use your favorite editor and  + add
these Two lines to...
*Edit.. -> /etc/NetworkManager/NetworkManager.conf
*Add.. [device]
*Add.. wifi.scan-rand-mac-address=0
```
[device]
wifi.scan-rand-mac-address=0
```
Disconnect wired connection..boot and test wireless
Thanks.

---

### Post by chili555 on 2017-07-15
In addition to the removal of ! in the SSID, we'd also like to see:```
cat /var/log/syslog | grep -i dns
```We also see this:> SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
DIRECT-roku-81B81E  <MAC 'DIRECT-roku-81B81E' [AN1]>  Infra  6     2437 MHz  54 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2      no        
BHNTG1682GDACB      <MAC 'BHNTG1682GDACB' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA2      no        
ATT3eD9rQa          <MAC 'ATT3eD9rQa' [AN3]>  Infra  5     2432 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
ARRIS-ABCF          <MAC 'ARRIS-ABCF' [AN4]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
dlink               <MAC 'dlink' [AN5]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  --        no        
WOW!2917            <MAC 'WOW!2917' [AN6]>  Infra  6     2437 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
BHNTG1682GC092      <MAC 'BHNTG1682GC092' [AN7]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
ATT8LNV3DD          <MAC 'ATT8LNV3DD' [AN8]>  Infra  11    2462 MHz  54 Mbit/s  29      &#9602;___  WPA2      no        
Aside from your Roku remote which, I assume, is sitting next to you, the highest signal strength is 37 (on a scale of 100). The access point you are trying to connect to is a puny 29.

Here is a comparison from my machine:> *  SSID                    MODE   CHAN  RATE       SIGNAL  BARS  SECURITY  
   GBR1                    Infra  6     54 Mbit/s  84      &#9602;&#9604;&#9606;&#9608;  WPA2      
*  GBR5                    Infra  149   54 Mbit/s  68      &#9602;&#9604;&#9606;_  WPA2      
   nx2.4                   Infra  11    54 Mbit/s  60      &#9602;&#9604;&#9606;_  WPA1 WPA2 
   DIRECT-roku-773-20C25D  Infra  6     54 Mbit/s  44      &#9602;&#9604;__  WPA2      
   MC1                     Infra  11    54 Mbit/s  40      &#9602;&#9604;__  WPA2      
   MC5                     Infra  149   54 Mbit/s  30      &#9602;___  WPA2      
   MAHB Wi-Fi              Infra  1     54 Mbit/s  20      &#9602;___  WPA2      
   nx5g                    Infra  36    54 Mbit/s  19      &#9602;___  WPA1 WPA2 
I also use an Intel, for what it's worth. 

Would you please double-check the antenna wires?

---

### Post by johndough2 on 2017-07-16
Hi

I notice the WiFi has/is MTU=0, whereas the ethernet is MTU=1500.

I doubt it means anything, but if there is a setting for the MTU make it 1500, just so it looks nice.

---

### Post by Dan_Bowser on 2017-07-16
OK I changed the country code with 

```

sudo iw reg set CA
sudo sed -i 's/=.*/=CA/' /etc/default/crda

```

then ran 

```
echo "options iwlwifi 11n_disable=8 | sudo tee -a /etc/modprobe.d/iwlwifi.conf

```

and changed the NetworkManager.conf file and saved.

I deleted the old WOW!2917 from the edit connections menu and restarted. After I restarted I left the cat line disconnected and the wifi still hangs at TLS handshake to google. So the connection doesn't appear to be useful.

Yesterday I did change the routers assigned name from WOW!2917 to WOW2917. Since the connection didn't seem to change I flipped it back to the old WOW!2917 name just so no one would have to re-input connection information.

Here is the output from cat /var/log/syslog | grep -i dns:

```
Jul 16 07:26:42 uH2 NetworkManager[860]: <info>  [1500204402.5466] policy: set 'WOW!2917' (wlp2s0) as default for IPv4 routing and DNS
Jul 16 07:26:42 uH2 avahi-daemon[868]: Leaving mDNS multicast group on interface enp0s31f6.IPv4 with address 192.168.0.8.
Jul 16 07:26:42 uH2 avahi-daemon[868]: Interface enp0s31f6.IPv4 no longer relevant for mDNS.
Jul 16 07:26:42 uH2 avahi-daemon[868]: Leaving mDNS multicast group on interface enp0s31f6.IPv6 with address fe80::afb1:c6e1:7b32:4e79.
Jul 16 07:26:42 uH2 avahi-daemon[868]: Interface enp0s31f6.IPv6 no longer relevant for mDNS.
Jul 16 07:26:44 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:14 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:14 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:14 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:15 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:15 uH2 systemd-resolved[997]: Using degraded feature set (UDP+EDNS0+DO) for DNS server 64.233.217.3.
Jul 16 07:27:16 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:16 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:16 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:16 uH2 systemd-resolved[997]: Using degraded feature set (UDP+EDNS0+DO) for DNS server 64.233.217.2.
Jul 16 07:27:16 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:18 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:18 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:18 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:18 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:22 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:22 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:22 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:22 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:27 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:27 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:27 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:27 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:33 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:33 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:33 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:33 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:38 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:38 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:38 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:43 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:43 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:43 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:48 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:49 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:49 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:54 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:54 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:28:00 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:28:00 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:28:05 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:28:05 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:28:10 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:28:10 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:30:23 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:30:28 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:31:08 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:31:14 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:31:19 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:31:24 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:31:29 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:31:35 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:31:42 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:31:48 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:34:09 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:34:09 uH2 systemd-resolved[997]: Grace period over, resuming full feature set (UDP+EDNS0+DO+LARGE) for DNS server 64.233.217.3.
Jul 16 07:34:14 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:34:55 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:35:00 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:35:05 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:35:42 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:35:47 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:35:52 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:35:57 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:36:03 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:36:12 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:36:12 uH2 systemd-resolved[997]: Using degraded feature set (UDP+EDNS0+DO) for DNS server 64.233.217.3.
Jul 16 07:36:17 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:36:22 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:36:28 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:36:30 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:36:33 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:36:35 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:36:41 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:36:46 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:36:51 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:37:00 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:37:06 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:37:11 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:37:16 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:37:28 uH2 avahi-daemon[868]: Leaving mDNS multicast group on interface wlp2s0.IPv6 with address fe80::9c2:bdb0:9d0c:cece.
Jul 16 07:37:28 uH2 avahi-daemon[868]: Interface wlp2s0.IPv6 no longer relevant for mDNS.
Jul 16 07:37:28 uH2 avahi-daemon[868]: Leaving mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.0.9.
Jul 16 07:37:28 uH2 avahi-daemon[868]: Interface wlp2s0.IPv4 no longer relevant for mDNS.
Jul 16 07:37:28 uH2 systemd-resolved[997]: Switching to fallback DNS server 8.8.8.8.
Jul 16 07:37:58 uH2 systemd[1]: Starting Clean up any mess left by 0dns-up...
Jul 16 07:37:58 uH2 systemd[1]: Started Clean up any mess left by 0dns-up.
Jul 16 07:37:58 uH2 systemd[1]: Listening on Avahi mDNS/DNS-SD Stack Activation Socket.
Jul 16 07:37:58 uH2 systemd[1]: Starting Avahi mDNS/DNS-SD Stack...
Jul 16 07:37:58 uH2 kernel: [    1.963564] Key type dns_resolver registered
Jul 16 07:37:58 uH2 NetworkManager[843]: <info>  [1500205078.8551] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf) (run: 10-globally-managed-devices.conf) (etc: default-wifi-powersave-on.conf)
Jul 16 07:37:58 uH2 NetworkManager[843]: <info>  [1500205078.8673] dns-mgr[0x55a3c0893a90]: init: dns=systemd-resolved, rc-manager=symlink, plugin=systemd-resolved
Jul 16 07:37:58 uH2 systemd[1]: Started Avahi mDNS/DNS-SD Stack.
Jul 16 07:38:19 uH2 systemd-resolved[989]: Switching to fallback DNS server 8.8.8.8.
Jul 16 07:38:39 uH2 avahi-daemon[844]: Joining mDNS multicast group on interface wlp2s0.IPv4 with address 192.168.0.9.
Jul 16 07:38:39 uH2 avahi-daemon[844]: New relevant interface wlp2s0.IPv4 for mDNS.
Jul 16 07:38:39 uH2 NetworkManager[843]: <info>  [1500205119.4391] policy: set 'WOW!2917' (wlp2s0) as default for IPv4 routing and DNS
Jul 16 07:38:39 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:38:40 uH2 avahi-daemon[844]: Joining mDNS multicast group on interface wlp2s0.IPv6 with address fe80::32a1:f5f4:89a8:a063.
Jul 16 07:38:40 uH2 avahi-daemon[844]: New relevant interface wlp2s0.IPv6 for mDNS.
Jul 16 07:38:46 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:38:46 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:38:47 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:38:48 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:38:48 uH2 systemd-resolved[989]: Using degraded feature set (UDP+EDNS0+DO) for DNS server 64.233.217.2.
Jul 16 07:38:48 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:38:50 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:39:47 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:39:47 uH2 systemd-resolved[989]: Using degraded feature set (UDP+EDNS0+DO) for DNS server 64.233.217.3.
Jul 16 07:39:51 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:39:52 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:39:52 uH2 avahi-daemon[844]: Joining mDNS multicast group on interface enp0s31f6.IPv4 with address 192.168.0.8.
Jul 16 07:39:52 uH2 avahi-daemon[844]: New relevant interface enp0s31f6.IPv4 for mDNS.
Jul 16 07:39:52 uH2 NetworkManager[843]: <info>  [1500205192.6476] policy: set 'Wired connection 1' (enp0s31f6) as default for IPv4 routing and DNS
Jul 16 07:39:52 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.2 for interface enp0s31f6.
Jul 16 07:39:53 uH2 systemd-resolved[989]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:39:54 uH2 avahi-daemon[844]: Joining mDNS multicast group on interface enp0s31f6.IPv6 with address fe80::afb1:c6e1:7b32:4e79.
Jul 16 07:39:54 uH2 avahi-daemon[844]: New relevant interface enp0s31f6.IPv6 for mDNS.


```

I ran the command that output this data just after trying the wifi and plugging the cat line back in.

---

### Post by chili555 on 2017-07-16
> Jul 16 07:27:49 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:27:54 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:27:54 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:28:00 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:28:00 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:28:05 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.
Jul 16 07:28:05 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.2 for interface wlp2s0.
Jul 16 07:28:10 uH2 systemd-resolved[997]: Switching to DNS server 64.233.217.3 for interface wlp2s0.Old Chili doesn't like this one bit!

Please Edit Connections in Network Manager to specify specific DNS nameservers:  [http://3.bp.blogspot.com/-7yAL1fjG_NY/TjqeB_PE-XI/AAAAAAAAAwk/USkoevbfSAg/s1600/Network-Manager-DNS+%25283%2529.png](http://3.bp.blogspot.com/-7yAL1fjG_NY/TjqeB_PE-XI/AAAAAAAAAwk/USkoevbfSAg/s1600/Network-Manager-DNS+%25283%2529.png)

Reboot and let us hear the result.

---

### Post by Dan_Bowser on 2017-07-16
OK, I changed the DNS settings in the edit connections menu and rebooted. The wifi appears to be working normally.

---

### Post by Hadaka on 2017-07-16
This is good news !
 "The wifi appears to be working normally."

*If everything is working to your satisfaction please take the time to
mark your thread solved by going to your thread, clicking Thread Tools
and choosing Solved.

and if you havent already...from a working wired connection please do..
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove
sudo apt-get autoclean
```
This will bring your system up to current security settings and
clean out unwanted stuff created during the install an trouble
shooting process..
Thanks

---

### Post by Dan_Bowser on 2017-07-16
Thank you for the help.

---

### Post by Hadaka on 2017-07-16
Thanks for hanging in there while we tried to find a solution,
and thank you for marking your thread Solved, it will help others
searching.
 
You may want to change your current DNS IP's 8.8.8.8,8.8.4.4 "Google"
to a faster local Canadian DNS provider..
#Radiant Communications Vancouver,Ca (RADT)
#66.163.0.173 - DNS  
#Hydro One Telecom, Inc. Toronto,Ca (OHYD)
#142.46.128.130 - DNS
#Rogers Communications Brampton Canada Inc.
#216.183.90.190 - DNS
#I run dnsbench.exe to get a speed ranking for several dozen DNS servers 
#It is a Windows utility.."yet another reason to dual boot or keep an old XP machine alive."
#[www.grc.com/dns/Benchmark.htm](www.grc.com/dns/Benchmark.htm)


#Your current isp default DNS server
#WideOpenWest Finance LLC. IL,USA (WOPW) 
#64.233.217.2 -DNS
Glad your wifi is working !

---

