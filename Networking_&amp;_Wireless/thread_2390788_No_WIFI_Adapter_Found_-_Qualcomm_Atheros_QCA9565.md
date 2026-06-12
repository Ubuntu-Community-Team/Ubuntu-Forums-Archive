---
title: "No WIFI Adapter Found - Qualcomm Atheros QCA9565"
date: 2018-05-02
forum: Networking &amp; Wireless
---

### Post by leocatto5 on 2018-05-02
[COLOR=#000000][INDENT]Hello everyone, 

I've just started in the "Ubuntu World" and I did the dual boot of the newest version 18.04 aside to my Windows 10. 

The installation was successful but apparently I'm not able to connect via wireless. I can't see the "[COLOR=#417394]Wifi[/COLOR]" icon on the top corner and when I go to Settings --> [COLOR=#417394]Wifi[/COLOR], 

the message "No [COLOR=#417394]Wifi[/COLOR] adapter found" is displayed. 

I've been looking for solutions but wasn't very successful. 

When I type in the terminal : lspci-nnk | grep -iA3 net, it shows the following version: Qualcomm Atheros QCA9565/AR9565 Wireless Network Adapter.

Thank you, 

Leonardo.[/INDENT]
[/COLOR]
[INDENT][Last edited by ]("https://ubuntuforums.org/posthistory.php?p=13762062")[/INDENT]

---

### Post by rsteinmetz70112 on 2018-05-02
It looks like the proper driver for that chip is not being loaded.

I'd suggest you try to boot using a live DVD or USB drive and see if the wifi adapter is found.

---

### Post by leocatto5 on 2018-05-02
I am currently dual booting alongside to my Windows 10. When I use the USB Drive to "Try Ubuntu without installing" I face the same error :(

---

### Post by rsteinmetz70112 on 2018-05-02
The Ubuntu is not correctly identifying your wifi adapter 

There are a number of similar questions for older versions of Ubuntu take a look at some of them like the one below.
[https://askubuntu.com/questions/773463/qualcomm-atheros-qca9565-not-detected-by-ubuntu-16-04](https://askubuntu.com/questions/773463/qualcomm-atheros-qca9565-not-detected-by-ubuntu-16-04)

---

### Post by jeremy31 on 2018-05-02
See the wireless script link in my signature and post results

---

### Post by leocatto5 on 2018-05-03
Thanks for the answer guys ! I'm new in the forum, so if I'm breaking any posting rules, sorry in advance ! Here follows the results for the Wireless-Info:


```
########## wireless info START ##########

Report from: 03 May 2018 20:07 CEST +0200

Booted last: 03 May 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:098a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0803]
    Kernel modules: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 1bcf:2c81 Sunplus Innovation Technology Inc. 
Bus 001 Device 005: ID 04ca:3014 Lite-On Technology Corp. 
Bus 001 Device 006: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 151552  0
ath3k                  20480  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              778240  1 ath9k
cfg80211              622592  4 mac80211,ath9k,ath,ath9k_common
bluetooth             548864  34 btrtl,btintel,bnep,btbcm,rfcomm,ath3k,btusb
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: enp0s20u2c4i2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s20u2c4i2' [IF2]> brd <MAC address>
    inet 172.20.10.3/28 brd 172.20.10.15 scope global dynamic noprefixroute enp0s20u2c4i2
       valid_lft 84862sec preferred_lft 84862sec
    inet6 fe80::d41e:9769:230a:ed01/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

enp0s20u2c4i2  no wireless extensions.

##### route #############################

default via 172.20.10.1 dev enp0s20u2c4i2 proto dhcp metric 100 
169.254.0.0/16 dev enp0s20u2c4i2 scope link metric 1000 
172.20.10.0/28 dev enp0s20u2c4i2 proto kernel scope link src 172.20.10.3 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       756     1  0 19:54 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u2c4i2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Apple Inc.
GENERAL.PRODUCT:                        iPhone
GENERAL.DRIVER:                         ipheth
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp0s20u2c4i2' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:4.2/net/enp0s20u2c4i2
GENERAL.IP-IFACE:                       enp0s20u2c4i2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       90a7bc45-db86-3fb0-849f-6553c9c234f5
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         172.20.10.3/28
IP4.GATEWAY:                            172.20.10.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 172.20.10.1, mt = 100
IP4.ROUTE[2]:                           dst = 172.20.10.0/28, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.20.10.1
DHCP4.OPTION[1]:                        expiry = 1525462883
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        server_name = iPhone
DHCP4.OPTION[4]:                        requested_host_name = 1
DHCP4.OPTION[5]:                        requested_broadcast_address = 1
DHCP4.OPTION[6]:                        requested_domain_name = 1
DHCP4.OPTION[7]:                        domain_name_servers = 172.20.10.1
DHCP4.OPTION[8]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[9]:                        requested_wpad = 1
DHCP4.OPTION[10]:                       requested_time_offset = 1
DHCP4.OPTION[11]:                       dhcp_lease_time = 85536
DHCP4.OPTION[12]:                       broadcast_address = 172.20.10.15
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_interface_mtu = 1
DHCP4.OPTION[15]:                       requested_subnet_mask = 1
DHCP4.OPTION[16]:                       ip_address = 172.20.10.3
DHCP4.OPTION[17]:                       next_server = 172.20.10.1
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.240
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       requested_domain_name_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_scope = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       routers = 172.20.10.1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       network_number = 172.20.10.0
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.20.10.1
IP6.ADDRESS[1]:                         fe80::d41e:9769:230a:ed01/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   90a7bc45-db86-3fb0-849f-6553c9c234f5 | Wired connection 2

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

enp0s20u2c4i2  no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

enp0s20u2c4i2  Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9CBF8CE71BEA33E6D6B79A5
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
parm:           use_msi:Use MSI instead of INTx if possible (int)

[ath3k]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     36C0F7AEF3B569F1798216D
depends:        bluetooth
retpoline:      Y
intree:         Y
name:           ath3k
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_common]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     94213E6B06C24095311E862
depends:        ath9k_hw,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_hw]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D5984DFEF6457DDB060988E
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   20.833342] platform regulatory.0: Direct firmware load for regulatory.db failed with error -2
[   22.152445] ath9k 0000:03:00.0: PCI INT A: not connected
[   22.152496] ath9k 0000:03:00.0: request_irq failed
[   22.152514] ath9k: probe of 0000:03:00.0 failed with error -107
[   37.729810] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   37.774959] r8169 0000:02:00.0 enp2s0: link down
[   37.775064] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[  120.624432] ipheth 1-2:4.2 enp0s20u2c4i2: renamed from eth0
[  120.659004] IPv6: ADDRCONF(NETDEV_UP): enp0s20u2c4i2: link is not ready (repeated 2 times)
[  128.796383] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s20u2c4i2: link becomes ready

########## wireless info END ############
```

---

### Post by jeremy31 on 2018-05-04
Reboot and access the Grub menu, press and hold Shift or ESC until the menu appears, after the menu appears press e to edit, scroll down to the line that starts with linux, scroll right to just after quiet splash and add  iommu=soft
Press F10 to boot and see if it works

---

### Post by leocatto5 on 2018-05-07
Unfortunately it didn’t work. I tried to add iommu=soft right after quiet splash, and I still get the message “No Wifi Adapter Found” in the Settings Menu. One thing that I’ve just realized is that when I open the GRUB screen and add this new command, right after that I press F10 to boot this command disappears from the edit screen.

---

### Post by jeremy31 on 2018-05-07
After booting with the change in grub, you can see if it used the parameter with ```
cat /proc/cmdline
```

---

### Post by leocatto5 on 2018-05-07
I ran the code and yes, the “iommu=soft” is there. But even that, I’m still not able to get wireless connection :(

---

### Post by jeremy31 on 2018-05-07
Can you try this card in a different computer maybe even with a Live Ubuntu USB to see if it works?
I am running out of ideas as there was some strange errors in the script report, any IOMMU settings in UEFI/BIOS to change?

---

### Post by leocatto5 on 2018-05-08
I tried to run with a Live Ubuntu USB in my computer, and apparently the same error occurs. Sorry, what do you mean by "this card" ? Do you think it's worth to try to reinstall the dual-boot to see what happens ? Thanks !

---

### Post by jeremy31 on 2018-05-08
I would try the wifi card in a different computer to verify it works

---

### Post by leocatto5 on 2018-05-08
Oh ok. Yeah, I don't have another computer to test it, unfortunately. Anway, I'll try to reinstall it and see what hapens. I would love to migrate from my windows 10 to the newest version of Ubuntu :( 
The thing is that my wifi card is working properly on my Windows 10 system, that's what I don't understand. It should work properly too in my Ubuntu, right ? 

But thanks anyway !

---

### Post by jeremy31 on 2018-05-08
It sounds like some BIOS setting might be causing the issue in Ubuntu if it works perfect in Windows.

---

### Post by leocatto5 on 2018-05-08
Do you know if there’s something I should change in BIOS to fix it ?

---

### Post by jeremy31 on 2018-05-08
The only results I found searching for some of your errors involved IOMMU settings.
It might be quicker if you searched for some of them
```
[   22.152445] ath9k PCI INT A: not connected
[   22.152496] ath9k  request_irq failed
[   22.152514] ath9k: probe of failed with error -107
```

Post if you get this fixed as most of these cards work but have issues with WEP/TKIP encryption on the router

---

### Post by leocatto5 on 2018-05-09
Hmm yes, as you said, I didn' find many results searching for some of these errors. I will try to reinstall it once my wifi is working perfectly in my windows 10 partition. Thanks !

---

### Post by leocatto5 on 2018-05-09
I reinstalled the Ubuntu 18.04 dualbooting alongside Windows 10 and the  same error occurs. I generated a new wireless-info file to see if any  code has changed, and apparently there are some different lines there. 

```
 
########## wireless info START ##########

Report from: 09 May 2018 20:09 CEST +0200

Booted last: 09 May 2018 00:00 CEST +0200

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:098a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0803]
    Kernel modules: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 1bcf:2c81 Sunplus Innovation Technology Inc. 
Bus 001 Device 006: ID 04ca:3014 Lite-On Technology Corp. 
Bus 001 Device 010: ID 05ac:12a8 Apple, Inc. iPhone5/5C/5S/6
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              778240  1 ath9k
cfg80211              622592  4 mac80211,ath9k,ath,ath9k_common
ath3k                  20480  0
bluetooth             548864  34 btrtl,btintel,bnep,btbcm,rfcomm,ath3k,btusb

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
4: enp0s20u1c4i2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s20u1c4i2' [IF2]> brd <MAC address>
    inet 172.20.10.3/28 brd 172.20.10.15 scope global dynamic noprefixroute enp0s20u1c4i2
       valid_lft 85100sec preferred_lft 85100sec
    inet6 fe80::4851:94b7:bc33:7608/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp2s0    no wireless extensions.

enp0s20u1c4i2  no wireless extensions.

lo        no wireless extensions.

##### route #############################

default via 172.20.10.1 dev enp0s20u1c4i2 proto dhcp metric 100 
169.254.0.0/16 dev enp0s20u1c4i2 scope link metric 1000 
172.20.10.0/28 dev enp0s20u1c4i2 proto kernel scope link src 172.20.10.3 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       785     1  0 20:00 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20u1c4i2
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Apple Inc.
GENERAL.PRODUCT:                        iPhone
GENERAL.DRIVER:                         ipheth
GENERAL.DRIVER-VERSION:                 --
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp0s20u1c4i2' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:4.2/net/enp0s20u1c4i2
GENERAL.IP-IFACE:                       enp0s20u1c4i2
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       6e5f94ad-9000-3a0b-b496-ef265464109e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         172.20.10.3/28
IP4.GATEWAY:                            172.20.10.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 172.20.10.1, mt = 100
IP4.ROUTE[2]:                           dst = 172.20.10.0/28, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             172.20.10.1
DHCP4.OPTION[1]:                        requested_domain_search = 1
DHCP4.OPTION[2]:                        server_name = iPhone
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        expiry = 1525974485
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 172.20.10.1
DHCP4.OPTION[10]:                       broadcast_address = 172.20.10.15
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 85536
DHCP4.OPTION[14]:                       routers = 172.20.10.1
DHCP4.OPTION[15]:                       ip_address = 172.20.10.3
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.240
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       requested_wpad = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       domain_name_servers = 172.20.10.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_routers = 1
DHCP4.OPTION[25]:                       requested_interface_mtu = 1
DHCP4.OPTION[26]:                       network_number = 172.20.10.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 172.20.10.1
IP6.ADDRESS[1]:                         fe80::4851:94b7:bc33:7608/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   6e5f94ad-9000-3a0b-b496-ef265464109e | Wired connection 1

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

enp0s20u1c4i2  no frequency information.

lo        no frequency information.

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

enp0s20u1c4i2  Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[ath9k]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9CBF8CE71BEA33E6D6B79A5
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     94213E6B06C24095311E862
depends:        ath9k_hw,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_hw]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D5984DFEF6457DDB060988E
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-20-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/4.15.0-20-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     36C0F7AEF3B569F1798216D
depends:        bluetooth
retpoline:      Y
intree:         Y
name:           ath3k
vermagic:       4.15.0-20-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

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

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   31.468730] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   31.558891] r8169 0000:02:00.0 enp2s0: link down
[   31.558991] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[  160.782721] ipheth 1-1:4.2 enp0s20u1c4i2: renamed from eth0
[  160.818062] IPv6: ADDRCONF(NETDEV_UP): enp0s20u1c4i2: link is not ready (repeated 2 times)
[  162.812383] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s20u1c4i2: link becomes ready

########## wireless info END ############ 

```

---

### Post by chili555 on 2018-05-09
Jeremy and I want to see some clues in:```
 dmesg | grep ath
```Did you try re-seating the card in its slot?

---

### Post by leocatto5 on 2018-05-09
I didn't re-seat the card in its slot. To be honest, I have no idea how to do that and I was afraid of damaging something. But as I said, the WIFI is working perfectly on my Windows 10, so it shouldn't be a hardware problem, right ?

Anyway, here follows the results:

```
dmesg | grep ath
[   12.802456] usbcore: registered new interface driver ath3k
[   12.929934] ath9k 0000:03:00.0: PCI INT A: not connected
[   12.929984] ath9k 0000:03:00.0: request_irq failed
[   12.930001] ath9k: probe of 0000:03:00.0 failed with error -107

```

Really thanks for the patience !

---

### Post by chili555 on 2018-05-09
> **leocatto5 said:**
> I didn't re-seat the card in its slot. To be honest, I have no idea how to do that and I was afraid of damaging something. But as I said, the WIFI is working perfectly on my Windows 10, so it shouldn't be a hardware problem, right ?

Anyway, here follows the results:

```
dmesg | grep ath
[   12.802456] usbcore: registered new interface driver ath3k
[   12.929934] [COLOR="#FF0000"]ath9k 0000:03:00.0: PCI INT A: not connected[/COLOR]
[   12.929984][COLOR="#FF0000"] ath9k 0000:03:00.0: request_irq failed[/COLOR]
[   12.930001] [COLOR="#FF0000"]ath9k: probe of 0000:03:00.0 failed with error -107[/COLOR]

```

Really thanks for the patience !There are the same errors as before.

Did you try resetting the BIOS to defaults?

---

### Post by leocatto5 on 2018-05-09
Yes, I pressed F2 until the BIOS windows opened and pressed F9 to Setup Defaults. Apparently it didn’t change anything. These errors just came up again right after I Unabled the “Secured Boot” option.

---

### Post by leocatto5 on 2018-05-10
Just for curiosity, I unistalled the 18.04 version and installed the 16.04 one. The same errors show up when I type dmesg | grep ath. 
I&#8217;m totally losing hope :(

[IMG]https://imgur.com/a/EXMGsaG[/IMG]
[IMG]https://imgur.com/a/EXMGsaG[/IMG]You can see in the image that no Wifi is found in the wireless tab: 

 [https://imgur.com/a/EXMGsaG](https://imgur.com/a/EXMGsaG)

---

### Post by chili555 on 2018-05-10
Perhaps others will chime in with other opinions, but I regret that I have no other suggestions. I'm sorry.

---

### Post by rsteinmetz70112 on 2018-05-10
Based on what you have posted so far it looks to me like Ubuntu is not recognizing the WiFi adapter as Wifi.
You appear to have tow network adapters one wired and one WiFi. 
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:098a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0803]
    Kernel modules: ath9k
```
It appears that both are being recognized 
```
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>

4: enp0s20u1c4i2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'enp0s20u1c4i2' [IF2]> brd <MAC address>
    inet 172.20.10.3/28 brd 172.20.10.15 scope global dynamic noprefixroute enp0s20u1c4i2
       valid_lft 85100sec preferred_lft 85100sec
    inet6 fe80::4851:94b7:bc33:7608/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever 
```


But the wireless one is not being recognized as wireless.
```
enp2s0    no wireless extensions.

enp0s20u1c4i2  no wireless extensions.
```

try running ifup on bothe adapters and see if you get any error messages 

Try running 
```

sudo dpkg --configure -a
sudo apt-get install -f

```
That should clean up and misconfiguration

If that doesn't work

```
sudo modprobe -v wl; dkms status
```
Post the results

---

### Post by jeremy31 on 2018-05-10
rsteinmetz70112  The interfaces shown are both ethernet, one internal- enp2s0 and one USB- enp0s20u1c4i2 and my guess the USB ethernet device is the Apple iPhone on  USB tethering

---

### Post by leocatto5 on 2018-05-11
I ran the commands mentioned above and it didn’t work. However, here follows the code result: 

```
 sudo modprobe -v -wl; dkms status

modprobe: FATAL : Module wl not found in directory /lib/modules/4.13.0-41-generic 
```

---

### Post by chili555 on 2018-05-11
> **leocatto5 said:**
> I ran the commands mentioned above and it didn&#8217;t work. However, here follows the code result: 

```
 sudo modprobe -v -wl; dkms status

modprobe: FATAL : Module wl not found in directory /lib/modules/4.13.0-41-generic 
```rsteinmetz70112  The driver wl, which is for Broadcom wireless devices, is not installed here and, even if it were, would do nothing to help his Atheros.

ifup will only be effective on interfaces declared in /etc/network/interfaces which is not the case here; OP is using Network Manager.

---

### Post by praseodym on 2018-05-11
[https://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507](https://forum.ubuntuusers.de/topic/wlan-hardware-geht-nicht-notebook/2/#post-6231507)

Check the bootoptions from here, the bold ones seemed to work

---

### Post by leocatto5 on 2018-05-13
Hi praseodym, how can I change these bootoptions ? Sorry, I'm totally newbie about it ..

---

### Post by TheDecaffeinatedCapacitor on 2018-05-15
Looks like I'm having the same issue too. I just got my old girl running again after over a year in the cabinet. Plugged in a new hard drive, installed Ubuntu, running beautifully. However, I cannot get it to locate my wifi card (Atheros) which was working perfectly at the time of the hard drive failure. I'll try all of the solutions up to this point, and post if one of them works, but I am in the same boat. At last resort, I'll probably just get one of those external wifi receivers.

---

### Post by chili555 on 2018-05-15
> **TheDecaffeinatedCapacitor said:**
> Looks like I'm having the same issue too. I just got my old girl running again after over a year in the cabinet. Plugged in a new hard drive, installed Ubuntu, running beautifully. However, I cannot get it to locate my wifi card (Atheros) which was working perfectly at the time of the hard drive failure. I'll try all of the solutions up to this point, and post if one of them works, but I am in the same boat. At last resort, I'll probably just get one of those external wifi receivers.I suggest that you start your own new thread and include the wireless info from here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by leocatto5 on 2018-05-15
I took a look at other forums, apparently no one seems to have the same problem as mine. The only guys I saw complaining about it couldn't solve it (or at least didn't post any solution until now). It's really weird how this bug persists after all the recommended suggestions. I even tried to install another version of Ubuntu, update de Kernel, redo the whole partition process of my hard disk. I'm actually completely lost, since I don't even know where the problem is. Do you guys think it's a BIOS problem ? I mean , it can’t be a hardware issue for sure ! :(

---

### Post by TheDecaffeinatedCapacitor on 2018-05-15
Thanks Chili. I was having the Broadcom issue. Fix was quick and simple.

---

### Post by leocatto5 on 2018-05-16
Just realized that when I type: sudo su -c 'modinfo ath9k', a message at the bottom says: 4.13.0-41-generic SMP mod_unload. Does it have something to do with the Kernel ?

---

### Post by jeremy31 on 2018-05-16
That is normal for the 4.13.0 kernels.  If that line doesn't match what the kernel expects, the kernel will not load the module

---

### Post by leocatto5 on 2018-05-16
Is there any specific Kernel version I should try to update or it has nothing to do with my problem ?

---

### Post by chili555 on 2018-05-16
I doubt that it has anything to do with your problem; however, it takes little to download and burn the DVD or USB of an earlier or later Ubuntu version to see if the wireless works. Check:```
dmesg | grep ath
```

---

### Post by leocatto5 on 2018-05-17
Hi chili555, the code results:
```
 dmesg | grep ath[   12.802456] usbcore: registered new interface driver ath3k[   12.929934]
 ath9k 0000:03:00.0: PCI INT A: not connected[   12.929984]
 ath9k 0000:03:00.0: request_irq failed[   12.930001]
 ath9k: probe of 0000:03:00.0 failed with error -107 
```

Are basically the same errors as before. They persist, no matter if I reinstall the same version or try an older/newer one.

---

### Post by leocatto5 on 2018-05-22
Guys, thanks for all your help ! Unfortunately I couldn't solve the problem. The solution for the moment is going back to my Windows OS. Anyway, thank you so much for the effort ! :)

Last try: do you think is it worth trying to update the BIOS ? (Acer Laptop)

---

### Post by vinioliveira on 2018-08-11
> **leocatto5 said:**
> Guys, thanks for all your help ! Unfortunately I couldn't solve the problem. The solution for the moment is going back to my Windows OS. Anyway, thank you so much for the effort ! :)

Last try: do you think is it worth trying to update the BIOS ? (Acer Laptop)

Hello, I know  this topic is a bit old, but I was just having the same problem as you,  reading the topic and seeing that it was possibly a problem on the  motherboard bios, I updated it, it worked for me, maybe it works to you too.

---

### Post by tehkos on 2018-09-16
I confirm. Had the same issue with Acer Laptop. Updating bios helped.

---

