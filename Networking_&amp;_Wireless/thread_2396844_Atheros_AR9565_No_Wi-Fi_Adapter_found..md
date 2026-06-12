---
title: "Atheros AR9565: No Wi-Fi Adapter found."
date: 2018-07-21
forum: Networking &amp; Wireless
---

### Post by lmonte on 2018-07-21
Hi all, i have installed recently Ubuntu 18.04 alongside Windows 10. The problem is that the OS is not recognizing the Wi-Fi adapter.

My notebook is an Acer Aspire E 15;
Windows 10 recognizes the Wi-Fi adapter and works fine;
Using wired internet works on Ubuntu;

I have seen another threads here and usually they ask you to run some commands on the terminal, here are the outputs from what i have seen asked:
```

user@user-Aspire-E5-573G:~$ lspci00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation HD Graphics 5500 (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
04:00.0 3D controller: NVIDIA Corporation GK208M [GeForce 920M] (rev a1)


user@user-Aspire-E5-573G:~$ iwconfig
lo        no wireless extensions.


enp2s0    no wireless extensions.


user@user-Aspire-E5-573G:~$ sudo modprobe ath9k && dmesg | grep ath
[   21.124397] ath9k 0000:03:00.0: PCI INT A: not connected
[   21.124437] ath9k 0000:03:00.0: request_irq failed
[   21.124452] ath9k: probe of 0000:03:00.0 failed with error -107
[   66.720109] usbcore: registered new interface driver ath3k


user@user-Aspire-E5-573G:~$ dmesg | grep ath
[   21.124397] ath9k 0000:03:00.0: PCI INT A: not connected
[   21.124437] ath9k 0000:03:00.0: request_irq failed
[   21.124452] ath9k: probe of 0000:03:00.0 failed with error -107
[   66.720109] usbcore: registered new interface driver ath3k

```

Also, i have seen a script here called wireless-info, here is the contents of the wireless-info.txt that this script creates:

```



########## wireless info START ##########


Report from: 20 Jul 2018 19:08 -03 -0300


Booted last: 20 Jul 2018 00:00 -03 -0300


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 18.04 LTS
Release:    18.04
Codename:    bionic


##### kernel ############################


Linux 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1025:098a]
    Kernel driver in use: r8169


03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Lite-On Communications Inc QCA9565 / AR9565 Wireless Network Adapter [11ad:0803]
    Kernel modules: ath9k, wl


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 004: ID 1bcf:2c81 Sunplus Innovation Technology Inc. 
Bus 001 Device 006: ID 04ca:3014 Lite-On Technology Corp. 
Bus 001 Device 002: ID 046d:c530 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              778240  1 ath9k
wl                   6447104  0
ath3k                  20480  0
bluetooth             548864  44 btrtl,btintel,bnep,btbcm,rfcomm,ath3k,btusb
cfg80211              622592  5 wl,mac80211,ath9k,ath,ath9k_common
mxm_wmi                16384  1 nouveau
wmi                    24576  2 mxm_wmi,nouveau


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.201  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::30ea:9127:ec3a:ae18  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 6184  bytes 4765483 (4.7 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5286  bytes 892189 (892.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 639  bytes 51871 (51.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 639  bytes 51871 (51.8 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


enp2s0    no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp2s0


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


    NetworkManager


Running:


root       717     1  0 18:42 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       ca881434-476f-3f64-bce4-24cede0b0ae2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.201/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             8.8.8.8
IP4.DNS[2]:                             8.8.4.4
DHCP4.OPTION[1]:                        requested_host_name = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[11]:                       dhcp_message_type = 5
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.0.1
DHCP4.OPTION[14]:                       dhcp_lease_time = 7200
DHCP4.OPTION[15]:                       ip_address = 192.168.0.201
DHCP4.OPTION[16]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       expiry = 1532130149
DHCP4.OPTION[20]:                       domain_name_servers = 8.8.8.8 8.8.4.4
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       requested_ntp_servers = 1
DHCP4.OPTION[23]:                       requested_routers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_interface_mtu = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::30ea:9127:ec3a:ae18/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ca881434-476f-3f64-bce4-24cede0b0ae2 | Wired connection 1


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


Region: America/Fortaleza (based on set time zone)


global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, PASSIVE-SCAN
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, PASSIVE-SCAN
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, PASSIVE-SCAN
    (5735 - 5835 @ 80), (N/A, 20), (N/A), PASSIVE-SCAN
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


enp2s0    no frequency information.


lo        no frequency information.


##### iwlist scan #######################


enp2s0    Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F4328CE52BA6067DD4EDE7B
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       4.15.0-29-generic SMP mod_unload 
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
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     94213E6B06C24095311E862
depends:        ath9k_hw,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[ath9k_hw]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D5984DFEF6457DDB060988E
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[ath]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[mac80211]
filename:       /lib/modules/4.15.0-29-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1CEA5CF286EDB289C1D0BF8
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-29-generic SMP mod_unload 
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


[wl]
filename:       /lib/modules/4.15.0-29-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[ath3k]
filename:       /lib/modules/4.15.0-29-generic/kernel/drivers/bluetooth/ath3k.ko
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
vermagic:       4.15.0-29-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4


[cfg80211]
filename:       /lib/modules/4.15.0-29-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     D5B0789D4C423C81CCFB437
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-29-generic SMP mod_unload 
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
nohwcrypt: 1
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


[/etc/modprobe.d/asus_nb_wmi.conf]
options asus_nb_wmi wapf=4


[/etc/modprobe.d/ath9k_htc.conf]
options ath9k_htc use_dev_fw=1


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


[/etc/modprobe.d/blacklist-hp.conf]
blacklist hp_wmi


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


##### rc.local ##########################


grep: /etc/rc.local: No such file or directory


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   19.992405] ath9k 0000:03:00.0: PCI INT A: not connected
[   19.992444] ath9k 0000:03:00.0: request_irq failed
[   19.992459] ath9k: probe of 0000:03:00.0 failed with error -107
[   20.440224] wl: loading out-of-tree module taints kernel.
[   20.440226] wl: module license 'MIXED/Proprietary' taints kernel.
[   20.441893] wl: module verification failed: signature and/or required key missing - tainting kernel
[ 1390.263906] ath9k: ath9k: Driver unloaded
[ 1390.435855] ath9k 0000:03:00.0: PCI INT A: no GSI
[ 1390.435957] ath9k 0000:03:00.0: request_irq failed
[ 1390.435976] ath9k: probe of 0000:03:00.0 failed with error -107


########## wireless info END ############

```

I think it is also worth noting that, on Ubuntu 18.04 Live and 16.10 Live, the OS was also not recognizing Wi-Fi.

Any help regarding this issue is appreciated. Thanks.

---

### Post by praseodym on 2018-07-22
Please check here

[https://ubuntuforums.org/showthread.php?t=2395941&page=2&p=13785787#post13785787](https://ubuntuforums.org/showthread.php?t=2395941&page=2&p=13785787#post13785787)

and uninstall this one
```

sudo apt-get remove --purge bcmwl-kernel-source
```

---

### Post by lmonte on 2018-07-22
Thanks for the suggestions. Unfortunately these commands did not solve my issue. Ubuntu still says "No Wi-Fi Adapter found."

---

### Post by lmonte on 2018-07-27
I have found that the wireless device has network unclaimed. Maybe this has something to do with the problem?

Output for lshw -C network:
```

[sudo] password for montesuma: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 15
       serial: 1c:39:47:52:dd:b9
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.1.8 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:-2147483648 ioport:4000(size=256) memory:c4204000-c4204fff memory:c4200000-c4203fff
  *-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:c4100000-c417ffff memory:c4180000-c418ffff

```

---

### Post by lmonte on 2018-09-02
Up.

---

### Post by garr2 on 2018-09-02
buen dia 

este es el codigo a tener en cuenta:

[COLOR=#333333][FONT=&quot]En este artículo vamos a tratar la solución al problema recurrente del **driver de la tarjeta inalámbrica** de la marca **Broadcom BCM4311** en sistemas Gnu Linux.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]En concreto veremos el caso de Ubuntu, Debian, Linux Mint y derivados de los anteriores, para lo cual deberemos de seguir los siguientes pasos:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Lo primero que haremos es **quitar el controlador por defecto**, para lo cual introduciremos el siguiente comando en la terminal:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]$ sudo apt-get remove --purge bcmwl-kernel-source[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Ahora **instalaremos los controladores privativos** del firmware:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]$ sudo apt-get install linux-firmware-nonfree[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Por último tendremos que **cargar el módulo b43** para su funcionamiento:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]$ sudo modprobe b43[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Como paso opcional (pero recomendado) podemos seguir un pequeño tip que hara que funcione de forma automática el módulo anterior:[/FONT][/COLOR]
[INDENT][COLOR=#999999][FONT=Georgia][I]$ sudo su
# echo "b43" >> /etc/modules[/I][/FONT][/COLOR]
[/INDENT]

---

