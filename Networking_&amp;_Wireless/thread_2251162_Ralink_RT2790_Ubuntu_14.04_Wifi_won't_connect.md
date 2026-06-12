---
title: "Ralink RT2790 Ubuntu 14.04 Wifi won't connect"
date: 2014-11-02
forum: Networking &amp; Wireless
---

### Post by UnderSurveillance on 2014-11-02
Having issues with my wireless connection.  In the Network Manager I can see all of the wifi signals available, however if I click on the connect button nothing happens.  There is also no wifi logo displayed in the notification bar (not sure if that's related).  Here is some info, hope someone can help.

```
########## wireless info START ##########

Report from: 01 Nov 2014 18:27 ADT -0300


Booted last: 01 Nov 2014 00:00 ADT -0300


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:2a74]
	Kernel driver in use: r8169


04:00.0 Network controller [0280]: Ralink corp. RT2790 Wireless 802.11n 1T/2R PCIe [1814:0781]
	Subsystem: Ralink corp. Device [1814:2790]
	Kernel driver in use: rt2800pci


##### lsusb #############################


Bus 002 Device 003: ID 04f2:b056 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1926:0003 NextWindow 1900 HID Touchscreen
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              630653  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
mxm_wmi                13021  1 nouveau
eeprom_93cx6           13344  1 rt2800pci
wmi                    19177  2 mxm_wmi,nouveau
crc_ccitt              12707  1 rt2800lib


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.0.112  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe9d:a42e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2645606 (2.6 MB)  TX bytes:167094 (167.0 KB)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth1      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.112
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             8.8.8.8
    DNS:             8.8.4.4
    DNS:             162.255.216.7


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points 
    CiscoC7901:      Infra, <MAC 'CiscoC7901' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA2
    Kallan24:        Infra, <MAC 'Kallan24' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA
    WhisperNet:      Infra, <MAC 'WhisperNet' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Warren86:        Infra, <MAC 'Warren86' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA


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


[[/etc/NetworkManager/system-connections/Warren86]] (600 root)
[connection] id=Warren86 | type=802-11-wireless
[802-11-wireless] ssid=Warren86 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/WhisperNet]] (600 root)
[connection] id=WhisperNet | type=802-11-wireless
[802-11-wireless] ssid=WhisperNet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Atlantic/Bermuda (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth1      no frequency information.


lo        no frequency information.


wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth1      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'WhisperNet' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-35 dBm  
                    Encryption key:on
                    ESSID:"WhisperNet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000742e4101f9
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'CiscoC7901' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"CiscoC7901"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000290af4150e
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Kallan24' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Kallan24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003f5dea4d0c
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Warren86' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"Warren86"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b0900c8b56
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[rt2800pci]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AF1E5AA2D7E623CCBA9A1CD
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2800mmio]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     AA2C68A3C0E9D5BDA2B36E9
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[rt2800lib]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     7A7EEDE3C2270AE56EB54F8
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[rt2x00pci]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     47F0A082BE7F0118126DD77
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[rt2x00mmio]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D5F2B94A767BFCDB29314F2
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[rt2x00lib]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     E9BB2D2E4429AB671216A29
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E3:C1:65:D0:89:1E:3C:EE:B6:DD:5C:18:C7:E1:99:3C:D2:49:56:B0
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rt2800pci]
nohwcrypt: N


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
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x1814:0x0781 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    4.281800] r8169 0000:02:00.0 eth1: link down
[    4.281918] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[  183.000645] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[  886.645763] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  886.840503] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  886.853720] r8169 0000:02:00.0 eth1: link down
[  886.853754] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[ 1016.753068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1016.770790] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1033.332261] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 1033.345724] r8169 0000:02:00.0 eth1: link down
[ 1033.345757] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[ 2121.076788] r8169 0000:02:00.0 eth1: link up
[ 2121.076803] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready


########## wireless info END ############
```

---

### Post by UnderSurveillance on 2014-11-04
Not sure what the issue was but it seemed to have corrected itself.  Was working on a few other things while waiting on a response here, did a system restart and now I have sound.  So I couldn't even pinpoint the source of the problem or the solution.  Fingers crossed I won't have to deal with the issue again.

---

### Post by UnderSurveillance on 2014-11-06
Well... that was short lived.  Any help would be appreciated.....

---

### Post by jeremy31 on 2014-11-06
The one thing I noticed is that both access points that you want to connect to use TKIP encryption.  It is best to set them for WPA2-AES only, it is better security and usually has less issues with Ubuntu.  And it might help change Network Manager settings for your connections to IPv6 Ignore

---

