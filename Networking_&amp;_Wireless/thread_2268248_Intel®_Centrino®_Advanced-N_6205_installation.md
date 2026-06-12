---
title: "Intel® Centrino® Advanced-N 6205 installation"
date: 2015-03-07
forum: Networking &amp; Wireless
---

### Post by Pierre_Causse on 2015-03-07
Hi everyone !

I'm new on ubuntu and i'm having a really hard time since several days installing my wifi card.
I have barebone desktop computer, and installed myself an Intel® Centrino® Advanced-N 6205. Problem is that i detect no network and then can't connect to my wifi, stuck with RJ45.

I know that this card should work as I found this page [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi) explaining that the card is supported and how to make it work but the fact that i'm new with this sytem and not english fluent gimme hard time on how make everthing works.

How should i install the card correctly ?
I copied the firmware to /lib/firware, the one corresponding to my kernel version (i guess), but now i should install driver right ? Firware and driver arn't the same thing or am i talking nonsens ? But can't find where to download the driver on the link i post above or even how to install it. 

I'm pretty lost right now : )

Would someone know how i could manage to do that ?

Thanks in advance,
Pierre.

---

### Post by jeremy31 on 2015-03-07
Read this post [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and run the wireless script and post the output.  Unless something strange is going on, that card should work without problems

---

### Post by Pierre_Causse on 2015-03-07
Thanks for so quick answer jeremy !

Here is the output :


```
########## wireless info START ##########

Report from: 07 Mar 2015 13:24 CET +0100

Booted last: 07 Mar 2015 13:23 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #77-Ubuntu SMP Mon Mar 2 18:23:39 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] [8086:0082] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1301]
    Kernel driver in use: iwlwifi

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:4025]
    Kernel driver in use: r8169

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device [1297:4025]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0461:4dbf Primax Electronics, Ltd 
Bus 003 Device 003: ID 046d:c01b Logitech, Inc. MX310 Optical Mouse
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                232285  0 
mac80211              630669  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::82ee:73ff:fe9f:26a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:604 errors:0 dropped:0 overruns:0 frame:0
          TX packets:837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:202502 (202.5 KB)  TX bytes:109548 (109.5 KB)

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             212.76.224.172
    DNS:             89.2.0.1
    DNS:             89.2.0.2

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

eth1      no frequency information.

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

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[iwldvm]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     496F157C6045EF8314B48BC
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B8DF1ECC076C2FCEAC70533
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     B81BA270CF5925E724426BD
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        C2:95:1C:E2:B9:DB:CF:2B:98:19:7D:B0:8C:AE:A2:D6:8B:7A:CB:E8
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

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
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x0082 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[    2.758649] iwlwifi 0000:01:00.0: irq 53 for MSI/MSI-X
[    2.804653] iwlwifi 0000:01:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    2.817766] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.817768] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.817769] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.817771] iwlwifi 0000:01:00.0: Detected Intel(R) Centrino(R) Advanced-N 6205 AGN, REV=0xB0
[    2.817817] iwlwifi 0000:01:00.0: L1 Disabled - LTR Disabled
[    2.835800] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    2.903666] iwlwifi 0000:01:00.0: L1 Disabled - LTR Disabled
[    2.910748] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[    3.175644] iwlwifi 0000:01:00.0: L1 Disabled - LTR Disabled
[    3.182375] iwlwifi 0000:01:00.0: Radio type=0x1-0x2-0x0
[    3.262349] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[    3.353884] r8169 0000:03:00.0 eth1: link down
[    3.353927] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)

########## wireless info END ############

```

---

### Post by jeremy31 on 2015-03-07
This problem might be because you don't have the country code set, so enter this in terminal```
sudo iw reg set FR
``` Then ```
gksudo gedit /etc/default/crda
``` and find ```
REGDOMAIN=
``` and change it to ```
REGDOMAIN=FR
``` Save, exit, and reboot and see if ```
iwlist scan
``` shows any wireless access points

---

### Post by Pierre_Causse on 2015-03-07
after reboot, the scan can't perform : /

```

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     No scan results

```

---

### Post by jeremy31 on 2015-03-07
How far away is the wireless router?  Are the antennas securely attached to the wireless card?

---

### Post by Pierre_Causse on 2015-03-08
I feel, so, stupid. 

My wifi card is a mini one. When i ordered it, I didn't exactly how it was working compare to a standard one, and didn't even think about antennas. Now i feel idiot not to see the two little connectors on the mini wifi card.
Classic rookie mistake. Is the device plugded ? No.

Anyway that's weird that the antennas weren't sell with the mini card i bought. Is it possible to buy antennas for mini wifi card separetly ?

Thanks jeremy for your help, I could have spend a lot of time thinking it was a software problem.

---

### Post by jeremy31 on 2015-03-08
At least they make the antennas for the mini cards [http://www.amazon.com/Wi-fi-Antenna-RP-SMA-Antennas-Cables/dp/B00A4I3AGE/ref=pd_cp_pc_2](http://www.amazon.com/Wi-fi-Antenna-RP-SMA-Antennas-Cables/dp/B00A4I3AGE/ref=pd_cp_pc_2)

You aren't the first and you won't be the last to forget about the antennas

---

### Post by Pierre_Causse on 2015-03-10
Last question, is it sure that the antennas you linked on amazon are compatible with the wifi card i already own ?

---

### Post by jeremy31 on 2015-03-10
If your card looks like this, it should work
[Img]http://ecx.images-amazon.com/images/I/51NBfu1RiLL._SL500_SR140,140_.jpg[/img]
or post a link to your card

---

