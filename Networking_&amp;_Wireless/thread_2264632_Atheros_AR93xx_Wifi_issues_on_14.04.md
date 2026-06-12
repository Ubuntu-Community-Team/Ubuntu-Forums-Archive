---
title: "Atheros AR93xx: Wifi issues on 14.04"
date: 2015-02-08
forum: Networking &amp; Wireless
---

### Post by najdorfchess on 2015-02-08
I apologize if this has been asked before and I did find some related posts but none of them got me a solution. 
So I built a new desktop and my wifi on 14.04 seems to be really inconsistent (keeps getting disconnected) and slow. I'm dual booting my machine and I consistently get 1/8th of the speed I get on windows. 

My network adapter is [h=1][SIZE=3]TP-LINK TL-WDN4800 Dual Band Wireless N900[/SIZE] ([Amazon link]("http://www.amazon.com/TP-LINK-TL-WDN4800-Wireless-Express-Low-profile/dp/B007GMPZ0A/ref=sr_1_1?ie=UTF8&qid=1423455396&sr=8-1&keywords=tp+link+wireless"))[/h]
The machine detects the hardware (bolded in last line): 

```


> lspci -nn

00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation Device [8086:8cb1]
00:16.0 Communication controller [0780]: Intel Corporation Device [8086:8cba]
00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
00:1a.0 USB controller [0c03]: Intel Corporation Device [8086:8cad]
00:1b.0 Audio device [0403]: Intel Corporation Device [8086:8ca0]
00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:8c90] (rev d0)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d0)
00:1c.7 PCI bridge [0604]: Intel Corporation Device [8086:8c9e] (rev d0)
00:1d.0 USB controller [0c03]: Intel Corporation Device [8086:8ca6]
00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:8cc4]
00:1f.2 SATA controller [0106]: Intel Corporation Device [8086:8c82]
00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:8ca2]
03:00.0 PCI bridge [0604]: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge [1b21:1080] (rev 04)
**05:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)**



``` 


Any help much appreciated. Thanks in advance.

---

### Post by Hadaka on 2015-02-09
hi try this..
```
sudo modprobe -rfv ath9k
sudo modprobe ath9k nohwcrypt=1

```
and change your router encryption from TKIP  to wap2

---

### Post by najdorfchess on 2015-02-10
I tried it and it didn't work. Gentle bounce ^^

---

### Post by Hadaka on 2015-02-10
Hi, please go here.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
read the instructions and post your wireless info text.
thanks

---

### Post by najdorfchess on 2015-02-10
> **Hadaka said:**
> Hi, please go here.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
read the instructions and post your wireless info text.
thanks

Pasted the output of the entire file below. 



```
########## wireless info START ##########


Report from: 10 Feb 2015 19:18 PST -0800


Booted last: 10 Feb 2015 07:36 PST -0800


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
	Kernel driver in use: e1000e


05:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)
	Subsystem: Qualcomm Atheros Device [168c:3112]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0b05:17cb ASUSTek Computer, Inc. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
video                  19476  2 i915,asus_wmi
wmi                    19177  2 mxm_wmi,asus_wmi


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
          Interrupt:20 Memory:dfd00000-dfd20000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c66e:1fff:fe1f:9b33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:209163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:79264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60511720 (60.5 MB)  TX bytes:27163624 (27.1 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"FA5E6C"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'FA5E6C' [AC1]>   
          Bit Rate=13 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/70  Signal level=-74 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1499  Invalid misc:5554   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [FA5E6C] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           19 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    PJ:              Infra, <MAC 'PJ' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2
    ATT775:          Infra, <MAC 'ATT775' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    *FA5E6C:         Infra, <MAC 'FA5E6C' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    HP-Print-73-ENVY 4500 series: Infra, <MAC 'HP-Print-73-ENVY 4500 series' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    EFAB69:          Infra, <MAC 'EFAB69' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    D031A9:          Infra, <MAC 'D031A9' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    A6CB63:          Infra, <MAC 'A6CB63' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


[[/etc/NetworkManager/system-connections/FA5E6C]] (600 root)
[connection] id=FA5E6C | type=802-11-wireless
[802-11-wireless] ssid=FA5E6C | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


wlan0     26 channels in total; available frequencies :
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
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FA5E6C' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"FA5E6C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001352562ead
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ATT775' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"ATT775"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000054d543cbab3
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'HP-Print-73-ENVY 4500 series' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-73-ENVY 4500 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000021e8e5e4727
                    Extra: Last beacon: 48ms ago
          Cell 04 - Address: <MAC 'PJ' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"PJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003aa305e183
                    Extra: Last beacon: 4760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'EFAB69' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"EFAB69"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000132ae0faa6
                    Extra: Last beacon: 3164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     94B3813AF84C49B115229AD
depends:        ath
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
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
# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0030 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[    2.410345] ath: EEPROM regdomain: 0x21
[    2.410345] ath: EEPROM indicates we should expect a direct regpair map
[    2.410346] ath: Country alpha2 being used: AU
[    2.410347] ath: Regpair used: 0x21
[    2.722259] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    6.138784] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[    6.154896] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[    6.156923] wlan0: authenticated
[    6.158556] wlan0: associate with <MAC 'FA5E6C' [AC1]> (try 1/3)
[    6.162178] wlan0: RX AssocResp from <MAC 'FA5E6C' [AC1]> (capab=0x411 status=0 aid=1)
[    6.162212] wlan0: associated
[    6.162218] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[    6.199268] wlan0: deauthenticating from <MAC 'FA5E6C' [AC1]> by local choice (reason=2)
[    6.205836] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[    6.217618] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[    6.219851] wlan0: authenticated
[    6.222609] wlan0: associate with <MAC 'FA5E6C' [AC1]> (try 1/3)
[    6.226250] wlan0: RX AssocResp from <MAC 'FA5E6C' [AC1]> (capab=0x411 status=0 aid=1)
[    6.226282] wlan0: associated


########## wireless info END ############



```

---

### Post by Hadaka on 2015-02-10
Hi , please do..
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
ubuntu doesnt run well with TKIP

```
wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FA5E6C' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"FA5E6C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001352562ead
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : [COLOR=#ff0000]TKIP[/COLOR]
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```Windows doesnt seem to be affected by it, Ubuntu is..once you can change that
value to just plain wap2 you will see a marked improvement in speed. I have no further
advice for you.
good luck.

---

### Post by najdorfchess on 2015-02-11
Thank you for your reply. Does it affect the speed on OS X? We have couple of macbook pros

---

### Post by najdorfchess on 2015-02-14
I changed the encryption in wifi router and it didn't fix the issue. Instead it slowed down the speed on all my devices which somehow seems to be okay now except on my ubuntu where it's cronically slow (barely 1mbps on a 30mbps connection). 

Am I missing any driver update? 
Worse case, I can install another debian distro like mint linux if that doesn't have similar issue. Let me know if this is an ubuntu specific issue. 

```




########## wireless info START ##########


Report from: 14 Feb 2015 16:00 PST -0800


Booted last: 13 Feb 2015 20:29 PST -0800


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
	Subsystem: ASUSTeK Computer Inc. Device [1043:85c4]
	Kernel driver in use: e1000e


05:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)
	Subsystem: Qualcomm Atheros Device [168c:3112]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 0b05:17cb ASUSTek Computer, Inc. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
mxm_wmi                13021  0 
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
video                  19476  2 i915,asus_wmi
wmi                    19177  2 mxm_wmi,asus_wmi


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
          Interrupt:20 Memory:dfd00000-dfd20000 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::c66e:1fff:fe1f:9b33/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:186537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35597950 (35.5 MB)  TX bytes:13983939 (13.9 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"FA5E6C"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'FA5E6C' [AC1]>   
          Bit Rate=28.9 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:765  Invalid misc:2491   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [FA5E6C] ------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           26 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    D031A9:          Infra, <MAC 'D031A9' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    *FA5E6C:         Infra, <MAC 'FA5E6C' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA2
    PJ:              Infra, <MAC 'PJ' [AC2]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    HP-Print-73-ENVY 4500 series: Infra, <MAC 'HP-Print-73-ENVY 4500 series' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52
    EFAB69:          Infra, <MAC 'EFAB69' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    A6CB63:          Infra, <MAC 'A6CB63' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             68.105.28.11
    DNS:             68.105.29.11
    DNS:             68.105.28.12


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


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


[[/etc/NetworkManager/system-connections/FA5E6C]] (600 root)
[connection] id=FA5E6C | type=802-11-wireless
[802-11-wireless] ssid=FA5E6C | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Los_Angeles (based on set time zone)


country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


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
          Current Frequency:2.412 GHz (Channel 1)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'FA5E6C' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"FA5E6C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000006cf5df1fd
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'PJ' [AC2]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"PJ"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000120789bf5d
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'A6CB63' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"A6CB63"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000195fd5219f8
                    Extra: Last beacon: 6784ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'D031A9' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"D031A9"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001524c074189
                    Extra: Last beacon: 1484ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'EFAB69' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"EFAB69"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000060e124c48f
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[ath9k]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     94B3813AF84C49B115229AD
depends:        ath
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-45-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        34:99:21:39:F3:DA:40:B6:20:BD:55:17:59:7B:A8:5A:F5:79:7C:9A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
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
# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0030 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[40556.880763] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[40556.893238] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[40556.895182] wlan0: authenticated
[40556.895851] wlan0: associate with <MAC 'FA5E6C' [AC1]> (try 1/3)
[40556.902011] wlan0: RX AssocResp from <MAC 'FA5E6C' [AC1]> (capab=0x411 status=0 aid=3)
[40556.902045] wlan0: associated
[40602.103330] wlan0: deauthenticating from <MAC 'FA5E6C' [AC1]> by local choice (reason=3)
[40604.922953] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[40604.935549] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[40604.937650] wlan0: authenticated
[40604.938339] wlan0: associate with <MAC 'FA5E6C' [AC1]> (try 1/3)
[40604.949153] wlan0: RX AssocResp from <MAC 'FA5E6C' [AC1]> (capab=0x411 status=0 aid=3)
[40604.949187] wlan0: associated
[40650.149201] wlan0: deauthenticating from <MAC 'FA5E6C' [AC1]> by local choice (reason=3)
[40951.801743] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[40951.817599] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[40951.819563] wlan0: authenticated
[40951.820944] wlan0: associate with <MAC 'FA5E6C' [AC1]> (try 1/3)
[40951.825153] wlan0: RX AssocResp from <MAC 'FA5E6C' [AC1]> (capab=0x411 status=0 aid=5)
[40951.825191] wlan0: associated
[40997.456277] wlan0: deauthenticating from <MAC 'FA5E6C' [AC1]> by local choice (reason=3)
[41000.264240] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[41000.277029] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[41000.354178] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 2/3)
[41000.472129] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 3/3)
[41000.526011] wlan0: authentication with <MAC 'FA5E6C' [AC1]> timed out
[41057.883472] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[41057.899072] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[41058.066890] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 2/3)
[41058.201924] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 3/3)
[41058.292828] wlan0: authentication with <MAC 'FA5E6C' [AC1]> timed out
[41066.939155] wlan0: authenticate with <MAC 'FA5E6C' [AC1]>
[41066.955207] wlan0: send auth to <MAC 'FA5E6C' [AC1]> (try 1/3)
[41066.957155] wlan0: authenticated
[41066.958701] wlan0: associate with <MAC 'FA5E6C' [AC1]> (try 1/3)
[41066.962345] wlan0: RX AssocResp from <MAC 'FA5E6C' [AC1]> (capab=0x411 status=0 aid=3)
[41066.962379] wlan0: associated


########## wireless info END ############



```

---

### Post by najdorfchess on 2015-02-16
^^gentle bounce

Sorry for spamming the thread. I noticed in the log file "[COLOR=#000000][FONT=Ubuntu Mono]Group Cipher : [/FONT][/COLOR][FONT=Ubuntu Mono]TKIP" [/FONT]although I changed in my router to use wpa2 instead. I'm not a networking guy, so someone please help me out here. I also did 

```

sudo vim /etc/modprobe.d/ath9k.conf

[I]and entered in this text 
[/I]options ath9k nohwcrypt=1

```

---

### Post by najdorfchess on 2015-02-18
I still haven't managed to get a decent speed in my wifi adapter. I'm thinking of returning the device and get a tried and tested one that works well on Ubuntu 14.04 64-bit. It's for my desktop and I prefer the one that I plug in my PCI Express slot. Any recommendations, one that works well with Cox ISP in California, USA and one that works well, please?

---

### Post by najdorfchess on 2015-03-05
I'm disappointed that ubuntuforum has gone very quiet. I ended up buying a powerline adapter and made my connection wired which solved my problem.

---

