---
title: "Wireless cards seen but not coming up on Ubuntu Server 24.04"
date: 2024-06-01
forum: Networking &amp; Wireless
---

### Post by Kainwolf on 2024-06-01
I cannot get wireless cards to come up on Ubuntu Server 24.04.  This is with both Atheros and Intel.  They appear to work on Kubuntu.

The card seems to be fully detected, but just won't come up.  It doesn't seem to even connect to the wireless router.
Cards seem to work on Kubuntu

I've seen a number of threads that aren't useful (mostly on StackExchange sites), as they are a decade or more old, and reference long-deprecated methods.  I haven't installed [FONT=Courier New]iw[/FONT] or [FONT=Courier New]network-manager[/FONT], as I've seen that they've been deprecated and replaced by ip and netplan(???).  They are also not on my (working) Kubuntu machines (though maybe Kubuntu has its own GUI-based tools instead of [FONT=Courier New]iw[/FONT]?).  If there's something already in the Ubuntu Server 24.04 install, I'd rather use it.

I am trying to use these machines as wireless access points with [FONT=Courier New]hostapd[/FONT] and [FONT=Courier New]isc-dhcp-server[/FONT] but right now, am trying to just connect it to my existing wireless network.

Attached here is the pastebin, along with some additional information that seems to be useful from other threads:
```
########## wireless info START ##########

Report from: 01 Jun 2024 18:22 PDT -0700

Booted last: 01 Jun 2024 00:00 PDT -0700

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 24.04 LTS
Release:	24.04
Codename:	noble

##### kernel ############################

Linux 6.8.0-31-generic #31-Ubuntu SMP PREEMPT_DYNAMIC Sat Apr 20 00:40:06 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /home/kain/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 11)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:861d]
	Kernel driver in use: r8169

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave AW-NE186H [1a3b:1186]
	Kernel driver in use: ath9k

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

ath9k                 253952  0
ath9k_common           49152  1 ath9k
ath9k_hw              671744  2 ath9k_common,ath9k
ath                    40960  3 ath9k_common,ath9k,ath9k_hw
mac80211             1728512  1 ath9k
eeepc_wmi              12288  0
asus_wmi               86016  2 eeepc_wmi,mfd_aaeon
ledtrig_audio          12288  1 asus_wmi
sparse_keymap          12288  1 asus_wmi
cfg80211             1339392  4 ath9k_common,ath9k,ath,mac80211
platform_profile       12288  1 asus_wmi
wmi_bmof               12288  0
libarc4                12288  1 mac80211
video                  73728  2 asus_wmi,i915
wmi                    32768  4 video,asus_wmi,wmi_bmof,mfd_aaeon

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp1s0' [IF1]> brd <MAC address>
    inet 172.24.48.243/23 brd 172.24.49.255 scope global enp1s0
       valid_lft forever preferred_lft forever
    inet6 fe80::<IP6 'enp1s0' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

./wireless-info: line 230: iwconfig: command not found

##### route #############################

default via 172.24.48.250 dev enp1s0 proto static 
172.24.48.0/23 dev enp1s0 proto kernel scope link src 172.24.48.243 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search rukario.net

##### network managers ##################

Installed:

	None found.

Running:

	None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager config #############

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-31-mac-addr-change]
match-device=driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

No NetworkManager profiles found.

##### Netplan config ####################

grep: /etc/netplan/50-cloud-init.yaml: Permission denied
[manually pasted]
# This file is generated from information provided by the datasource.  Changes
# to it will not persist across an instance reboot.  To disable cloud-init's
# network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    ethernets:
        enp1s0:
            dhcp4: no
            addresses: [172.24.48.243/23]
            routes:
            - to: default
              via: 172.24.48.250
            nameservers:
                addresses: [172.24.48.250]
                search: [kainwolf.com]
            optional: true
    version: 2
    renderer: networkd
    wifis:
        wlp2s0:
            dhcp4: true
            optional: true
            access-points:
                "MyNetworkSSID":
                    password: "MyNetworkPassword"

##### iw reg get ########################

'iw' is not installed (package "iw").

##### iwlist channels ###################

'iwlist' is not installed (package "wireless-tools").

##### iwlist scan #######################

'iwlist' is not installed (package "wireless-tools").

##### module infos ######################

[ath9k]
filename:       /lib/modules/6.8.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko.zst
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
depends:        ath9k_hw,mac80211,ath9k_common,ath,cfg80211
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       6.8.0-31-generic SMP preempt mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
parm:           use_msi:Use MSI instead of INTx if possible (int)

[ath9k_common]
filename:       /lib/modules/6.8.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko.zst
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
depends:        ath9k_hw,ath,cfg80211
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       6.8.0-31-generic SMP preempt mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/6.8.0-31-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko.zst
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       6.8.0-31-generic SMP preempt mod_unload modversions 

[ath]
filename:       /lib/modules/6.8.0-31-generic/kernel/drivers/net/wireless/ath/ath.ko.zst
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       6.8.0-31-generic SMP preempt mod_unload modversions 

[mac80211]
filename:       /lib/modules/6.8.0-31-generic/kernel/net/mac80211/mac80211.ko.zst
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       6.8.0-31-generic SMP preempt mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/6.8.0-31-generic/kernel/net/wireless/cfg80211.ko.zst
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       6.8.0-31-generic SMP preempt mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0
use_msi: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mdadm.conf]
options md_mod start_ro=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

### dmesg - my additions ###
[   10.352040] ath9k 0000:02:00.0: enabling device (0000 -> 0002)
[   10.352394] ath: phy0: Disable PLL PowerSave
[   10.359369] ath: phy0: Enable LNA combining
[   10.360598] ath: EEPROM regdomain: 0x6a
[   10.360605] ath: EEPROM indicates we should expect a direct regpair map
[   10.360610] ath: Country alpha2 being used: 00
[   10.360612] ath: Regpair used: 0x6a
[   10.396374] ath9k 0000:02:00.0 wlp2s0: renamed from wlan0
### dmest - my additions end ###

[   12.943800] r8169 0000:01:00.0 enp1s0: Link is Up - 1Gbps/Full - flow control rx/tx

########## wireless info END ############
### additiional info ###
### lshw -C network ###
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 11
       serial: 9c:5c:8e:02:35:89
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100
bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.8.0-31-generic duplex=ful
l firmware=rtl8168g-2_0.0.1 02/06/13 ip=172.24.48.243 latency=0 link=yes multicast=yes port=twisted pair spee
d=1Gbit/s
       resources: irq:16 ioport:e000(size=256) memory:91304000-91304fff memory:91300000-91303fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 01
       serial: 74:c6:3b:43:03:51
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=6.8.0-31-generic firmware=N/A latency=0 link=n
o multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:91200000-9127ffff memory:91280000-9128ffff

### wpa_supplicant: ###
kain@raikou:~$ sudo wpa_cli scan
Selected interface 'wlp2s0'
OK
```
Am I missing anything? Thanks in advance.

---

### Post by currentshaft on 2024-06-04
I would install and use rfkill to check the status and possibly enable the wireless adapter(s).

---

