---
title: "Very slow wireless download speed EeePC - with Broadcom Wifi"
date: 2015-12-04
forum: Networking &amp; Wireless
---

### Post by makem2 on 2015-12-04
I Have a BCM4313 wireless card in my EeePC netbook and have installed the latest driver and common files via synaptic.

The netbook is running xubuntu and has download speeds around 3 to 18 Mbps - never the same each time.

The Internet connection is cable with a download speed available of 50 Mbps.

I have another laptop with the same version of xubuntu and it always gets the full 50 Mps

Apart from ensuring the driver is correct I have no idea how to correct the slow speed and am wondering if it is the machine which is running slow but don't know how to check.

---

### Post by praseodym on 2015-12-04
Please run the wireless-script from the sticky-thread and show the outputs.

---

### Post by makem2 on 2015-12-04
Thank you for the quick reply.

I performed the updates which found nothing to update and then ran the script.

```


########## wireless info START ##########

Report from: 04 Dec 2015 21:17 GMT +0000

Booted last: 04 Dec 2015 21:09 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-39-generic #44~14.04.1-Ubuntu SMP Wed Dec 2 10:01:00 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 003: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
wl                   6148096  0 
cfg80211              450560  1 wl
video                  20480  2 i915,asus_wmi
sparse_keymap          16384  1 asus_wmi
wmi                    20480  1 asus_wmi

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
          inet addr:192.168.2.64  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7888 errors:0 dropped:0 overruns:0 frame:66210
          TX packets:4231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9241082 (9.2 MB)  TX bytes:551251 (551.2 KB)
          Interrupt:18 Base address:0xc000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"makem_2.4GHz"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'makem_2.4GHz' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       691     1  0 21:09 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [makem_2.4GHz] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTBusinessHub-773: Infra, <MAC 'BTBusinessHub-773' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    VM389200-2G:     Infra, <MAC 'VM389200-2G' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    virginmedia0907166: Infra, <MAC 'virginmedia0907166' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    TP-LINK_2FF848:  Infra, <MAC 'TP-LINK_2FF848' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    VM443055-2G:     Infra, <MAC 'VM443055-2G' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    roy:             Infra, <MAC 'roy' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    SKYAA379:        Infra, <MAC 'SKYAA379' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    VM703957-2G:     Infra, <MAC 'VM703957-2G' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    TonyVirgin-2G:   Infra, <MAC 'TonyVirgin-2G' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    TALKTALK4BC3BD:  Infra, <MAC 'TALKTALK4BC3BD' [AN10]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2 Enterprise
    BTOpenzone:      Infra, <MAC 'BTOpenzone' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    *makem_2.4GHz:   Infra, <MAC 'makem_2.4GHz' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2

  IPv4 Settings:
    Address:         192.168.2.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
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

[[/etc/NetworkManager/system-connections/makem_2.4GHz]] (600 root)
[connection] id=makem_2.4GHz | type=802-11-wireless
[802-11-wireless] ssid=makem_2.4GHz | bssid=<MAC 'makem_2.4GHz' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
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

lo        no frequency information.

eth0      no frequency information.

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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'makem_2.4GHz' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"makem_2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTBusinessHub-773' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"BTBusinessHub-773"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TP-LINK_2FF848' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_2FF848"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'BTOpenzone' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
          Cell 05 - Address: <MAC 'virginmedia0907166' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"virginmedia0907166"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SKYCDD48' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"SKYCDD48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VM703957-2G' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"VM703957-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'VM389200-2G' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"VM389200-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'VM443055-2G' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"VM443055-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-39-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-39-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        5F:47:0D:50:C8:0D:C3:A7:26:10:0B:0B:DB:54:40:20:A6:88:67:2C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

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
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.095048] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.147094] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.301548] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   16.994526] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  488.090412] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############



```

I am sorry but having read the output I cannot see anything I can use to help.

I rebooted and noticed a program error which asked that I report it. I don't think it detailed what the error was so I will try another reboot which the error suggested.

Edit: No error on reboot.

---

### Post by praseodym on 2015-12-04
Deactivate IPv6 in the network-manager settings. Alternatively, install the missing firmware for the card and use the native driver instead

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo apt-get remove --purge bcmwl-kernel-source 
```
Reboot

---

### Post by makem2 on 2015-12-04
> **praseodym said:**
> Deactivate IPv6 in the network-manager settings. Alternatively, install the missing firmware for the card and use the native driver instead

```
wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo apt-get remove --purge bcmwl-kernel-source 
```
Reboot

Did that and now don't have a network connection. Not sure how to use the native driver.

Output of script currently:

```


########## wireless info START ##########

Report from: 04 Dec 2015 21:17 GMT +0000

Booted last: 04 Dec 2015 21:09 GMT +0000

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.19.0-39-generic #44~14.04.1-Ubuntu SMP Wed Dec 2 10:01:00 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: AzureWave Device [1a3b:2047]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 003: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

eeepc_wmi              16384  0 
asus_wmi               24576  1 eeepc_wmi
wl                   6148096  0 
cfg80211              450560  1 wl
video                  20480  2 i915,asus_wmi
sparse_keymap          16384  1 asus_wmi
wmi                    20480  1 asus_wmi

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
          inet addr:192.168.2.64  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7888 errors:0 dropped:0 overruns:0 frame:66210
          TX packets:4231 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9241082 (9.2 MB)  TX bytes:551251 (551.2 KB)
          Interrupt:18 Base address:0xc000 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"makem_2.4GHz"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'makem_2.4GHz' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       691     1  0 21:09 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [makem_2.4GHz] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    BTBusinessHub-773: Infra, <MAC 'BTBusinessHub-773' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    VM389200-2G:     Infra, <MAC 'VM389200-2G' [AC8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    virginmedia0907166: Infra, <MAC 'virginmedia0907166' [AC5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    TP-LINK_2FF848:  Infra, <MAC 'TP-LINK_2FF848' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    VM443055-2G:     Infra, <MAC 'VM443055-2G' [AC9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    roy:             Infra, <MAC 'roy' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    SKYAA379:        Infra, <MAC 'SKYAA379' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA2
    VM703957-2G:     Infra, <MAC 'VM703957-2G' [AC7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    TonyVirgin-2G:   Infra, <MAC 'TonyVirgin-2G' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    TALKTALK4BC3BD:  Infra, <MAC 'TALKTALK4BC3BD' [AN10]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2 Enterprise
    BTOpenzone:      Infra, <MAC 'BTOpenzone' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    *makem_2.4GHz:   Infra, <MAC 'makem_2.4GHz' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2

  IPv4 Settings:
    Address:         192.168.2.64
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             208.67.222.222
    DNS:             208.67.220.220
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

[[/etc/NetworkManager/system-connections/makem_2.4GHz]] (600 root)
[connection] id=makem_2.4GHz | type=802-11-wireless
[802-11-wireless] ssid=makem_2.4GHz | bssid=<MAC 'makem_2.4GHz' [AC1]> | mac-address=<MAC 'wlan0' [IF]>
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

lo        no frequency information.

eth0      no frequency information.

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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      3   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'makem_2.4GHz' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"makem_2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'BTBusinessHub-773' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"BTBusinessHub-773"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'TP-LINK_2FF848' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_2FF848"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'BTOpenzone' [AC4]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"BTOpenzone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
          Cell 05 - Address: <MAC 'virginmedia0907166' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"virginmedia0907166"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SKYCDD48' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"SKYCDD48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'VM703957-2G' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"VM703957-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'VM389200-2G' [AC8]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"VM389200-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'VM443055-2G' [AC9]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"VM443055-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.19.0-39-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.19.0-39-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.19.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     F28307769349A31F4B24FC2
depends:        
intree:         Y
vermagic:       3.19.0-39-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        5F:47:0D:50:C8:0D:C3:A7:26:10:0B:0B:DB:54:40:20:A6:88:67:2C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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

[/etc/modprobe.d/broadcom-sta-common.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS

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
# PCI device 0x1969:0x1062 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   14.095048] wl: module license 'MIXED/Proprietary' taints kernel.
[   14.147094] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   14.301548] wlan0: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   16.994526] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  488.090412] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############



```

---

### Post by praseodym on 2015-12-04
Ok, so run:
```

sudo modprobe -rfv wl
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*) 
```
You can copy/paste the lines. Reboot afterwards.

---

### Post by makem2 on 2015-12-04
I have network connection now but the speed has not improved.

Test shows ping of 16 ms, download of 5.59 Mbps and upload 2.57 Mbps

I have been unable to disable ipv6 in network as there is only an ignore option which I chose. I disabled ipv6 in Firefox.

I have tried searching for methods of disabling ipv6 but none worked.

[URL="http://speedtest.net"]http://speedtest.net

[/URL]

---

### Post by praseodym on 2015-12-04
Lets try
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by makem2 on 2015-12-04
> **praseodym said:**
> Lets try
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
```


```

makem@netbook:~/Desktop$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
makem@netbook:~/Desktop$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 2634
makem@netbook:~/Desktop$ 


```

19; 7.65; 2.83 is the speed output from the test.

I will reboot and test again

Success!

15; 47.9; 3.10


So download speed is close to the maximum.

I am very grateful for your help and patience.

PS. I enjoyed my stay in Berlin last year :p

Edit: For the future, were all steps necessary or just one step?

I appear to have spoken to soon - the speed has dropped to 11 Mbps. I will leave it for now and try again tomorrow.

---

### Post by praseodym on 2015-12-05
Ok, so uninstall this file:
```

sudo apt-get remove --purge resolvconf
```
Repeat the other commands and reboot. Now it should be stable.

Yes, Berlin is the place to be ;)

---

### Post by makem2 on 2015-12-05
> **praseodym said:**
> Ok, so uninstall this file:
```

sudo apt-get remove --purge resolvconf
```
Repeat the other commands and reboot. Now it should be stable.

Yes, Berlin is the place to be ;)

"Other commands" being which?

I have repeated:
 	```
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart

```

After a reboot the speed is still slow = 760 ms ping 6.82 Mbps upload and 1.57 Mbps upload

---

### Post by praseodym on 2015-12-05
Lets check
```

lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
route -n
```

---

### Post by makem2 on 2015-12-05
I decided to run all the commands again:

```

makem@netbook:~/Desktop$ wget http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz
--2015-12-05 11:38:11--  http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz
Resolving media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)... 213.95.41.4, 2001:780:0:25:dead:beef:cafe:1
Connecting to media.cdn.ubuntu-de.org (media.cdn.ubuntu-de.org)|213.95.41.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 99011 (97K) [application/octet-stream]
Saving to: ‘2480236-Broadcom_Firmware.tar.gz.2’

100%[======================================>] 99,011       472KB/s   in 0.2s   

2015-12-05 11:38:12 (472 KB/s) - ‘2480236-Broadcom_Firmware.tar.gz.2’ saved [99011/99011]

makem@netbook:~/Desktop$ sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
b43/
b43legacy/
b43/b0g0initvals5.fw
b43/b0g0bsinitvals5.fw
b43/a0g0initvals5.fw
b43/a0g1initvals5.fw
b43/a0g0bsinitvals5.fw
b43/a0g1bsinitvals5.fw
b43/b0g0initvals9.fw
b43/b0g0bsinitvals9.fw
b43/a0g0initvals9.fw
b43/a0g1initvals9.fw
b43/a0g0bsinitvals9.fw
b43/a0g1bsinitvals9.fw
b43/n0initvals11.fw
b43/n0bsinitvals11.fw
b43/n0absinitvals11.fw
b43/lp0initvals13.fw
b43/lp0bsinitvals13.fw
b43/b0g0initvals13.fw
b43/b0g0bsinitvals13.fw
b43/a0g1initvals13.fw
b43/a0g1bsinitvals13.fw
b43/lp0initvals14.fw
b43/lp0bsinitvals14.fw
b43/lp0initvals15.fw
b43/lp0bsinitvals15.fw
b43/ucode5.fw
b43/ucode9.fw
b43/ucode11.fw
b43/ucode13.fw
b43/ucode14.fw
b43/ucode15.fw
b43/pcm5.fw
b43legacy/a0g0bsinitvals5.fw
b43legacy/b0g0initvals2.fw
b43legacy/b0g0initvals5.fw
b43legacy/b0g0bsinitvals2.fw
b43legacy/a0g1initvals5.fw
b43legacy/a0g0initvals2.fw
b43legacy/a0g1bsinitvals5.fw
b43legacy/a0g0initvals5.fw
b43legacy/b0g0bsinitvals5.fw
b43legacy/a0g0bsinitvals2.fw
b43legacy/pcm5.fw
b43legacy/pcm4.fw
b43legacy/ucode11.fw
b43legacy/ucode5.fw
b43legacy/ucode4.fw
b43legacy/ucode2.fw
makem@netbook:~/Desktop$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
makem@netbook:~/Desktop$ sudo reboot

```


```

makem@netbook:~/Desktop$ sudo modprobe -rfv wl
[sudo] password for makem: 
modprobe: FATAL: Module wl not found.
makem@netbook:~/Desktop$ sudo rm /etc/modprobe.d/blacklist-bcm43.conf
rm: cannot remove ‘/etc/modprobe.d/blacklist-bcm43.conf’: No such file or directory
makem@netbook:~/Desktop$ sudo rm /etc/modprobe.d/broadcom-sta-common.conf
rm: cannot remove ‘/etc/modprobe.d/broadcom-sta-common.conf’: No such file or directory
makem@netbook:~/Desktop$ sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf
rm: cannot remove ‘/etc/modprobe.d/broadcom-sta-dkms.conf’: No such file or directory
makem@netbook:~/Desktop$ sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sed: no input files
makem@netbook:~/Desktop$ sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sed: no input files
makem@netbook:~/Desktop$ sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*)
sed: no input files
makem@netbook:~/Desktop$ sudo sed -i "s/blacklist brcmsmac/#blacklist brcmsmac/g" $(egrep -lo 'blacklist brcmsmac' /etc/modprobe.d/*)
sed: no input files
makem@netbook:~/Desktop$ echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
nameserver 8.8.8.8
nameserver 8.8.4.4
makem@netbook:~/Desktop$ sudo service network-manager restart
network-manager stop/waiting
network-manager start/running, process 2139
makem@netbook:~/Desktop$ sudo apt-get remove --purge resolvconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'resolvconf' is not installed, so not removed
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
makem@netbook:~/Desktop$ 

```

The download speed went s follows over 10 tests:

47.5; 23.1; 5.9; 2.3; 51.48; 81.46; 43.99; 21.61; 29.88; 34.46

At times the output rose to 100 Mbps during the test, dropping back to the above latter faster speeds.

I think I should leave it at this stage and see what happens over a few days.

I have the feeling that the OS itself may have something to do with this as it does seem rather slow. I may be wrong as this netbook is a far slower machine than the one I use daily and I may be biased. I think while I wait to see if the speed becomes more stable, I will see if I can find a method to 'refresh' the  OS

Thanks again for the input, I will report back.

> **praseodym said:**
> Lets check
```

lsmod
ifconfig -a
iwconfig
cat /etc/resolv.conf
route -n
```

```

makem@netbook:~/Desktop$ lsmod
Module                  Size  Used by
ctr                    16384  2 
ccm                    20480  2 
arc4                   16384  2 
bnep                   20480  2 
rfcomm                 61440  4 
bluetooth             430080  10 bnep,rfcomm
brcmsmac              536576  0 
cordic                 16384  1 brcmsmac
brcmutil               16384  1 brcmsmac
b43                   397312  0 
mac80211              618496  2 b43,brcmsmac
cfg80211              450560  3 b43,brcmsmac,mac80211
ssb                    57344  1 b43
eeepc_wmi              16384  0 
snd_hda_codec_realtek    69632  1 
asus_wmi               24576  1 eeepc_wmi
snd_hda_codec_generic    65536  1 snd_hda_codec_realtek
snd_hda_intel          32768  3 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         122880  4 snd_hda_codec_realtek,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              16384  1 snd_hda_codec
uvcvideo               73728  0 
snd_pcm                94208  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
videobuf2_vmalloc      16384  1 uvcvideo
videobuf2_memops       16384  1 videobuf2_vmalloc
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
videodev              139264  3 uvcvideo,v4l2_common,videobuf2_core
media                  24576  2 uvcvideo,videodev
snd_seq_midi           16384  0 
snd_seq_midi_event     16384  1 snd_seq_midi
coretemp               16384  0 
snd_rawmidi            28672  1 snd_seq_midi
i915                  921600  3 
snd_seq                57344  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0 
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              16384  0 
snd_timer              28672  2 snd_pcm,snd_seq
drm_kms_helper        114688  1 i915
bcma                   49152  3 b43,brcmsmac
lpc_ich                20480  0 
snd                    69632  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   286720  5 i915,drm_kms_helper
soundcore              16384  2 snd,snd_hda_codec
i2c_algo_bit           16384  1 i915
shpchp                 32768  0 
wmi                    20480  1 asus_wmi
video                  20480  2 i915,asus_wmi
mac_hid                16384  0 
sparse_keymap          16384  1 asus_wmi
parport_pc             32768  0 
ppdev                  20480  0 
lp                     16384  0 
parport                40960  3 lp,ppdev,parport_pc
hid_generic            16384  0 
usbhid                 49152  0 
hid                    98304  3 hid_generic,usbhid
psmouse               102400  0 
ahci                   28672  2 
libahci                32768  1 ahci
atl1c                  45056  0 
makem@netbook:~/Desktop$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:39:9e:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:693 errors:0 dropped:0 overruns:0 frame:0
          TX packets:693 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:71309 (71.3 KB)  TX bytes:71309 (71.3 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:a8:5d:fa  
          inet addr:192.168.2.64  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::4a5d:60ff:fea8:5dfa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:301959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:447027470 (447.0 MB)  TX bytes:9660322 (9.6 MB)

makem@netbook:~/Desktop$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"makem_2.4GHz"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: AC:9E:17:66:5D:58   
          Bit Rate=72.2 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:181   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

makem@netbook:~/Desktop$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 127.0.1.1
makem@netbook:~/Desktop$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
makem@netbook:~/Desktop$ 

```

---

### Post by praseodym on 2015-12-06
Two modules are loaded:
```

sudo modprobe -rfv b43 brcmsmac
sudo modprobe -v brcmsmac
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by makem2 on 2015-12-06
> **praseodym said:**
> Two modules are loaded:
```

sudo modprobe -rfv b43 brcmsmac
sudo modprobe -v brcmsmac
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo depmod -a
sudo update-initramfs -u
```

Do you mean I should not have two modules loaded?

Do I need to run that code?

---

### Post by praseodym on 2015-12-06
Yes, and yes ;)

---

### Post by makem2 on 2015-12-06
> **praseodym said:**
> Yes, and yes ;)

```

makem@netbook:~/Desktop$ sudo modprobe -rfv b43 brcmsmac
makem@netbook:~/Desktop$ sudo modprobe -v brcmsmac
insmod /lib/modules/3.19.0-39-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.19.0-39-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.19.0-39-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko 
insmod /lib/modules/3.19.0-39-generic/kernel/lib/cordic.ko 
insmod /lib/modules/3.19.0-39-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko 
makem@netbook:~/Desktop$ echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist b43
makem@netbook:~/Desktop$ sudo depmod -a
makem@netbook:~/Desktop$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.19.0-39-generic
makem@netbook:~/Desktop$ sudo reboot


```

The online speed test shows these results:

ping 28 ms 6.65 Mbps download 2.96 Mbps upload

I started a 1 GB download and checked the speed using my router bandwidth monitor. That showed a variable speed of between 11 and 40 Mbps averaging about 25 Mbps.

Do you think that would be what I should expect? It is certainly better than when I started.

Edit: I timed the 1 GB download and it took 6 min 3 sec.

---

