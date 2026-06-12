---
title: "Intel 7260 AC: Everything works but not AC connection. 2.4 ghz &amp; 5ghz N is ok."
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by ahears on 2016-11-15
I've burned myself out trying to figure this out. I can connect to wireless N on both 2.4ghz and 5 ghz bands but cannot connect to the access Point if I specify to use AC only. I have attempted to reproduce the problem by using an ALFA USB wireless AC adapter and it connects just fine so I've ruled out the AP, and now I'm sure it's a Driver issue. I may still have old Broad-comm drivers from when I upgraded to the new Intel Wireless 7260-AC card... All of the tutorials say to just drop the .ucode driver into '/lib/firmware', but I still don't get Wireless AC.

See below: *My computer is a Laptop with Ubuntu 14.04 completely up to date.


```



########## wireless info START ##########

Report from: 14 Nov 2016 20:53 PST -0800

Booted last: 14 Nov 2016 20:45 PST -0800

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-76-generic #98~14.04.1-Ubuntu SMP Fri Jun 24 17:04:54 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, apm=off

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: **Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]**
    Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:fc50]
    Kernel driver in use: atl1c

##### lsusb #############################

Bus 002 Device 004: ID 05e3:0745 Genesys Logic, Inc. Logilink CR0012
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 8087:07dc Intel Corp. 
Bus 001 Device 005: ID 058f:b003 Alcor Micro Corp. 
Bus 001 Device 004: ID 1050:0403 Yubico.com 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                320527  0 
mac80211              635281  1 iwlmvm
iwlwifi               193129  1 iwlmvm
cfg80211              540661  3 iwlwifi,mac80211,iwlmvm
compat                 30231  4 cfg80211,iwlwifi,mac80211,iwlmvm
wmi                    19193  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback
iface wlan0 inet6 static
pre-up modprobe ipv6
address 2001:bad:a55::2
netmask 64

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

teredo    Link encap:UNSPEC  HWaddr <MAC 'teredo' [IF2]>  
          inet6 addr: 2001:0:53aa:64c:3438:2a5a:b818:832e/32 Scope:Global
          inet6 addr: fe80::ffff:ffff:ffff/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2304 (2.3 KB)  TX bytes:2448 (2.4 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF6]>  
          inet addr:192.168.2.127  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF6]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2858 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2851 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1268013 (1.2 MB)  TX bytes:1043722 (1.0 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

teredo    no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Dirty Boy"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'Dirty Boy' [AC1]>   
          Bit Rate=135 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-36 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:278   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      3840     1  0 20:45 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF1]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Dirty Boy] ----------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF6]>

  Capabilities:
    Speed:           135 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    It Burns When IP: Infra, <MAC 'It Burns When IP' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    It Burns When IP_5G: Infra, <MAC 'It Burns When IP_5G' [AC3]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 80 WPA2
    It Burns When IP: Infra, <MAC 'It Burns When IP' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA2
    *Dirty Boy: Infra, <MAC 'Dirty Boy' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2
    It Burns When IP_5G: Infra, <MAC 'It Burns When IP_5G' [AN6]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 44 WPA2
    
  IPv4 Settings:
    Address:         192.168.2.127
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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

no-auto-default=<MAC address>,<MAC 'eth0' [IF1]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Malware Repository]] (600 root)
[connection] id=Malware Repository | type=802-11-wireless
[802-11-wireless] ssid=Malware Repository | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/It Burns When IP_5G]] (600 root)
[connection] id=It Burns When IP_5G | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=It Burns When IP_5G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/KRL Public Access]] (600 root)
[connection] id=KRL Public Access | type=802-11-wireless
[802-11-wireless] ssid=KRL Public Access | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/It Burns When IP]] (600 root)
[connection] id=It Burns When IP | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=It Burns When IP | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Dirty Boy 1]] (600 root)
[connection] id=Dirty Boy | type=802-11-wireless
[802-11-wireless] ssid=Dirty Boy | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country US:
    (2402 - 2472 @ 40), (N/A, 30)
    (5170 - 5250 @ 80), (N/A, 17)
    (5250 - 5330 @ 80), (N/A, 23), DFS
    (5490 - 5730 @ 160), (N/A, 23), DFS
    (5735 - 5835 @ 80), (N/A, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

teredo    no frequency information.

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
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

teredo    Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.765 GHz

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Dirty Boy' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Dirty Boy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000266ce1f56
                    Extra: Last beacon: 3924ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'It Burns When IP' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"It Burns When IP"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000060d0a77e1
                    Extra: Last beacon: 3924ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC 'It Burns When IP_5G' [AC3]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"It Burns When IP_5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000060d20e487
                    Extra: Last beacon: 632ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.16.0-76-generic/updates/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
version:        backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
**_description:    The new Intel(R) wireless AGN driver for Linux_**
srcversion:     FACC2752C818A66B5590A44
depends:        iwlwifi,mac80211,compat,cfg80211
vermagic:       3.16.0-76-generic SMP mod_unload modversions 
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/3.16.0-76-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
srcversion:     34AABACEC8D7D74DBE4B7F0
depends:        cfg80211,compat
vermagic:       3.16.0-76-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-76-generic/updates/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
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
firmware:       iwlwifi-7265D-13.ucode
firmware:       iwlwifi-7265-13.ucode
firmware:       iwlwifi-3160-13.ucode
firmware:       iwlwifi-7260-13.ucode
firmware:       iwlwifi-8000-13.ucode
srcversion:     24812413D73101402BD3EA4
depends:        compat,cfg80211
vermagic:       3.16.0-76-generic SMP mod_unload modversions 
parm:           debug:debug output mask (uint)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:            11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg  TX, 4: disable agg RX, 8 enable agg TX (uint)
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
filename:       /lib/modules/3.16.0-76-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.4.2-0-g1cb8570) using backports v4.4.2-1-0-gbec4037
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     2CB14CC06DF6CF12845374C
depends:        compat
vermagic:       3.16.0-76-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 8
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
debug: 0
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

lp
rtc

coretemp

<insert your gameport module here>
analog map=gamepad
<insert your gamepad/joystick module here>
joydev

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist rtl8188ce
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
[B]options iwlwifi 11n_disable=1
options iwlwifi 11n_disable=8
options iwlwifi wd_disable=1[/B]

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=0
options rtl8192ce fwlps=0
options rtl8192ce swenc=1

[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
Binary file /etc/udev/rules.d/70-persistent-net.rules matches

##### dmesg #############################

[   20.614553] iwlwifi 0000:02:00.0: L1 Enabled - LTR Disabled (repeated 4 times)
[   20.836221] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.836325] bridge-wlan0: device is wireless, enabling SMAC
[   20.836328] bridge-wlan0: up
[   20.836331] bridge-wlan0: attached
[   20.836365] bridge-wlan0: disabling the bridge
[   20.842083] bridge-wlan0: down
[   20.842088] bridge-wlan0: detached
[   21.005235] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.085827] wlan0: authenticate with <MAC 'Dirty Boy' [AC1]>
[   24.088989] wlan0: send auth to <MAC 'Dirty Boy' [AC1]> (try 1/3)
[   24.090777] wlan0: authenticated
[   24.092358] wlan0: associate with <MAC 'Dirty Boy' [AC1]> (try 1/3)
[   24.096419] wlan0: RX AssocResp from <MAC 'Dirty Boy' [AC1]> (capab=0x411 status=0 aid=2)
[   24.097161] wlan0: associated
[   24.097210] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.132411] bridge-wlan0: device is wireless, enabling SMAC
[   24.132415] bridge-wlan0: up
[   24.132418] bridge-wlan0: attached

########## wireless info END ############




```


Any help would be appreciated. Thank you:)

---

### Post by ahears on 2016-11-25
Replaced the Access point and problem is solved.

---

