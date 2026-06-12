---
title: "Atheros QCA9565 / AR9565"
date: 2014-11-10
forum: Networking &amp; Wireless
---

### Post by nyancat120 on 2014-11-10
I have a Acer Aspire V5 - 131 notebook that cannot connect to my home wireless network. I factory reseted it a couple of days ago (I had some troubles with it so I send it into the official Acer service and they fac. reseted the notebook) and then I tried connecting to my home network with no luck. It accepts the password, but then just fails with the no connection message.... :( output of rfkill list:
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
I tried changing the hwcrypt thing I found somewhere else but with no luck... Anyone can help me?

---

### Post by wildmanne39 on 2014-11-10
Hi, click on the wireless script in my signature and follow the directions for running it then post the file here in code tags or attach as a zip file.

---

### Post by nyancat120 on 2014-11-11
```
########## wireless info START ##########

Report from: 11 Nov 2014 15:36 CET +0100

Booted last: 11 Nov 2014 15:33 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:31:23 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc Device [11ad:0632]
    Kernel driver in use: ath9k

04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0742]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b3f6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546051  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221a:6ff:fed1:5de1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:576 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:173589 (173.5 KB)  TX bytes:72762 (72.7 KB)
          Interrupt:18 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Havko Domaci :   Infra, <MAC 'Havko Domaci ' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 82 WPA WPA2

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

[[/etc/NetworkManager/system-connections/Havko Domaci ]] (600 root)
[connection] id=Havko Domaci  | type=802-11-wireless
[802-11-wireless] ssid=Havko Domaci  | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bgmh-club]] (600 root)
[connection] id=bgmh-club | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=bgmh-club | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Bratislava (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

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

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Havko Domaci ' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Havko Domaci "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000059b7f99a4
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B822641624778B987844F6F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
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
vermagic:       3.13.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A6:96:31:EE:84:32:BD:22:00:4B:A4:DA:A9:78:CF:D9:2C:D5:5E:69
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
# PCI device 0x14e4:0x16b5 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0036 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.129752] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  114.310866] wlan0: authenticate with <MAC 'Havko Domaci ' [AC1]>
[  114.324727] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 1/3)
[  114.396415] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 2/3)
[  114.501991] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 3/3)
[  114.576906] wlan0: authentication with <MAC 'Havko Domaci ' [AC1]> timed out
[  115.542652] wlan0: authenticate with <MAC 'Havko Domaci ' [AC1]>
[  115.556520] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 1/3)
[  115.668609] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 2/3)
[  115.775597] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 3/3)
[  115.871319] wlan0: authentication with <MAC 'Havko Domaci ' [AC1]> timed out
[  117.238379] wlan0: authenticate with <MAC 'Havko Domaci ' [AC1]>
[  117.252185] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 1/3)
[  117.316856] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 2/3)
[  117.464421] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 3/3)
[  117.521064] wlan0: authentication with <MAC 'Havko Domaci ' [AC1]> timed out
[  119.389871] wlan0: authenticate with <MAC 'Havko Domaci ' [AC1]>
[  119.403706] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 1/3)
[  119.501224] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 2/3)
[  119.574239] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 3/3)
[  119.637767] wlan0: authentication with <MAC 'Havko Domaci ' [AC1]> timed out
[  131.359186] wlan0: authenticate with <MAC 'Havko Domaci ' [AC1]>
[  131.373402] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 1/3)
[  131.459090] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 2/3)
[  131.550065] wlan0: send auth to <MAC 'Havko Domaci ' [AC1]> (try 3/3)
[  131.582094] wlan0: authentication with <MAC 'Havko Domaci ' [AC1]> timed out

########## wireless info END ############

```

---

### Post by jeremy31 on 2014-11-11
Change router encryption to WPA2-AES as you have a mixed mode now that does cause issues

---

### Post by nyancat120 on 2014-11-11
could you please explain how do I do that? Sorry, but I'm a beginner :)

---

### Post by jeremy31 on 2014-11-11
What is the model number on your wifi router, I might be able to find something

---

### Post by nyancat120 on 2014-11-11
It's not a problem with the router... Other devices can connect fine only this notebook can't....

---

### Post by nyancat120 on 2014-11-19
Guys please help me... I really don't know what's wrong with this... It has to be something with the drivers because my router is fine, and I can connect with the ethernet cable on other network (eg. IT room in our school)

---

### Post by chili555 on 2014-11-19
Please open a terminal and do:```
sudo -i
echo "options ath9k nohwcrypt=1"  >  /etc/modprobe.d/ath9k.conf
exit
```Detach the ethernet and reboot. Does it connect?

If not, please post:```
dmesg | grep -e wlan -e ath
```Thanks.

---

### Post by nyancat120 on 2014-11-19
```
[    1.739846] Loaded X.509 cert 'Magrathea: Glacier signing key: a69631ee8432bd22004ba4daa978cfd92cd55e69'
[   12.644524] ath: phy0: WB335 1-ANT card detected
[   12.699541] ath: phy0: Enable LNA combining
[   12.701551] ath: phy0: ASPM enabled: 0x42
[   12.701553] ath: EEPROM regdomain: 0x65
[   12.701554] ath: EEPROM indicates we should expect a direct regpair map
[   12.701556] ath: Country alpha2 being used: 00
[   12.701556] ath: Regpair used: 0x65
[   15.906106] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.910387] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   40.842307] wlan0: authenticate with 1c:af:f7:32:0d:51
[   40.858168] wlan0: send auth to 1c:af:f7:32:0d:51 (try 1/3)
[   40.931707] wlan0: send auth to 1c:af:f7:32:0d:51 (try 2/3)
[   40.999844] wlan0: send auth to 1c:af:f7:32:0d:51 (try 3/3)
[   41.042649] wlan0: authentication with 1c:af:f7:32:0d:51 timed out
[   42.061589] wlan0: authenticate with 1c:af:f7:32:0d:51
[   42.078471] wlan0: send auth to 1c:af:f7:32:0d:51 (try 1/3)
[   42.158471] wlan0: send auth to 1c:af:f7:32:0d:51 (try 2/3)
[   42.241671] wlan0: send auth to 1c:af:f7:32:0d:51 (try 3/3)
[   42.284094] wlan0: authentication with 1c:af:f7:32:0d:51 timed out
[   43.636381] wlan0: authenticate with 1c:af:f7:32:0d:51
[   43.650401] wlan0: send auth to 1c:af:f7:32:0d:51 (try 1/3)
[   43.731726] wlan0: send auth to 1c:af:f7:32:0d:51 (try 2/3)
[   43.786801] wlan0: send auth to 1c:af:f7:32:0d:51 (try 3/3)
[   43.828130] wlan0: authentication with 1c:af:f7:32:0d:51 timed out
[   45.690895] wlan0: authenticate with 1c:af:f7:32:0d:51
[   45.705108] wlan0: send auth to 1c:af:f7:32:0d:51 (try 1/3)
[   45.778446] wlan0: send auth to 1c:af:f7:32:0d:51 (try 2/3)
[   45.822518] wlan0: send auth to 1c:af:f7:32:0d:51 (try 3/3)
[   45.879583] wlan0: authentication with 1c:af:f7:32:0d:51 timed out
[   57.574486] wlan0: authenticate with 1c:af:f7:32:0d:51
[   57.588453] wlan0: send auth to 1c:af:f7:32:0d:51 (try 1/3)
[   57.684799] wlan0: send auth to 1c:af:f7:32:0d:51 (try 2/3)
[   57.773848] wlan0: send auth to 1c:af:f7:32:0d:51 (try 3/3)
[   57.853382] wlan0: authentication with 1c:af:f7:32:0d:51 timed out

```
So that's the output.... I have already tried the nohwcrypt thing but it didn't work and now the same result :(

---

### Post by chili555 on 2014-11-23
Let's try a few things and see if we can coax this to life. I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

Let's see what channel your router is on and compare that to what channels your wireless card does:```
sudo iwlist wlan0 scan
sudo iwlist wlan0 chan
```I have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection in the router.

---

### Post by nyancat120 on 2014-11-27
This is the sudo iwlist wlan0 scan

```

wlan0     Scan completed :
          Cell 01 - Address: 1C:AF:F7:32:0D:51
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-19 dBm  
                    Encryption key:on
                    ESSID:"Havko Domaci "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000063633e0e9
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000D4861766B6F20446F6D61636920
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```
And then this is the sudo iwlist wlan0 chan:
```

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

```
Sorry for such a late reply, but I missed the second page :/

---

### Post by nyancat120 on 2014-12-06
Does anyone have any suggestions? :/

---

### Post by nyancat120 on 2014-12-09
Alright guys. I found something. Right now I'm at a train station in a city that I've been once before to and suddenly I can connect just fine. It may be that my home router is messed up or something... When I come home I'm going to switch my home router (we have a couple of them from promo actions by the ISP) I will post ASAP I get home. This happened a couple times before that on some weird random cafe networks my internet connected fine but it was a randomly selected group of netowkrs..... :D

---

### Post by jeremy31 on 2014-12-09
If you are still connected to that router, run the wireless script again

---

### Post by nyancat120 on 2014-12-11
It's most likely my mistake, since I can connect to our school IT network (wifi) just fine so it's probably a problem with my home router. When I get home, I'll try to do something about it... Thanks for your help :)

---

