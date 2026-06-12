---
title: "no network device samsung tabpro s"
date: 2018-04-12
forum: Networking &amp; Wireless
---

### Post by jasonscottlloyd on 2018-04-12
Hi, just installed ubuntu on my Samsung Galaxy TabPro S and everything seems to work fine so far...except wifi.
I managed to connect by bluetooth to my S8+ and run the updates and the wireless info script, but i have no wireless device showing.
here is the info from the script.



```
########## wireless info START ##########


Report from: 12 Apr 2018 21:36 AEST +1000


Booted last: 12 Apr 2018 00:00 AEST +1000


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Samsung Electronics Co Ltd QCA6174 802.11ac Wireless Network Adapter [144d:c135]
    Kernel driver in use: ath10k_pci


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0cf3:e300 Qualcomm Atheros Communications 
Bus 001 Device 002: ID 04e8:a00a Samsung Electronics Co., Ltd 
Bus 001 Device 005: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


ath10k_pci             45056  0
ath10k_core           352256  1 ath10k_pci
ath                    28672  1 ath10k_core
mac80211              782336  1 ath10k_core
cfg80211              614400  3 mac80211,ath,ath10k_core
wmi                    24576  0


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


bnep0     Link encap:Ethernet  HWaddr <MAC 'bnep0' [IF1]>  
          inet addr:192.168.44.132  Bcast:192.168.44.255  Mask:255.255.255.0
          inet6 addr: fe80::d6bc:639f:cab4:dcf8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1446 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:960489 (960.4 KB)  TX bytes:172974 (172.9 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77663 (77.6 KB)  TX bytes:77663 (77.6 KB)


##### iwconfig ##########################


bnep0     no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.44.1    0.0.0.0         UG    750    0        0 bnep0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 bnep0
192.168.44.0    0.0.0.0         255.255.255.0   U     750    0        0 bnep0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root       759     1  0 21:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         <MAC address>
GENERAL.TYPE:                           bt
GENERAL.NM-TYPE:                        NMDeviceBt
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         bluez
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /org/bluez/hci0/dev_D4_AE_05_B8_CB_34
GENERAL.IP-IFACE:                       bnep0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Galaxy S8+ Network
GENERAL.CON-UUID:                       20d2573b-e2f6-4bb4-b8c3-fcf0607e5b1d
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
BLUETOOTH.CAPABILITIES:                 NAP
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   20d2573b-e2f6-4bb4-b8c3-fcf0607e5b1d | Galaxy S8+ Network
IP4.ADDRESS[1]:                         192.168.44.132/24
IP4.GATEWAY:                            192.168.44.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.44.1
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.44.1
DHCP4.OPTION[5]:                        ip_address = 192.168.44.132
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.44.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.44.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.44.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1523536487
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = jason-Galaxy-TabPro-S-LTE
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.44.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.44.1
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::d6bc:639f:cab4:dcf8/64
IP6.GATEWAY:                            


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=true


##### NetworkManager profiles ###########


##### Netplan config ####################


##### iw reg get ########################


Region: Australia/Melbourne (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)


##### iwlist channels ###################


bnep0     no frequency information.


lo        no frequency information.


##### iwlist scan #######################


bnep0     Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[ath10k_pci]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-6.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
srcversion:     8D7A52EE462CD73D0445DB2
depends:        ath10k_core
intree:         Y
name:           ath10k_pci
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)


[ath10k_core]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     7F06478F5745B064BF3BC89
depends:        mac80211,cfg80211,ath
intree:         Y
name:           ath10k_core
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)


[ath]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     555BBBB9D4FCA58A05E7C0D
depends:        cfg80211
intree:         Y
name:           ath
vermagic:       4.13.0-38-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     125925493BE4168AD62F1ED
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath10k_pci]
irq_mode: 0
reset_mode: 0


[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N


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


[/etc/modprobe.d/ideapad.conf]
blacklist samsung_tabpro


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


##### dmesg #############################


[    4.435827] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[    4.437994] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[    4.721098] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c135
[    4.721101] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[    4.721753] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411
[    4.786816] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 20d869c3
[    5.404520] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    5.407753] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    5.408895] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    5.494754] ath: EEPROM regdomain: 0x5f
[    5.494755] ath: EEPROM indicates we should expect a direct regpair map
[    5.494756] ath: invalid regulatory domain/country code 0x5f
[    5.494756] ath: Invalid EEPROM contents
[    5.494763] ath10k_pci 0000:01:00.0: failed to initialise regulatory: -22


########## wireless info END ############
```


I havent used linux for years so im basically a new starter again.
Any help would be greatly appreciated.

Thanks

---

### Post by jeremy31 on 2018-04-12
Since you have the 4.13 kernel see [https://ubuntuforums.org/showthread.php?t=2384640&p=13738753#post13738753](https://ubuntuforums.org/showthread.php?t=2384640&p=13738753#post13738753)

---

### Post by jasonscottlloyd on 2018-04-12
Thanks for the reply Jeremy

after following steps from the beginning of the suggested post, i changed country codes and that gave me the wifi networks option in network-manager but it is greyed out saying device not ready. I re-ran the script and have posted output. there is some changes. I even went to the bios and made sure secure boot was not enabled but no difference.

```


########## wireless info START ##########

Report from: 13 Apr 2018 15:48 AEST +1000

Booted last: 13 Apr 2018 00:00 AEST +1000

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Samsung Electronics Co Ltd QCA6174 802.11ac Wireless Network Adapter [144d:c135]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0cf3:e300 Atheros Communications, Inc. 
Bus 001 Device 003: ID 04e8:a00a Samsung Electronics Co., Ltd 
Bus 001 Device 002: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
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

ath10k_pci             45056  0
ath10k_core           266240  1 ath10k_pci
ath                    28672  1 ath10k_core
mac80211              671744  1 ath10k_core
cfg80211              614400  3 mac80211,ath,ath10k_core
compat                 16384  6 rndis_host,usbnet,mac80211,cdc_ether,ath10k_pci,cfg80211
wmi                    24576  0

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

enp0s20f0u1 Link encap:Ethernet  HWaddr <MAC 'enp0s20f0u1' [IF1]>  
          inet addr:192.168.42.240  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::b9d1:3eec:aed7:d16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:272421 (272.4 KB)  TX bytes:119890 (119.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30373 (30.3 KB)  TX bytes:30373 (30.3 KB)

wlp1s0    Link encap:Ethernet  HWaddr <MAC 'wlp1s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

lo        no wireless extensions.

enp0s20f0u1  no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    100    0        0 enp0s20f0u1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp0s20f0u1
192.168.42.0    0.0.0.0         255.255.255.0   U     100    0        0 enp0s20f0u1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       759     1  0 15:41 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20f0u1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'enp0s20f0u1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/net/enp0s20f0u1
GENERAL.IP-IFACE:                       enp0s20f0u1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       11c0a154-8602-3fd3-9720-e8e5285050e2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        yes (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   11c0a154-8602-3fd3-9720-e8e5285050e2 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.42.240/24
IP4.GATEWAY:                            192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.240
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1523601705
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = jason-Galaxy-TabPro-S-LTE
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       requested_host_name = 1
DHCP4.OPTION[30]:                       dhcp_lease_time = 3600
DHCP4.OPTION[31]:                       requested_ntp_servers = 1
IP6.ADDRESS[1]:                         fe80::b9d1:3eec:aed7:d16/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.13.0-38-generic
GENERAL.FIRMWARE-VERSION:               WLAN.RM.4.4.1-00051-QCARMSWP-1
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

##### Netplan config ####################

##### iw reg get ########################

Region: Australia/Sydney (based on set time zone)

country 98: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 17), (N/A)
    (5250 - 5330 @ 80), (N/A, 23), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 23), (0 ms), DFS
    (5735 - 5835 @ 80), (N/A, 30), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp0s20f0u1  no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 144 : 5.72 GHz
          Channel 149 : 5.745 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp0s20f0u1  Interface doesn't support scanning.

wlp1s0    Interface doesn't support scanning : Network is down

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.13.0-38-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-6.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/firmware-4.bin
firmware:       ath10k/QCA6174/hw2.1/board-2.bin
firmware:       ath10k/QCA6174/hw2.1/board.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-5.bin
firmware:       ath10k/QCA6174/hw2.1/firmware-4.bin
firmware:       ath10k/QCA9887/hw1.0/board-2.bin
firmware:       ath10k/QCA9887/hw1.0/board.bin
firmware:       ath10k/QCA9887/hw1.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
license:        Dual BSD/GPL
description:    Driver support for Qualcomm Atheros 802.11ac WLAN PCIe/AHB devices
author:         Qualcomm Atheros
version:        backported from Linux (v4.14-rc2-0-ge19b205be43d) using backports v4.14-rc2-1-0-g8bfe0960
srcversion:     2718197D8A944E7789B0F38
depends:        ath10k_core,compat
name:           ath10k_pci
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.13.0-38-generic/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     0D2D8B06098B0F6F29ADFF3
depends:        mac80211,cfg80211,ath
name:           ath10k_core
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.13.0-38-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     E7DE70D4EB8D914C33CE5A3
depends:        cfg80211
name:           ath
vermagic:       4.13.0-38-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/4.13.0-38-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v4.14-rc2-0-ge19b205be43d) using backports v4.14-rc2-1-0-g8bfe0960
srcversion:     AF8C376C5A7BF91F8B02728
depends:        cfg80211,compat
name:           mac80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.13.0-38-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v4.14-rc2-0-ge19b205be43d) using backports v4.14-rc2-1-0-g8bfe0960
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2787BAC896593E121076D1
depends:        compat
name:           cfg80211
vermagic:       4.13.0-38-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath10k_pci]
irq_mode: 0
reset_mode: 0

[ath10k_core]
cryptmode: 0
debug_mask: 0
rawmode: N
skip_otp: N
uart_print: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: AU

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

[/etc/modprobe.d/cfg80211.conf]
options cfg80211 ieee80211_regdom=AU

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

##### dmesg #############################

[    5.314135] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:01:00.0.bin failed with error -2
[    5.314153] ath10k_pci 0000:01:00.0: Direct firmware load for ath10k/cal-pci-0000:01:00.0.bin failed with error -2
[    5.316926] ath10k_pci 0000:01:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 144d:c135
[    5.316931] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[    5.317616] ath10k_pci 0000:01:00.0: firmware ver WLAN.RM.4.4.1-00051-QCARMSWP-1 api 6 features wowlan,ignore-otp crc32 c3fd4411
[    5.385559] ath10k_pci 0000:01:00.0: failed to fetch board data for bus=pci,vendor=168c,device=003e,subsystem-vendor=144d,subsystem-device=c135 from ath10k/QCA6174/hw3.0/board-2.bin
[    5.385808] ath10k_pci 0000:01:00.0: board_file api 1 bmi_id N/A crc32 ed5f849a
[    5.644169] IPv6: ADDRCONF(NETDEV_UP): enp0s20f0u1: link is not ready
[    5.996438] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    5.999394] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[    6.000064] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[    7.012017] ath10k_pci 0000:01:00.0: suspend timed out - target pause event never came
[    7.102023] ath: EEPROM regdomain: 0x0
[    7.102024] ath: EEPROM indicates default country code should be used
[    7.102025] ath: doing EEPROM country->regdmn map search
[    7.102026] ath: country maps to regdmn code: 0x3a
[    7.102027] ath: Country alpha2 being used: US
[    7.102027] ath: Regpair used: 0x3a
[    7.109234] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[    7.135716] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    7.859597] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[    7.862570] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   10.976055] ath10k_pci 0000:01:00.0: failed to set rx-chainmask: -11, req 0x3
[   14.048586] ath10k_pci 0000:01:00.0: failed to set arp ac override parameter: -11
[   17.120658] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   17.959497] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   17.962467] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   21.216517] ath10k_pci 0000:01:00.0: failed to set rx-chainmask: -11, req 0x3
[   24.288496] ath10k_pci 0000:01:00.0: failed to set arp ac override parameter: -11
[   27.360422] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   28.165240] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   28.168281] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   31.200570] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   31.200575] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   31.281740] ath10k_pci 0000:01:00.0: Could not init core: -110
[   42.825406] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   42.828388] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   45.903344] ath10k_pci 0000:01:00.0: failed to enable adaptive qcs: -11
[   48.988653] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   49.799741] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   49.802728] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   52.839025] ath10k_pci 0000:01:00.0: failed to enable adaptive qcs: -11
[   55.916411] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   66.881380] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   66.884200] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   69.998385] ath10k_pci 0000:01:00.0: htt version request timed out
[   69.998400] ath10k_pci 0000:01:00.0: failed to setup htt: -110
[   70.078810] ath10k_pci 0000:01:00.0: Could not init core: -110
[   70.800469] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   70.803693] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   73.828416] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[   73.828434] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[   73.909331] ath10k_pci 0000:01:00.0: Could not init core: -110
[   84.852740] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   84.855660] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   87.884598] ath10k_pci 0000:01:00.0: failed to enable adaptive qcs: -11
[   90.953551] ath10k_pci 0000:01:00.0: could not suspend target (-11)
[   91.757666] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[   91.760652] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[   94.789755] ath10k_pci 0000:01:00.0: htt version request timed out
[   94.789767] ath10k_pci 0000:01:00.0: failed to setup htt: -110
[   94.872590] ath10k_pci 0000:01:00.0: Could not init core: -110
[  105.823009] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[  105.826060] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[  108.860067] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[  108.860085] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[  108.942737] ath10k_pci 0000:01:00.0: Could not init core: -110
[  109.664558] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[  109.667623] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[  112.702048] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[  112.702056] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[  112.783335] ath10k_pci 0000:01:00.0: Could not init core: -110
[  123.825749] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[  123.828735] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[  127.027410] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[  127.027432] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[  127.112130] ath10k_pci 0000:01:00.0: Could not init core: -110
[  127.835739] ath10k_pci 0000:01:00.0: Unknown eventid: 118809
[  127.838909] ath10k_pci 0000:01:00.0: Unknown eventid: 90118
[  130.866162] ath10k_pci 0000:01:00.0: failed to ping firmware: -110
[  130.866184] ath10k_pci 0000:01:00.0: failed to reset rx filter: -110
[  130.947871] ath10k_pci 0000:01:00.0: Could not init core: -110

########## wireless info END ############


```


I followed the instructions to update to 4.14 but got errors and it wouldn't install.


```

jason@jason-Galaxy-TabPro-S-LTE:~/backports-4.14$ sudo make install
  Building modules, stage 2.
  MODPOST 120 modules
  INSTALL /home/jason/backports-4.14/compat/compat.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/bcma/bcma.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/usb/cdc_ether.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/usb/cdc_ncm.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/usb/rndis_host.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/usb/usbnet.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/admtek/adm8211.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ar5523/ar5523.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath10k/ath10k_core.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath5k/ath5k.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath6kl/ath6kl_core.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath6kl/ath6kl_sdio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath6kl/ath6kl_usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath9k/ath9k.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath9k/ath9k_common.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath9k/ath9k_htc.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/carl9170/carl9170.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ath/wil6210/wil6210.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/atmel/at76c50x-usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/atmel/atmel.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/atmel/atmel_cs.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/atmel/atmel_pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/broadcom/b43/b43.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/broadcom/b43legacy/b43legacy.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/broadcom/brcm80211/brcmfmac/brcmfmac.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/broadcom/brcm80211/brcmsmac/brcmsmac.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/broadcom/brcm80211/brcmutil/brcmutil.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/cisco/airo.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/cisco/airo_cs.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/ipw2x00/ipw2100.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/ipw2x00/ipw2200.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/ipw2x00/libipw.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/iwlegacy/iwl3945.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/iwlegacy/iwl4965.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/iwlegacy/iwlegacy.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intel/iwlwifi/mvm/iwlmvm.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/orinoco.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/orinoco_cs.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/orinoco_nortel.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/orinoco_pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/orinoco_plx.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/orinoco_tmd.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/orinoco_usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/orinoco/spectrum_cs.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/p54/p54common.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/p54/p54pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/p54/p54spi.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/intersil/p54/p54usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/mac80211_hwsim.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/libertas/libertas.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/libertas/libertas_cs.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/libertas/libertas_sdio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/libertas/libertas_spi.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/libertas/usb8xxx.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/libertas_tf/libertas_tf.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/libertas_tf/libertas_tf_usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/mwifiex/mwifiex.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/mwifiex/mwifiex_pcie.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/mwifiex/mwifiex_sdio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/mwifiex/mwifiex_usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/marvell/mwl8k.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/mediatek/mt7601u/mt7601u.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2400pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2500pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2500usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2800usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt2x00usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt61pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ralink/rt2x00/rt73usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtl818x/rtl8180/rtl818x_pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtl818x/rtl8187/rtl8187.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/btcoexist/btcoexist.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8192c/rtl8192c-common.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8192ce/rtl8192ce.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8192cu/rtl8192cu.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8192de/rtl8192de.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8192ee/rtl8192ee.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8192se/rtl8192se.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8723ae/rtl8723ae.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8723be/rtl8723be.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8723com/rtl8723-common.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl8821ae/rtl8821ae.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtl_usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/rndis_wlan.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/rsi/rsi_91x.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/rsi/rsi_sdio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/rsi/rsi_usb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/st/cw1200/cw1200_core.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/st/cw1200/cw1200_wlan_sdio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/st/cw1200/cw1200_wlan_spi.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ti/wl1251/wl1251.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ti/wl1251/wl1251_spi.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ti/wl12xx/wl12xx.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ti/wl18xx/wl18xx.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ti/wlcore/wlcore.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/ti/wlcore/wlcore_sdio.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/zydas/zd1201.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/net/wireless/zydas/zd1211rw/zd1211rw.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/drivers/ssb/ssb.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/net/mac80211/mac80211.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/net/wireless/cfg80211.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/net/wireless/lib80211.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/net/wireless/lib80211_crypt_ccmp.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/net/wireless/lib80211_crypt_tkip.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  INSTALL /home/jason/backports-4.14/net/wireless/lib80211_crypt_wep.ko
At main.c:160:
- SSL error:02001002:system library:fopen:No such file or directory: bss_file.c:175
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: bss_file.c:178
sign-file: certs/signing_key.pem: No such file or directory
  DEPMOD  4.13.0-38-generic
depmod will prefer updates/ over kernel/ -- OK!
Note:
You may or may not need to update your initramfs, you should if
any of the modules installed are part of your initramfs. To add
support for your distribution to do this automatically send a
patch against "update-initramfs.sh". If your distribution does not
require this send a patch with the '/usr/bin/lsb_release -i -s'
("Ubuntu") tag for your distribution to avoid this warning.

Your backported driver modules should be installed now.
Reboot.



```


Any more help would be appreciated. 
Thanks

FWW: I did try renaming the driver files in QCA6174 folder as described in several other posts and tried downloading new drivers and replacing them in the appropriate folders but doesn't seem to have made any difference.

I really don't want to go back to windows because I caught a ransomware and lost everything that's why I changed to Ubuntu, but this is a little frustrating.

---

### Post by jasonscottlloyd on 2018-04-13
its ok im on :D
i reinstalled ubuntu fresh, updated, went through the region changes, downloaded drivers from github and installed and everything works. im so happy :D lol
thanks for pointing me in the right direction Jeremy.

---

