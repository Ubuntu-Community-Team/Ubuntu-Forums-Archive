---
title: "WIFI not detecting in 18.04"
date: 2018-08-29
forum: Networking &amp; Wireless
---

### Post by Hansih on 2018-08-29
Hi am using Hp Laptop with Intel® Core&#8482; i5-4200M CPU @ 2.50GHz × 4, I have updated my Ubuntu from 16.04 to 18.04 all was fine initially and updating my software as I get the updates. From past one week my wifi was dropping all of a sudden and then from past couple of days wifi itself is not detecting in my ubuntu. I have tried few solutions after googling but did not fix. Can you kindly help me how can I fix it. 

Output for sudo lshw -C network

*-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:0f:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b7500000-b757ffff memory:b7580000-b758ffff

---

### Post by jeremy31 on 2018-08-30
```
sudo apt install --reinstall linux-modules-extra-$(uname -r)
```
Then reboot

---

### Post by Hansih on 2018-08-31
Thank you jeremy31  but, still the same.
  *-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:0f:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b7500000-b757ffff memory:b7580000-b758ffff

I have tried below commands
sudo apt-get purge bcmwl-kernel-source

sudo apt-get update
sudo apt-get install bcmwl-kernel-source

OUTPUT: lspci -knn | grep Net -A3; rfkill list
0f:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
	Subsystem: Hewlett-Packard Company QCA9565 / AR9565 Wireless Network Adapter [103c:217f]
	Kernel modules: ath9k, wl
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

but no luck...

---

### Post by jeremy31 on 2018-08-31
See the wireless script link in my signature and post results

---

### Post by Hansih on 2018-08-31
Still the same not working here are the results

```
########## wireless info START ##########

Report from: 31 Aug 2018 16:17 IST +0530

Booted last: 31 Aug 2018 00:00 IST +0530

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-33-generic #36-Ubuntu SMP Wed Aug 15 16:00:05 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=1

##### desktop ###########################

Ubuntu

##### lspci #############################

libkmod: ERROR ../libkmod/libkmod-config.c:656 kmod_config_parse: /etc/modprobe.d/iwlwifi.conf line 2: ignoring bad line starting with '&#8220;options'

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:225d]
    Kernel driver in use: r8169

0f:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Hewlett-Packard Company QCA9565 / AR9565 Wireless Network Adapter [103c:217f]
    Kernel modules: ath9k, wl

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 3938:1031  
Bus 003 Device 005: ID 0cf3:3121 Atheros Communications, Inc. 
Bus 003 Device 002: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6447104  0
hp_wmi                 16384  0
wmi_bmof               16384  0
sparse_keymap          16384  1 hp_wmi
ath3k                  20480  0
bluetooth             548864  34 btrtl,btintel,bnep,btbcm,rfcomm,ath3k,btusb
wmi                    24576  2 wmi_bmof,hp_wmi
ath9k                 151552  0
ath9k_common           36864  1 ath9k
ath9k_hw              471040  2 ath9k,ath9k_common
ath                    28672  3 ath9k_hw,ath9k,ath9k_common
mac80211              741376  1 ath9k
cfg80211              634880  5 wl,mac80211,ath9k,ath,ath9k_common
compat                 16384  2 mac80211,cfg80211

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp8s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.117  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::8d2f:b14c:2daf:13f0  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 88731  bytes 83231795 (83.2 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 55543  bytes 7861149 (7.8 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 13001  bytes 7588243 (7.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 13001  bytes 7588243 (7.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

lo        no wireless extensions.

enp8s0    no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp8s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp8s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp8s0

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       786     1  0 14:11 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp8s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:08:00.0/net/enp8s0
GENERAL.IP-IFACE:                       enp8s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       52159a4d-d052-310a-bfdc-f0808a717399
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.117/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        dhcp_rebinding_time = 6071
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_broadcast_address = 1
DHCP4.OPTION[4]:                        host_name = dream-big
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_time_offset = 1
DHCP4.OPTION[7]:                        requested_domain_name = 1
DHCP4.OPTION[8]:                        expiry = 1535718385
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 192.168.0.1
DHCP4.OPTION[11]:                       requested_wpad = 1
DHCP4.OPTION[12]:                       dhcp_message_type = 5
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 7200
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       ip_address = 192.168.0.117
DHCP4.OPTION[17]:                       requested_domain_name_servers = 1
DHCP4.OPTION[18]:                       requested_static_routes = 1
DHCP4.OPTION[19]:                       dhcp_renewal_time = 3371
DHCP4.OPTION[20]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[21]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ntp_servers = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[26]:                       requested_routers = 1
DHCP4.OPTION[27]:                       requested_interface_mtu = 1
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::8d2f:b14c:2daf:13f0/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{26}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   52159a4d-d052-310a-bfdc-f0808a717399 | Wired connection 1

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

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

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

lo        no frequency information.

enp8s0    no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp8s0    Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/4.15.0-33-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[ath3k]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/bluetooth/ath3k.ko
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
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     F4328CE52BA6067DD4EDE7B
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k
vermagic:       4.15.0-33-generic SMP mod_unload 
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
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     94213E6B06C24095311E862
depends:        ath9k_hw,cfg80211,ath
retpoline:      Y
intree:         Y
name:           ath9k_common
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath9k_hw]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     D5984DFEF6457DDB060988E
depends:        ath
retpoline:      Y
intree:         Y
name:           ath9k_hw
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[ath]
filename:       /lib/modules/4.15.0-33-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           ath
vermagic:       4.15.0-33-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4

[mac80211]
filename:       /lib/modules/4.15.0-33-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        iwlwifi-stack-public:master:7156:f6032645
srcversion:     BCDB4384EBC49BFFE8CE5D3
depends:        cfg80211,compat
retpoline:      Y
name:           mac80211
vermagic:       4.15.0-33-generic SMP mod_unload 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.15.0-33-generic/updates/net/wireless/cfg80211.ko
version:        iwlwifi-stack-public:master:7156:f6032645
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     BEBD8A56F26E70547E14AA1
depends:        compat
retpoline:      Y
name:           cfg80211
vermagic:       4.15.0-33-generic SMP mod_unload 
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
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

ath9k

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
options iwlwifi wd_disable=0 bt_coex_active=0 11n_disable=1
&#8220;options iwlwifi disable_msix=1&#8221;

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=0 ant_sel=1

[/etc/modprobe.d/rtl8723de.conf]
options rtl8723de ant_sel=2

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="iwlwifi wlp2s0"

[/etc/pm/sleep.d/00_check_touchpad_status] (755 root)
LOGFILE="/var/log/sleep.log"
case "$1" in
        resume|thaw)
                echo "Resume normal from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /usr/share/touchpad-indicator/check_touchpad_status.py resume
                echo "Touchpad enabled"
                ;;
esac

##### udev rules ########################

##### dmesg #############################

[   24.495080] wl: module license 'MIXED/Proprietary' taints kernel.

########## wireless info END ############
```

---

### Post by Hansih on 2018-09-04
Can someone kindly help on this.

---

### Post by jeremy31 on 2018-09-04
Try ```
sudo apt remove bcmwl-kernel-source
sudo rm /etc/modprobe.d/iwlwifi.conf
```
Reboot and post results  for ```
dmesg | grep ath
```

---

### Post by Hansih on 2018-09-04
Thank you for your reply here is the results **dmesg | grep ath**[   22.122810] ath: (null): WB335 1-ANT card detected
[   22.122811] ath: (null): Set BT/WLAN RX diversity capability
[   22.131818] ath: (null): Enable LNA combining
[   22.133055] ath: (null): ASPM enabled: 0x43
[   22.133056] ath: EEPROM regdomain: 0x6a
[   22.133056] ath: EEPROM indicates we should expect a direct regpair map
[   22.133057] ath: Country alpha2 being used: 00
[   22.133058] ath: Regpair used: 0x6a
[   22.133083] Modules linked in: ath9k(+) ath9k_common ath9k_hw ath mac80211(OE) cfg80211(OE) compat(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse r8169 mii drm rtsx_pci ahci libahci video
[   22.133124]  ? ath9k_op_ps_wakeup+0x20/0x20 [ath9k]
[   22.133126]  ath_regd_init+0x98/0x150 [ath]
[   22.133131]  ath9k_init_device+0xd39/0xea0 [ath9k]
[   22.133140]  ath_pci_probe+0x254/0x490 [ath9k]
[   22.133161]  ? set_use_msi+0x1a/0x1a [ath9k]
[   22.133166]  ? set_use_msi+0x1a/0x1a [ath9k]
[   22.133172]  ath_pci_init+0x23/0x30 [ath9k]
[   22.133176]  ath9k_init+0xe/0xfe6 [ath9k]
[   22.133244] Modules linked in: ath9k(+) ath9k_common ath9k_hw ath mac80211(OE) cfg80211(OE) compat(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse r8169 mii drm rtsx_pci ahci libahci video
[   22.133277]  ? ath9k_op_ps_wakeup+0x20/0x20 [ath9k]
[   22.133279]  ath_regd_init+0x98/0x150 [ath]
[   22.133282]  ath9k_init_device+0xd39/0xea0 [ath9k]
[   22.133289]  ath_pci_probe+0x254/0x490 [ath9k]
[   22.133306]  ? set_use_msi+0x1a/0x1a [ath9k]
[   22.133311]  ? set_use_msi+0x1a/0x1a [ath9k]
[   22.133316]  ath_pci_init+0x23/0x30 [ath9k]
[   22.133319]  ath9k_init+0xe/0xfe6 [ath9k]
[   22.133725] Modules linked in: ath9k(+) ath9k_common ath9k_hw ath mac80211(OE) cfg80211(OE) compat(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse r8169 mii drm rtsx_pci ahci libahci video
[   22.133785]  ath9k_init_device+0xde3/0xea0 [ath9k]
[   22.133791]  ath_pci_probe+0x254/0x490 [ath9k]
[   22.133808]  ? set_use_msi+0x1a/0x1a [ath9k]
[   22.133813]  ? set_use_msi+0x1a/0x1a [ath9k]
[   22.133818]  ath_pci_init+0x23/0x30 [ath9k]
[   22.133821]  ath9k_init+0xe/0xfe6 [ath9k]
[   22.134308] ath9k 0000:0f:00.0: Failed to initialize device
[   22.134394] ath9k: probe of 0000:0f:00.0 failed with error -22
[   24.271339] usbcore: registered new interface driver ath3k

---

### Post by jeremy31 on 2018-09-04
I think those errors mean we should try ```
echo "options ath9k use_msi=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
Reboot

---

### Post by Hansih on 2018-09-04
Not much luck again am posting the result: [COLOR=#000000][FONT=&quot]dmesg | grep ath[/FONT][/COLOR]

[   21.735545] ath9k 0000:0f:00.0: Using MSI
[   21.735585] ath: (null): WB335 1-ANT card detected
[   21.735586] ath: (null): Set BT/WLAN RX diversity capability
[   21.744594] ath: (null): Enable LNA combining
[   21.745838] ath: (null): ASPM enabled: 0x43
[   21.745839] ath: EEPROM regdomain: 0x6a
[   21.745840] ath: EEPROM indicates we should expect a direct regpair map
[   21.745841] ath: Country alpha2 being used: 00
[   21.745842] ath: Regpair used: 0x6a
[   21.745870] Modules linked in: ath9k(+) ath9k_common ath9k_hw ath mac80211(OE) cfg80211(OE) compat(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse rtsx_pci ahci r8169 drm libahci mii video
[   21.745917]  ? ath9k_op_ps_wakeup+0x20/0x20 [ath9k]
[   21.745919]  ath_regd_init+0x98/0x150 [ath]
[   21.745925]  ath9k_init_device+0xd39/0xea0 [ath9k]
[   21.745936]  ath_pci_probe+0x254/0x490 [ath9k]
[   21.745960]  ? set_use_msi+0x1a/0x1a [ath9k]
[   21.745967]  ? set_use_msi+0x1a/0x1a [ath9k]
[   21.745974]  ath_pci_init+0x23/0x30 [ath9k]
[   21.745978]  ath9k_init+0xe/0xfe6 [ath9k]
[   21.746054] Modules linked in: ath9k(+) ath9k_common ath9k_hw ath mac80211(OE) cfg80211(OE) compat(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse rtsx_pci ahci r8169 drm libahci mii video
[   21.746091]  ? ath9k_op_ps_wakeup+0x20/0x20 [ath9k]
[   21.746093]  ath_regd_init+0x98/0x150 [ath]
[   21.746098]  ath9k_init_device+0xd39/0xea0 [ath9k]
[   21.746105]  ath_pci_probe+0x254/0x490 [ath9k]
[   21.746125]  ? set_use_msi+0x1a/0x1a [ath9k]
[   21.746131]  ? set_use_msi+0x1a/0x1a [ath9k]
[   21.746137]  ath_pci_init+0x23/0x30 [ath9k]
[   21.746141]  ath9k_init+0xe/0xfe6 [ath9k]
[   21.746600] Modules linked in: ath9k(+) ath9k_common ath9k_hw ath mac80211(OE) cfg80211(OE) compat(OE) parport_pc ppdev lp parport ip_tables x_tables autofs4 hid_generic usbhid hid i915 rtsx_pci_sdmmc i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse rtsx_pci ahci r8169 drm libahci mii video
[   21.746662]  ath9k_init_device+0xde3/0xea0 [ath9k]
[   21.746668]  ath_pci_probe+0x254/0x490 [ath9k]
[   21.746686]  ? set_use_msi+0x1a/0x1a [ath9k]
[   21.746692]  ? set_use_msi+0x1a/0x1a [ath9k]
[   21.746697]  ath_pci_init+0x23/0x30 [ath9k]
[   21.746701]  ath9k_init+0xe/0xfe6 [ath9k]
[   21.747221] ath9k 0000:0f:00.0: Failed to initialize device
[   21.747373] ath9k: probe of 0000:0f:00.0 failed with error -22
[   23.650917] usbcore: registered new interface driver ath3k

---

### Post by Hansih on 2018-09-04
sudo lshw -class network
  *-network                 
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: enp8s0
       version: 07
       serial: 40:a8:f0:01:f8:a4
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:4000(size=256) memory:b7600000-b7600fff memory:b7400000-b7403fff
  *-network UNCLAIMED
       description: Network controller
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:0f:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:b7500000-b757ffff memory:b7580000-b758ffff

---

### Post by jeremy31 on 2018-09-04
Uninstall the iwlwifi backports and reboot
```
cd backports-iwlwifi
sudo make uninstall
```

---

### Post by Hansih on 2018-09-05
Thank you. Now I can see wifi networks list but not connecting to wifi. Connection failed is coming.

---

### Post by jeremy31 on 2018-09-05
The parameter options might not be needed so ```
sudo rm /etc/modprobe.d/ath9k.conf
sudo modprobe -r ath9k
sudo modprobe ath9k
```

If that doesn't work post new wireless script results

---

### Post by Hansih on 2018-09-05
After running above commands and then selected saved wifi network but keep asking password again and again. not connecting


Can't able to paste the total thing. kindly look into above link

---

### Post by jeremy31 on 2018-09-05
Can you change router encryption to WPA2 AES/PSK without WEP, WPA, or TKIP?  I have had poor results with Atheros wifi when TKIP is used

---

### Post by Hansih on 2018-09-05
It is working fine. I can able to access wifi connection. it was password was changed. now it is connecting fine.Thanks a lot @[COLOR=#DD4814][COLOR=#C61919][jeremy31]("https://ubuntuforums.org/member.php?u=1924242") for your time.[/COLOR][/COLOR]

---

