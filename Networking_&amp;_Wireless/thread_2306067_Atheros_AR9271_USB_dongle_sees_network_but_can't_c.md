---
title: "Atheros AR9271 USB dongle sees network but can't connect (Ubuntu 14.04)"
date: 2015-12-11
forum: Networking &amp; Wireless
---

### Post by jremington on 2015-12-11
I spent a few days trying to get Realtek wifi dongles working with this newly installed Ubuntu 14.04/Dell 980 system, and finally gave up. Then I purchased the Atheros AR9271 dongle, because the ads claim that it "just works" with Linux, but I have the same problem. 

At the moment, I'm using an unencrypted wifi network for debugging the problem (dd-wrt running on a Linksys router).

The dongle sees the network but cannot connect. I cannot force it into "up" mode with ip as follows:

```
root@Dell980:/etc/network# iw dev
phy#2
    Interface wlan3
        ifindex 5
        type managed

root@Dell980:/etc/network# ip link show wlan3
5: wlan3: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 30:14:4a:7d:b2:07 brd ff:ff:ff:ff:ff:ff
root@Dell980:/etc/network# ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 84:2b:2b:9a:8d:1d brd ff:ff:ff:ff:ff:ff
5: wlan3: <BROADCAST,MULTICAST> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 30:14:4a:7d:b2:07 brd ff:ff:ff:ff:ff:ff

root@Dell980:/etc/network# ip link set wlan3 up

root@Dell980:/etc/network# ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 84:2b:2b:9a:8d:1d brd ff:ff:ff:ff:ff:ff
5: wlan3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 30:14:4a:7d:b2:07 brd ff:ff:ff:ff:ff:ff

root@Dell980:/etc/network# ip link set wlan3 up

root@Dell980:/etc/network# ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN mode DEFAULT group default qlen 1000
    link/ether 84:2b:2b:9a:8d:1d brd ff:ff:ff:ff:ff:ff
5: wlan3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 30:14:4a:7d:b2:07 brd ff:ff:ff:ff:ff:ff


root@Dell980:/etc/network# iw wlan3 scan

BSS 00:23:69:de:e0:4a (on wlan3)
    TSF: 5732674148055 usec (66d, 08:24:34)
    freq: 2412
    beacon interval: 100
    capability: ESS ShortSlotTime (0x0401)
    signal: -70.00 dBm
    last seen: 1112 ms ago
    Information elements from Probe Response frame:
    SSID: dd-wrt
    Supported rates: 1.0* 2.0* 5.5* 11.0* 6.0 9.0 12.0 18.0 
    DS Parameter set: channel 1
    ERP: Barker_Preamble_Mode
    Extended supported rates: 24.0 36.0 48.0 54.0 
    HT capabilities:
        Capabilities: 0x11cc
            HT20
            SM Power Save disabled
            RX HT40 SGI
            TX STBC
            RX STBC 1-stream
            Max AMSDU length: 3839 bytes
            DSSS/CCK HT40
        Maximum RX AMPDU length 65535 bytes (exponent: 0x003)
        Minimum RX AMPDU time spacing: 8 usec (0x06)
        HT TX/RX MCS rate indexes supported: 0-15
    HT operation:
         * primary channel: 1
         * secondary channel offset: no secondary
         * STA channel width: 20 MHz
         * RIFS: 0
         * HT protection: non-HT mixed
         * non-GF present: 1
         * OBSS non-GF present: 1
         * dual beacon: 0
         * dual CTS protection: 0
         * STBC beacon: 0
         * L-SIG TXOP Prot: 0
         * PCO active: 0
         * PCO phase: 0
    WMM:     * Parameter version 1
         * BE: CW 15-1023, AIFSN 3
         * BK: CW 15-1023, AIFSN 7
         * VI: CW 7-15, AIFSN 2, TXOP 3008 usec
         * VO: CW 3-7, AIFSN 2, TXOP 1504 usec

root@Dell980:/etc/network# uname -a
Linux Dell980 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:12:35 UTC 2015 i686 i686 i686 GNU/Linux

```

 The output of wireless-info is shown below. Any advice will be gratefully received and much appreciated!

```

########## wireless info START ##########

Report from: 11 Dec 2015 17:41 PST -0800

Booted last: 11 Dec 2015 16:54 PST -0800

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-26-generic #28~14.04.1-Ubuntu SMP Wed Aug 12 14:12:35 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82578DM Gigabit Network Connection [8086:10ef] (rev 05)
    Subsystem: Dell OptiPlex 980 [1028:02da]
    Kernel driver in use: e1000e

##### lsusb #############################

Bus 002 Device 005: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 002 Device 008: ID 1516:8628 CompUSA Pen Drive
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

2: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k_htc              65536  0 
ath9k_common           32768  1 ath9k_htc
ath9k_hw              442368  2 ath9k_common,ath9k_htc
dell_wmi               16384  0 
sparse_keymap          16384  1 dell_wmi
ath                    24576  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211              618496  1 ath9k_htc
cfg80211              450560  4 ath,ath9k_common,mac80211,ath9k_htc
wmi                    20480  1 dell_wmi

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
          Interrupt:21 Memory:f7fe0000-f8000000 

wlan3     Link encap:Ethernet  HWaddr <MAC 'wlan3' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan3     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       757     1  0 16:54 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan3 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k_htc
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan3' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    dd-wrt:          Infra, <MAC 'dd-wrt' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52

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

[[/etc/NetworkManager/system-connections/NETGEAR]] (600 root)
[connection] id=NETGEAR | type=802-11-wireless
[802-11-wireless] ssid=NETGEAR | bssid=<MAC address> | mac-address=00:E0:4C:10:41:C5
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/Los_Angeles (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan3     13 channels in total; available frequencies :
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

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan3     Scan completed :
          Cell 01 - Address: <MAC 'dd-wrt' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"dd-wrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000536fc4c540f
                    Extra: Last beacon: 1284ms ago

##### module infos ######################

[ath9k_htc]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
firmware:       htc_9271.fw
firmware:       htc_7010.fw
description:    Atheros driver 802.11n HTC based wireless devices
license:        Dual BSD/GPL
author:         Atheros Communications
srcversion:     9FC596B0C1CEBEED9FFC60F
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A9:0C:A5:C5:24:E2:3A:FE:22:C9:47:A3:15:A8:52:38:50:22:46:62
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     8836292C9539A29CB162A5D
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A9:0C:A5:C5:24:E2:3A:FE:22:C9:47:A3:15:A8:52:38:50:22:46:62
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     C1A24C37619ED65AB1240B9
depends:        ath
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A9:0C:A5:C5:24:E2:3A:FE:22:C9:47:A3:15:A8:52:38:50:22:46:62
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.19.0-26-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A9:0C:A5:C5:24:E2:3A:FE:22:C9:47:A3:15:A8:52:38:50:22:46:62
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     DF4E06FB15FF0707074A816
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A9:0C:A5:C5:24:E2:3A:FE:22:C9:47:A3:15:A8:52:38:50:22:46:62
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.19.0-26-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-26-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        A9:0C:A5:C5:24:E2:3A:FE:22:C9:47:A3:15:A8:52:38:50:22:46:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k_htc]
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
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
blacklist rlt8192cu
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
# PCI device 0x8086:0x10ef (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"
# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan3' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan3"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by jremington on 2015-12-13
Alternatively, can someone recommend a USB wifi dongle that _actually works_ with Ubuntu 14.04?

---

### Post by kurt18947 on 2015-12-20
I'm surprised your AR9271 device isn't working. I have a Netgear WNA1100 which uses the same chipset and it connected perfectly last time I used it - a few months ago. Which RealTek device do you have? The RTL-8188cu* and RTL8192cu* work but not well out of the box. There's a patched RealTek driver that helps with those devices.

---

### Post by praseodym on 2015-12-20
Same driver here. Deactivate the hardware encryption:


```
echo "options ath9k_htc nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k_htc
sudo modprobe -v ath9k_htc
```
Re-plug the stick. If it gets too hot reduce the current:
```

echo 'KERNEL=="wlan*", ACTION=="add", RUN+="/sbin/iwconfig wlan0 txpower 15"' | sudo tee /etc/udev/rules.d/10-wlan-stick.rules
sudo service udev reload
sudo service udev restart
```

---

