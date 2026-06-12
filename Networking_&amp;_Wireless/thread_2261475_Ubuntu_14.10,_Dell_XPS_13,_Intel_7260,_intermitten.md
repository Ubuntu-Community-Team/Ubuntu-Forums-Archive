---
title: "Ubuntu 14.10, Dell XPS 13, Intel 7260, intermittent wireless connection"
date: 2015-01-19
forum: Networking &amp; Wireless
---

### Post by aridus on 2015-01-19
I have an intermittent wireless connection with a Dell XPS 13 (Intel Wireless 7260, Ubuntu 14.10). I provide the output of the wireless script below (when connection was working). This problem persists across different routers. Sometimes the 2.4 connection works and the 5.0 doesn't, sometimes both work. When the connection works it can be excellent but it randomly disconnects. If anybody could look at the output of the script and suggest where the problem lies and any potential solution(s), I would be grateful. With thanks. 

```

########## wireless info START ##########

Report from: 19 Jan 2015 11:25 GMT +0000

Booted last: 19 Jan 2015 11:22 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.10
Release:	14.10
Codename:	utopic

##### kernel ############################

Linux 3.16.0-29-generic #39-Ubuntu SMP Mon Dec 15 22:27:29 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c470]
	Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 8087:07dc Intel Corp. 
Bus 002 Device 004: ID 0bda:5752 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 06cb:0af8 Synaptics, Inc. 
Bus 002 Device 007: ID 1058:070a Western Digital Technologies, Inc. My Passport Essential SE
Bus 002 Device 006: ID 059f:0c41 LaCie, Ltd 
Bus 002 Device 002: ID 04b4:6570 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18227  0 
dcdbas                 14928  1 dell_laptop
iwlmvm                217797  0 
mac80211              660592  1 iwlmvm
iwlwifi               183038  1 iwlmvm
cfg80211              510218  3 iwlwifi,mac80211,iwlmvm
wmi                    19193  1 dell_wmi
snd_soc_rt5640         93042  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200108  1 snd_soc_rt5640
snd_pcm               104102  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

lxcbr0    Link encap:Ethernet  HWaddr <MAC 'lxcbr0' [IF]>  
          inet addr:10.0.3.1  Bcast:10.0.3.255  Mask:255.255.255.0
          inet6 addr: fe80::28fe:ccff:fe1f:3e3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:12624 (12.6 KB)

virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::5ec5:d4ff:fe50:4c95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1023120 (1.0 MB)  TX bytes:397220 (397.2 KB)

##### iwconfig ##########################

virbr0    no wireless extensions.

lo        no wireless extensions.

lxcbr0    no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Pescador"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Pescador' [AC1]>   
          Bit Rate=86.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:130   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
10.0.3.0        0.0.0.0         255.255.255.0   U     0      0        0 lxcbr0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Pescador] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           86 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia6835145: Infra, <MAC 'virginmedia6835145' [AN1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Pescador5:       Infra, <MAC 'Pescador5' [AC4]>, Freq 5500 MHz, Rate 54 Mb/s, Strength 49 WPA2
    mineimo:         Infra, <MAC 'mineimo' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    ADDON GWAR3000:  Infra, <MAC 'ADDON GWAR3000' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WEP
    *Pescador:       Infra, <MAC 'Pescador' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2

  IPv4 Settings:
    Address:         192.168.0.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/Pescador5]] (600 root)
[connection] id=Pescador5 | type=802-11-wireless
[802-11-wireless] ssid=Pescador5 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Pescador]] (600 root)
[connection] id=Pescador | type=802-11-wireless
[802-11-wireless] ssid=Pescador | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CambridgePlace]] (600 root)
[connection] id=CambridgePlace | type=802-11-wireless
[802-11-wireless] ssid=CambridgePlace | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOTEL BROADBAND]] (600 root)
[connection] id=HOTEL BROADBAND | type=802-11-wireless
[802-11-wireless] ssid=HOTEL BROADBAND | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB: DFS-UNSET
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

virbr0    no frequency information.

lo        no frequency information.

lxcbr0    no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Pescador' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"Pescador"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010ca0668f6
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ADDON GWAR3000' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ADDON GWAR3000"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002667540e107
                    Extra: Last beacon: 88ms ago
          Cell 03 - Address: <MAC 'mineimo' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"mineimo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000099d8e6f35b
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

lo        Interface doesn't support scanning.

lxcbr0    Interface doesn't support scanning.

00000000000000000000000000000000
          Cell 04 - Address: <MAC 'Pescador5' [AC4]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Pescador5"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000010c5f395a8
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.16.0-29-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     DF2B4108DD59AC2EC4C7D5B
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        70:63:7F:DE:89:46:26:78:AF:F2:D9:C2:BB:12:90:BE:2F:ED:1F:B1
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.16.0-29-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B3A65EB1DAE59CB6B5FD971
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        70:63:7F:DE:89:46:26:78:AF:F2:D9:C2:BB:12:90:BE:2F:ED:1F:B1
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-29-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     D335B9FC08B25C4ADA0BD33
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        70:63:7F:DE:89:46:26:78:AF:F2:D9:C2:BB:12:90:BE:2F:ED:1F:B1
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: N) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
intree:         Y
vermagic:       3.16.0-29-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        70:63:7F:DE:89:46:26:78:AF:F2:D9:C2:BB:12:90:BE:2F:ED:1F:B1
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: N
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
lp

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

[/etc/modprobe.d/usbhid.conf]
options usbhid quirks=0x06cb:0x0af8:0x20000000

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   76.094626] wlan0: deauthenticating from <MAC 'Pescador5' [AC4]> by local choice (Reason: 3=DEAUTH_LEAVING)
[   78.101347] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 2
[   78.101352] iwlwifi 0000:02:00.0: Current SW read_ptr 147 write_ptr 1
[   78.101390] iwl data: 00000000: 00 00 f8 ff 00 00 00 00 07 00 00 00 00 00 00 00  ................
[   78.101402] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[   78.101414] iwlwifi 0000:02:00.0: FH TRBs(1) = 0x801020a2
[   78.101425] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[   78.101437] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x8030000a
[   78.101448] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[   78.101460] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[   78.101471] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[   78.101483] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x0070907e
[   78.101532] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [11,11]
[   78.101581] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[   78.101629] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [147,1]
[   78.101678] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.101726] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.101775] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.101823] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.101872] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.101920] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.101969] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [127,127]
[   78.102017] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102066] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102114] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102163] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102212] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102260] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102309] iwlwifi 0000:02:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102357] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102406] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   78.102454] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.111581] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 0
[   80.111588] iwlwifi 0000:02:00.0: Current SW read_ptr 11 write_ptr 12
[   80.111628] iwl data: 00000000: 00 08 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   80.111649] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[   80.111662] iwlwifi 0000:02:00.0: FH TRBs(1) = 0x801020a2
[   80.111675] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[   80.111687] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x8030000b
[   80.111701] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[   80.111714] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[   80.111727] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[   80.111740] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x0070907e
[   80.111792] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [11,12]
[   80.111852] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[   80.111901] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [147,6]
[   80.111950] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.111998] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112047] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112096] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112144] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112193] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112242] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [127,127]
[   80.112291] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112340] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112388] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112437] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112485] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112534] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112582] iwlwifi 0000:02:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112631] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112679] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   80.112728] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   83.742366] wlan0: authenticate with <MAC 'Pescador' [AC1]>
[   83.745295] wlan0: send auth to <MAC 'Pescador' [AC1]> (try 1/3)
[   83.747062] wlan0: authenticated
[   83.747649] wlan0: associate with <MAC 'Pescador' [AC1]> (try 1/3)
[   83.752265] wlan0: RX AssocResp from <MAC 'Pescador' [AC1]> (capab=0x411 status=0 aid=1)
[   83.753366] wlan0: associated

########## wireless info END ############

```

---

### Post by chili555 on 2015-01-19
> [   78.101347] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 2
[   78.101352] iwlwifi 0000:02:00.0: Current SW read_ptr 147 write_ptr 1Wonderful. It's a well known bug that I thought had been fixed. Let's see if we can try a fix. From the terminal:```
sudo -i
echo "options iwlwifi wd_disable=0"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and let us hear the result. If it is not working as expected, post:```
dmesg | grep iwl
```


--------------
Reference: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1270808](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1270808)

[http://people.canonical.com/~sforshee/iwlwifi/utopic/](http://people.canonical.com/~sforshee/iwlwifi/utopic/)

---

### Post by aridus on 2015-01-19
Dear Chili555 - Many thanks for this response. I have made the change and am now monitoring the situation. I will re-post my conclusions here. With thanks!

---

### Post by aridus on 2015-01-19
An interim report: I have been successfully using the wirless for the previous 3 hours. I will make one final report tomorrow, following further use. 

Thank you chili555 for the reference to the bug in launchpad.

---

### Post by aridus on 2015-01-19
A further report: after successfully using the wireless connection all afternoon (and I could switch between 2.4 and 5.0 frequencies) I suspended the laptop. Upon resume I could not connect to either frequency. The output of dmesg | grep iwl was 
```
martin@martin:~$ dmesg | grep iwl
[ 6162.337110] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[ 6165.395377] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 6165.395628] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9025.567346] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9025.567595] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9072.128213] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 16
[ 9072.128216] iwlwifi 0000:02:00.0: Current SW read_ptr 246 write_ptr 19
[ 9072.128252] iwl data: 00000000: 3f 00 00 00 00 00 00 00 00 00 c0 ff 00 00 00 00  ?...............
[ 9072.128264] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[ 9072.128275] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc0110005
[ 9072.128286] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[ 9072.128297] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x80300006
[ 9072.128307] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[ 9072.128318] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[ 9072.128329] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[ 9072.128340] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x00709059
[ 9072.128388] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [7,7]
[ 9072.128435] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 9072.128482] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [124,124]
[ 9072.128530] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128577] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128624] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128672] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128719] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128766] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128814] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [90,90]
[ 9072.128862] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128909] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.128957] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.129005] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.129052] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.129100] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.129148] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [246,19]
[ 9072.129197] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.129244] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9072.129291] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.132420] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 0
[ 9074.132424] iwlwifi 0000:02:00.0: Current SW read_ptr 7 write_ptr 8
[ 9074.132460] iwl data: 00000000: 80 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 9074.132472] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[ 9074.132483] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc0110005
[ 9074.132494] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[ 9074.132504] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x80300007
[ 9074.132515] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[ 9074.132526] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[ 9074.132537] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[ 9074.132548] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x00709059
[ 9074.132596] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [7,8]
[ 9074.132643] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 9074.132690] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [124,124]
[ 9074.132738] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.132801] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.132849] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.132896] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.132944] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.132992] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133039] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [90,90]
[ 9074.133087] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133135] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133183] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133230] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133278] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133325] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133373] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [246,20]
[ 9074.133421] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133468] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9074.133515] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9079.517862] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9079.518114] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9086.925067] iwlwifi 0000:02:00.0: No association and the time event is over already...
[ 9101.410571] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9101.410825] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9279.415117] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9279.415370] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9368.356520] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 16
[ 9368.356524] iwlwifi 0000:02:00.0: Current SW read_ptr 2 write_ptr 163
[ 9368.356561] iwl data: 00000000: fc ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 9368.356572] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[ 9368.356583] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc011000f
[ 9368.356594] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[ 9368.356605] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x8030000b
[ 9368.356616] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[ 9368.356627] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[ 9368.356638] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[ 9368.356649] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x00709080
[ 9368.356697] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [12,12]
[ 9368.356745] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 9368.356792] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [120,120]
[ 9368.356840] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.356888] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.356935] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.356984] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357034] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357082] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357130] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [129,129]
[ 9368.357178] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357225] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357273] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357321] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357372] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357421] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357470] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [2,163]
[ 9368.357520] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357569] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9368.357617] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.365756] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 0
[ 9370.365759] iwlwifi 0000:02:00.0: Current SW read_ptr 12 write_ptr 13
[ 9370.365797] iwl data: 00000000: 00 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 9370.365808] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[ 9370.365819] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc011000f
[ 9370.365830] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[ 9370.365841] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x8030000c
[ 9370.365853] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[ 9370.365864] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[ 9370.365875] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[ 9370.365886] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x00709080
[ 9370.365935] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [12,13]
[ 9370.365983] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 9370.366031] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [120,120]
[ 9370.366079] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366127] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366175] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366223] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366271] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366319] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366367] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [129,129]
[ 9370.366414] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366462] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366510] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366558] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366606] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366654] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366702] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [2,168]
[ 9370.366750] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366798] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9370.366846] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 9809.946253] Modules linked in: hid_generic hidp nls_utf8 udf crc_itu_t ctr ccm xt_conntrack ipt_REJECT ses enclosure pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) nvram xt_CHECKSUM iptable_mangle ipt_MASQUERADE iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack xt_tcpudp bridge stp llc iptable_filter ip_tables x_tables uas usb_storage uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media hid_multitouch snd_hda_codec_hdmi joydev arc4 btusb dell_wmi hid_rmi sparse_keymap dell_laptop dcdbas intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel dm_multipath scsi_dh kvm iwlmvm mac80211 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel iwlwifi aes_x86_64 lrw snd_hda_codec_realtek gf128mul glue_helper snd_hda_codec_generic
[ 9809.946390] Modules linked in: hid_generic hidp nls_utf8 udf crc_itu_t ctr ccm xt_conntrack ipt_REJECT ses enclosure pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) nvram xt_CHECKSUM iptable_mangle ipt_MASQUERADE iptable_nat nf_conntrack_ipv4 nf_defrag_ipv4 nf_nat_ipv4 nf_nat nf_conntrack xt_tcpudp bridge stp llc iptable_filter ip_tables x_tables uas usb_storage uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core v4l2_common videodev media hid_multitouch snd_hda_codec_hdmi joydev arc4 btusb dell_wmi hid_rmi sparse_keymap dell_laptop dcdbas intel_rapl x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel dm_multipath scsi_dh kvm iwlmvm mac80211 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel iwlwifi aes_x86_64 lrw snd_hda_codec_realtek gf128mul glue_helper snd_hda_codec_generic
[ 9810.818075] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9810.818321] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[ 9818.075576] iwlwifi 0000:02:00.0: No association and the time event is over already...
```

I rebooted and could connect on 2.4 but not on 5.0. The output of grep iwl when connected on 2.4 was: 
```
[    3.056511] iwlwifi 0000:02:00.0: irq 59 for MSI/MSI-X
[    3.070285] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    3.114035] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.114118] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.114365] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.089407] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.096759] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.097015] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled

```

and when apparently connected (icon in panel shows connection but cannot access internet) on 5.0 the output of grep was:
```
[    3.056511] iwlwifi 0000:02:00.0: irq 59 for MSI/MSI-X
[    3.070285] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    3.114035] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.114118] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.114365] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.089407] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.096759] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.097015] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
martin@martin:~$ dmesg | grep iwl
[    3.056511] iwlwifi 0000:02:00.0: irq 59 for MSI/MSI-X
[    3.070285] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    3.114035] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.114118] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.114365] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.089407] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.096759] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.097015] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   96.818071] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 16
[   96.818075] iwlwifi 0000:02:00.0: Current SW read_ptr 139 write_ptr 76
[   96.818133] iwl data: 00000000: 00 f8 ff 07 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   96.818146] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[   96.818157] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc011009a
[   96.818169] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[   96.818180] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x8030000b
[   96.818192] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[   96.818203] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[   96.818215] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[   96.818226] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x0070907e
[   96.818275] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [12,12]
[   96.818324] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[   96.818372] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [131,131]
[   96.818421] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818469] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818518] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818566] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818614] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818663] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818711] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [127,127]
[   96.818760] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818809] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818859] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818908] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.818957] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.819006] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.819055] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [139,76]
[   96.819103] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.819152] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   96.819201] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.828286] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 0
[   98.828291] iwlwifi 0000:02:00.0: Current SW read_ptr 12 write_ptr 13
[   98.828329] iwl data: 00000000: 00 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   98.828341] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[   98.828353] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc011009a
[   98.828364] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[   98.828376] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x8030000c
[   98.828387] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[   98.828399] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[   98.828410] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[   98.828422] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x0070907e
[   98.828471] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [12,13]
[   98.828519] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[   98.828568] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [131,131]
[   98.828616] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.828665] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.828713] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.828762] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.828810] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.828859] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.828907] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [127,127]
[   98.828956] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829004] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829054] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829104] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829155] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829211] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829260] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [139,77]
[   98.829308] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829357] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   98.829405] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]

```

With thanks.

---

### Post by chili555 on 2015-01-19
We see the symptom here again in both dmesg listings:> fail to flush all tx fifo queues Q 16In the referenced bug report, there is a link to a patched kernel, also known in Ubuntu as linux-image: [http://people.canonical.com/~sforshee/iwlwifi/utopic/](http://people.canonical.com/~sforshee/iwlwifi/utopic/)

I suggest you download and install the 64-bit (amd64) deb files for linux-image and linux-image-extras and install them with:```
cd ~/Downloads
```...or wherever you downloaded the files.```
sudo dpkg linux-image*.deb
```Reboot into the newer kernel and test. As before, if the performance isn't fixed, please post:```
dmesg | grep iwl
```

---

### Post by aridus on 2015-01-19
Thank you. Following installation of the two files you suggested and booting wiith the correct kernel, the problem persists. Herewith

```
dmesg | grep iwl
[    0.000000] Linux version 3.16.0-23-generic (sforshee@gloin) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #30+iwlwifi201410162230 SMP Thu Oct 16 20:42:30 UTC 2014 (Ubuntu 3.16.0-23.30+iwlwifi201410162230-generic 3.16.4)
[    3.288174] iwlwifi 0000:02:00.0: irq 60 for MSI/MSI-X
[    3.296928] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    3.332156] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.332241] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.332513] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.635394] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.961255] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.961505] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
martin@martin:~$ dmesg | grep iwl
[    0.000000] Linux version 3.16.0-23-generic (sforshee@gloin) (gcc version 4.9.1 (Ubuntu 4.9.1-16ubuntu6) ) #30+iwlwifi201410162230 SMP Thu Oct 16 20:42:30 UTC 2014 (Ubuntu 3.16.0-23.30+iwlwifi201410162230-generic 3.16.4)
[    3.288174] iwlwifi 0000:02:00.0: irq 60 for MSI/MSI-X
[    3.296928] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    3.332156] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.332241] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.332513] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.635394] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.961255] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.961505] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[   92.434269] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 16
[   92.434274] iwlwifi 0000:02:00.0: Current SW read_ptr 136 write_ptr 5
[   92.434311] iwl data: 00000000: 00 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   92.434323] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[   92.434335] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc0110097
[   92.434346] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[   92.434358] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x80300006
[   92.434369] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[   92.434381] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[   92.434392] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[   92.434404] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x0070905a
[   92.434453] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [7,7]
[   92.434501] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[   92.434550] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [126,126]
[   92.434598] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.434647] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.434695] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.434744] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.434792] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.434840] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.434889] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [91,91]
[   92.434938] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.434986] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.435035] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.435084] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.435133] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.435181] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.435229] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [136,5]
[   92.435278] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.435326] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   92.435375] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.442532] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues Q 0
[   94.442537] iwlwifi 0000:02:00.0: Current SW read_ptr 7 write_ptr 8
[   94.442575] iwl data: 00000000: 80 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[   94.442587] iwlwifi 0000:02:00.0: FH TRBs(0) = 0x00000000
[   94.442599] iwlwifi 0000:02:00.0: FH TRBs(1) = 0xc0110097
[   94.442610] iwlwifi 0000:02:00.0: FH TRBs(2) = 0x00000000
[   94.442622] iwlwifi 0000:02:00.0: FH TRBs(3) = 0x80300007
[   94.442633] iwlwifi 0000:02:00.0: FH TRBs(4) = 0x00000000
[   94.442665] iwlwifi 0000:02:00.0: FH TRBs(5) = 0x00000000
[   94.442677] iwlwifi 0000:02:00.0: FH TRBs(6) = 0x00000000
[   94.442688] iwlwifi 0000:02:00.0: FH TRBs(7) = 0x0070905a
[   94.442738] iwlwifi 0000:02:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [7,8]
[   94.442786] iwlwifi 0000:02:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[   94.442835] iwlwifi 0000:02:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [126,126]
[   94.442883] iwlwifi 0000:02:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.442931] iwlwifi 0000:02:00.0: Q 4 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.442980] iwlwifi 0000:02:00.0: Q 5 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443028] iwlwifi 0000:02:00.0: Q 6 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443077] iwlwifi 0000:02:00.0: Q 7 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443125] iwlwifi 0000:02:00.0: Q 8 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443174] iwlwifi 0000:02:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [91,91]
[   94.443222] iwlwifi 0000:02:00.0: Q 10 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443271] iwlwifi 0000:02:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443319] iwlwifi 0000:02:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443367] iwlwifi 0000:02:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443416] iwlwifi 0000:02:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443464] iwlwifi 0000:02:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443513] iwlwifi 0000:02:00.0: Q 16 is active and mapped to fifo 1 ra_tid 0x0000 [136,7]
[   94.443561] iwlwifi 0000:02:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443610] iwlwifi 0000:02:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[   94.443658] iwlwifi 0000:02:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]

```

'...fail to flush...' is still there.

With thanks.

---

### Post by jeremy31 on 2015-01-19
I think you should file a bug report [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+filebug) and mention that the proposed fix from Seth Forshee doesn't fix it for you

---

### Post by chili555 on 2015-01-19
I suggest we install the iwlwifi suite from 3.18.1 where there is some indication this may be fixed. To compile the driver suite requires linux-headers which are unavailable for download for linux-image-3.16.0-23-generic_3.16.0-23.30+iwlwifi201410162230_amd64. Therefore, reboot, get to the GRUB menu by pressing both Shift keys and select the original 3.16.0-29-generic kernel you started with. Then remove the ineffective kernel:```
sudo apt-get purge linux-image-3.16.0-23-generic_3.16.0-23.30+iwlwifi201410162230_amd64
sudo apt-get purge linux-image-extras-3.16.0-23-generic_3.16.0-23.30+iwlwifi201410162230_amd64 
```

Please download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.18.1/backports-3.18.1-1.tar.xz)

Right-click and select 'Extract Here.' Now, in the terminal:```
sudo apt-get install linux-headers-generic build-essential
cd ~/Desktop/backports-3.18.1-1
make defconfig-iwlwifi
make
sudo make install
sudo reboot
```

---

### Post by aridus on 2015-01-20
Thank you again chili555! I have successfully followed your instructions. So far all is well and I can connect on both 2.4 and 5.0. The output of dmesg | grep iwl is currently:
```
[    3.183683] iwlwifi 0000:02:00.0: irq 60 for MSI/MSI-X
[    3.185701] iwlwifi 0000:02:00.0: Direct firmware load failed with error -2
[    3.185704] iwlwifi 0000:02:00.0: Falling back to user helper
[    4.086827] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    4.098052] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    4.098133] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.098382] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.309693] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.317851] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.318097] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
```
I will monitor the situation as I work today and report back.
With thanks1

---

### Post by aridus on 2015-01-20
Thank you jeremy31 for the suggestion of filing a bug report. I will do so once I have determined whether chili555's solution (see below) has solved the problem. With thanks!

---

### Post by aridus on 2015-01-20
Following on from my post this morning, I have used the laptop all day, rebooting several times, and using wireless on both 2.4 and 5.0. All seems well. I t is a great relief to be able to work all day without being encumbered by this problem! The current output of 

dmesg | grep iwl

remains the same as after I followed chili555's earlier instructions:

```
[    3.877943] iwlwifi 0000:02:00.0: irq 62 for MSI/MSI-X
[    3.878745] iwlwifi 0000:02:00.0: Direct firmware load failed with error -2
[    3.878749] iwlwifi 0000:02:00.0: Falling back to user helper
[    3.883696] iwlwifi 0000:02:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    3.908404] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    3.908490] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    3.908770] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.128970] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.136883] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled
[    4.137140] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled

```

Is there anything in this output of relevance to the situation?

With thansk< Martin

---

### Post by chili555 on 2015-01-20
The only thing that's informative is what's not there; ugly warnings about fifo queues. Your dmesg looks entirely fine and the performance seems to agree.

You have compiled the driver for your currently running kernel only. When Update Manager installs a later linux-image, after the required reboot, re-compile:```
cd ~/Desktop/backports-3.18.1-1
make clean
make defconfig-iwlwifi
make
sudo make install
sudo reboot
```Please retain the files and these instructions for that time.

The searchers with fifo queue issues will appreciate it if you'd use thread tools at the top to mark Solved.

Have fun!

---

### Post by aridus on 2015-01-20
chili555, thanks again. I have added a note at [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1270808](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1270808).

You have also answered my final question (what to do when a later linux-image is installed), thank you.

I will now mark this thread as solved, yeah!

---

### Post by cnbiz850 on 2015-06-06
Hi aridus,

Is this about the new XPS 13 of 2015?  If so then you got Ubuntu to run well on it?  Would you kindly share about the progress in installing it?  I am also looking to buy this laptop.

---

