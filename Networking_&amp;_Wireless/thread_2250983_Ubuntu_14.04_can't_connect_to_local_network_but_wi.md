---
title: "Ubuntu 14.04 can't connect to local network but wireless is fine"
date: 2014-11-01
forum: Networking &amp; Wireless
---

### Post by berndt3 on 2014-11-01
new user here. I've been trying to figure this out the past few days.  I'm running Ubuntu Studio 14.04 and the wireless works fine, but it won't connect to a local network (a macbook).  It sees the network, but won't connect. Everything else is fine. 
I've tried a few things I've found on the forums, but to no avail, and I'm not even sure they are applicable..like installing fresh Samba, trying to manually connect via terminal.  Any help greatly appreciated, and if you need more info, please tell me.

---

### Post by wildmanne39 on 2014-11-01
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here.
Thanks

---

### Post by berndt3 on 2014-11-01
########## wireless info START ##########

Report from: 01 Nov 2014 15:22 CET +0100

Booted last: 01 Nov 2014 00:00 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-lowlatency #57-Ubuntu SMP PREEMPT Tue Jul 15 04:23:12 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu Studio

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8324]
    Kernel driver in use: ATL1E

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: AzureWave AW-GE780 802.11bg Wireless Mini PCIe Card [1a3b:1026]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 001 Device 002: ID 093a:2700 Pixart Imaging, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: eeepc-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 134977  0 
ath                    23922  1 ath5k
mac80211              558411  1 ath5k
cfg80211              421682  3 ath,ath5k,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::222:43ff:fe37:cf86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19049506 (19.0 MB)  TX bytes:1310981 (1.3 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"EasyBox-28D950"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'EasyBox-28D950' [AN21]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:97   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            ATL1E
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [EasyBox-28D950] ----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ALICE-WLAN82:    Infra, <MAC 'ALICE-WLAN82' [AN1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 72 WPA2
    o2-WLAN58:       Infra, <MAC 'o2-WLAN58' [AN2]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 40 WPA2
    EasyBox-182302:  Infra, <MAC 'EasyBox-182302' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Malt2SpeedLAN:   Infra, <MAC 'Malt2SpeedLAN' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA2
    Kaplan:          Infra, <MAC 'Kaplan' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    o2-WLAN96:       Infra, <MAC 'o2-WLAN96' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA2
    ALICE-WLAN07:    Infra, <MAC 'ALICE-WLAN07' [AN7]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 15 WPA2
    FRITZ!Box 7312:  Infra, <MAC 'FRITZ!Box 7312' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    WLAN-BC05437F5A57: Infra, <MAC 'WLAN-BC05437F5A57' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Thom_D0041963:   Infra, <MAC 'Thom_D0041963' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    WLAN-1E4D63:     Infra, <MAC 'WLAN-1E4D63' [AN11]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 4 WPA2
    sculpt:          Infra, <MAC 'sculpt' [AN12]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    Maedcheninternat:Infra, <MAC 'Maedcheninternat' [AN13]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 15 WPA2
    ALICE-WLAN16:    Infra, <MAC 'ALICE-WLAN16' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    EasyBox-12A246:  Infra, <MAC 'EasyBox-12A246' [AN15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA WPA2
    o2-WLAN18:       Infra, <MAC 'o2-WLAN18' [AN16]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 14 WPA2
    o2-WLAN90:       Infra, <MAC 'o2-WLAN90' [AN17]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 4 WPA2
    OLALAN:          Infra, <MAC 'OLALAN' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 7 WPA2
    EasyBox-5C1506:  Infra, <MAC 'EasyBox-5C1506' [AN19]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    ALICE-WLAN18:    Infra, <MAC 'ALICE-WLAN18' [AN20]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 0 WPA2
    *EasyBox-28D950: Infra, <MAC 'EasyBox-28D950' [AN21]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA WPA2
    EasyBox-BD9C41:  Infra, <MAC 'EasyBox-BD9C41' [AN22]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    ALICE-WLAN:      Infra, <MAC 'ALICE-WLAN' [AN23]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 4 WEP
    FRITZ!Box Fon WLAN 7112: Infra, <MAC 'FRITZ!Box Fon WLAN 7112' [AN24]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    MaltLAN:         Infra, <MAC 'MaltLAN' [AN25]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Zuhause:         Infra, <MAC 'Zuhause' [AN26]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2
    Finn:            Infra, <MAC 'Finn' [AN27]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    belkin.481:      Infra, <MAC 'belkin.481' [AN28]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 0 WPA2
    MaltLAN:         Infra, <MAC 'MaltLAN' [AN29]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    FRITZ!Box 7312:  Infra, <MAC 'FRITZ!Box 7312' [AN30]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    EasyBox-152814:  Infra, <MAC 'EasyBox-152814' [AN31]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    Plejade:         Infra, <MAC 'Plejade' [AN32]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WEP

  IPv4 Settings:
    Address:         192.168.2.102
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

[ifupdown]
managed=false

##### NetworkManager profiles ###########

Acquisition of admin privileges failed.

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

Acquisition of admin privileges failed.

##### module infos ######################

[ath5k]
filename:       /lib/modules/3.13.0-32-lowlatency/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     F36818A2F0BCB2B0CC9BB8C
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.13.0-32-lowlatency SMP preempt mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        CC:C9:1C:30:25:46:99:E5:C4:31:1F:BF:57:75:77:48:78:81:26:95
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.13.0-32-lowlatency/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-lowlatency SMP preempt mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        CC:C9:1C:30:25:46:99:E5:C4:31:1F:BF:57:75:77:48:78:81:26:95
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-32-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-lowlatency SMP preempt mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        CC:C9:1C:30:25:46:99:E5:C4:31:1F:BF:57:75:77:48:78:81:26:95
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-lowlatency SMP preempt mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        CC:C9:1C:30:25:46:99:E5:C4:31:1F:BF:57:75:77:48:78:81:26:95
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 3503.517234] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3503.518876] wlan0: Selected IBSS BSSID <MAC address> based on configured SSID
[ 3503.529743] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3503.538172] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3549.253494] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3552.123995] wlan0: authenticate with <MAC 'EasyBox-28D950' [AN21]>
[ 3552.128677] wlan0: send auth to <MAC 'EasyBox-28D950' [AN21]> (try 1/3)
[ 3552.131273] wlan0: authenticated
[ 3552.132105] wlan0: associate with <MAC 'EasyBox-28D950' [AN21]> (try 1/3)
[ 3552.134553] wlan0: RX AssocResp from <MAC 'EasyBox-28D950' [AN21]> (capab=0x411 status=0 aid=1)
[ 3552.135421] wlan0: associated
[ 3552.135527] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3552.180876] ath: EEPROM regdomain: 0x8114
[ 3552.180888] ath: EEPROM indicates we should expect a country code
[ 3552.180894] ath: doing EEPROM country->regdmn map search
[ 3552.180900] ath: country maps to regdmn code: 0x37
[ 3552.180906] ath: Country alpha2 being used: DE
[ 3552.180911] ath: Regpair used: 0x37
[ 3552.180919] ath: regdomain 0x8114 dynamically updated by country IE
[ 3564.977850] wlan0: deauthenticating from <MAC 'EasyBox-28D950' [AN21]> by local choice (reason=3)
[ 3566.347480] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3566.349705] wlan0: Selected IBSS BSSID <MAC address> based on configured SSID
[ 3566.357752] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3566.377692] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 3612.253473] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 3615.130434] wlan0: authenticate with <MAC 'EasyBox-28D950' [AN21]>
[ 3615.135469] wlan0: send auth to <MAC 'EasyBox-28D950' [AN21]> (try 1/3)
[ 3615.137149] wlan0: authenticated
[ 3615.138630] wlan0: associate with <MAC 'EasyBox-28D950' [AN21]> (try 1/3)
[ 3615.141572] wlan0: RX AssocResp from <MAC 'EasyBox-28D950' [AN21]> (capab=0x411 status=0 aid=1)
[ 3615.142440] wlan0: associated
[ 3615.142557] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3615.174206] ath: EEPROM regdomain: 0x8114
[ 3615.174218] ath: EEPROM indicates we should expect a country code
[ 3615.174223] ath: doing EEPROM country->regdmn map search
[ 3615.174229] ath: country maps to regdmn code: 0x37
[ 3615.174234] ath: Country alpha2 being used: DE
[ 3615.174239] ath: Regpair used: 0x37
[ 3615.174245] ath: regdomain 0x8114 dynamically updated by country IE
[ 5212.817822] wlan0: deauthenticating from <MAC 'EasyBox-28D950' [AN21]> by local choice (reason=3)
[ 5262.001449] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5262.002643] wlan0: Selected IBSS BSSID <MAC address> based on configured SSID
[ 5262.012775] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5262.049386] wlan0: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge)
[ 5307.249189] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5310.159579] wlan0: authenticate with <MAC 'EasyBox-28D950' [AN21]>
[ 5310.165697] wlan0: send auth to <MAC 'EasyBox-28D950' [AN21]> (try 1/3)
[ 5310.167608] wlan0: authenticated
[ 5310.169189] wlan0: associate with <MAC 'EasyBox-28D950' [AN21]> (try 1/3)
[ 5310.174940] wlan0: RX AssocResp from <MAC 'EasyBox-28D950' [AN21]> (capab=0x411 status=0 aid=1)
[ 5310.175807] wlan0: associated
[ 5310.176340] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5310.211861] ath: EEPROM regdomain: 0x8114
[ 5310.211873] ath: EEPROM indicates we should expect a country code
[ 5310.211880] ath: doing EEPROM country->regdmn map search
[ 5310.211886] ath: country maps to regdmn code: 0x37
[ 5310.211892] ath: Country alpha2 being used: DE
[ 5310.211898] ath: Regpair used: 0x37
[ 5310.211905] ath: regdomain 0x8114 dynamically updated by country IE

########## wireless info END ############

---

### Post by berndt3 on 2014-11-01
oh, sorry:) I see you meant posting results here, not *here.*

in any case, I'm not able to tell what's right or wrong in this output. I also haven't found a similar topic in searching the forums. wireless works fine, on it right now. But since upgrading from carrot & corriander, I can't connect to the mac's local wireless network.

---

### Post by wildmanne39 on 2014-11-01
Please try:
```
sudo modprobe -rv ath5k
sudo modprobe -v ath5k nohwcrypt=y
```
if it helps we will need to make it permantent, do not reboot after running the command or the changes will be lost.
Thanks

---

### Post by berndt3 on 2014-11-01
no dice. nothing works now, but I'll reboot.

---

