---
title: "BCM4360 &amp; bcmwl-kernel-source cause high cpu use"
date: 2015-04-08
forum: Networking &amp; Wireless
---

### Post by CMDR:ZOD on 2015-04-08
Hi I have no issues with installing the software and getting my wifi running. What my problems is, when I use the driver my system grinds to a halt for 2-5 seconds every 2-5 seconds making the system unusable. This only occurs while wifi is running. I do a fresh install of 14.04.2 x64 and first thing I do is install bcmwl-kernel-source so I can untether my phone and use wifi. 

As soon as the driver is making use of the hardware, the lags begin. Xorg, kworker, migration and even network manager tasks will show intermittent high cpu use (30-70%) while the lags are taking place. I am using an ASUS PCE-AC68 wifi card. 

Has anyone run into this before or know how to solve the issue of high CPU use while using bcmwl-kernel driver for the BCM4360?

---

### Post by Hadaka on 2015-04-08
was this the method you used to load your wifi driver?
[URL="http://ubuntuforums.org/showthread.php?t=2159851"]http://ubuntuforums.org/showthread.php?t=2159851

#post 4,5,6
[/URL]

---

### Post by CMDR:ZOD on 2015-04-08
> **Hadaka said:**
> was this the method you used to load your wifi driver?
[URL="http://ubuntuforums.org/showthread.php?t=2159851"]http://ubuntuforums.org/showthread.php?t=2159851

#post 4,5,6
[/URL]

No I used "sudo apt-get install bcmwl-kernel-source". I tried using ndiswrapper, but its a PITA and I could not get it to work properly.

---

### Post by Hadaka on 2015-04-08
Hi, that was an outdated method anyway, I aoplogize for that
i dint notice the date.Try posting the wireless script and we
will see what may be causing your lag.
 [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)
thanks

---

### Post by CMDR:ZOD on 2015-04-08
Here is the output of the network test script while connected to wifi using the wl driver.

```

########## wireless info START ##########

Report from: 08 Apr 2015 18:49 MDT -0600

Booted last: 08 Apr 2015 18:37 MDT -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:854f]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 003: ID 0bc2:3008 Seagate RSS LLC 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04e8:6864 Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6367819  0 
cfg80211              484040  1 wl
eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
video                  19476  1 asus_wmi
mxm_wmi                13021  0 
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

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet6 addr: fe80::3:4ff:fe5a:3664/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:216484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:113246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:321735877 (321.7 MB)  TX bytes:12825271 (12.8 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.83  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::5246:5dff:fe6b:b9c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:3847
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15747 (15.7 KB)  TX bytes:15762 (15.7 KB)
          Interrupt:19 

##### iwconfig ##########################

usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Renegade"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Renegade' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

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

- Device: wlan0  [Renegade] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           175 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Renegade_NeXT:   Infra, <MAC 'Renegade_NeXT' [AN1]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 85 WPA2
    TELUS7741:       Infra, <MAC 'TELUS7741' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89 WPA WPA2
    TELUS0821:       Infra, <MAC 'TELUS0821' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    SHAW-E961E1:     Infra, <MAC 'SHAW-E961E1' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 75 WPA WPA2
    TELUS2033:       Infra, <MAC 'TELUS2033' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA2
    Tammy:           Infra, <MAC 'Tammy' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    TELUS0853:       Infra, <MAC 'TELUS0853' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    TELUS1103:       Infra, <MAC 'TELUS1103' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA2
    TELUS3032:       Infra, <MAC 'TELUS3032' [AN9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    pfaffy:          Infra, <MAC 'pfaffy' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Jennifer:        Infra, <MAC 'Jennifer' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    TELUS4524:       Infra, <MAC 'TELUS4524' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA WPA2
    vasilica:        Infra, <MAC 'vasilica' [AN13]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    SHAW-E961E1-5G:  Infra, <MAC 'SHAW-E961E1-5G' [AN14]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2
    743961:          Infra, <MAC '743961' [AN15]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    OptikTV_9601C16D:Infra, <MAC 'OptikTV_9601C16D' [AN16]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 45 WPA2
    SHAW-9E6097-5G:  Infra, <MAC 'SHAW-9E6097-5G' [AN17]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    TELUS1103-5G:    Infra, <MAC 'TELUS1103-5G' [AN18]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 35 WPA2
    OptikTV_96119649:Infra, <MAC 'OptikTV_96119649' [AN19]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 34 WPA2
    OptikTV_96029A37:Infra, <MAC 'OptikTV_96029A37' [AN20]>, Freq 5220 MHz, Rate 54 Mb/s, Strength 32 WPA2
    SHAW-9CACF5-5G:  Infra, <MAC 'SHAW-9CACF5-5G' [AN21]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SHAW-6562AF-5G:  Infra, <MAC 'SHAW-6562AF-5G' [AN22]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SHAW-9DB84F-5G:  Infra, <MAC 'SHAW-9DB84F-5G' [AN23]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SHAW-EEAC81-5G:  Infra, <MAC 'SHAW-EEAC81-5G' [AN24]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Reopard-5G:      Infra, <MAC 'Reopard-5G' [AN25]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Jennifer:        Infra, <MAC 'Jennifer' [AN26]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SHAW-FD4A33-5G:  Infra, <MAC 'SHAW-FD4A33-5G' [AN27]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    SHAW-5E8348-5G:  Infra, <MAC 'SHAW-5E8348-5G' [AN28]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    SHAW-BDDE69-5G:  Infra, <MAC 'SHAW-BDDE69-5G' [AN29]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    SHAW-CDEE90-5G:  Infra, <MAC 'SHAW-CDEE90-5G' [AN30]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 24 WPA2
    OpenWifiMovement:Infra, <MAC 'OpenWifiMovement' [AN31]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    *Renegade:       Infra, <MAC 'Renegade' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    6360B9:          Infra, <MAC '6360B9' [AN33]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.83
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

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

[[/etc/NetworkManager/system-connections/OpenWifiMovement]] (600 root)
[connection] id=OpenWifiMovement | type=802-11-wireless
[802-11-wireless] ssid=OpenWifiMovement | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Renegade]] (600 root)
[connection] id=Renegade | type=802-11-wireless
[802-11-wireless] ssid=Renegade | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Edmonton (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

usb0      no frequency information.

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 50 : 5.25 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

usb0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Renegade' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Renegade"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 33492ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x43a0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  671.093202] wlan0: Broadcom BCM43a0 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[  675.168431] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22) (repeated 2 times)
[  766.853709] ERROR @wl_dev_intvar_get : error (-1)
[  772.158741] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)

########## wireless info END ############

```

---

### Post by Hadaka on 2015-04-08
Let's start by doing a little cleanup and then post the wireless info again please.
```
sudo iw reg set CA
sudo sed -i 's/^REG.*=$/&CA/' /etc/default/crda
```
also change your IPv6 to Ignore
thanks.

---

### Post by CMDR:ZOD on 2015-04-09
Ok I've run those commands and set IPv6 to ignore in my connection settings.
```

########## wireless info START ##########

Report from: 09 Apr 2015 10:46 MDT -0600

Booted last: 09 Apr 2015 10:36 MDT -0600

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-48-generic #80-Ubuntu SMP Thu Mar 12 11:16:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash

##### desktop ###########################

Ubuntu

##### lspci #############################

09:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 09)
    Subsystem: ASUSTeK Computer Inc. P8H77-I Motherboard [1043:8505]
    Kernel driver in use: r8169

0a:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device [1043:854f]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 003: ID 0bc2:3008 Seagate RSS LLC 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 04e8:6864 Samsung Electronics Co., Ltd 
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

eeepc_wmi              13151  0 
asus_wmi               24191  1 eeepc_wmi
sparse_keymap          13948  1 asus_wmi
video                  19476  1 asus_wmi
mxm_wmi                13021  0 
wl                   6367819  0 
cfg80211              484040  1 wl
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

usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet6 addr: fe80::3:4ff:fe5a:3664/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4684000 (4.6 MB)  TX bytes:522791 (522.7 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.2.83  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::5246:5dff:fe6b:b9c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:116 errors:0 dropped:0 overruns:0 frame:3784
          TX packets:253 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39036 (39.0 KB)  TX bytes:34124 (34.1 KB)
          Interrupt:19 

##### iwconfig ##########################

usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Renegade"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'Renegade' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

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

- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'usb0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

- Device: wlan0  [Renegade] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           216 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Renegade_NeXT:   Infra, <MAC 'Renegade_NeXT' [AC20]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 94 WPA2
    TELUS3032:       Infra, <MAC 'TELUS3032' [AC10]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 92 WPA2
    SHAW-E961E1:     Infra, <MAC 'SHAW-E961E1' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    Tammy:           Infra, <MAC 'Tammy' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    TELUS4524:       Infra, <MAC 'TELUS4524' [AN5]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    SHAW-9E6097:     Infra, <MAC 'SHAW-9E6097' [AN6]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    2A50EE:          Infra, <MAC '2A50EE' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    Jennifer:        Infra, <MAC 'Jennifer' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    vasilica:        Infra, <MAC 'vasilica' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    TELUS2033:       Infra, <MAC 'TELUS2033' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA2
    6360B9:          Infra, <MAC '6360B9' [AN11]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    SHAW-E961E1-5G:  Infra, <MAC 'SHAW-E961E1-5G' [AC16]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    TELUS0853:       Infra, <MAC 'TELUS0853' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    8BF23B:          Infra, <MAC '8BF23B' [AN14]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    OptikTV_96029A37:Infra, <MAC 'OptikTV_96029A37' [AC22]>, Freq 5805 MHz, Rate 54 Mb/s, Strength 47 WPA2
    OptikTV_9601C16D:Infra, <MAC 'OptikTV_9601C16D' [AC15]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 44 WPA2
    SHAW-9E6097-5G:  Infra, <MAC 'SHAW-9E6097-5G' [AC17]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    8CC012:          Infra, <MAC '8CC012' [AN18]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    OptikTV_96119649:Infra, <MAC 'OptikTV_96119649' [AC12]>, Freq 5180 MHz, Rate 54 Mb/s, Strength 37 WPA2
    Jennifer:        Infra, <MAC 'Jennifer' [AC14]>, Freq 5240 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SHAW-9CACF5-5G:  Infra, <MAC 'SHAW-9CACF5-5G' [AC18]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    SHAW-CDEE90-5G:  Infra, <MAC 'SHAW-CDEE90-5G' [AC21]>, Freq 5785 MHz, Rate 54 Mb/s, Strength 29 WPA2
    TELUS1103-5G:    Infra, <MAC 'TELUS1103-5G' [AN23]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Reopard-5G:      Infra, <MAC 'Reopard-5G' [AC13]>, Freq 5200 MHz, Rate 54 Mb/s, Strength 25 WPA2
    SHAW-9DB84F-5G:  Infra, <MAC 'SHAW-9DB84F-5G' [AN25]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    SHAW-EEAC81-5G:  Infra, <MAC 'SHAW-EEAC81-5G' [AC19]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    OpenWifiMovement:Infra, <MAC 'OpenWifiMovement' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    pfaffy:          Infra, <MAC 'pfaffy' [AN28]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    TELUS1103:       Infra, <MAC 'TELUS1103' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    TELUS0821:       Infra, <MAC 'TELUS0821' [AN30]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    TELUS0492:       Infra, <MAC 'TELUS0492' [AC11]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    CDC12D:          Infra, <MAC 'CDC12D' [AC5]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    TELUS1882:       Infra, <MAC 'TELUS1882' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    58A723:          Infra, <MAC '58A723' [AN34]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    FLAMENCO:        Infra, <MAC 'FLAMENCO' [AN35]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA
    TELUS7741:       Infra, <MAC 'TELUS7741' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    SHAW-6562AF-5G:  Infra, <MAC 'SHAW-6562AF-5G' [AN37]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    SHAW-5E8348-5G:  Infra, <MAC 'SHAW-5E8348-5G' [AN38]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    SHAW-BDDE69-5G:  Infra, <MAC 'SHAW-BDDE69-5G' [AN39]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    SHAW-FD4A33-5G:  Infra, <MAC 'SHAW-FD4A33-5G' [AN40]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    SHAW-EEAC81:     Infra, <MAC 'SHAW-EEAC81' [AN41]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    743961:          Infra, <MAC '743961' [AC9]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    SHAW-CDEE90:     Infra, <MAC 'SHAW-CDEE90' [AN43]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    TELUS4613:       Infra, <MAC 'TELUS4613' [AN44]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    SHAW-6562AF:     Infra, <MAC 'SHAW-6562AF' [AN45]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    *Renegade:       Infra, <MAC 'Renegade' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 97 WPA2

  IPv4 Settings:
    Address:         192.168.2.83
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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

[[/etc/NetworkManager/system-connections/OpenWifiMovement]] (600 root)
[connection] id=OpenWifiMovement | type=802-11-wireless
[802-11-wireless] ssid=OpenWifiMovement | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=ignore
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Renegade]] (600 root)
[connection] id=Renegade | type=802-11-wireless
[802-11-wireless] ssid=Renegade | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: America/Edmonton (based on set time zone)

country CA:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)

##### iwlist channels ###################

usb0      no frequency information.

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Channel 108 : 5.54 GHz
          Channel 110 : 5.55 GHz
          Channel 112 : 5.56 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      4   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      4   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      2   APs on   Frequency:5.24 GHz (Channel 48)
      1   APs on   Frequency:5.2 GHz (Channel 40)
      4   APs on   Frequency:5.745 GHz
      2   APs on   Frequency:5.785 GHz
      1   APs on   Frequency:5.805 GHz

usb0      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Renegade' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"Renegade"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'OpenWifiMovement' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-23 dBm  
                    Encryption key:off
                    ESSID:"OpenWifiMovement"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
          Cell 03 - Address: <MAC 'TELUS1882' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"TELUS1882"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'vasilica' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"vasilica"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'CDC12D' [AC5]>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"CDC12D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'SHAW-E961E1' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"SHAW-E961E1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'TELUS1103' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"TELUS1103"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'TELUS7741' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"TELUS7741"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC '743961' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"743961"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'TELUS3032' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"TELUS3032"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC 'TELUS0492' [AC11]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"TELUS0492"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'OptikTV_96119649' [AC12]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"OptikTV_96119649"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC 'Reopard-5G' [AC13]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Reopard-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC 'Jennifer' [AC14]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Jennifer"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC 'OptikTV_9601C16D' [AC15]>
                    Channel:48
                    Frequency:5.24 GHz (Channel 48)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"OptikTV_9601C16D"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC 'SHAW-E961E1-5G' [AC16]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"SHAW-E961E1-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC 'SHAW-9E6097-5G' [AC17]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"SHAW-9E6097-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC 'SHAW-9CACF5-5G' [AC18]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"SHAW-9CACF5-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC 'SHAW-EEAC81-5G' [AC19]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"SHAW-EEAC81-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC 'Renegade_NeXT' [AC20]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Renegade_NeXT"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC 'SHAW-CDEE90-5G' [AC21]>
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"SHAW-CDEE90-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC 'OptikTV_96029A37' [AC22]>
                    Channel:161
                    Frequency:5.805 GHz
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"OptikTV_96029A37"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 27436ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.13.0-48-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.13.0-48-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

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

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapper

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x43a0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  305.475326] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)
[  568.990563] ERROR @wl_notify_scan_status : wlan0 Scan_results error (-22)

########## wireless info END ############


```

---

### Post by chili555 on 2015-04-09
> [/etc/modprobe.d/ndiswrapper.conf]
alias wlan0 ndiswrapperI'm pretty sure that isn't helping us much. Let's remove it and make sure ndiswrapper is completely gone:```
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo apt-get purge ndiswrapper*
```Did the crda take effect?```
sudo iw reg get
```Finally, run this command:```
top
```What are the processes that are using up more than 15% of your CPU cycles? Get out of 'top' with q.

---

### Post by CMDR:ZOD on 2015-04-10
So I completely removed ndiswrapper using your commands above. The output of sudo iw reg get:

country CA:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)


while in top the highest CPU tasks are:
migration/1 to migration/3
kworker/1,2,3 spike high during the system lags as well.
Also networkmanager shows spikes into 70% while lags are occuring. 
The Xorg process also shows high CPU use while idle and connected to wifi. Up to 70%.

Also, when the lag happens while I am using the keyboard, when the PC becomes responsive again it will keep typing the last key pressed during the PC 2-5 second lag. I have to hit a key on the keyboard to make it stop.

---

