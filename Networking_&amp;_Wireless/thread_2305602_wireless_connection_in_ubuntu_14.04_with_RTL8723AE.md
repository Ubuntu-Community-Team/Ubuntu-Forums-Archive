---
title: "wireless connection in ubuntu 14.04 with RTL8723AE not working"
date: 2015-12-07
forum: Networking &amp; Wireless
---

### Post by ulises2 on 2015-12-07
[ATTACH]266021[/ATTACH]



Sorry if this question has already been solved before and for my bad english, the wireless network appears disconnected. So far there were no problems, today the computer crashed and turns off abruptly. When reboot was done, it couldn't make any connection. I attached the script output for troubleshooting.  Thank you for your time, 
if this message lacks some necessary information, let me know


```
########## wireless info START ##########
Report from: 07 Dec 2015 18:24 CET +0100

Booted last: 07 Dec 2015 18:16 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.18.3-031803-generic #201501161810 SMP Fri Jan 16 18:12:22 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory
Could not be determined.

##### lspci #############################

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter [10ec:8723]
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:0726]
    Kernel driver in use: rtl8723ae

03:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 12)
    Subsystem: CLEVO/KAPOK Computer Device [1558:5455]

##### lsusb #############################

Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0718:0627 Imation Corp. 
Bus 001 Device 003: ID 04f2:b43b Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 0bda:8723 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723ae              89213  0 
btcoexist              51822  1 rtl8723ae
rtl8723_common         23662  1 rtl8723ae
rtl_pci                27417  1 rtl8723ae
rtlwifi                74744  2 rtl_pci,rtl8723ae
ath5k                 152410  0 
ath                    29397  1 ath5k
mac80211              697212  3 ath5k,rtl_pci,rtlwifi
cfg80211              520257  4 ath,ath5k,mac80211,rtlwifi
wmi                    19379  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### nm-tool ###########################

NetworkManager Tool

State: disconnected

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723ae
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

[[/etc/NetworkManager/system-connections/Wifi_Movil]] (600 root)
[connection] id=Wifi_Movil | type=802-11-wireless
[802-11-wireless] ssid=Wifi_Movil | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-VD-[LG] webOS TV]] (600 root)

[[/etc/NetworkManager/system-connections/MOVISTAR_CB7D]] (600 root)
[connection] id=MOVISTAR_CB7D | type=802-11-wireless
[802-11-wireless] ssid=MOVISTAR_CB7D | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/uib_(key=password2014)]] (600 root)
[connection] id=uib_(key=password2014) | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=uib_(key=password2014) | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WLAN_E6]] (600 root)
[connection] id=WLAN_E6 | type=802-11-wireless
[802-11-wireless] ssid=WLAN_E6 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ZAAPA]] (600 root)
[connection] id=ZAAPA | type=802-11-wireless
[802-11-wireless] ssid=ZAAPA | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/uib1x]] (600 root)
[ipv6] method=auto
[connection] id=uib1x | type=802-11-wireless
[802-11-wireless] ssid=uib1x | mac-address=<MAC 'wlan0' [IF]>
[802-1x] ca-cert=/home/ulises/Descargas/uib_ca.pem
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Cowalski]] (600 root)
[connection] id=Cowalski | type=802-11-wireless
[802-11-wireless] ssid=Cowalski | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/JAZZTEL-7NP6RE]] (600 root)
[connection] id=JAZZTEL-7NP6RE | type=802-11-wireless
[802-11-wireless] ssid=JAZZTEL-7NP6RE | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DIRECT-0B-[LG] webOS TV]] (600 root)

[[/etc/NetworkManager/system-connections/eduroam]] (600 root)
[ipv6] method=auto
[connection] id=eduroam | type=802-11-wireless
[802-11-wireless] ssid=eduroam | mac-address=<MAC 'wlan0' [IF]>
[802-1x] ca-cert=/home/ulises/Descargas/uib_ca.pem
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/MOVISTAR_A52A]] (600 root)
[connection] id=MOVISTAR_A52A | type=802-11-wireless
[802-11-wireless] ssid=MOVISTAR_A52A | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/pacientes]] (600 root)
[connection] id=pacientes | type=802-11-wireless
[802-11-wireless] ssid=pacientes | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Michel]] (600 root)
[connection] id=Michel | type=802-11-wireless
[802-11-wireless] ssid=Michel | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/LG-D855_2223]] (600 root)
[connection] id=LG-D855_2223 | type=802-11-wireless
[802-11-wireless] ssid=LG-D855_2223 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[rtl8723ae]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723ae/rtl8723ae.ko
firmware:       rtlwifi/rtl8723efw.bin
description:    Realtek 8723E 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     1B4E8962E5096837ACDD0E3
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     584D147C0DFDC3466E73BFD
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     6AEB0158CC8A2AAB1BFB4FD
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[ath5k]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     177DB3858D433799916EC44
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.18.3-031803-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0D7DE85EF15890F115735E2
depends:        cfg80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.18.3-031803-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F2E189013C3BA380B28AA09
depends:        cfg80211
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.18.3-031803-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.3-031803-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        29:DB:FD:FC:5A:CC:82:3C:C5:2C:39:4C:C1:C7:4C:01:C3:BE:BF:78
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723ae]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
swenc: N
swlps: N

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: N

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
lp
rtc
ath5k

##### modprobe options ##################

[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=1

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

[/etc/modprobe.d/r8168-dkms.conf]
blacklist r8169

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8723 (rtl8723ae)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   15.944803] rtl8723ae: Using firmware rtlwifi/rtl8723fw_B.bin
[   16.046456] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.046675] rtlwifi: rtlwifi: wireless switch is on
[   17.064259] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b43b)
[   23.911320] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
 ########## wireless info END ############
```

---

### Post by praseodym on 2015-12-07
Please run:
```

sudo apt-get remove --purge resolvconf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
sudo service network-manager restart
```
Does wireless work? If yes, change the LAN driver (if necessary)

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.040.00
sudo dkms build -m r8168-dkms -v 8.040.00
sudo dkms install -m r8168-dkms -v 8.040.00
sudo depmod -a
sudo update-initramfs -u
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Edit: Blacklist the wrongly loaded ath5k:

```
echo "blacklist ath5k" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot.

Edit 2: Take ath5k from the whitelist:

```
gksudo gedit /etc/modules
```
Remove "ath5k", save, close and reboot

---

### Post by ulises2 on 2015-12-07
thanks for answering !! I tried to use the code that you propose, but still doesn't work, every time I start the computer comes a warning: the connection has been closed,

I deleted the entry etc / modules ath5k

PD:  the wired connection don't work either, so i can't download any file (like the drivers or even reinstall) (but i can download in another computer and use them with an usb)

i don't found the update-initramfs order.

---

### Post by praseodym on 2015-12-07
Deactivate IPv6 in the network-manager settings, encryption in your router to WPA2-AES (CCMP) and a fixed channel

---

### Post by ulises2 on 2015-12-07
I'm not entirely sure that I understand, I've disabled ipv6, and the security that has my router is WPA2, how to establish the connection channel?
Sorry for my ignorance in addition to all so sorry,

---

