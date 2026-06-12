---
title: "how to install new drivers for a WiFi adapter"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by Hodor on 2015-12-02
Not sure of the correct forum for this post, but here goes ...
- I'm considering trying a new driver for a WiFi adapter.  
- The driver(s) are here (at [COLOR=#333333][FONT=Arial]Intel® Wireless 7260[/FONT][/COLOR]): [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi)
- I have quite a few questions:
1. Is this a good plan?
2. I would like to try new drivers for 14.04.3 (kernel 3.16.0-53-generic) and 15.10 (kernel 4.2.0-18-generic ) - what would be the correct firmware to download (e.g. for 14.04.3: iwlwifi-7260-ucode-22.24.8.0.tgz)?
3. At the previous step, is the firmware being installed onto the motherboard/drive or the network adapter?  (Important for me as the adapter now works fine in windows, so I don't want to mangle it for both os's trying to fix it for one.)
4. After installing the firmware, the instructions at the above page confidently pronounce '[COLOR=#333333][FONT=Arial]You can now load the driver.'  Is this a procedure along the lines of chili555's tutorial ([/FONT][/COLOR]http://ubuntuforums.org/showthread.php?t=2242147&page=2, thanks to Hadaka for this link[COLOR=#333333][FONT=Arial]) or something else?
[/FONT][/COLOR]5. Is there a simple way I can tell whether my current driver is up to date, or whether it might be updated by the above (or some such)? at /lib/firmware/ I currently have iwlwifi-7260-10.ucode in 14.04, iwlwifi-7260-13.ucode in 15.10
Edit: 6. How do I get the pci.id. for this adapter?  I'll attach the contents of the script below (for 14.04, wireless off, 20 m of cat 6 running to the main router across the floor, mind your step:).


Thanks very much.

Some background:
- with some excellent help from praseodym and Hadaka ([http://ubuntuforums.org/showthread.php?t=2303564&page=2](http://ubuntuforums.org/showthread.php?t=2303564&page=2)) I thought I had this adapter running well but it has crashed again to 1 Mb/S (power off doesn't help).
- I have an alternative usb adapter that now works well (thanks again) but the intel card works better on windows and frees a usb port, so if I can get it to work on Ubuntu I can just use the intel card (much better option for me).
- I'm hoping to stick with 14.04, but I'm trying 15.10 in parallel to see if I get a better outcome.

```



########## wireless info START ##########


Report from: 03 Dec 2015 12:53 AEDT +1100


Booted last: 03 Dec 2015 01:40 AEDT +1100


Script from: 27 Sep 2015 00:34 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-53-generic #72~14.04.1-Ubuntu SMP Fri Nov 6 18:17:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, usbcore.autosuspend=-1


##### desktop ###########################


Ubuntu


##### lspci #############################


00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (2) I218-V [8086:15a1]
    Subsystem: ASRock Incorporation Device [1849:15a1]
    Kernel driver in use: e1000e


04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
    Subsystem: ASRock Incorporation Motherboard (one of many) [1849:8168]
    Kernel driver in use: r8169


07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 002: ID 8087:8001 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 8087:8009 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 174c:2074 ASMedia Technology Inc. 
Bus 003 Device 005: ID 0b38:0010 Gear Head 107-Key Keyboard
Bus 003 Device 004: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 002: ID 03f0:2b17 Hewlett-Packard LaserJet 1020
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwlmvm                217725  0 
mxm_wmi                13021  0 
mac80211              652777  1 iwlmvm
iwlwifi               179412  1 iwlmvm
cfg80211              498458  3 iwlwifi,mac80211,iwlmvm
snd_soc_rt5640         93124  0 
snd_soc_rl6231         13037  1 snd_soc_rt5640
snd_soc_core          200204  1 snd_soc_rt5640
snd_pcm               104112  7 snd_soc_rt5640,snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller,snd_pcm_dmaengine
wmi                    19193  1 mxm_wmi


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


eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth1' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29769563 (29.7 MB)  TX bytes:1144387 (1.1 MB)
          Interrupt:20 Memory:efc00000-efc20000 


virbr0    Link encap:Ethernet  HWaddr <MAC 'virbr0' [IF]>  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


eth0      no wireless extensions.


eth1      no wireless extensions.


virbr0    no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.122.0   0.0.0.0         255.255.255.0   U     0      0        0 virbr0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      1092     1  0 12:40 ?        00:00:00 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             unavailable
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
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


- Device: eth1  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=<MAC 'eth1' [IF]>,<MAC 'eth0' [IF]>,


[ifupdown]
managed=false


##### NetworkManager profiles ###########


Sorry, try again.
[[/etc/NetworkManager/system-connections/SignalFault]] (600 root)
[connection] id=SignalFault | type=802-11-wireless
[802-11-wireless] ssid=SignalFault | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/sound]] (600 root)
[connection] id=sound | type=802-11-wireless
[802-11-wireless] ssid=sound | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/SignalFault 1]] (600 root)
[connection] id=SignalFault 1 | type=802-11-wireless
[802-11-wireless] ssid=SignalFault | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Australia/Canberra (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


eth0      no frequency information.


eth1      no frequency information.


virbr0    no frequency information.


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


wlan0     Interface doesn't support scanning : Network is down


eth1      Interface doesn't support scanning.


virbr0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[iwlmvm]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     C3CE81DD94553577D83E97E
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)


[mac80211]
filename:       /lib/modules/3.16.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     477882071593B10E01388C8
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[iwlwifi]
filename:       /lib/modules/3.16.0-53-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
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
filename:       /lib/modules/3.16.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     046346857FD53951C911443
depends:        
intree:         Y
vermagic:       3.16.0-53-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        EA:BD:AC:AF:3A:4B:5E:C1:64:B4:EE:22:6A:09:F9:D1:B2:BC:EB:6D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


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
options iwlwifi wd_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1


[/etc/modprobe.d/r8712u.conf]
options r8712u low_power=1 power_mgnt=0 ht_enable=0


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a1 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x8086:0x08b1 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (r8712u)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[    2.438272] iwlwifi 0000:07:00.0: irq 69 for MSI/MSI-X
[    2.451468] iwlwifi 0000:07:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    2.479181] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.479236] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled (repeated 2 times)
[    2.687738] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.933262] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    2.979305] r8169 0000:04:00.0 eth0: link down
[    2.979344] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.706056] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
[    5.749905] e1000e: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[    5.749932] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready


########## wireless info END ############



```

---

### Post by praseodym on 2015-12-03
Try
```

sudo rfkill unblock all
rfkill list
iwconfig
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by Hodor on 2015-12-03
Thanks.
For the following I've had the ethernet unplugged, wifi on, usb (realtek) dongle out.
No output from sudo rfkill unblock all


rfkill list yields:
```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
iwconfig yields (anonymise a mac):
```

eth0      no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"myWifi"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 30:85:A9:...  
          Bit Rate=18 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


eth1      no wireless extensions.


virbr0    no wireless extensions.


lo        no wireless extensions.

```
cat /var/lib/NetworkManager/NetworkManager.state yields
```

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

---

### Post by chili555 on 2015-12-03
> - The driver(s) are here (at Intel® Wireless 7260): [https://wireless.wiki.kernel.org/en/...rivers/iwlwifi](https://wireless.wiki.kernel.org/en/...rivers/iwlwifi)
- I have quite a few questions:
1. Is this a good plan?That is only the firmware. The driver is built in to the kernel. > 2. I would like to try new drivers for 14.04.3 (kernel 3.16.0-53-generic) and 15.10 (kernel 4.2.0-18-generic ) - what would be the correct firmware to download (e.g. for 14.04.3: iwlwifi-7260-ucode-22.24.[COLOR="#FF0000"]8[/COLOR].0.tgz)?The correct firmware is the firmware your driver version calls up. Check:```
modinfo iwlwifi | grep 7260
```For the driver version in 15.10, it is:```
firmware:       iwlwifi-7260-[COLOR="#FF0000"]12[/COLOR].ucode
```You can download and install the -8 firmware or any other, but the driver calls the version it is written for.> 3. At the previous step, is the firmware being installed onto the motherboard/drive or the network adapter? (Important for me as the adapter now works fine in windows, so I don't want to mangle it for both os's trying to fix it for one.)No. It is called up by the driver alone. The driver *iwlwifi* covers many different devices. I believe the firmware tells the driver about the card specifics; that is, how is your 7260 different from my 6200.> 4. After installing the firmware, the instructions at the above page confidently pronounce 'You can now load the driver.' Is this a procedure along the lines of chili555's tutorial ([http://ubuntuforums.org/showthread.php?t=2242147&page=2](http://ubuntuforums.org/showthread.php?t=2242147&page=2), thanks to Hadaka for this link) or something else?My post you referenced is a whole other issue. 'You can now load the driver' simply means to unload the driver holding the old firmware and reload it so it sees and uses the new:```
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
```> 5. Is there a simple way I can tell whether my current driver is up to date, or whether it might be updated by the above (or some such)? at /lib/firmware/ I currently have iwlwifi-7260-10.ucode in 14.04, iwlwifi-7260-13.ucode in 15.10There is no doubt that the driver in 15.10 is newer than 14.04. After a reboot, what does the message log report?```
dmesg | grep iwl
```In your script, it says:> iwlwifi 0000:07:00.0: loaded firmware version 25.228.[COLOR="#FF0000"]9[/COLOR].0 op_mode iwlmvmObviously, it does no good to install the -8 firmware, your driver is already using -9!>  6. How do I get the pci.id. for this adapter? From the terminal:```
lspci -nnk | grep 0280 -A2
```

More in my next post.

---

### Post by chili555 on 2015-12-03
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
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

If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot and tell us if there is any improvement.

---

### Post by Hodor on 2015-12-05
Thanks chilli555,
After going through all of the above, there is an improvement on 14.04, I haven't gone through 15.10 yet (I'll update when I do).
outputt of  lspci -nnk | grep 0280 -A2
```

07:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev bb)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:4070]
    Kernel driver in use: iwlwifi

```
so the pci.id is ? 08b1?

output of dmesg | grep iwl on 14.04:
```

[    2.496249] iwlwifi 0000:07:00.0: enabling device (0000 -> 0002)
[    2.496379] iwlwifi 0000:07:00.0: irq 69 for MSI/MSI-X
[    2.510330] iwlwifi 0000:07:00.0: loaded firmware version 25.228.9.0 op_mode iwlmvm
[    2.529032] iwlwifi 0000:07:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.529086] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.529322] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    2.748292] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    3.084272] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.084509] iwlwifi 0000:07:00.0: L1 Disabled - LTR Enabled
[    3.402106] Modules linked in: ip6table_filter ip6_tables iptable_filter ip_tables ebtable_nat ebtables x_tables pci_stub vboxpci(OE) vboxnetadp(OE) vboxnetflt(OE) vboxdrv(OE) snd_hda_codec_realtek snd_hda_codec_generic snd_hda_codec_hdmi arc4 btusb intel_rapl x86_pkg_temp_thermal intel_powerclamp joydev coretemp hid_generic kvm_intel kvm mxm_wmi r8712u(C) crct10dif_pclmul usbhid iwlmvm crc32_pclmul mac80211 ghash_clmulni_intel aesni_intel aes_x86_64 lrw dm_multipath gf128mul snd_soc_rt5640 scsi_dh snd_hda_intel glue_helper iwlwifi snd_hda_controller snd_soc_rl6231 ablk_helper cryptd snd_soc_core snd_hda_codec snd_compress snd_hwdep snd_pcm_dmaengine snd_pcm serio_raw cfg80211 i915 snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq snd_seq_device drm_kms_helper snd_timer bnep dw_dmac drm rfcomm i2c_hid wmi dw_dmac_core bluetooth hid mei_me snd snd_soc_sst_acpi mei video i2c_designware_platform 8250_dw soundcore i2c_designware_core i2c_algo_bit 6lowpan_iphc spi_pxa2xx_platform shpchp mac_hid acpi_pad parport_pc ppdev lp parport binfmt_misc nls_iso8859_1 e1000e psmouse ahci ptp r8169 pps_core mii libahci sdhci_acpi sdhci

```

As far as I can tell, performance of the wifi adapter is now satisfactory on 14.04!  Thanks again.

---

### Post by chili555 on 2015-12-05
> so the pci.id is ? 08b1?The pci.id is 8086:08b1. The driver *iwlwifi*, like a few others in Linux, also looks at the subsystem. The driver needs to see the pci.id exactly, as well as the subsystem, in your case 4070.

We check *modinfo*:```
modinfo iwlwifi | grep 08B1
```One of the lines we see is:```
pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]08B1[/COLOR]sv*sd0000[COLOR="#FF0000"]4070[/COLOR]bc*sc*i*
```The post you linked is an apparently successful attempt to amend the driver to accept a previously unknown subsystem. Pretty arcane stuff, but I quite enjoy tinkering around in the warp core!

---

### Post by Hodor on 2015-12-05
The driver update on 15.10 seems to have done the trick as well, though I haven't tested it as much.  Also I wasn't able to start Network Manager - I tried a work around that's suppose to work for 15.04 without success.  My plan is to continue testing this system in parallel.  Thanks again chili555.

---

