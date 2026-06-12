---
title: "wifi problem: acer aspire 5800t with intel wifi link 5100 no work on ub.14.10"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by asa4 on 2015-04-20
hello on my acer 5810 t the wifi is off . no connection 

i'm a new on ubuntu so i don't know if is correct , i read a lot of post without good result 

in terminal i do :


uname -r  ( to know the version i take a look to some post)   3.16.0-34-generic what i can do to solve the wifi problem?

---

### Post by slickymaster on 2015-04-20
Hi asa4, welcome to the forums.

Please have a read at the [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") sticky and then post, here in the thread, the results of the wireless script in [CODE tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168") (or attach the .tar.gz-file).

---

### Post by asa4 on 2015-04-20
> **slickymaster said:**
> Hi asa4, welcome to the forums.

Please have a read at the [Before posting in Networking & Wireless]("http://ubuntuforums.org/showthread.php?t=370108") sticky and then post, here in the thread, the results of the wireless script in [CODE tags]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168") (or attach the .tar.gz-file).

ok excuse me ... but is my first time with ubuntu ... i hope to solve the problem because i like it ... 
```


########## wireless info START ##########

Report from: 20 Apr 2015 18:39 CEST +0200

Booted last: 20 Apr 2015 17:12 CEST +0200

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:51 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8131 Gigabit Ethernet [1969:1063] (rev c0)
    Subsystem: Acer Incorporated [ALI] Device [1025:022b]
    Kernel driver in use: atl1c

02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1301]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 002 Device 002: ID 04f2:b160 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 059f:0c41 LaCie, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6144840  0 
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
iwldvm                219044  0 
mac80211              559049  1 iwldvm
iwlwifi               157209  1 iwldvm
cfg80211              418839  4 wl,iwlwifi,mac80211,iwldvm
wmi                    18689  1 acer_wmi
video                  19475  2 i915,acer_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

auto wlan0
iface wlan0 inet manual

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:fe9a:bba4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:483984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:285604 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:671236579 (671.2 MB)  TX bytes:63488541 (63.4 MB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:100.65.83.77  P-t-P:81.174.0.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:482546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282162 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:660522390 (660.5 MB)  TX bytes:56967068 (56.9 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

ppp0      no wireless extensions.

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0
81.174.0.21     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

##### resolv.conf #######################

nameserver 192.168.1.1
nameserver 88.149.128.22
nameserver 88.149.128.12

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

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

Region: Europe/Rome (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

ppp0      no frequency information.

lo        no frequency information.

eth0      no frequency information.

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

ppp0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-34-generic SMP mod_unload modversions 686 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[iwldvm]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     716426034C9E4259C23DEDA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        75:21:B7:4E:6D:2D:7C:F5:30:AC:BC:55:D6:62:AF:90:B2:C3:EE:D4
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5410C94462FA26A0A3F256C
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        75:21:B7:4E:6D:2D:7C:F5:30:AC:BC:55:D6:62:AF:90:B2:C3:EE:D4
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     93D664267873827B22C4309
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        75:21:B7:4E:6D:2D:7C:F5:30:AC:BC:55:D6:62:AF:90:B2:C3:EE:D4
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        75:21:B7:4E:6D:2D:7C:F5:30:AC:BC:55:D6:62:AF:90:B2:C3:EE:D4
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
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
iwlwifi

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1969:0x1063 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4232 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 4847.930313] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[ 4852.463247] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[ 4859.518328] iwlwifi 0000:02:00.0: RF_KILL bit toggled to disable radio.
[ 5188.448084] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.

########## wireless info END ############


 
```

i write also the version:

 ```

lspci -vvnn | grep Network
02:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]


 
```

---

### Post by wildmanne39 on 2015-04-20
That file should have a lot more information in it, we need to see it all.
Thanks

---

### Post by asa4 on 2015-04-20
> **Wild Man said:**
> That file should have a lot more information in it, we need to see it all.
Thanks

ok i up date all the info 

the first time i have no copy all

---

### Post by asa4 on 2015-04-21
some one know how i can do to solve this problem , i no won't to to install windows again  :(

---

### Post by wildmanne39 on 2015-04-21
Sorry I did not know you edited your post, if you had posted a new file I would have been notified of a new post.
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
Why is all this in the interface file? > 
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual

auto wlan0
iface wlan0 inet manual
This should be the only thing in that file:
```
auto lo
iface lo inet loopback

```Are you using network manager? if so remove everything but the two lines I just posted.
Reboot

---

### Post by asa4 on 2015-04-21
thanks Wild Man for your answer:

i don't know if could be this the reason of your answer:
i have a wifi router , but the adsl have a rj11 connector, for my house i have a radio connection that use the radio wave to allow a connection to some poeple that live in farm where the normal adsl no arrive.
the modem of this service have a rj45 connector so to connect it with the wifi ruoter i use the lan port , if i need to connect using wifi , i connect the pc with the wifi line and then with the radio modem of the provider.
looking in the guide to connect to a pppoe service i have to use the " sudo pppoeconf" i think this is the best thing i have seen in ubuntu respect Windows. in Windows i have to connect every time , in ubuntu if i use the lan and i take out the connection and then restart it the internet connection is automatic. fantastic

i will lunch the code and the script and i will you know Tomorrow because i have to reinstall again ubuntu

---

