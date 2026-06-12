---
title: "cant connect to network intel pro wireless please help"
date: 2016-05-18
forum: Networking &amp; Wireless
---

### Post by hamlet89 on 2016-05-18
```

########## wireless info START ##########

Report from: 18 May 2016 21:14 EDT -0400

Booted last: 18 May 2016 20:20 EDT -0400

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:50:54 UTC 2014 i686 i686 i386 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Intel Corporation 82573L Gigabit Ethernet Controller [8086:109a]
    Subsystem: Lenovo ThinkPad T60 [17aa:2001]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Subsystem: Intel Corporation Device [8086:1010]
    Kernel driver in use: iwl3945

##### lsusb #############################

Bus 005 Device 003: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

iwl3945                64640  0 
iwlegacy               88342  1 iwl3945
mac80211              564484  2 iwl3945,iwlegacy
cfg80211              423921  3 iwl3945,iwlegacy,mac80211

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:173.247.14.206  Bcast:173.247.14.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11616244 (11.6 MB)  TX bytes:1104733 (1.1 MB)
          Interrupt:16 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr <MAC 'irda0' [IF]>  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:203 errors:0 dropped:0 overruns:0 frame:0
          TX packets:203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27405 (27.4 KB)  TX bytes:31465 (31.4 KB)

##### iwconfig ##########################

irda0     no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         173.247.14.1    0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
173.247.14.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       923     1  0 20:20 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
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
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         173.247.14.206
    Prefix:          24 (255.255.255.0)
    Gateway:         173.247.14.1

    DNS:             66.18.32.2
    DNS:             66.18.32.3

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Tyler1027 1]] (600 root)
[connection] id=Tyler1027 1 | type=802-11-wireless
[802-11-wireless] ssid=Tyler1027 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tyler1027]] (600 root)
[connection] id=Tyler1027 | type=802-11-wireless
[802-11-wireless] ssid=Tyler1027 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Tyler1027-5G]] (600 root)
[connection] id=Tyler1027-5G | type=802-11-wireless
[802-11-wireless] ssid=Tyler1027-5G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

irda0     no frequency information.

lo        no frequency information.

eth0      no frequency information.

wlan0     24 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

irda0     Interface doesn't support scanning.

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[iwl3945]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     C93C31FCEBBAE1F376E495F
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  412.394125] wlan0: authenticate with <MAC address>
[  412.397211] wlan0: send auth to <MAC address> (try 1/3)
[  412.399046] wlan0: authenticated
[  412.400086] wlan0: associate with <MAC address> (try 1/3)
[  412.403954] wlan0: RX AssocResp from <MAC address> (capab=0x1411 status=0 aid=1)
[  412.405694] wlan0: associated
[  420.412427] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  422.560821] wlan0: authenticate with <MAC address>
[  422.562736] wlan0: send auth to <MAC address> (try 1/3)
[  422.564590] wlan0: authenticated
[  422.568162] wlan0: associate with <MAC address> (try 1/3)
[  422.571578] wlan0: RX AssocResp from <MAC address> (capab=0x1411 status=0 aid=1)
[  422.576609] wlan0: associated
[  430.572427] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  432.720672] wlan0: authenticate with <MAC address>
[  432.722488] wlan0: send auth to <MAC address> (try 1/3)
[  432.724335] wlan0: authenticated
[  432.728093] wlan0: associate with <MAC address> (try 1/3)
[  432.731529] wlan0: RX AssocResp from <MAC address> (capab=0x1411 status=0 aid=1)
[  432.736448] wlan0: associated
[  440.734035] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  442.880753] wlan0: authenticate with <MAC address>
[  442.884700] wlan0: send auth to <MAC address> (try 1/3)
[  442.887301] wlan0: authenticated
[  442.892104] wlan0: associate with <MAC address> (try 1/3)
[  442.895576] wlan0: RX AssocResp from <MAC address> (capab=0x1411 status=0 aid=1)
[  442.897304] wlan0: associated
[  450.004344] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[  575.067227] wlan0: authenticate with <MAC address>
[  575.069029] wlan0: send auth to <MAC address> (try 1/3)
[  575.070468] wlan0: authenticated
[  575.072070] wlan0: associate with <MAC address> (try 1/3)
[  575.073009] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  575.074122] wlan0: associated
[  583.081537] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  585.225214] wlan0: authenticate with <MAC address>
[  585.226847] wlan0: send auth to <MAC address> (try 1/3)
[  585.227430] wlan0: authenticated
[  585.228295] wlan0: associate with <MAC address> (try 1/3)
[  585.229280] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  585.231809] wlan0: associated
[  593.231841] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  595.372701] wlan0: authenticate with <MAC address>
[  595.374087] wlan0: send auth to <MAC address> (try 1/3)
[  595.374618] wlan0: authenticated
[  595.376200] wlan0: associate with <MAC address> (try 1/3)
[  595.377101] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  595.381061] wlan0: associated
[  603.381581] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  605.525145] wlan0: authenticate with <MAC address>
[  605.526370] wlan0: send auth to <MAC address> (try 1/3)
[  605.526905] wlan0: authenticated
[  605.528238] wlan0: associate with <MAC address> (try 1/3)
[  605.529166] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  605.530381] wlan0: associated
[  613.531538] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  615.708928] wlan0: authenticate with <MAC address>
[  615.712410] wlan0: send auth to <MAC address> (try 1/3)
[  615.712934] wlan0: authenticated
[  615.716375] wlan0: associate with <MAC address> (try 1/3)
[  615.717285] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  615.718395] wlan0: associated
[  623.721577] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  625.877724] wlan0: authenticate with <MAC address>
[  625.883656] wlan0: send auth to <MAC address> (try 1/3)
[  625.884222] wlan0: authenticated
[  625.888131] wlan0: associate with <MAC address> (try 1/3)
[  625.889047] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  625.890152] wlan0: associated
[  633.002277] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[  644.481085] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: None
[  644.481249] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  649.168701] wlan0: authenticate with <MAC address>
[  649.170344] wlan0: send auth to <MAC address> (try 1/3)
[  649.170899] wlan0: authenticated
[  649.172157] wlan0: associate with <MAC address> (try 1/3)
[  649.173094] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  649.174283] wlan0: associated
[  657.180797] wlan0: deauthenticated from <MAC address> (Reason: 15)
[  659.325092] wlan0: authenticate with <MAC address>
[  659.330688] wlan0: send auth to <MAC address> (try 1/3)
[  659.331554] wlan0: authenticated
[  659.340050] wlan0: associate with <MAC address> (try 1/3)
[  659.341008] wlan0: RX AssocResp from <MAC address> (capab=0x1011 status=0 aid=1)
[  659.342094] wlan0: associated
[  661.484717] wlan0: deauthenticating from <MAC address> by local choice (reason=3)

########## wireless info END ############

```

---

### Post by howefield on 2016-05-19
Thread closed, duplicate here  [http://ubuntuforums.org/showthread.php?t=2324960](http://ubuntuforums.org/showthread.php?t=2324960)

---

