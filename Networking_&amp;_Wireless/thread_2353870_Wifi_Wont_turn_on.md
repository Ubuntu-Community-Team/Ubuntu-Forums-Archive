---
title: "Wifi Wont turn on"
date: 2017-02-25
forum: Networking &amp; Wireless
---

### Post by baileyt380 on 2017-02-25
HI 

I've just installed Ubuntu (16.04.02) on to my Laptop and the wifi won't turn on I've tried updating drivers and updates etc.
If i open network manger and click on wifi and press the turn on button it will simple turn on for half a second and switch back.... so frustrating !

I have an Alineware r3 17 

Apparently these are the drivers i need 

                                                             **Intel 8260/7265/3165/7260/3160 WiFi Driver**

                                                                                                                                                                                                                                                                                                      [B]                                                                 source: DELL support 

[/B]If the problem lies with divers could someone also tell me the right way to about installing them correctly as im new the Linux 

Many Thanks !

---

### Post by RobGoss on 2017-02-25
How did you try installing the proprietary drivers provided by Ubuntu **Software & Updates **?

Did you have a internet connected were you wired?

---

### Post by wildmanne39 on 2017-02-25
*Thread moved to **Networking & Wireless**.*

---

### Post by wildmanne39 on 2017-02-25
Click on the wireless script in my signature and follow the directions for running it and posting the file it creates here using code tags.

---

### Post by baileyt380 on 2017-02-26
i tried downloading the drivers off the killer wireless website as my Ethernet still works and extracting them too /lib/firmware/ auth10k/ QACA6174 and replacing the files in the folder

---

### Post by baileyt380 on 2017-02-26
wildmanne Ive run your script and its created an txt file with a bunch of information is there anything specific in the file that would be a massive help to people trying to help me :)

---

### Post by jeremy31 on 2017-02-26
Please post the entire file using code tags.  I am not sure what wireless device you have as your original post shows Intel models but now you have installed Atheros firmware.  It shouldn't cause any issues.

---

### Post by baileyt380 on 2017-02-26
```
########## wireless info START ##########

Report from: 26 Feb 2017 13:00 GMT +0000

Booted last: 26 Feb 2017 00:00 GMT +0000

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-39-generic #42~16.04.1-Ubuntu SMP Mon Feb 20 15:06:07 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

3b:00.0 Ethernet controller [0200]: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller [1969:e0a1] (rev 10)
    Subsystem: Device [0707:2400]
    Kernel driver in use: alx

3c:00.0 Network controller [0280]: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter [168c:003e] (rev 32)
    Subsystem: Bigfoot Networks, Inc. QCA6174 802.11ac Wireless Network Adapter [1a56:1535]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 1bcf:2b8c Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0cf3:e301 Atheros Communications, Inc. 
Bus 001 Device 002: ID 187c:0528 Alienware Corporation 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: dell-rbtn: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               16384  0
sparse_keymap          16384  1 dell_wmi
dell_smbios            16384  1 dell_wmi
ath10k_pci             45056  0
ath10k_core           335872  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              761856  1 ath10k_core
cfg80211              581632  3 mac80211,ath,ath10k_core
mxm_wmi                16384  1 nouveau
wmi                    16384  3 dell_wmi,mxm_wmi,nouveau
video                  40960  3 dell_wmi,nouveau,i915

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp59s0   Link encap:Ethernet  HWaddr <MAC 'enp59s0' [IF1]>  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ec5f:321a:c349:5298/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7699 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18861415 (18.8 MB)  TX bytes:751108 (751.1 KB)
          Interrupt:16 

wlp60s0   Link encap:Ethernet  HWaddr <MAC 'wlp60s0' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

enp59s0   no wireless extensions.

lo        no wireless extensions.

wlp60s0   IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 enp59s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp59s0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 enp59s0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      1087     1  0 12:52 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp59s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Killer E2400 Gigabit Ethernet Controller
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp59s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.4/0000:3b:00.0/net/enp59s0
GENERAL.IP-IFACE:                       enp59s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       14b629b2-c944-3103-b909-19ee8109a16c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   14b629b2-c944-3103-b909-19ee8109a16c | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.12/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        host_name = thomas-Alienware-17-R3
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1488199996
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 86400
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.0.12
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.0.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::ec5f:321a:c349:5298/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp60s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        QCA6174 802.11ac Wireless Network Adapter
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlp60s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.5/0000:3c:00.0/net/wlp60s0
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

##### iw reg get ########################

Region: Europe/London (based on set time zone)

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

enp59s0   no frequency information.

lo        no frequency information.

wlp60s0   32 channels in total; available frequencies :
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

##### iwlist scan #######################

enp59s0   Interface doesn't support scanning.

wlp60s0   Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
firmware:       ath10k/QCA9377/hw1.0/board.bin
firmware:       ath10k/QCA9377/hw1.0/firmware-5.bin
firmware:       ath10k/QCA6174/hw3.0/board-2.bin
firmware:       ath10k/QCA6174/hw3.0/board.bin
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
srcversion:     8DB6E266EF9D63EC5C2B007
depends:        ath10k_core
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for Qualcomm Atheros 802.11ac wireless LAN cards.
author:         Qualcomm Atheros
srcversion:     663DAB23AD4CFA103833EE1
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.8.0-39-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     5C13C1638BE3EDB7B93F6A7
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     9AF49B72127065FCF655D6A
depends:        cfg80211
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.8.0-39-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-39-generic SMP mod_unload modversions 
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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

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

[   12.316832] ath10k_pci 0000:3c:00.0: enabling device (0000 -> 0002)
[   12.317772] ath10k_pci 0000:3c:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[   12.593621] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/pre-cal-pci-0000:3c:00.0.bin failed with error -2
[   12.593630] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/cal-pci-0000:3c:00.0.bin failed with error -2
[   12.595914] ath10k_pci 0000:3c:00.0: Direct firmware load for ath10k/QCA6174/hw3.0/firmware-5.bin failed with error -2
[   12.595916] ath10k_pci 0000:3c:00.0: could not fetch firmware file 'ath10k/QCA6174/hw3.0/firmware-5.bin': -2
[   12.599565] ath10k_pci 0000:3c:00.0: qca6174 hw3.2 target 0x05030000 chip_id 0x00340aff sub 1a56:1535
[   12.599566] ath10k_pci 0000:3c:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[   12.599995] ath10k_pci 0000:3c:00.0: firmware ver WLAN.RM.2.0-00180-QCARMSWPZ-1 api 4 features wowlan,ignore-otp,no-4addr-pad crc32 75dee6c5
[   12.667247] ath10k_pci 0000:3c:00.0: board_file api 2 bmi_id N/A crc32 6fc88fe7
[   12.898506] IPv6: ADDRCONF(NETDEV_UP): enp59s0: link is not ready (repeated 2 times)
[   14.787068] ath10k_pci 0000:3c:00.0: htt-ver 3.26 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[   14.870364] ath: EEPROM regdomain: 0x69
[   14.870365] ath: EEPROM indicates we should expect a direct regpair map
[   14.870366] ath: Country alpha2 being used: 00
[   14.870366] ath: Regpair used: 0x69
[   14.874187] ath10k_pci 0000:3c:00.0 wlp60s0: renamed from wlan0
[   14.902888] IPv6: ADDRCONF(NETDEV_UP): wlp60s0: link is not ready
[   41.389451] alx 0000:3b:00.0 enp59s0: NIC Up: 100 Mbps Full
[   41.389679] IPv6: ADDRCONF(NETDEV_CHANGE): enp59s0: link becomes ready

########## wireless info END ############
```

---

### Post by RobGoss on 2017-02-26
You may also want to use the ** code tags **when posting your results

---

### Post by jeremy31 on 2017-02-26
Try the keyboard shortcut to see if it will enable wireless, usually FN + some other key

---

### Post by baileyt380 on 2017-02-26
Any suggestion based on the text file?

---

### Post by jeremy31 on 2017-02-26
My first suggestion is based on the text file as it contained
```
0: dell-rbtn: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```
The dell-rbtn is a module that is loaded that should allow the FN combo to toggle the blocks on the wifi card.  There is a chance that blacklisting that module may work
```
echo "blacklist dell-rbtn" | sudo tee /etc/modprobe.d/dell-rbtn.conf
```

Reboot, if it still doesn't work, post the model of the laptop as I know of at least one Dell model needs a command entered in the grub file for that module to work correctly

---

### Post by baileyt380 on 2017-02-26
It worked!!!!!!!!!!!!! im not sure how but it did !!!!!!!!!!!!! this has been bugging me all weekend ! Thank you!
Any ideas of why that was happening ?

---

### Post by jeremy31 on 2017-02-26
Probably a bug in the code for dell-rbtn that only affects a few laptops so nobody has filed a bug report to indicate an issue with it.

---

### Post by baileyt380 on 2017-02-26
Thanks Again!

---

