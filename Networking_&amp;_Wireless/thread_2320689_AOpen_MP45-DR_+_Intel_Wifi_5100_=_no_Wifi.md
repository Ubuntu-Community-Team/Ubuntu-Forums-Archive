---
title: "AOpen MP45-DR + Intel Wifi 5100 = no Wifi"
date: 2016-04-16
forum: Networking &amp; Wireless
---

### Post by renta2 on 2016-04-16
Hello,

i am like Princiess Leila in Star Wars, who is asking help in hologram to Ben Kennoby : ***You are my last hope !!***
:)

my pc is :
AOpen MP45-DR
with Intel Wifi 5100 PCIe inside

this always worked good under Windows7-64bit

I recently installed Ubuntu 14.04 LTS 64bit but wifi don't work

this pc is a mini-pc, with portable pc components inside, but it don't have any wifi hardware switch.
And the keyboard is a standard pc, si there is no Fn+??? to switch wifi on-off

lspci can list wifi card 5100
rkill list "do nothing"

i also tried liveusb ubuntu 15.10, the the result is the same :
lspci can list wifi card 5100
rkill list "do nothing"

i have try some thing but always don't work, with help form ubuntu-fr forum.

here is wireless-info log :

```

########## wireless info START ##########

Report from: 16 Apr 2016 17:41 CEST +0200

Booted last: 16 Apr 2016 17:39 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF Gigabit Network Connection [8086:10bf] (rev 03)
    Subsystem: AOPEN Inc. Device [a0a0:0647]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 0fd9:0051 Elgato Systems GmbH 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 002: ID 1934:0702 Feature Integration Technology Inc. (Fintek) Integrated Consumer Infrared Receiver/Transceiver
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 06f2:0011 Emine Technology Co. KVM Switch Keyboard
Bus 007 Device 004: ID 413c:2107 Dell Computer Corp. 
Bus 007 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 007 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

iwldvm                233472  0 
mac80211              741376  1 iwldvm
iwlwifi               208896  1 iwldvm
cfg80211              552960  3 iwlwifi,mac80211,iwldvm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a01:e34:ee6b:49f0:54a:562f:b8aa:b053/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2a01:e34:ee6b:49f0:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:425 errors:0 dropped:0 overruns:0 frame:0
          TX packets:550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:194786 (194.7 KB)  TX bytes:80095 (80.0 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       719     1  0 17:39 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e34:ee6b:49f0:54a:562f:b8aa:b053
    Prefix:          64
    Gateway:         fe80::207:cbff:feb0:4914

    Address:         2a01:e34:ee6b:49f0:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::207:cbff:feb0:4914

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::207:cbff:feb0:4914

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

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

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     B715639CA9F6E3BA25A93FD
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     2AFF7BF1EB0D33D3ACDC867
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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
# PCI device 0x8086:0x10bf (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    2.233082] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.233086] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.233088] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.233091] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x50
[    2.233153] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled
[    2.283383] iwlwifi 0000:02:00.0: Unsupported (too old) EEPROM VER=0x114 < 0x11a CALIB=0x1 < 0x4
[    3.072221] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    4.704874] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[    4.704995] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[    4.705031] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-04-16
Buy a new wifi card from someplace other than where the one you have is from.  A google search on an error in dmesg indicates that your card may be a leaked engineering sample

---

### Post by renta2 on 2016-04-16
i don't agreee in my case, my wifi card work good,

it work fully perfect under Windows.

There's must be only one setting to do in ubuntu (under windows it work)

---

### Post by jeremy31 on 2016-04-16
It doesn't matter if it works in Windows, Intel is not going to release any source code or firmware to make it work in Linux per [http://article.gmane.org/gmane.linux.kernel.commits.head/198188](http://article.gmane.org/gmane.linux.kernel.commits.head/198188)

Why they allow them to work in Windows is something we may never know

---

### Post by renta2 on 2016-04-16
ok, i read the link, but this is not very happy for me,

i think to buy a new card, but i have only 3 choice, and if i do, i would to be sure the card will work good under ubuntu.

Can you tell me witch card to choose ?

Intel 7260
[http://www.ldlc.com/fiche/PB00172163.html](http://www.ldlc.com/fiche/PB00172163.html)

Gigabyte GAXM31SR-00-G
[http://www.ldlc.com/fiche/PB00179048.html](http://www.ldlc.com/fiche/PB00179048.html)

Silverstone ECW02
[http://www.ldlc.com/fiche/PB00190824.html](http://www.ldlc.com/fiche/PB00190824.html)

---

### Post by jeremy31 on 2016-04-16
Intel 7260 is the choice I would make, actually it is a choice I did make and I bought 2 different versions.  One has bluetooth and one doesn't and they work with Linux.  If it doesn't work after installing, post back and we will make it work

I doubt if any changes will be needed as the kernel source code for the 4.2 kernel supports 64 different versions of the 7260

---

### Post by renta2 on 2016-04-16
ok

---

### Post by renta2 on 2016-04-23
hello, i'm back,
i have now an Intel 7260 now, the wifi menu appear near clock (bluetooth too)

it can list all the wifi around.
It create a manual connection to my wifi (hiden ssid, with wpa) but it don't connect...

when i used others devices to connect to my wifi, it's working.

i don't what i can do ?

here is wireless-info
```

########## wireless info START ##########

Report from: 23 Apr 2016 13:55 CEST +0200

Booted last: 23 Apr 2016 13:52 CEST +0200

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.2.0-35-generic #40~14.04.1-Ubuntu SMP Fri Mar 18 16:37:35 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82567LF Gigabit Network Connection [8086:10bf] (rev 03)
    Subsystem: AOPEN Inc. Device [a0a0:0647]
    Kernel driver in use: e1000e

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:4060]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 0fd9:0051 Elgato Systems GmbH 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 008 Device 002: ID 1934:0702 Feature Integration Technology Inc. (Fintek) Integrated Consumer Infrared Receiver/Transceiver
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 005: ID 06f2:0011 Emine Technology Co. KVM Switch Keyboard
Bus 007 Device 004: ID 413c:2107 Dell Computer Corp. 
Bus 007 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 007 Device 002: ID 05e3:0604 Genesys Logic, Inc. USB 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 8087:07dc Intel Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                290816  0 
mac80211              741376  1 iwlmvm
iwlwifi               208896  1 iwlmvm
cfg80211              552960  3 iwlwifi,mac80211,iwlmvm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2a01:e34:ee6b:49f0:a465:b876:fdcd:a8b/64 Scope:Global
          inet6 addr: 2a01:e34:ee6b:49f0:<IP6 'eth0' [IF]>/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197771 (197.7 KB)  TX bytes:130912 (130.9 KB)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.254   0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       747     1  0 13:52 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    freeboxminouche: Infra, <MAC 'freeboxminouche' [AC2]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 62 WPA
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC4]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 59 WPA Enterprise
    FreeWifi_secure: Infra, <MAC 'FreeWifi_secure' [AC13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC3]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 54
    freebox_EnJarez: Infra, <MAC 'freebox_EnJarez' [AC8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WPA
    FREEBOX_LOUISA_6R: Infra, <MAC 'FREEBOX_LOUISA_6R' [AC11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50 WPA
    SFR WiFi Mobile: Infra, <MAC 'SFR WiFi Mobile' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    FreeWifi:        Infra, <MAC 'FreeWifi' [AC12]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    SFR WiFi FON:    Infra, <MAC 'SFR WiFi FON' [AC7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.254

    DNS:             212.27.40.240
    DNS:             212.27.40.241

  IPv6 Settings:
    Address:         2a01:e34:ee6b:49f0:a465:b876:fdcd:a8b
    Prefix:          64
    Gateway:         fe80::207:cbff:feb0:4914

    Address:         2a01:e34:ee6b:49f0:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::207:cbff:feb0:4914

    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::207:cbff:feb0:4914

    DNS:             2a01:e00::2
    DNS:             2a01:e00::1

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

[[/etc/NetworkManager/system-connections/Olivier_Maison]] (600 root)
[connection] id=Olivier_Maison | type=802-11-wireless
[802-11-wireless] ssid=Olivier_Maison | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Paris (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      5   APs on   Frequency:2.412 GHz (Channel 1)
      5   APs on   Frequency:2.462 GHz (Channel 11)
      3   APs on   Frequency:2.472 GHz (Channel 13)

wlan0     Scan completed :
          Cell 01 - Address: <MAC '' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ebe9a7b30
                    Extra: Last beacon: 20748ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'freeboxminouche' [AC2]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"freeboxminouche"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025b41601b04
                    Extra: Last beacon: 3040ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'FreeWifi' [AC3]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025b41602607
                    Extra: Last beacon: 17772ms ago
          Cell 04 - Address: <MAC 'FreeWifi_secure' [AC4]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000025b41605025
                    Extra: Last beacon: 17772ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC 'SFR WiFi Mobile' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"SFR WiFi Mobile"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e70be871bb
                    Extra: Last beacon: 17772ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ebfa8c1d6
                    Extra: Last beacon: 3024ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'SFR WiFi FON' [AC7]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"SFR WiFi FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e70be89865
                    Extra: Last beacon: 17772ms ago
          Cell 08 - Address: <MAC 'freebox_EnJarez' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"freebox_EnJarez"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024d64ca5e9
                    Extra: Last beacon: 88ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'NEUF_7140' [AC9]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"NEUF_7140"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000e70be88da6
                    Extra: Last beacon: 17772ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC 'FreeWifi' [AC10]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000024d53f0c32
                    Extra: Last beacon: 17772ms ago
          Cell 11 - Address: <MAC 'FREEBOX_LOUISA_6R' [AC11]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FREEBOX_LOUISA_6R"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002bbef019854
                    Extra: Last beacon: 17772ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC 'FreeWifi' [AC12]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:off
                    ESSID:"FreeWifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002bbef01a0d1
                    Extra: Last beacon: 3092ms ago
          Cell 13 - Address: <MAC 'FreeWifi_secure' [AC13]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FreeWifi_secure"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s
                    Bit Rates:18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002bbef01a826
                    Extra: Last beacon: 17772ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     1A9BDCF22FA3483FDCED0D6
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)
parm:           tfd_q_hang_detect:TFD queues hang detection (default: true (bool)

[mac80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.2.0-35-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <ilw@linux.intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265D-12.ucode
firmware:       iwlwifi-7265-12.ucode
firmware:       iwlwifi-3160-12.ucode
firmware:       iwlwifi-7260-12.ucode
firmware:       iwlwifi-8000-12.ucode
srcversion:     2AFF7BF1EB0D33D3ACDC867
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/4.2.0-35-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-generic SMP mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        78:A2:B1:7E:20:A3:96:76:A3:5E:2C:3E:16:0E:70:1F:99:E0:65:9B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2
tfd_q_hang_detect: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y

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
# PCI device 0x8086:0x10bf (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    2.234706] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-15.ucode failed with error -2
[    2.234731] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-7260-14.ucode failed with error -2
[    2.259270] iwlwifi 0000:02:00.0: loaded firmware version 25.30.13.0 op_mode iwlmvm
[    2.349071] iwlwifi 0000:02:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[    2.350129] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled (repeated 2 times)
[    2.599808] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.044234] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.046282] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled (repeated 4 times)
[    3.283962] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.848890] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[    4.849002] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[    4.849037] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   99.374250] e1000e: eth0 NIC Link is Down
[  106.440211] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[  106.441671] iwlwifi 0000:02:00.0: L1 Disabled - LTR Disabled (repeated 4 times)
[  106.662626] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  108.112889] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[  108.113000] e1000e 0000:00:19.0 eth0: 10/100 speed: disabling TSO
[  108.113034] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############

```

---

### Post by jeremy31 on 2016-04-23
I would let the wifi broadcast the SSID and change it to channel 6 or 9.  Reboot with ethernet cable unplugged, if it doesn't connect, run ```
wireless-info
``` and post the new results

---

### Post by renta2 on 2016-04-24
i try with SSID show, and it work, i'm connected with my wifi.

is there a possibility to do one setting, to make it work with hidden SSID ?

---

### Post by jeremy31 on 2016-04-24
It may be possible but I am not sure why you couldn't connect to it while hidden.  There may have been a typo in the SSID or password, Linux is caps sensitive and even spaces in a name can cause problems

Being hidden is not more secure, the best security is WPA2 with a good password

---

### Post by renta2 on 2016-04-24
ok, but i type my ssid name correctly because (i use underscore as space, and take care of caps)

and my pc connect successfully when ssid is showed (so it the ssid name i typed in my pc is working good)

---

### Post by jeremy31 on 2016-04-24
See if your settings in Network Manager are set to automatically connect to the wifi, if it is then change back to hidden SSID and see if it works

I tested on my 16.04 and it is still connected even after a reboot of the laptop

---

### Post by renta2 on 2016-04-24
i understand how it work,

i solved myself the problem of hidden SSID :

1. first create normal wifi SSID connection (like it was a showed SSID), enter SSID name, protection type and password

2. then clic on wifi icon (near clock) select "Coeenct to hidden wifi"
3. then choose in the list the normal wifi connection (that was create step 1) and it will connect (for me it work)

---

