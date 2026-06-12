---
title: "Netwok Icon Missing; I can't View Network Info; I can't Connect to Internet"
date: 2015-04-28
forum: Networking &amp; Wireless
---

### Post by oshupa on 2015-04-28
Hello Y'all,

I have just installed Ubuntu 15.04. Initially my network icon was visible on top right corner and I was able to connect to my home wifi network and browse. But now I have noticed that the network icon is missing and I cannot connect to any network (wireless or wired) as a result. (This happened after instaling an HP pinter.)

What to do?

The following is the result from the Wireless Script:

```
########## wireless info START ##########

Report from: 28 Apr 2015 15:03 CAT +0200

Booted last: 28 Apr 2015 18:05 CAT +0200

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 15.04
Release:    15.04
Codename:    vivid

##### kernel ############################

Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 130 [8086:0896] (rev 34)
    Subsystem: Intel Corporation Centrino Wireless-N 130 BGN [8086:5005]
    Kernel driver in use: iwlwifi

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Samsung Electronics Co Ltd Device [144d:c606]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 004: ID 8086:0189 Intel Corp. 
Bus 002 Device 006: ID 0781:556b SanDisk Corp. 
Bus 002 Device 005: ID 12d1:142d Huawei Technologies Co., Ltd. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2232:1020  
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: samsung-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: samsung-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                237568  0 
mac80211              720896  1 iwldvm
iwlwifi               196608  1 iwldvm
cfg80211              540672  3 iwlwifi,mac80211,iwldvm

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
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dea9:71ff:fe66:fa26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:238 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:137908 (137.9 KB)  TX bytes:26179 (26.1 KB)

wwan0     Link encap:Ethernet  HWaddr <MAC 'wwan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

wwan0     no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Oshupa"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Oshupa' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:74   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    1024   0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

Error: NetworkManager is not running.

Error: NetworkManager is not running.

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Oshupa]] (600 root)
[connection] id=Oshupa | type=wifi
[wifi] ssid=Oshupa | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Africa/Lusaka (based on set time zone)

country US: DFS-FCC
    (2402 - 2472 @ 40), (3, 27), (N/A)
    (5170 - 5250 @ 40), (3, 17), (N/A)
    (5250 - 5330 @ 40), (3, 20), (0 ms), DFS
    (5490 - 5600 @ 40), (3, 20), (0 ms), DFS
    (5650 - 5710 @ 40), (3, 20), (0 ms), DFS
    (5735 - 5835 @ 40), (3, 30), (N/A)
    (57240 - 63720 @ 2160), (N/A, 40), (N/A)

##### iwlist channels ###################

eth0      no frequency information.

wwan0     no frequency information.

lo        no frequency information.

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

eth0      Interface doesn't support scanning.

wwan0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Oshupa' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"Oshupa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000073a924610
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     259D494A97B601F302CD790
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
firmware:       iwlwifi-7265D-10.ucode
firmware:       iwlwifi-7265-10.ucode
firmware:       iwlwifi-3165-10.ucode
firmware:       iwlwifi-3160-10.ucode
firmware:       iwlwifi-7260-10.ucode
firmware:       iwlwifi-8000-10.ucode
srcversion:     ADFD966DF2A9D56EE93BE48
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
uapsd_disable: Y
wd_disable: 1

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
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0896 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   31.625795] cdc_ether 2-1.1:1.3 wwan0: register 'cdc_ether' at usb-0000:00:1d.0-1.1, Mobile Broadband Network Device, <MAC 'wwan0' [IF]>
[   32.419150] iwlwifi 0000:01:00.0: L1 Enabled - LTR Disabled
[   32.425673] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[   32.491969] iwlwifi 0000:01:00.0: L1 Enabled - LTR Disabled
[   32.498488] iwlwifi 0000:01:00.0: Radio type=0x2-0x2-0x1
[   33.058798] wlan0: authenticate with <MAC 'Oshupa' [AC1]>
[   33.059957] wlan0: send auth to <MAC 'Oshupa' [AC1]> (try 1/3)
[   33.062424] wlan0: authenticated
[   33.062654] iwlwifi 0000:01:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   33.062656] iwlwifi 0000:01:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   33.062658] iwlwifi 0000:01:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   33.062660] wlan0: waiting for beacon from <MAC 'Oshupa' [AC1]>
[   33.069449] wlan0: associate with <MAC 'Oshupa' [AC1]> (try 1/3)
[   33.071875] wlan0: RX AssocResp from <MAC 'Oshupa' [AC1]> (capab=0x431 status=0 aid=3)
[   33.074924] wlan0: associated

########## wireless info END ############
```

---

### Post by michi1983 on 2015-04-28
Well, obviously you are connected to the Internet.
It just looks like your network-manager applet is kind of 'hanging'.
You could try a ```
sudo killall nm-applet; nm-applet
``` in terminal.

---

### Post by slickymaster on 2015-04-28
@oshupa:
I've edited your firs post, adding code tags to it because output code, posted as plain text, loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. In the future, [please use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") to make your post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by oshupa on 2015-04-28
slickymaster,
Thanks for the edit. 


michi1983
I tried that code in terminal. It didnt solve the problem.

When I open the network setting under system settings, I still don't see the wireless and wired network icons and settings.

---

### Post by oshupa on 2015-05-03
This problem just resolved on its own. I do not know how to explain it. And I am not sure it will recur. Thanks for your assistance.

---

### Post by Rana_Muhammad_Zees on 2015-09-10
I am experiencing the same problem. I've tried the above code. This is the result:
```
nm-applet: no process found

(nm-applet:4313): nm-applet-WARNING **: Cannot grab information for modem at /org/freedesktop/ModemManager1/Modem/0: No ModemManager support


(nm-applet:4313): nm-applet-WARNING **: ModemManager is not available for modem at /org/freedesktop/ModemManager1/Modem/0
**
nm-applet:ERROR:applet-device-broadband.c:636:get_icon: assertion failed: (info)
Aborted (core dumped)



```

---

