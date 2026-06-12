---
title: "Wireless ground to a halt after update."
date: 2014-12-25
forum: Networking &amp; Wireless
---

### Post by warren3 on 2014-12-25
Hi.

I had an update which required a restart.  Since then my  wireless has crapped out.  I get a signal and the first page loads up in  the browser.  After that all I get is a spinning circle and pages take  an age to load.

I did change my wireless PCI-E card before the update from a Realtek to Intel  7260.  I didn't reinstall Ubuntu or anything I just changed the card and  booted up and it was fine.  Since the update though it is not working.

I am currently using an older kernel (3.13.0-40) at the momemt because that seems to be fine.  3.13.0-43  I get problems as described above.

Any help would be appreciated.

---

### Post by Hadaka on 2014-12-25
Hi, please post the wireless script from here
 [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks

---

### Post by warren3 on 2014-12-26
Thanks.

Here we go:

```

########## wireless info START ##########

Report from: 26 Dec 2014 10:41 GMT +0000

Booted last: 26 Dec 2014 10:38 GMT +0000

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)
    Subsystem: Intel Corporation Wireless-N 7260 [8086:4062]
    Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 002: ID 062a:4101 Creative Labs 
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

iwlmvm                189813  0 
mac80211              630653  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm

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

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fde2:f42b:506e:0:f181:1276:c574:a328/64 Scope:Global
          inet6 addr: fde2:f42b:506e:0:8286:f2ff:fe96:8bab/64 Scope:Global
          inet6 addr: fe80::8286:f2ff:fe96:8bab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3127848 (3.1 MB)  TX bytes:226884 (226.8 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"SKYDBE00"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'SKYDBE00' [AC1]>   
          Bit Rate=130 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:86   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan1
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### nm-tool ###########################

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

- Device: wlan1  [SKYDBE00] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:
    Speed:           130 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *SKYDBE00:       Infra, <MAC 'SKYDBE00' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA WPA2
    SKY56044:        Infra, <MAC 'SKY56044' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA
    SKYABA6D:        Infra, <MAC 'SKYABA6D' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA2
    BTHub3-CD08:     Infra, <MAC 'BTHub3-CD08' [AN4]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2

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

[[/etc/NetworkManager/system-connections/SKYDBE00]] (600 root)
[connection] id=SKYDBE00 | type=802-11-wireless
[802-11-wireless] ssid=SKYDBE00 | mac-address=<MAC 'wlan1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan1     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)

wlan1     Scan completed :
          Cell 01 - Address: <MAC 'SKYDBE00' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"SKYDBE00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000fb7a52f
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SKY56044' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"SKY56044"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000575b4990602
                    Extra: Last beacon: 52ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SKYABA6D' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"SKYABA6D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f8a26183
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
           eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     D028925649B62FC6CDB3FDB
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     446B3604A9C5461044DD691
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-43-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     72E4ECE7C2CBAA62E552DCE
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        55:AB:2F:E2:8E:D5:C6:0D:F9:58:71:50:D1:73:4C:92:0E:A7:B8:18
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
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[    4.290457] iwlwifi 0000:02:00.0: irq 64 for MSI/MSI-X
[    4.294556] iwlwifi 0000:02:00.0: loaded firmware version 22.24.8.0 op_mode iwlmvm
[    4.335618] iwlwifi 0000:02:00.0: Detected Intel(R) Wireless N 7260, REV=0x144
[    4.335944] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    4.347225] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[    4.555843] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    4.604854] systemd-udevd[363]: renamed network interface wlan0 to wlan1
[    5.026372] iwlwifi 0000:02:00.0: L1 Enabled - LTR Enabled (repeated 2 times)
[    5.046971] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[    5.870991] wlan1: authenticate with <MAC 'SKYDBE00' [AC1]>
[    5.875086] wlan1: send auth to <MAC 'SKYDBE00' [AC1]> (try 1/3)
[    5.876904] wlan1: authenticated
[    5.877186] wlan1: associate with <MAC 'SKYDBE00' [AC1]> (try 1/3)
[    5.880598] wlan1: RX AssocResp from <MAC 'SKYDBE00' [AC1]> (capab=0x411 status=0 aid=1)
[    5.881594] wlan1: associated
[    5.881620] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

########## wireless info END ############

```

For some reason it seems to be acting OK today with the latest kernel.  Usually I browse for 5 minutes and then I just get a spinning circle in FF and nothing loads.  But today it seems fine.  Very strange. Hopefully the above code may shed some light on the matter.

edit - its now gone back to not working again.

---

### Post by Hadaka on 2014-12-26
give this a try..
[http://askubuntu.com/questions/411475/intel-wireless-7260-driver-crashes-how-do-i-work-around-it/411515#411515](http://askubuntu.com/questions/411475/intel-wireless-7260-driver-crashes-how-do-i-work-around-it/411515#411515)

---

### Post by warren3 on 2015-01-04
> **Hadaka said:**
> give this a try..
[http://askubuntu.com/questions/411475/intel-wireless-7260-driver-crashes-how-do-i-work-around-it/411515#411515](http://askubuntu.com/questions/411475/intel-wireless-7260-driver-crashes-how-do-i-work-around-it/411515#411515)

Hello again.

OK so after using the previous kernel pretty much for a week I decided to try the updated firmware using the latest kernel and I still have the same problem.  Anything else I could try?

---

### Post by Hadaka on 2015-01-04
try these changes,,
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
boot
then reset your router to wpa2 no tkip
also set your network mgr to ignore for the wireless ipv6 setting
then do..
```
echo "options iwlwifi 11n_disable=8" /etc/modprobe.d/iwlwifi.conf
```

---

