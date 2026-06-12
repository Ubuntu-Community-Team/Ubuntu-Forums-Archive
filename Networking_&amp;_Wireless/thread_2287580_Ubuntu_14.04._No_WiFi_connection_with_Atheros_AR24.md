---
title: "Ubuntu 14.04. No WiFi connection with Atheros AR242x / AR542x on Compaq Presario CQ60"
date: 2015-07-20
forum: Networking &amp; Wireless
---

### Post by ken-norris on 2015-07-20
I followed steps outlined in [http://ubuntuforums.org/showthread.php?t=2212616](http://ubuntuforums.org/showthread.php?t=2212616) by and for StealthMode but came to the same result of no resolution. That thread is marked as [SOLVED] but really wasn't, unless you count giving up as [SOLVED].

Has any advance or further thoughts gone into this?

Any comments very welcome including those that say the  Atheros AR242x / AR542x matters are no resolvable in Ubuntu.

Script output:

```

########## wireless info START ##########

Report from: 20 Jul 2015 14:36 CST -0600

Booted last: 20 Jul 2015 13:32 CST -0600

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169

02:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC [103c:137a]
    Kernel driver in use: ath5k

##### lsusb #############################

Bus 002 Device 002: ID 03f0:b107 Hewlett-Packard v255w/c310w Flash Drive
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 064e:a102 Suyin Corp. Acer/Lenovo Webcam [CN0316]
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath5k                 149944  0 
ath                    29006  1 ath5k
mac80211              652777  1 ath5k
hp_wmi                 14109  0 
cfg80211              494362  3 ath,ath5k,mac80211
sparse_keymap          13948  1 hp_wmi
wmi                    19193  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth2      Link encap:Ethernet  HWaddr <MAC 'eth2' [IF]>  
          inet addr:192.168.10.147  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth2' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10641 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7805101 (7.8 MB)  TX bytes:1316424 (1.3 MB)

wlan1     Link encap:Ethernet  HWaddr <MAC 'wlan1' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth2      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.20   0.0.0.0         UG    0      0        0 eth2
192.168.10.0    0.0.0.0         255.255.255.0   U     1      0        0 eth2

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       835     1  0 13:32 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan1' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth2  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth2' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.147
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.20

    DNS:             192.168.10.20

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

Region: America/Guatemala (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth2      no frequency information.

lo        no frequency information.

wlan1     11 channels in total; available frequencies :
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

##### iwlist scan #######################

eth2      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     No scan results

##### module infos ######################

[ath5k]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     563E14135660CD2526C6909
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)

[ath]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     165C1DF76AF8C8B6A45DA4F
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath5k]
fastchanswitch: N
nohwcrypt: Y
no_hw_rfkill_switch: Y

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

##### modprobe options ##################

[/etc/modprobe.d/ath5k.conf]
options ath5k no_hw_rfkill_switch=Y nohwcrypt=Y

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x1969:0x2060 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   15.877915] ath5k 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   15.878094] ath5k 0000:02:00.0: registered as 'phy0'
[   16.462731] ath: EEPROM regdomain: 0x64
[   16.462736] ath: EEPROM indicates we should expect a direct regpair map
[   16.462741] ath: Country alpha2 being used: 00
[   16.462742] ath: Regpair used: 0x64
[   16.580685] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   16.596242] systemd-udevd[319]: renamed network interface wlan0 to wlan1
[   24.717236] r8169 0000:01:00.0 eth2: link down
[   24.717272] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[   24.741387] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[  337.141160] r8169 0000:01:00.0 eth2: link up
[  337.141176] IPv6: ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready

########## wireless info END ############

```

---

### Post by ken-norris on 2015-07-21
Wish I knew exactly how but very pleased to say the WiFi is now working.

I hit an apparently random series of "sudo ifconfig wlan1 down" "sudo ifconfig wlan1 up" while turning the console "Enable Networking" on or off and a long press on the always blue-lit keyboard WiFi switch. Have no idea what combination worked but the "iwlist wlan1 scan" finally kicked in with the many sources around here. It is also automatically logged in on reboot.

NB. wlan1 is my wifi adapter.

For those clever enough to work through the entrails of this matter, the latest, working response of the wireless-info script is attached (I hope)

---

