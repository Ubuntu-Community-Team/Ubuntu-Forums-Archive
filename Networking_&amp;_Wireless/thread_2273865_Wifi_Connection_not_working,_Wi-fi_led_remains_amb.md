---
title: "Wifi Connection not working, Wi-fi led remains amber/orange: Ubuntu 14.04 LST, HP 430"
date: 2015-04-16
forum: Networking &amp; Wireless
---

### Post by Mohit_Jiindal on 2015-04-16
Hello Friends/ Experts.

   I have just installed the Ubuntu 14.04 LST on my HP 430 Notebook/Laptop but even after doing whatever little best I could do , I am uanble to get wi-fi working on my laptop/Notebook. Please help me resolve this issue. I shall be thankful for the kind favor.

Required info is as under:

Pastebin - ```
http://pastebin.ubuntu.com/10832076/
```

Text 
```

########## wireless info START ##########

Report from: 16 Apr 2015 12:03 IST +0530

Booted last: 15 Apr 2015 23:10 IST +0530

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3674]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 003: ID 0c45:6321 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath3k                  13110  0 
ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              545990  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
bluetooth             342263  23 bnep,ath3k,btusb,rfcomm
wmi                    18673  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae16:2dff:fe53:e3fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:78257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67989 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69564169 (69.5 MB)  TX bytes:7430816 (7.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.1.70
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             59.179.243.70
    DNS:             203.94.243.70

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

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath3k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     98A5245588C09E5E41690D0
depends:        bluetooth
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[ath9k]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     BAF225EEB618908380B28DA
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     4809F3842A0542CD6B556D3
depends:        ath
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 2541.892123] ath: phy0: ASPM enabled: 0x43
[ 2542.202411] usb 1-1.4: device firmware changed
[ 2544.554000] ath9k 0000:02:00.0: no hotplug settings from platform

########## wireless info END ############


```

P.S: These results were gathered before I run these commands:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
System is still downloading the necessary stuff as a result of these two commands.


Thank you again.

---

### Post by ajgreeny on 2015-04-16
I'm pretty sure that wifi chip should be fully supported in 14.04, so reboot after doing the update (I presume you have a cable connection for that?) and tell us if all is now working with your wifi.

Detach the cable connection before trying wifi again as it will not work if still connected by cable.

---

### Post by Mohit_Jiindal on 2015-04-16
@ [**[COLOR=#000000]ajgreeny[/COLOR]**]("http://ubuntuforums.org/member.php?u=27747") 	 

  Thank you for your reply.

  Only once when update  installed was interpreted mid way and system was rebooted , did that  wi-fi led changed to white color but immediately in less then two  seconds time, it reverted to its original amber/orange color state ,  with wi-fi not working. Afterwards nothing happened and status quo  remained in place after the update was completed. So in short things  remain same for me even after update.
  Hope to find some solution here soon.

---

### Post by Mohit_Jiindal on 2015-04-16
Ok here are the results of the wireless script after upgrade:
```

########## wireless info START ##########

Report from: 16 Apr 2015 22:46 IST +0530

Booted last: 16 Apr 2015 21:40 IST +0530

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:14:51 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:3674]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 001 Device 003: ID 0c45:6321 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

ath9k                 144602  0 
ath9k_common           13359  1 ath9k
ath9k_hw              438205  2 ath9k_common,ath9k
hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
ath                    23922  3 ath9k_common,ath9k,ath9k_hw
mac80211              546067  1 ath9k
cfg80211              409394  3 ath,ath9k,mac80211
wmi                    18673  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ae16:2dff:fe53:e3fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:121109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164567613 (164.5 MB)  TX bytes:12851342 (12.8 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
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
    Address:         192.168.1.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

wlan0     14 channels in total; available frequencies :
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

##### iwlist scan #######################

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     274594FBD61F5DF88102A4C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     93644B269B570BC55CF5154
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     65C14EF588BF1A68181643C
depends:        ath
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.13.0-49-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     29A87AE7782ED3657631C32
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     176113E009F723E69BE9BAB
depends:        
intree:         Y
vermagic:       3.13.0-49-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        84:C0:9E:2E:78:FF:91:BA:42:96:F5:F5:42:5F:BD:BB:4A:B0:5A:BE
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
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.205636] ath: phy0: ASPM enabled: 0x43
[   15.205638] ath: EEPROM regdomain: 0x60
[   15.205639] ath: EEPROM indicates we should expect a direct regpair map
[   15.205640] ath: Country alpha2 being used: 00
[   15.205641] ath: Regpair used: 0x60
[   22.367548] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############


```

---

### Post by rktompsett on 2015-04-16
Wifi works with 12.04 LTS, but is not detected on 14.04.2 LTS, Asus Laptop

---

### Post by Mohit_Jiindal on 2015-04-16
> **rktompsett said:**
> Wifi works with 12.04 LTS, but is not detected on 14.04.2 LTS, Asus Laptop

So do you intend to say that wi-fi won't work with 14.04.2 or 14.10 on my Hp 430 laptop?

---

### Post by rktompsett on 2015-04-16
14.04.2 appears to lack a driver. Install 12.04 first then upgrade to 14.04.2 on line. Do Not install 14.04.2 with a disk.

---

### Post by Mohit_Jiindal on 2015-04-16
@ [ 						 							 						 					]("http://ubuntuforums.org/member.php?u=564782") 				 				 					 						 	[**[COLOR=#000000]rktompsett[/COLOR]**]("http://ubuntuforums.org/member.php?u=564782")

   Well this is really strange but I am certainly gonna do as suggested by you and later report my findings here. Thanks for your help bro ;)

---

### Post by wildmanne39 on 2015-04-16
This is the kernel driver it is installed by default:
```
Kernel driver in use: ath9k
```
@ rktompsett
>  14.04.2 appears to lack a driver. Install 12.04 first then upgrade to 14.04.2 on line. Do Not install 14.04.2 with a disk. Can you please provide a link to your research that says his device does not have the driver installed in 14.0 4?

This device is not the best in linux but the driver is installed, it is soft blocked and hard blocked so it may not be easy to get working.
Try:
```
echo "blacklist hp-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then reboot and there is a hard block that usually means the switch is off so try to turn it on with the switch or it may be a key combination like fn+f5.
Then check for the soft and hard blocks with:
```
rfkill list all
```
Thanks

---

### Post by Mohit_Jiindal on 2015-04-17
> **Wild Man said:**
> 

Hello

Today morning after reading some more articles on the web, I found that the problem here was that my wi-fi was disabled by default in the BIOS which when tweaked gave the desired results. Thanks Wild Man brother and rktompsett for your help. I am really appreciative of it. Now that problem has been resolved, I am of the opinion that this thread can be marked as solved. Thank you again everyone :KS

---

