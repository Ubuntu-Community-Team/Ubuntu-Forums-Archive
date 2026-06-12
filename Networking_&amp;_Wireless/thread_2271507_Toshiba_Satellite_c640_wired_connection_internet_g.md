---
title: "Toshiba Satellite c640 wired connection internet getting off periodically on 14.04"
date: 2015-03-30
forum: Networking &amp; Wireless
---

### Post by nitin7 on 2015-03-30
Hi I am using Toshiba c640 laptop. On windows internet works fine using wired connection but in Ubuntu 14.04 wired internet connection getting disconnected periodically....PLz. help

---

### Post by praseodym on 2015-03-30
Please run the wireless-script from the sticky thread and show the output.

Thanks.

---

### Post by nitin7 on 2015-03-31
Output of the command lspci -nnk

00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Toshiba America Info Systems Device [1179:fcf0]
    Kernel driver in use: i915
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c
02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6613]
    Kernel driver in use: ath9k

---

### Post by nitin7 on 2015-03-31
hi praseodym...
i am novice in linux ...so kindly elaborate what command the type....

---

### Post by nitin7 on 2015-03-31
output of the command ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:26:6c:dd:cc:f3  
          inet addr:172.16.216.254  Bcast:172.16.216.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fedd:ccf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13642 errors:0 dropped:146 overruns:0 frame:0
          TX packets:36215 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3326464 (3.3 MB)  TX bytes:6439537 (6.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1151875 (1.1 MB)  TX bytes:1151875 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:4d:d8:ef  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nitin@nitin-Satellite-C640:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:6c:dd:cc:f3  
          inet addr:172.16.216.254  Bcast:172.16.216.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fedd:ccf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13693 errors:0 dropped:146 overruns:0 frame:0
          TX packets:36307 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:3331561 (3.3 MB)  TX bytes:6455008 (6.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:14610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1153950 (1.1 MB)  TX bytes:1153950 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:4d:d8:ef  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by nitin7 on 2015-03-31
hi... i am using wired connection and typed the command lspci -nnk

---

### Post by praseodym on 2015-03-31
Deactivate the hardware encryption:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by nitin7 on 2015-04-01
########## wireless info START ##########

Report from: 01 Apr 2015 15:37 IST +0530

Booted last: 01 Apr 2015 15:35 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:6613]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 10f1:1a36 Importek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

ath3k                  13318  0 
bluetooth             391136  23 bnep,ath3k,btusb,rfcomm
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 toshiba_acpi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.16.216.254  Bcast:172.16.216.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fedd:ccf3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:634 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:76129 (76.1 KB)  TX bytes:102822 (102.8 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.16.216.2    0.0.0.0         UG    0      0        0 eth0
172.16.216.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.16.216.254
    Prefix:          24 (255.255.255.0)
    Gateway:         172.16.216.2

    DNS:             8.8.8.8

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/mumwifi]] (600 root)
[connection] id=mumwifi | type=802-11-wireless
[802-11-wireless] ssid=mumwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/multilink]] (600 root)
[connection] id=multilink | type=802-11-wireless
[802-11-wireless] ssid=multilink | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/mumwifi 1]] (600 root)
[connection] id=mumwifi 1 | type=802-11-wireless
[802-11-wireless] ssid=mumwifi | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     E2684CD158D2A5868338981
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512

[ath9k]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     65C14EF588BF1A68181643C
depends:        ath
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-48-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-48-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-48-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        4E:B2:DE:24:99:17:CB:F3:9C:B8:56:92:E5:4C:EB:AD:E5:94:D6:80
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 1
ps_enable: 0

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
rtc

##### modprobe options ##################

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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
blacklist r8169
blacklist r8169

[/etc/modprobe.d/blacklist-ethernet.conf]
blacklist atl1c

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

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   18.299527] ath: phy0: ASPM enabled: 0x42
[   18.299531] ath: EEPROM regdomain: 0x65
[   18.299533] ath: EEPROM indicates we should expect a direct regpair map
[   18.299535] ath: Country alpha2 being used: 00
[   18.299537] ath: Regpair used: 0x65
[   23.707720] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############

---

### Post by praseodym on 2015-04-01
> ```
0: phy0: Wireless LAN
Soft blocked: yes
Hard blocked: no
1: hci0: Bluetooth
Soft blocked: yes
Hard blocked: no
```
Check:
```

sudo rfkill unblock all
rfkill list
```

---

### Post by nitin7 on 2015-04-02
Here is the output of the commands
nitin@nitin-Satellite-C640:~$ sudo rfkill unblock all
[sudo] password for nitin: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
nitin@nitin-Satellite-C640:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
nitin@nitin-Satellite-C640:~$

---

### Post by nitin7 on 2015-04-02
hi praseodym,
THanks for the guidance.
I haven't understood what to do with the code.
I ran the command as suggested and ooutput is displayed

Thanks in advance for further guidance

---

### Post by praseodym on 2015-04-02
Go to the wired profile in the network manager and set IPv6 to "Ignore" and add the mtu-value of your ISP (here: 1500) instead of "Automatically" into the profile

---

### Post by nitin7 on 2015-04-03
Hi Praseodym,

Thnx. I put the IPv6 setting to ignore and it worked. 
Many many thanks....

---

