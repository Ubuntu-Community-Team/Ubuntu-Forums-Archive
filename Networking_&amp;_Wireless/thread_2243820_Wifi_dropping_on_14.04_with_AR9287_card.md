---
title: "Wifi dropping on 14.04 with AR9287 card"
date: 2014-09-11
forum: Networking &amp; Wireless
---

### Post by BeerMonstaa on 2014-09-11
Hi Guys,

I am expiring problems with AR9287 wifi card on 14.04. It works fine for a while and then randomly when I turn the machine on it will not connect to any networks at all.  After leaving the machine off for another half an hour or so I will then turn it on and it will work fine.

I have done some research into this issue with the card but the solution seemed to upgrade the kernel (older versions of ubuntu).  As my kernel is the latest (as far as I am aware) I am unsure as to what action to take.

Here is some output:

```
uname -a
Linux rob-Aspire-5742 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:40:53 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

```
sudo lshw -C network  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 88:ae:1d:92:e8:91
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 memory:b3400000-b340ffff
  *-network
       description: Wireless interface
       product: AR9287 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 1c:65:9d:34:88:dc
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.13.0-30-generic firmware=N/A ip=192.168.0.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:b2400000-b240ffff

```

Any help you can provide me will be greatfully appreciated, thanks for your time,

Rob

---

### Post by varunendra on 2014-09-11
Welcome to the forums BeerMonstaa!

Please try this in a terminal (can be opened with Ctrl-Alt-T) -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

Reboot and reconnect, see if the connection is stable now. If not, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by BeerMonstaa on 2014-09-15
Hi,

Thanks for the reply and apologies for the late response - have been on holiday.

I will give that a try and follow your instructions if it doesn't work.

Thanks

---

### Post by BeerMonstaa on 2015-01-18
Hi,

Your solution seemed to work for a while but now I am facing the same issue.  [COLOR=#000000][FONT=Ubuntu Mono]/etc/modprobe.d/ath9k.conf still exists with the parameters you provided.  Below is the output from the script you provided:

```
[/FONT][/COLOR]

########## wireless info START ##########


Report from: 18 Jan 2015 14:42 GMT +0000


Booted last: 18 Jan 2015 14:03 GMT +0000


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:42 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:036d]
	Kernel driver in use: tg3


02:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6603]
	Kernel driver in use: ath9k


##### lsusb #############################


Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0402:9665 ALi Corp. Gateway Webcam
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
mxm_wmi                13021  0 
video                  19476  2 i915,acer_wmi
wmi                    19177  2 acer_wmi,mxm_wmi


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
          Interrupt:16 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e65:9dff:fe34:88dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57880 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38089 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64771465 (64.7 MB)  TX bytes:6607423 (6.6 MB)


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"VM270761-2G"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'VM270761-2G' [AC1]>   
          Bit Rate=130 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:280   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #######################


nameserver 127.0.1.1


##### nm-tool ###########################


** (process:6260): WARNING **: error: cannot retrieve connection: uid 1000 has no permission to perform this operation


NetworkManager Tool


State: connected (global)


- Device: wlan0  [VM270761-2G] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           130 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    3MobileWiFi-A38C:Infra, <MAC '3MobileWiFi-A38C' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    virginmedia3762411: Infra, <MAC 'virginmedia3762411' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    *VM270761-2G:    Infra, <MAC 'VM270761-2G' [AC1]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA WPA2
    SKY793EC:        Infra, <MAC 'SKY793EC' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    BTHomeHub-753B:  Infra, <MAC 'BTHomeHub-753B' [AN5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 27 WEP
    BTOpenzone:      Infra, <MAC 'BTOpenzone' [AN6]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 25


  IPv4 Settings:
    Address:         192.168.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
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


[[/etc/NetworkManager/system-connections/Rob’s iPhone]] (600 root)
[connection] id=Rob’s iPhone | type=802-11-wireless
[802-11-wireless] ssid=82;111;98;226;128;153;115;32;105;80;104;111;110;101; | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/virginmedia3762411]] (600 root)
[connection] id=virginmedia3762411 | type=802-11-wireless
[802-11-wireless] ssid=virginmedia3762411 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Maiky]] (600 root)
[connection] id=Maiky | type=802-11-wireless | permissions=user:maiky:;
[802-11-wireless] ssid=Maiky | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/BTWiFi-with-FON]] (600 root)
[connection] id=BTWiFi-with-FON | type=802-11-wireless
[802-11-wireless] ssid=BTWiFi-with-FON | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/VM270761-2G]] (600 root)
[connection] id=VM270761-2G | type=802-11-wireless
[802-11-wireless] ssid=VM270761-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


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
          Current Frequency:2.462 GHz (Channel 11)


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.462 GHz (Channel 11)


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM270761-2G' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"VM270761-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c3dc1eb374
                    Extra: Last beacon: 184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '3MobileWiFi-A38C' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"3MobileWiFi-A38C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001534db7d42
                    Extra: Last beacon: 2252ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'SKY793EC' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"SKY793EC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000023e680bf84
                    Extra: Last beacon: 2304ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'virginmedia3762411' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"virginmedia3762411"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000191a8f164be
                    Extra: Last beacon: 124ms ago
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
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-35-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B1:41:4A:E9:6C:1B:0E:BB:7C:14:1F:A4:05:C1:F6:C9:8E:8A:66:F0
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
# PCI device 0x14e4:0x1692 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002e (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[  158.388871] wlan0: deauthenticating from <MAC 'VM270761-2G' [AC1]> by local choice (reason=3)
[  159.341635] wlan0: authenticate with <MAC address>
[  159.368860] wlan0: send auth to <MAC address> (try 1/3)
[  159.370868] wlan0: authenticated
[  159.371084] wlan0: AP has invalid WMM params (AIFSN=0 for ACI 0), disabling WMM
[  159.372187] wlan0: associate with <MAC address> (try 1/3)
[  159.374816] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[  159.375029] wlan0: associated
[  159.421084] wlan0: deauthenticating from <MAC address> by local choice (reason=2)
[  159.432351] wlan0: authenticate with <MAC address>
[  159.452296] wlan0: send auth to <MAC address> (try 1/3)
[  159.453852] wlan0: authenticated
[  159.454074] wlan0: AP has invalid WMM params (AIFSN=0 for ACI 0), disabling WMM
[  159.456249] wlan0: associate with <MAC address> (try 1/3)
[  159.458908] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[  159.459155] wlan0: associated
[  170.968492] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[  171.804892] wlan0: authenticate with <MAC address>
[  171.832302] wlan0: send auth to <MAC address> (try 1/3)
[  171.833838] wlan0: authenticated
[  171.834041] wlan0: AP has invalid WMM params (AIFSN=0 for ACI 0), disabling WMM
[  171.835860] wlan0: associate with <MAC address> (try 1/3)
[  171.838209] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[  171.838435] wlan0: associated
[  524.112699] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[  525.200254] wlan0: authenticate with <MAC 'VM270761-2G' [AC1]>
[  525.227955] wlan0: send auth to <MAC 'VM270761-2G' [AC1]> (try 1/3)
[  525.230237] wlan0: authenticated
[  525.231274] wlan0: associate with <MAC 'VM270761-2G' [AC1]> (try 1/3)
[  525.235847] wlan0: RX AssocResp from <MAC 'VM270761-2G' [AC1]> (capab=0x411 status=0 aid=3)
[  525.235927] wlan0: associated
[  525.239835] ath: EEPROM regdomain: 0x833a
[  525.239841] ath: EEPROM indicates we should expect a country code
[  525.239845] ath: doing EEPROM country->regdmn map search
[  525.239847] ath: country maps to regdmn code: 0x37
[  525.239850] ath: Country alpha2 being used: GB
[  525.239852] ath: Regpair used: 0x37
[  525.239855] ath: regdomain 0x833a dynamically updated by country IE


########## wireless info END ############


[COLOR=#000000][FONT=Ubuntu Mono]
```

Thanks again for your help! [/FONT][/COLOR]

---

### Post by BeerMonstaa on 2015-01-27
bump!

---

