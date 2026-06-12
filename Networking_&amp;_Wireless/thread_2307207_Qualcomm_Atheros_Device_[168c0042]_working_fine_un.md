---
title: "Qualcomm Atheros Device [168c:0042] working fine until the internet suddenly stops"
date: 2015-12-22
forum: Networking &amp; Wireless
---

### Post by iacobus2 on 2015-12-22
I configured my wireless card with backports (backports-20151120.tar.gz) and firmware ([https://github.com/kvalo/ath10k-firmware.git](https://github.com/kvalo/ath10k-firmware.git)). And the internet works until suddenly stops. May be i have interference with bluetooth but i don't know how can i see that. Thank you for your help.

```
########## wireless info START ##########

Report from: 22 Dec 2015 22:09 CLT -0300

Booted last: 22 Dec 2015 00:00 CLT -0300

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Debian
Description:    Debian GNU/Linux testing-updates (sid)
Release:    testing-updates
Codename:    sid

##### kernel ############################

Linux 4.2.0-1-amd64 #1 SMP Debian 4.2.6-3 (2015-12-06) x86_64 unknown unknown GNU/Linux

Parameters: ro, initrd=/install/initrd.gz, quiet, rcutree.rcu_idle_gp_delay=1

##### desktop ###########################

/usr/share/xsessions/plasma

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:098a]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Qualcomm Atheros Device [168c:0042] (rev 30)
    Subsystem: Lite-On Communications Inc Device [11ad:0806]
    Kernel driver in use: ath10k_pci

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 002 Device 004: ID 1bcf:2c81 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 04ca:3015 Lite-On Technology Corp. 
Bus 002 Device 002: ID 09da:90a0 A4Tech Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: línea 192: rfkill: command not found

##### lsmod #############################

ath10k_pci             40960  0
ath10k_core           221184  1 ath10k_pci
ath                    32768  1 ath10k_core
mac80211              618496  1 ath10k_core
cfg80211              536576  3 ath,mac80211,ath10k_core
acer_wmi               20480  0
sparse_keymap          16384  1 acer_wmi
compat                 16384  3 cfg80211,mac80211,ath10k_pci
rfkill                 24576  8 cfg80211,acer_wmi,bluetooth
wmi                    20480  1 acer_wmi
video                  36864  2 i915,acer_wmi

##### interfaces ########################

source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 0  (Local Loopback)
        RX packets 142289  bytes 261083946 (248.9 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 142289  bytes 261083946 (248.9 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.15  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::ba86:87ff:fe31:b153  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1063905  bytes 1048486834 (999.9 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1187245  bytes 606916955 (578.8 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlp3s0    IEEE 802.11abgn  ESSID:"casa"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'casa' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:307   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.0.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0

##### resolv.conf #######################

nameserver 200.30.192.15
nameserver 190.160.0.11
nameserver 190.160.0.14

##### network managers ##################

Installed:

    NetworkManager

Running:

root       879     1  0 20:11 ?        00:00:08 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        Wildcat Point-LP PCI Express Root Port
GENERAL.DRIVER:                         ath10k_pci
GENERAL.DRIVER-VERSION:                 4.2.0-1-amd64
GENERAL.FIRMWARE-VERSION:               WLAN.TF.1.0-00267-1
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     casa
GENERAL.CON-UUID:                       dc76fe49-d5c5-468f-b681-2bbe363634a1
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     1 Mb/s
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   dc76fe49-d5c5-468f-b681-2bbe363634a1 | casa
IP4.ADDRESS[1]:                         192.168.0.15/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             200.30.192.15
IP4.DNS[2]:                             190.160.0.11
IP4.DNS[3]:                             190.160.0.14
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_interface_mtu = 1
DHCP4.OPTION[4]:                        requested_broadcast_address = 1
DHCP4.OPTION[5]:                        requested_time_offset = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        default_ip_ttl = 64
DHCP4.OPTION[8]:                        time_offset = 0
DHCP4.OPTION[9]:                        expiry = 1450918170
DHCP4.OPTION[10]:                       requested_wpad = 1
DHCP4.OPTION[11]:                       next_server = 192.168.0.1
DHCP4.OPTION[12]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_subnet_mask = 1
DHCP4.OPTION[15]:                       requested_domain_name = 1
DHCP4.OPTION[16]:                       routers = 192.168.0.1
DHCP4.OPTION[17]:                       ip_address = 192.168.0.15
DHCP4.OPTION[18]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[19]:                       requested_static_routes = 1
DHCP4.OPTION[20]:                       dhcp_lease_time = 86400
DHCP4.OPTION[21]:                       domain_name_servers = 200.30.192.15 190.160.0.11 190.160.0.14
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_ntp_servers = 1
DHCP4.OPTION[26]:                       requested_domain_name_servers = 1
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       network_number = 192.168.0.0
DHCP4.OPTION[29]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::ba86:87ff:fe31:b153/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/eth0
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
casa  <MAC 'casa' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  68      ***   WPA2      yes     * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/casa-550942f8-c139-42f6-9f63-85009dd7a8ee]] (600 root)
[connection] id=casa | type=wifi | permissions=user:sbv:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=casa
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/casa-dc76fe49-d5c5-468f-b681-2bbe363634a1]] (600 root)
[connection] id=casa | type=wifi | permissions=user:sbv:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=casa
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/casa]] (600 root)
[connection] id=casa | type=wifi
[wifi] ssid=casa | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Santiago (based on set time zone)

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

eth0      no frequency information.

lo        no frequency information.

wlp3s0    32 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)

wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'casa' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"casa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010b36c2e50
                    Extra: Last beacon: 68ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[ath10k_pci]
filename:       /lib/modules/4.2.0-1-amd64/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
srcversion:     EBB3D4E36DE49B7EC8057D0
depends:        ath10k_core,compat
vermagic:       4.2.0-1-amd64 SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

[ath10k_core]
filename:       /lib/modules/4.2.0-1-amd64/updates/drivers/net/wireless/ath/ath10k/ath10k_core.ko
license:        Dual BSD/GPL
description:    Core module for QCA988X PCIe devices.
author:         Qualcomm Atheros
depends:        mac80211,cfg80211,ath
vermagic:       4.2.0-1-amd64 SMP mod_unload modversions 
parm:           debug_mask:Debugging mask (uint)
parm:           uart_print:Uart target debugging (bool)
parm:           skip_otp:Skip otp failure for calibration in testmode (bool)
parm:           cryptmode:Crypto mode: 0-hardware, 1-software (uint)
parm:           rawmode:Use raw 802.11 frame datapath (bool)

[ath]
filename:       /lib/modules/4.2.0-1-amd64/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
depends:        cfg80211
vermagic:       4.2.0-1-amd64 SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.2.0-1-amd64/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
srcversion:     2C80E97047B792154BF55FA
depends:        cfg80211,compat
vermagic:       4.2.0-1-amd64 SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-1-amd64/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     23A01DB42292FFA2C48ACC7
depends:        rfkill,compat
vermagic:       4.2.0-1-amd64 SMP mod_unload modversions 
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
skip_otp: Y
uart_print: N

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

coretemp

##### modprobe options ##################

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/ath10k_pci.conf]
options ath10k_pci skip_otp=y

[/etc/modprobe.d/broadcom-sta-dkms.conf]
blacklist b43
blacklist b43legacy
blacklist b44
blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/nouveau-blacklist.conf]
blacklist nouveau

[/etc/modprobe.d/open-vm-tools-dkms.conf]
install pcnet32 /sbin/modprobe -q --ignore-install vmxnet; /sbin/modprobe -q --ignore-install pcnet32 $CMDLINE_OPTS; /bin/true;

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ath9k_htc)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 5614.996715] wlp3s0: deauthenticating from <MAC 'casa' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5619.918093] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 5624.908676] wlp3s0: authenticate with <MAC 'casa' [AC1]>
[ 5624.938479] wlp3s0: send auth to <MAC 'casa' [AC1]> (try 1/3)
[ 5624.940162] wlp3s0: authenticated
[ 5624.944055] wlp3s0: associate with <MAC 'casa' [AC1]> (try 1/3)
[ 5624.947253] wlp3s0: RX AssocResp from <MAC 'casa' [AC1]> (capab=0x431 status=0 aid=7)
[ 5624.948763] wlp3s0: associated
[ 5624.948789] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 5700.849113] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 5722.262775] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.186.132 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=37816 PROTO=TCP SPT=443 DPT=57174 WINDOW=350 RES=0x00 ACK PSH URGP=0 
[ 5722.478606] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=190.45.0.50 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=60 ID=47124 PROTO=TCP SPT=443 DPT=33712 WINDOW=288 RES=0x00 ACK PSH URGP=0 
[ 5722.511367] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.186.132 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=37958 PROTO=TCP SPT=443 DPT=57174 WINDOW=350 RES=0x00 ACK PSH URGP=0 
[ 5722.574994] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.190.93 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=6976 PROTO=TCP SPT=443 DPT=52710 WINDOW=384 RES=0x00 ACK PSH URGP=0 
[ 5722.751190] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=190.45.0.50 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=60 ID=47309 PROTO=TCP SPT=443 DPT=33712 WINDOW=288 RES=0x00 ACK PSH URGP=0 
[ 5722.846315] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.190.93 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=7031 PROTO=TCP SPT=443 DPT=52710 WINDOW=384 RES=0x00 ACK PSH URGP=0 
[ 5722.945025] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.186.132 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=38295 PROTO=TCP SPT=443 DPT=57174 WINDOW=350 RES=0x00 ACK PSH URGP=0 
[ 5723.198308] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=190.45.0.50 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=60 ID=47397 PROTO=TCP SPT=443 DPT=33712 WINDOW=288 RES=0x00 ACK PSH URGP=0 
[ 5723.294250] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.190.93 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=7303 PROTO=TCP SPT=443 DPT=52710 WINDOW=384 RES=0x00 ACK PSH URGP=0 
[ 5723.811839] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.186.132 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=38951 PROTO=TCP SPT=443 DPT=57174 WINDOW=350 RES=0x00 ACK PSH URGP=0 
[ 5745.941885] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.186.132 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=51394 PROTO=TCP SPT=443 DPT=57174 WINDOW=350 RES=0x00 ACK PSH URGP=0 
[ 5790.566257] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=111.248.145.125 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=111 ID=31485 PROTO=UDP SPT=20413 DPT=7881 LEN=273 
[ 5804.888189] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=124.85.44.172 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=112 ID=30257 PROTO=UDP SPT=25181 DPT=7881 LEN=273 
[ 5810.251360] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=82.99.109.154 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=114 ID=32172 PROTO=UDP SPT=13326 DPT=7881 LEN=273 
[ 5826.473242] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=82.221.103.244 DST=192.168.0.15 LEN=98 TOS=0x00 PREC=0x00 TTL=47 ID=46703 DF PROTO=UDP SPT=6881 DPT=7881 LEN=78 
[ 5848.672126] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=85.91.136.158 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=115 ID=38639 PROTO=UDP SPT=11968 DPT=7881 LEN=273 
[ 5867.273016] wlp3s0: deauthenticating from <MAC 'casa' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 5871.302470] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 5876.048587] wlp3s0: authenticate with <MAC 'casa' [AC1]>
[ 5876.085266] wlp3s0: send auth to <MAC 'casa' [AC1]> (try 1/3)
[ 5876.088348] wlp3s0: authenticated
[ 5876.089784] wlp3s0: associate with <MAC 'casa' [AC1]> (try 1/3)
[ 5876.093097] wlp3s0: RX AssocResp from <MAC 'casa' [AC1]> (capab=0x431 status=0 aid=7)
[ 5876.094636] wlp3s0: associated
[ 5876.094662] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 5890.577134] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=92.52.138.132 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=110 ID=30 PROTO=UDP SPT=22477 DPT=7881 LEN=111 
[ 5892.502222] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=82.221.103.244 DST=192.168.0.15 LEN=98 TOS=0x00 PREC=0x00 TTL=47 ID=55302 DF PROTO=UDP SPT=6881 DPT=7881 LEN=78 
[ 5906.889637] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=78.67.246.204 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=113 ID=6962 PROTO=UDP SPT=30419 DPT=7881 LEN=111 
[ 5952.625739] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 5963.109022] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=190.45.0.174 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=60 ID=28082 PROTO=TCP SPT=443 DPT=38820 WINDOW=330 RES=0x00 ACK PSH URGP=0 
[ 5963.380399] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=190.45.0.174 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=60 ID=28245 PROTO=TCP SPT=443 DPT=38820 WINDOW=330 RES=0x00 ACK PSH URGP=0 
[ 5985.243725] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=32811 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6006.538158] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=64.233.190.84 DST=192.168.0.15 LEN=115 TOS=0x00 PREC=0x00 TTL=48 ID=58198 PROTO=TCP SPT=443 DPT=36172 WINDOW=372 RES=0x00 ACK PSH URGP=0 
[ 6034.327739] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=76.108.190.197 DST=192.168.0.15 LEN=132 TOS=0x00 PREC=0x00 TTL=114 ID=11924 PROTO=UDP SPT=13854 DPT=7881 LEN=112 
[ 6058.846684] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=36.233.176.57 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=112 ID=24060 PROTO=UDP SPT=27589 DPT=7881 LEN=273 
[ 6078.742279] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 6093.005866] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=46.44.197.74 DST=192.168.0.15 LEN=129 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=6881 DPT=7881 LEN=109 
[ 6204.682595] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2  (repeated 4 times)
[ 6642.013751] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=78.0.238.107 DST=192.168.0.15 LEN=125 TOS=0x00 PREC=0x00 TTL=50 ID=14160 DF PROTO=UDP SPT=51413 DPT=7881 LEN=105 
[ 6708.292204] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 6709.845235] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=111.253.198.109 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=111 ID=8341 PROTO=UDP SPT=26971 DPT=7881 LEN=273 
[ 6762.518465] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=176.116.63.20 DST=192.168.0.15 LEN=132 TOS=0x00 PREC=0x00 TTL=114 ID=18166 PROTO=UDP SPT=6881 DPT=7881 LEN=112 
[ 6772.488670] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=118.241.225.192 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=111 ID=26094 PROTO=UDP SPT=17935 DPT=7881 LEN=273 
[ 6802.194362] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=82.221.103.244 DST=192.168.0.15 LEN=98 TOS=0x00 PREC=0x00 TTL=47 ID=40203 DF PROTO=UDP SPT=6881 DPT=7881 LEN=78 
[ 6803.456618] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=221.245.41.2 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=111 ID=2467 PROTO=UDP SPT=27383 DPT=7881 LEN=273 
[ 6804.760399] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=88.215.150.2 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=117 ID=4556 PROTO=UDP SPT=27017 DPT=7881 LEN=111 
[ 6819.795699] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=82.241.224.126 DST=192.168.0.15 LEN=126 TOS=0x00 PREC=0x00 TTL=107 ID=4224 PROTO=UDP SPT=22193 DPT=7881 LEN=106 
[ 6823.307145] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=89.179.122.55 DST=192.168.0.15 LEN=125 TOS=0x00 PREC=0x00 TTL=50 ID=57919 DF PROTO=UDP SPT=51413 DPT=7881 LEN=105 
[ 6834.222634] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 6835.695035] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=82.221.103.244 DST=192.168.0.15 LEN=98 TOS=0x00 PREC=0x00 TTL=47 ID=44457 DF PROTO=UDP SPT=6881 DPT=7881 LEN=78 
[ 6839.997240] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=89.179.122.55 DST=192.168.0.15 LEN=125 TOS=0x00 PREC=0x00 TTL=50 ID=59750 DF PROTO=UDP SPT=51413 DPT=7881 LEN=105 
[ 6841.482830] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=119.247.34.74 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=117 ID=19405 PROTO=UDP SPT=25188 DPT=7881 LEN=273 
[ 6885.305554] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=4599 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6889.276062] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=17002 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6893.269689] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=12100 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6897.331063] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=58619 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6901.256147] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=28416 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6905.259516] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=44346 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6960.459995] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
[ 6987.226130] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=72.76.112.254 DST=192.168.0.15 LEN=131 TOS=0x00 PREC=0x00 TTL=52 ID=39056 PROTO=UDP SPT=62348 DPT=7881 LEN=111 
[ 6994.890385] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=223.17.30.66 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=112 ID=25531 PROTO=UDP SPT=19838 DPT=7881 LEN=273 
[ 7024.170397] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=81.106.132.166 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=114 ID=9679 PROTO=UDP SPT=65535 DPT=7881 LEN=273 
[ 7086.697958] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 

########## wireless info END ############
```

This is my /var/log/syslog when the connection stops.

```
Dec 22 21:41:11 iacobus-t systemd[1]: Reloading.
Dec 22 21:41:11 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:41:11 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:41:11 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:41:11 iacobus-t systemd[1]: Reloading.
Dec 22 21:41:11 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:41:11 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:41:11 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:41:11 iacobus-t systemd[1]: Reloading.
Dec 22 21:41:11 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:41:11 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:41:11 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:41:11 iacobus-t systemd[1]: Reexecuting.
Dec 22 21:41:11 iacobus-t systemd[1]: systemd 228 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
Dec 22 21:41:11 iacobus-t systemd[1]: Detected architecture x86-64.
Dec 22 21:41:11 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:41:11 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:41:11 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:41:11 iacobus-t systemd[1]: Stopping Network Time Synchronization...
Dec 22 21:41:12 iacobus-t systemd[1]: Stopped Network Time Synchronization.
Dec 22 21:41:12 iacobus-t systemd[1]: Starting Network Time Synchronization...
Dec 22 21:41:12 iacobus-t systemd[1]: Started Network Time Synchronization.
Dec 22 21:41:12 iacobus-t systemd-timesyncd[9387]: Synchronized to time server 200.89.75.197:123 (0.debian.pool.ntp.org).
Dec 22 21:41:12 iacobus-t dbus[891]: [system] Reloaded configuration
Dec 22 21:41:31 iacobus-t systemd[1]: Reloading.
Dec 22 21:41:31 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:41:31 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:41:31 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:41:49 iacobus-t systemd[1]: Reloading.
Dec 22 21:41:49 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:41:49 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:41:49 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:14 iacobus-t kernel: [ 5449.089833] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 22 21:42:35 iacobus-t kernel: [ 5469.959418] wlp3s0: AP 70:54:d2:c9:b1:65 tries to chanswitch to same channel, ignore
Dec 22 21:42:35 iacobus-t kernel: [ 5469.960509] wlp3s0: cannot understand ECSA IE operating class 32, disconnecting
Dec 22 21:42:38 iacobus-t systemd[1]: Stopping udev Kernel Device Manager...
Dec 22 21:42:38 iacobus-t systemd[1]: Stopped udev Kernel Device Manager.
Dec 22 21:42:38 iacobus-t systemd[1]: Reloading.
Dec 22 21:42:38 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:42:38 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:42:38 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:38 iacobus-t systemd[1]: Reloading.
Dec 22 21:42:38 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:42:38 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:42:38 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:38 iacobus-t systemd[1]: Stopped udev Kernel Device Manager.
Dec 22 21:42:38 iacobus-t systemd[1]: Starting udev Kernel Device Manager...
Dec 22 21:42:38 iacobus-t systemd[1]: Started udev Kernel Device Manager.
Dec 22 21:42:38 iacobus-t kernel: [ 5472.997969] ath10k_pci 0000:03:00.0: failed to install key for vdev 0 peer 70:54:d2:c9:b1:65: -110
Dec 22 21:42:38 iacobus-t kernel: [ 5472.997975] wlp3s0: failed to remove key (0, 70:54:d2:c9:b1:65) from hardware (-110)
Dec 22 21:42:38 iacobus-t wpa_supplicant[1331]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=70:54:d2:c9:b1:65 reason=4 locally_generated=1
Dec 22 21:42:38 iacobus-t NetworkManager[879]: <warn>  Connection disconnected (reason -4)
Dec 22 21:42:38 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: completed -> disconnected
Dec 22 21:42:38 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: disconnected -> scanning
Dec 22 21:42:39 iacobus-t wpa_supplicant[1331]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387371] cfg80211: World regulatory domain updated:
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387377] cfg80211:  DFS Master region: unset
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387378] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387380] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387382] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387383] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387384] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387386] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387387] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387388] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:42:39 iacobus-t kernel: [ 5473.387389] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Dec 22 21:42:39 iacobus-t systemd[1]: Reloading.
Dec 22 21:42:39 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:42:39 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:42:39 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: SME: Trying to authenticate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.171717] wlp3s0: authenticate with 70:54:d2:c9:b1:65
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: scanning -> authenticating
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: Trying to associate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.201441] wlp3s0: send auth to 70:54:d2:c9:b1:65 (try 1/3)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.203159] wlp3s0: authenticated
Dec 22 21:42:42 iacobus-t kernel: [ 5477.204354] wlp3s0: associate with 70:54:d2:c9:b1:65 (try 1/3)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.207885] wlp3s0: RX AssocResp from 70:54:d2:c9:b1:65 (capab=0x431 status=0 aid=7)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.209401] wlp3s0: associated
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: Associated with 70:54:d2:c9:b1:65
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: associating -> associated
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: WPA: Key negotiation completed with 70:54:d2:c9:b1:65 [PTK=CCMP GTK=CCMP]
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 70:54:d2:c9:b1:65 completed [id=0 id_str=]
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Dec 22 21:42:43 iacobus-t systemd[1]: Reloading.
Dec 22 21:42:43 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:42:43 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:42:43 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:43 iacobus-t systemd[1]: Reloading.
Dec 22 21:42:43 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:42:43 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:42:43 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:43 iacobus-t systemd[1]: Started LSB: Prepare console.
Dec 22 21:43:07 iacobus-t systemd[1]: Reloading.
Dec 22 21:43:07 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:43:07 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:43:07 iacobus-t systemd[1]: Started CUPS Scheduler.




*************




Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: scanning -> authenticating
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: Trying to associate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.201441] wlp3s0: send auth to 70:54:d2:c9:b1:65 (try 1/3)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.203159] wlp3s0: authenticated
Dec 22 21:42:42 iacobus-t kernel: [ 5477.204354] wlp3s0: associate with 70:54:d2:c9:b1:65 (try 1/3)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.207885] wlp3s0: RX AssocResp from 70:54:d2:c9:b1:65 (capab=0x431 status=0 aid=7)
Dec 22 21:42:42 iacobus-t kernel: [ 5477.209401] wlp3s0: associated
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: Associated with 70:54:d2:c9:b1:65
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: associating -> associated
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: WPA: Key negotiation completed with 70:54:d2:c9:b1:65 [PTK=CCMP GTK=CCMP]
Dec 22 21:42:42 iacobus-t wpa_supplicant[1331]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 70:54:d2:c9:b1:65 completed [id=0 id_str=]
Dec 22 21:42:42 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Dec 22 21:42:43 iacobus-t systemd[1]: Reloading.
Dec 22 21:42:43 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:42:43 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:42:43 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:43 iacobus-t systemd[1]: Reloading.
Dec 22 21:42:43 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:42:43 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:42:43 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:42:43 iacobus-t systemd[1]: Started LSB: Prepare console.
Dec 22 21:43:07 iacobus-t systemd[1]: Reloading.
Dec 22 21:43:07 iacobus-t systemd[1]: squid.service: Supervising process 3593 which is not our child. We'll most likely not notice when it exits.
Dec 22 21:43:07 iacobus-t systemd[1]: Started ACPI event daemon.
Dec 22 21:43:07 iacobus-t systemd[1]: Started CUPS Scheduler.
Dec 22 21:44:20 iacobus-t kernel: [ 5575.020528] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 22 21:45:00 iacobus-t wpa_supplicant[1331]: rfkill: WLAN soft blocked
Dec 22 21:45:00 iacobus-t systemd[1]: Starting Load/Save RF Kill Switch Status...
Dec 22 21:45:00 iacobus-t kernel: [ 5614.996715] wlp3s0: deauthenticating from 70:54:d2:c9:b1:65 by local choice (Reason: 3=DEAUTH_LEAVING)
Dec 22 21:45:00 iacobus-t wpa_supplicant[1331]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=70:54:d2:c9:b1:65 reason=3 locally_generated=1
Dec 22 21:45:00 iacobus-t NetworkManager[879]: <info>  WiFi hardware radio set disabled
Dec 22 21:45:00 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Dec 22 21:45:00 iacobus-t wpa_supplicant[1331]: rfkill: WLAN soft blocked
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010582] cfg80211: World regulatory domain updated:
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010585] cfg80211:  DFS Master region: unset
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010586] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010588] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010589] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010590] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010592] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010593] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010595] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010596] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Dec 22 21:45:00 iacobus-t kernel: [ 5615.010597] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Dec 22 21:45:00 iacobus-t systemd[1]: Started Load/Save RF Kill Switch Status.
Dec 22 21:45:00 iacobus-t NetworkManager[879]: <info>  (wlp3s0): canceled DHCP transaction, DHCP client pid 4083
Dec 22 21:45:00 iacobus-t NetworkManager[879]: <info>  (wlp3s0): DHCPv4 state changed bound -> done
Dec 22 21:45:00 iacobus-t NetworkManager[879]: <info>  NetworkManager state is now CONNECTED_LOCAL
Dec 22 21:45:00 iacobus-t NetworkManager[879]: <info>  NetworkManager state is now DISCONNECTED
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Interface wlp3s0.IPv6 no longer relevant for mDNS.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fe80::ba86:87ff:fe31:b153.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Withdrawing address record for fe80::ba86:87ff:fe31:b153 on wlp3s0.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Withdrawing address record for 192.168.0.15 on wlp3s0.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Joining mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: New relevant interface wlp3s0.IPv4 for mDNS.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Registering new address record for 192.168.0.15 on wlp3s0.IPv4.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Withdrawing address record for 192.168.0.15 on wlp3s0.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 22 21:45:00 iacobus-t avahi-daemon[860]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Dec 22 21:45:01 iacobus-t dbus[891]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec 22 21:45:01 iacobus-t NetworkManager[879]: <info>  WiFi now disabled by radio killswitch
Dec 22 21:45:01 iacobus-t NetworkManager[879]: <warn>  Failed to GDBus.Error:fi.w1.wpa_supplicant1.NotConnected: This interface is not connected: disconnect.
Dec 22 21:45:01 iacobus-t systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 22 21:45:01 iacobus-t NetworkManager[879]: <warn>  Failed to GDBus.Error:fi.w1.wpa_supplicant1.NotConnected: This interface is not connected: disconnect.
Dec 22 21:45:01 iacobus-t dbus[891]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 22 21:45:01 iacobus-t systemd[1]: Started Network Manager Script Dispatcher Service.
Dec 22 21:45:01 iacobus-t nm-dispatcher: Dispatching action 'down' for wlp3s0
Dec 22 21:45:03 iacobus-t NetworkManager[879]: <info>  WiFi hardware radio set enabled
Dec 22 21:45:05 iacobus-t kernel: [ 5619.918093] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Dec 22 21:45:05 iacobus-t NetworkManager[879]: <info>  WiFi now enabled by radio killswitch
Dec 22 21:45:06 iacobus-t NetworkManager[879]: <info>  (wlp3s0) supports 5 scan SSIDs
Dec 22 21:45:06 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: starting -> ready
Dec 22 21:45:06 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 22 21:45:06 iacobus-t kernel: [ 5620.145309] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Dec 22 21:45:09 iacobus-t wpa_supplicant[1331]: wlp3s0: Reject scan trigger since one is already pending
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: ready -> inactive
Dec 22 21:45:10 iacolen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelebus-t NetworkManager[879]: <info>  Auto-activating connection 'casa'.
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): Activation: starting connection 'casa' (dc76fe49-d5c5-468f-b681-2bbe363634a1)
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  NetworkManager state is now CONNECTING
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): Activation: (wifi) access point 'casa' has security, but secrets are required.
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 22 21:45:10 iacobus-t kernel: [ 5624.908676] wlp3s0: authenticate with 70:54:d2:c9:b1:65
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): Activation: (wifi) connection 'casa' has security, and secrets exist.  No new secrets needed.
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  Config: added 'ssid' value 'casa'
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  Config: added 'scan_ssid' value '1'
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  Config: added 'auth_alg' value 'OPEN'
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  Config: added 'psk' value '<omitted>'
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  Config: set interface ap_scan to 1
Dec 22 21:45:10 iacobus-t wpa_supplicant[1331]: wlp3s0: SME: Trying to authenticate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: inactive -> authenticating
Dec 22 21:45:10 iacobus-t kernel: [ 5624.938479] wlp3s0: send auth to 70:54:d2:c9:b1:65 (try 1/3)
Dec 22 21:45:10 iacobus-t wpa_supplicant[1331]: wlp3s0: Trying to associate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 22 21:45:10 iacobus-t kernel: [ 5624.940162] wlp3s0: authenticated
Dec 22 21:45:10 iacobus-t kernel: [ 5624.944055] wlp3s0: associate with 70:54:d2:c9:b1:65 (try 1/3)
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
Dec 22 21:45:10 iacobus-t kernel: [ 5624.947253] wlp3s0: RX AssocResp from 70:54:d2:c9:b1:65 (capab=0x431 status=0 aid=7)
Dec 22 21:45:10 iacobus-t wpa_supplicant[1331]: wlp3s0: Associated with 70:54:d2:c9:b1:65
Dec 22 21:45:10 iacobus-t kernel: [ 5624.948763] wlp3s0: associated
Dec 22 21:45:10 iacobus-t kernel: [ 5624.948789] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: associating -> associated
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
Dec 22 21:45:10 iacobus-t wpa_supplicant[1331]: wlp3s0: WPA: Key negotiation completed with 70:54:d2:c9:b1:65 [PTK=CCMP GTK=CCMP]
Dec 22 21:45:10 iacobus-t wpa_supplicant[1331]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 70:54:d2:c9:b1:65 completed [id=0 id_str=]
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'casa'.
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  Activation (wlp3s0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 22 21:45:10 iacobus-t NetworkManager[879]: <info>  dhclient started with pid 18956
Dec 22 21:45:11 iacobus-t dhclient[18956]: DHCPREQUEST of 192.168.0.15 on wlp3s0 to 255.255.255.255 port 67
Dec 22 21:45:12 iacobus-t avahi-daemon[860]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::ba86:87ff:fe31:b153.
Dec 22 21:45:12 iacobus-t avahi-daemon[860]: New relevant interface wlp3s0.IPv6 for mDNS.
Dec 22 21:45:12 iacobus-t avahi-daemon[860]: Registering new address record for fe80::ba86:87ff:fe31:b153 on wlp3s0.*.
Dec 22 21:45:16 iacobus-t dhclient[18956]: DHCPREQUEST of 192.168.0.15 on wlp3s0 to 255.255.255.255 port 67
Dec 22 21:45:17 iacobus-t dhclient[18956]: DHCPACK of 192.168.0.15 from 192.168.0.1
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    address 192.168.0.15
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    plen 24 (255.255.255.0)
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    gateway 192.168.0.1
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    server identifier 192.168.0.1
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    lease time 86400
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    nameserver '200.30.192.15'
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    nameserver '190.160.0.11'
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>    nameserver '190.160.0.14'
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  (wlp3s0): DHCPv4 state changed unknown -> bound
Dec 22 21:45:17 iacobus-t avahi-daemon[860]: Joining mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 22 21:45:17 iacobus-t avahi-daemon[860]: New relevant interface wlp3s0.IPv4 for mDNS.
Dec 22 21:45:17 iacobus-t avahi-daemon[860]: Registering new address record for 192.168.0.15 on wlp3s0.IPv4.
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  (wlp3s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  NetworkManager state is now CONNECTED_LOCAL
Dec 22 21:45:17 iacobus-t dhclient[18956]: bound to 192.168.0.15 -- renewal in 39416 seconds.
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  Policy set 'casa' (wlp3s0) as default for IPv4 routing and DNS.
Dec 22 21:45:17 iacobus-t NetworkManager[879]: <info>  (wlp3s0): Activation: successful, device activated.
Dec 22 21:45:17 iacobus-t dbus[891]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec 22 21:45:17 iacobus-t systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 22 21:45:17 iacobus-t dbus[891]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 22 21:45:17 iacobus-t systemd[1]: Started Network Manager Script Dispatcher Service.


```

---

### Post by jeremy31 on 2015-12-23
See if disabling the firewall helps as your syslog messages show leaving mDNS multicast group and the firewall is blocking messages for mDNS

---

### Post by iacobus2 on 2015-12-23
Thank you for your answer. I disabled the firewall and the internet is fine. But when i enabled firewall the internet immediatly stops. Then i tried to repeat this and nothing. Internet works fine even if i have the firewall enabled.

Another strange behavior is when i start the x session and try to navigate with squid proxy (to block publicity). Always i must to restart the squid service to use the proxy because other way i can't. 

I don't had these problems with my usb-wireless. And the debian returns to works really good if i try to use again the usb-wireless.

This is my ufw status:

```
Status: active

To                         Action      From
--                         ------      ----
443/tcp                    ALLOW       Anywhere
6881/tcp                   ALLOW       Anywhere
4444/udp                   ALLOW       Anywhere
443/tcp (v6)               ALLOW       Anywhere (v6)
6881/tcp (v6)              ALLOW       Anywhere (v6)
4444/udp (v6)              ALLOW       Anywhere (v6)

443/tcp                    ALLOW OUT   Anywhere
6881/tcp                   ALLOW OUT   Anywhere
4444/udp                   ALLOW OUT   Anywhere
443/tcp (v6)               ALLOW OUT   Anywhere (v6)
6881/tcp (v6)              ALLOW OUT   Anywhere (v6)
4444/udp (v6)              ALLOW OUT   Anywhere (v6)
```

modinfo cfg80211

```
filename:       /lib/modules/4.2.0-1-amd64/updates/net/wireless/cfg80211.ko
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
alias:          net-pf-16-proto-16-family-nl80211
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     23A01DB42292FFA2C48ACC7
depends:        rfkill,compat
vermagic:       4.2.0-1-amd64 SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

```

modinfo ath10k_pci

```
filename:       /lib/modules/4.2.0-1-amd64/updates/drivers/net/wireless/ath/ath10k/ath10k_pci.ko
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
firmware:       ath10k/QCA988X/hw2.0/board-2.bin
firmware:       ath10k/QCA988X/hw2.0/board.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-5.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-4.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-3.bin
firmware:       ath10k/QCA988X/hw2.0/firmware-2.bin
firmware:       ath10k/QCA988X/hw2.0/firmware.bin
license:        Dual BSD/GPL
description:    Driver support for Atheros QCA988X PCIe devices
author:         Qualcomm Atheros
version:        backported from Linux (next-20151120-0-ga78de01) using backports backports-20151120-0-g906a6b3
srcversion:     EBB3D4E36DE49B7EC8057D0
alias:          pci:v0000168Cd00000042sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000040sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000041sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000003Csv*sd*bc*sc*i*
depends:        ath10k_core,compat
vermagic:       4.2.0-1-amd64 SMP mod_unload modversions 
parm:           irq_mode:0: auto, 1: legacy, 2: msi (default: 0) (uint)
parm:           reset_mode:0: auto, 1: warm only (default: 0) (uint)

```

dmesg |grep ath10

```
[   25.154772] ath10k_pci: unknown parameter 'skip_otp' ignored
[   25.157015] ath10k_pci 0000:03:00.0: pci irq msi-x interrupts 8 irq_mode 0 reset_mode 0
[   25.449010] ath10k_pci 0000:03:00.0: firmware: failed to load ath10k/cal-pci-0000:03:00.0.bin (-2)
[   25.449047] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/cal-pci-0000:03:00.0.bin failed with error -2
[   25.502451] ath10k_pci 0000:03:00.0: firmware: direct-loading firmware ath10k/QCA9377/hw1.0/firmware-5.bin
[   25.563966] ath10k_pci 0000:03:00.0: firmware: failed to load ath10k/QCA9377/hw1.0/board-2.bin (-2)
[   25.564002] ath10k_pci 0000:03:00.0: Direct firmware load for ath10k/QCA9377/hw1.0/board-2.bin failed with error -2
[   25.586114] ath10k_pci 0000:03:00.0: firmware: direct-loading firmware ath10k/QCA9377/hw1.0/board.bin
[   27.355800] ath10k_pci 0000:03:00.0: qca9377 hw1.0 (0x05020000, 0x003820ff sub 11ad:0806) fw WLAN.TF.1.0-00267-1 fwapi 5 bdapi 1 htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1 features ignore-otp
[   27.355804] ath10k_pci 0000:03:00.0: debug 0 debugfs 0 tracing 0 dfs 0 testmode 0
[   27.654264] ath10k_pci 0000:03:00.0 wlp3s0: renamed from wlan0
[ 4724.063382] ath10k_pci 0000:03:00.0: failed to install key for vdev 0 peer 70:54:d2:c9:b1:65: -110
[ 7838.670694] ath10k_pci 0000:03:00.0: failed to install key for vdev 0 peer 70:54:d2:c9:b1:65: -110

```


My syslog:

```
ec 23 18:37:54 iacobus-t kernel: [  839.664490] wlp3s0: associated
Dec 23 18:37:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: associating -> associated
Dec 23 18:37:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
Dec 23 18:37:54 iacobus-t wpa_supplicant[1332]: wlp3s0: WPA: Key negotiation completed with 70:54:d2:c9:b1:65 [PTK=CCMP GTK=CCMP]
Dec 23 18:37:54 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 70:54:d2:c9:b1:65 completed [id=0 id_str=]
Dec 23 18:37:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Dec 23 18:39:01 iacobus-t systemd[1]: Starting Cleanup of Temporary Directories...
Dec 23 18:39:01 iacobus-t systemd[1]: Started Cleanup of Temporary Directories.
Dec 23 18:39:54 iacobus-t kernel: [  959.688004] perf interrupt took too long (2527 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
Dec 23 19:06:37 iacobus-t kernel: [ 2561.156034] perf interrupt took too long (5095 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
Dec 23 19:17:01 iacobus-t CRON[4338]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 23 19:23:02 iacobus-t wpa_supplicant[1332]: wlp3s0: WPA: Group rekeying completed with 70:54:d2:c9:b1:65 [GTK=CCMP]
Dec 23 19:32:17 iacobus-t kernel: [ 4098.991834] usb 2-2: new high-speed USB device number 6 using xhci_hcd
Dec 23 19:32:17 iacobus-t kernel: [ 4099.120121] usb 2-2: New USB device found, idVendor=0471, idProduct=218c
Dec 23 19:32:17 iacobus-t kernel: [ 4099.120124] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Dec 23 19:32:17 iacobus-t kernel: [ 4099.120126] usb 2-2: Product: GoGear Azure
Dec 23 19:32:17 iacobus-t kernel: [ 4099.120127] usb 2-2: Manufacturer: Philips
Dec 23 19:32:17 iacobus-t kernel: [ 4099.120129] usb 2-2: SerialNumber: A68EB12A31716F45
Dec 23 19:32:17 iacobus-t mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:14.0/usb2/2-2"
Dec 23 19:32:17 iacobus-t mtp-probe: bus: 2, device: 6 was not an MTP device
Dec 23 19:32:17 iacobus-t kernel: [ 4099.283102] usb-storage 2-2:1.0: USB Mass Storage device detected
Dec 23 19:32:17 iacobus-t kernel: [ 4099.283926] scsi host4: usb-storage 2-2:1.0
Dec 23 19:32:17 iacobus-t kernel: [ 4099.284040] usbcore: registered new interface driver usb-storage
Dec 23 19:32:18 iacobus-t kernel: [ 4100.282991] scsi 4:0:0:0: Direct-Access     Philips  GoGear Azure     2.00 PQ: 0 ANSI: 0 CCS
Dec 23 19:32:18 iacobus-t kernel: [ 4100.283269] sd 4:0:0:0: Attached scsi generic sg1 type 0
Dec 23 19:32:18 iacobus-t kernel: [ 4100.283390] sd 4:0:0:0: [sdb] 8087552 1024-byte logical blocks: (8.08 GB/7.71 GiB)
Dec 23 19:32:18 iacobus-t kernel: [ 4100.283546] sd 4:0:0:0: [sdb] Write Protect is off
Dec 23 19:32:18 iacobus-t kernel: [ 4100.283549] sd 4:0:0:0: [sdb] Mode Sense: 00 c0 00 00
Dec 23 19:32:18 iacobus-t kernel: [ 4100.283689] sd 4:0:0:0: [sdb] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
Dec 23 19:32:18 iacobus-t kernel: [ 4100.284284] sd 4:0:0:0: [sdb] 8087552 1024-byte logical blocks: (8.08 GB/7.71 GiB)
Dec 23 19:32:18 iacobus-t kernel: [ 4100.285856]  sdb:
Dec 23 19:32:18 iacobus-t kernel: [ 4100.287308] sd 4:0:0:0: [sdb] 8087552 1024-byte logical blocks: (8.08 GB/7.71 GiB)
Dec 23 19:32:18 iacobus-t kernel: [ 4100.289029] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Dec 23 19:42:39 iacobus-t NetworkManager[852]: <info>  sleep requested (sleeping: no  enabled: yes)
Dec 23 19:42:39 iacobus-t NetworkManager[852]: <info>  sleeping...
Dec 23 19:42:39 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: activated -> unmanaged (reason 'sleeping') [100 10 37]
Dec 23 19:42:39 iacobus-t NetworkManager[852]: <info>  (wlp3s0): canceled DHCP transaction, DHCP client pid 2941
Dec 23 19:42:39 iacobus-t NetworkManager[852]: <info>  (wlp3s0): DHCPv4 state changed bound -> done
Dec 23 19:42:39 iacobus-t avahi-daemon[842]: Withdrawing address record for 192.168.0.15 on wlp3s0.
Dec 23 19:42:39 iacobus-t avahi-daemon[842]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 23 19:42:39 iacobus-t kernel: [ 4721.062260] wlp3s0: deauthenticating from 70:54:d2:c9:b1:65 by local choice (Reason: 3=DEAUTH_LEAVING)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.063382] ath10k_pci 0000:03:00.0: failed to install key for vdev 0 peer 70:54:d2:c9:b1:65: -110
Dec 23 19:42:43 iacobus-t kernel: [ 4724.063386] wlp3s0: failed to remove key (0, 70:54:d2:c9:b1:65) from hardware (-110)
Dec 23 19:42:43 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=70:54:d2:c9:b1:65 reason=3 locally_generated=1
Dec 23 19:42:43 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now ASLEEP
Dec 23 19:42:43 iacobus-t avahi-daemon[842]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Dec 23 19:42:43 iacobus-t avahi-daemon[842]: Withdrawing address record for fe80::ba86:87ff:fe31:b153 on wlp3s0.
Dec 23 19:42:43 iacobus-t avahi-daemon[842]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fe80::ba86:87ff:fe31:b153.
Dec 23 19:42:43 iacobus-t avahi-daemon[842]: Interface wlp3s0.IPv6 no longer relevant for mDNS.
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074608] cfg80211: World regulatory domain updated:
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074611] cfg80211:  DFS Master region: unset
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074612] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074614] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074616] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074617] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074618] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074620] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074621] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074622] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.074624] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Dec 23 19:42:43 iacobus-t dbus[853]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec 23 19:42:43 iacobus-t NetworkManager[852]: <warn>  Failed to GDBus.Error:fi.w1.wpa_supplicant1.NotConnected: This interface is not connected: disconnect.
Dec 23 19:42:43 iacobus-t systemd[1]: Reached target Sleep.
Dec 23 19:42:43 iacobus-t systemd[1]: Starting Suspend...
Dec 23 19:42:43 iacobus-t systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 23 19:42:43 iacobus-t dbus[853]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 23 19:42:43 iacobus-t systemd[1]: Started Network Manager Script Dispatcher Service.
Dec 23 19:42:43 iacobus-t nm-dispatcher: Dispatching action 'down' for wlp3s0
Dec 23 19:42:43 iacobus-t systemd-sleep[4516]: Suspending system...
Dec 23 19:42:43 iacobus-t kernel: [ 4724.346788] PM: Syncing filesystems ... done.
Dec 23 19:42:43 iacobus-t kernel: [ 4724.759574] PM: Preparing system for sleep (mem)
Dec 23 19:42:43 iacobus-t kernel: [ 4724.759725] bbswitch: enabling discrete graphics
Dec 23 19:42:48 iacobus-t kernel: [ 4724.808271] Freezing user space processes ... (elapsed 0.001 seconds) done.
Dec 23 19:42:48 iacobus-t kernel: [ 4724.810091] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
Dec 23 19:42:48 iacobus-t kernel: [ 4724.811268] PM: Suspending system (mem)
Dec 23 19:42:48 iacobus-t kernel: [ 4724.811290] Suspending console(s) (use no_console_suspend to debug)
Dec 23 19:42:48 iacobus-t kernel: [ 4724.811548] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Dec 23 19:42:48 iacobus-t kernel: [ 4724.979639] sd 0:0:0:0: [sda] Stopping disk
Dec 23 19:42:48 iacobus-t kernel: [ 4725.490063] PM: suspend of devices complete after 679.307 msecs
Dec 23 19:42:48 iacobus-t kernel: [ 4725.505931] PM: late suspend of devices complete after 15.875 msecs
Dec 23 19:42:48 iacobus-t kernel: [ 4725.508170] r8169 0000:02:00.0: System wakeup enabled by ACPI
Dec 23 19:42:48 iacobus-t kernel: [ 4725.508371] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
Dec 23 19:42:48 iacobus-t kernel: [ 4725.508562] xhci_hcd 0000:00:14.0: System wakeup enabled by ACPI
Dec 23 19:42:48 iacobus-t kernel: [ 4725.522221] PM: noirq suspend of devices complete after 16.303 msecs
Dec 23 19:42:48 iacobus-t kernel: [ 4725.522552] ACPI: Preparing to enter system sleep state S3
Dec 23 19:42:48 iacobus-t kernel: [ 4725.522891] ACPI : EC: EC stopped
Dec 23 19:42:48 iacobus-t kernel: [ 4725.522892] PM: Saving platform NVS memory
Dec 23 19:42:48 iacobus-t kernel: [ 4725.522898] Disabling non-boot CPUs ...
Dec 23 19:42:48 iacobus-t kernel: [ 4725.523132] Broke affinity for irq 53
Dec 23 19:42:48 iacobus-t kernel: [ 4725.524166] smpboot: CPU 1 is now offline
Dec 23 19:42:48 iacobus-t kernel: [ 4725.524674] Broke affinity for irq 46
Dec 23 19:42:48 iacobus-t kernel: [ 4725.524683] Broke affinity for irq 53
Dec 23 19:42:48 iacobus-t kernel: [ 4725.525715] smpboot: CPU 2 is now offline
Dec 23 19:42:48 iacobus-t kernel: [ 4725.526639] Broke affinity for irq 23
Dec 23 19:42:48 iacobus-t kernel: [ 4725.526646] Broke affinity for irq 43
Dec 23 19:42:48 iacobus-t kernel: [ 4725.526653] Broke affinity for irq 45
Dec 23 19:42:48 iacobus-t kernel: [ 4725.526656] Broke affinity for irq 46
Dec 23 19:42:48 iacobus-t kernel: [ 4725.526660] Broke affinity for irq 47
Dec 23 19:42:48 iacobus-t kernel: [ 4725.526665] Broke affinity for irq 48
Dec 23 19:42:48 iacobus-t kernel: [ 4725.526672] Broke affinity for irq 53
Dec 23 19:42:48 iacobus-t kernel: [ 4725.527725] smpboot: CPU 3 is now offline
Dec 23 19:42:48 iacobus-t kernel: [ 4725.529956] ACPI: Low-level resume complete
Dec 23 19:42:48 iacobus-t kernel: [ 4725.530024] ACPI : EC: EC started
Dec 23 19:42:48 iacobus-t kernel: [ 4725.530025] PM: Restoring platform NVS memory
Dec 23 19:42:48 iacobus-t kernel: [ 4725.532248] microcode: CPU0 microcode updated early to revision 0x22, date = 2015-09-11
Dec 23 19:42:48 iacobus-t kernel: [ 4725.532379] Enabling non-boot CPUs ...
Dec 23 19:42:48 iacobus-t kernel: [ 4725.532426] x86: Booting SMP configuration:
Dec 23 19:42:48 iacobus-t kernel: [ 4725.532427] smpboot: Booting Node 0 Processor 1 APIC 0x2
Dec 23 19:42:48 iacobus-t kernel: [ 4725.534556] microcode: CPU1 microcode updated early to revision 0x22, date = 2015-09-11
Dec 23 19:42:48 iacobus-t kernel: [ 4725.537845]  cache: parent cpu1 should not be sleeping
Dec 23 19:42:48 iacobus-t kernel: [ 4725.537984] CPU1 is up
Dec 23 19:42:48 iacobus-t kernel: [ 4725.538024] smpboot: Booting Node 0 Processor 2 APIC 0x1
Dec 23 19:42:48 iacobus-t kernel: [ 4725.542462]  cache: parent cpu2 should not be sleeping
Dec 23 19:42:48 iacobus-t kernel: [ 4725.542597] CPU2 is up
Dec 23 19:42:48 iacobus-t kernel: [ 4725.542636] smpboot: Booting Node 0 Processor 3 APIC 0x3
Dec 23 19:42:48 iacobus-t kernel: [ 4725.547080]  cache: parent cpu3 should not be sleeping
Dec 23 19:42:48 iacobus-t kernel: [ 4725.547216] CPU3 is up
Dec 23 19:42:48 iacobus-t kernel: [ 4725.550870] ACPI: Waking up from system sleep state S3
Dec 23 19:42:48 iacobus-t kernel: [ 4725.566097] xhci_hcd 0000:00:14.0: System wakeup disabled by ACPI
Dec 23 19:42:48 iacobus-t kernel: [ 4725.581970] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
Dec 23 19:42:48 iacobus-t kernel: [ 4725.582157] PM: noirq resume of devices complete after 16.212 msecs
Dec 23 19:42:48 iacobus-t kernel: [ 4725.588012] PM: early resume of devices complete after 5.594 msecs
Dec 23 19:42:48 iacobus-t kernel: [ 4725.588351] r8169 0000:02:00.0: System wakeup disabled by ACPI
Dec 23 19:42:48 iacobus-t kernel: [ 4725.589424] rtc_cmos 00:01: System wakeup disabled by ACPI
Dec 23 19:42:48 iacobus-t kernel: [ 4725.589945] sd 0:0:0:0: [sda] Starting disk
Dec 23 19:42:48 iacobus-t kernel: [ 4725.596875] r8169 0000:02:00.0 eth0: link down
Dec 23 19:42:48 iacobus-t kernel: [ 4725.625295] xhci_hcd 0000:00:14.0: port 7 resume PLC timeout
Dec 23 19:42:48 iacobus-t kernel: [ 4725.640714] xhci_hcd 0000:00:14.0: port 4 resume PLC timeout
Dec 23 19:42:48 iacobus-t kernel: [ 4725.656135] xhci_hcd 0000:00:14.0: port 1 resume PLC timeout
Dec 23 19:42:48 iacobus-t kernel: [ 4725.881778] usb 2-7: reset high-speed USB device number 4 using xhci_hcd
Dec 23 19:42:48 iacobus-t kernel: [ 4726.177579] usb 2-8: reset high-speed USB device number 5 using xhci_hcd
Dec 23 19:42:48 iacobus-t kernel: [ 4726.417401] usb 2-5: reset full-speed USB device number 3 using xhci_hcd
Dec 23 19:42:48 iacobus-t kernel: [ 4726.546996] PM: resume of devices complete after 959.934 msecs
Dec 23 19:42:48 iacobus-t kernel: [ 4726.547466] PM: Finishing wakeup.
Dec 23 19:42:48 iacobus-t kernel: [ 4726.547468] Restarting tasks ... 
Dec 23 19:42:48 iacobus-t kernel: [ 4726.547650] usb 2-2: USB disconnect, device number 6
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548247] pci_bus 0000:01: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548261] pci_bus 0000:02: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548274] pcieport 0000:00:1c.2: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 02] add_size 200000 add_align 100000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548281] pci_bus 0000:03: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548427] pcieport 0000:00:1c.3: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548430] pcieport 0000:00:1c.3: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548436] pci_bus 0000:04: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548448] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548455] pcieport 0000:00:1c.2: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548457] pcieport 0000:00:1c.2: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548460] pcieport 0000:00:1c.3: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548462] pcieport 0000:00:1c.3: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548464] pcieport 0000:00:1c.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548467] pcieport 0000:00:1c.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548475] pcieport 0000:00:1c.2: BAR 15: assigned [mem 0xa0500000-0xa06fffff 64bit pref]
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548479] pcieport 0000:00:1c.3: BAR 15: assigned [mem 0xa0700000-0xa08fffff 64bit pref]
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548483] pcieport 0000:00:1c.3: BAR 13: assigned [io  0x6000-0x6fff]
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548936] pci_bus 0000:01: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548949] pci_bus 0000:02: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.548964] pci_bus 0000:03: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.549113] pci_bus 0000:04: Allocating resources
Dec 23 19:42:48 iacobus-t kernel: [ 4726.549126] i915 0000:00:02.0: BAR 6: [??? 0x00000000 flags 0x2] has bogus alignment
Dec 23 19:42:48 iacobus-t systemd[1432]: Time has been changed
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSource
Dec 23 19:42:48 iacobus-t systemd[1]: Time has been changed
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSink
Dec 23 19:42:48 iacobus-t systemd[1]: Starting Load/Save RF Kill Switch Status...
Dec 23 19:42:48 iacobus-t systemd[1698]: Time has been changed
Dec 23 19:42:48 iacobus-t systemd[1]: bluetooth.target: Unit not needed anymore. Stopping.
Dec 23 19:42:48 iacobus-t systemd[1]: Stopped target Bluetooth.
Dec 23 19:42:48 iacobus-t kernel: [ 4726.573317] done.
Dec 23 19:42:48 iacobus-t kernel: [ 4726.574183] bbswitch: disabling discrete graphics
Dec 23 19:42:48 iacobus-t kernel: [ 4726.574194] ACPI Warning: \_SB_.PCI0.RP05.PXSX._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
Dec 23 19:42:48 iacobus-t systemd-sleep[4516]: System resumed.
Dec 23 19:42:48 iacobus-t systemd[1]: Started Suspend.
Dec 23 19:42:48 iacobus-t systemd[1]: sleep.target: Unit not needed anymore. Stopping.
Dec 23 19:42:48 iacobus-t systemd[1]: Stopped target Sleep.
Dec 23 19:42:48 iacobus-t systemd[1]: Reached target Suspend.
Dec 23 19:42:48 iacobus-t systemd[1]: suspend.target: Unit is bound to inactive unit systemd-suspend.service. Stopping, too.
Dec 23 19:42:48 iacobus-t systemd[1]: Stopped target Suspend.
Dec 23 19:42:48 iacobus-t systemd[1]: Started Run anacron jobs at resume.
Dec 23 19:42:48 iacobus-t NetworkManager[852]: <info>  wake requested (sleeping: yes  enabled: yes)
Dec 23 19:42:48 iacobus-t NetworkManager[852]: <info>  waking up...
Dec 23 19:42:48 iacobus-t NetworkManager[852]: <info>  (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Dec 23 19:42:48 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 23 19:42:48 iacobus-t kernel: [ 4726.623339] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Failed to obtain handles for "Service Changed" characteristic
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Not enough free handles to register service
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Error adding Link Loss service
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Not enough free handles to register service
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Not enough free handles to register service
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Not enough free handles to register service
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Current Time Service could not be registered
Dec 23 19:42:48 iacobus-t bluetoothd[839]: gatt-time-server: Input/output error (5)
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Not enough free handles to register service
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Not enough free handles to register service
Dec 23 19:42:48 iacobus-t bluetoothd[839]: Sap driver initialization failed.
Dec 23 19:42:48 iacobus-t bluetoothd[839]: sap-server: Operation not permitted (1)
Dec 23 19:42:49 iacobus-t kernel: [ 4728.143342] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
Dec 23 19:42:49 iacobus-t kernel: [ 4728.208766] ata1.00: configured for UDMA/133
Dec 23 19:42:49 iacobus-t systemd-udevd[4613]: inotify_add_watch(9, /dev/sdb, 10) failed: No such file or directory
Dec 23 19:42:49 iacobus-t systemd-udevd[4615]: Process '/bin/hciconfig hci0 up' failed with exit code 1.
Dec 23 19:42:49 iacobus-t systemd[1]: Started Load/Save RF Kill Switch Status.
Dec 23 19:42:49 iacobus-t systemd[1]: Reached target Bluetooth.
Dec 23 19:42:49 iacobus-t bluetoothd[839]: Endpoint registered: sender=:1.34 path=/MediaEndpoint/A2DPSource
Dec 23 19:42:49 iacobus-t bluetoothd[839]: Endpoint registered: sender=:1.34 path=/MediaEndpoint/A2DPSink
Dec 23 19:42:50 iacobus-t NetworkManager[852]: <info>  (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Dec 23 19:42:50 iacobus-t kernel: [ 4728.529222] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Dec 23 19:42:50 iacobus-t kernel: [ 4728.530855] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 19:42:50 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now DISCONNECTED
Dec 23 19:42:50 iacobus-t kernel: [ 4728.541643] r8169 0000:02:00.0 eth0: link down
Dec 23 19:42:50 iacobus-t kernel: [ 4728.541744] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 23 19:42:50 iacobus-t NetworkManager[852]: <info>  (wlp3s0) supports 5 scan SSIDs
Dec 23 19:42:50 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: starting -> ready
Dec 23 19:42:50 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 23 19:42:50 iacobus-t kernel: [ 4728.584309] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Dec 23 19:42:52 iacobus-t wpa_supplicant[1332]: wlp3s0: Reject scan trigger since one is already pending
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: ready -> inactive
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Auto-activating connection 'casa'.
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: starting connection 'casa' (dc76fe49-d5c5-468f-b681-2bbe363634a1)
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now CONNECTING
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: (wifi) access point 'casa' has security, but secrets are required.
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: (wifi) connection 'casa' has security, and secrets exist.  No new secrets needed.
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Config: added 'ssid' value 'casa'
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Config: added 'scan_ssid' value '1'
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Config: added 'auth_alg' value 'OPEN'
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Config: added 'psk' value '<omitted>'
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Config: set interface ap_scan to 1
Dec 23 19:42:54 iacobus-t wpa_supplicant[1332]: wlp3s0: SME: Trying to authenticate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 23 19:42:54 iacobus-t kernel: [ 4733.288421] wlp3s0: authenticate with 70:54:d2:c9:b1:65
Dec 23 19:42:54 iacobus-t kernel: [ 4733.318016] wlp3s0: send auth to 70:54:d2:c9:b1:65 (try 1/3)
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: inactive -> authenticating
Dec 23 19:42:54 iacobus-t wpa_supplicant[1332]: wlp3s0: Trying to associate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 23 19:42:54 iacobus-t kernel: [ 4733.319704] wlp3s0: authenticated
Dec 23 19:42:54 iacobus-t kernel: [ 4733.322188] wlp3s0: associate with 70:54:d2:c9:b1:65 (try 1/3)
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
Dec 23 19:42:54 iacobus-t kernel: [ 4733.325386] wlp3s0: RX AssocResp from 70:54:d2:c9:b1:65 (capab=0x431 status=0 aid=12)
Dec 23 19:42:54 iacobus-t wpa_supplicant[1332]: wlp3s0: Associated with 70:54:d2:c9:b1:65
Dec 23 19:42:54 iacobus-t kernel: [ 4733.326966] wlp3s0: associated
Dec 23 19:42:54 iacobus-t kernel: [ 4733.326987] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: associating -> associated
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
Dec 23 19:42:54 iacobus-t wpa_supplicant[1332]: wlp3s0: WPA: Key negotiation completed with 70:54:d2:c9:b1:65 [PTK=CCMP GTK=CCMP]
Dec 23 19:42:54 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 70:54:d2:c9:b1:65 completed [id=0 id_str=]
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'casa'.
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  Activation (wlp3s0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 23 19:42:54 iacobus-t NetworkManager[852]: <info>  dhclient started with pid 4633
Dec 23 19:42:54 iacobus-t dhclient[4633]: DHCPREQUEST of 192.168.0.15 on wlp3s0 to 255.255.255.255 port 67
Dec 23 19:42:56 iacobus-t avahi-daemon[842]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::ba86:87ff:fe31:b153.
Dec 23 19:42:56 iacobus-t avahi-daemon[842]: New relevant interface wlp3s0.IPv6 for mDNS.
Dec 23 19:42:56 iacobus-t avahi-daemon[842]: Registering new address record for fe80::ba86:87ff:fe31:b153 on wlp3s0.*.
Dec 23 19:42:57 iacobus-t dhclient[4633]: DHCPREQUEST of 192.168.0.15 on wlp3s0 to 255.255.255.255 port 67
Dec 23 19:42:58 iacobus-t dhclient[4633]: DHCPACK of 192.168.0.15 from 192.168.0.1
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    address 192.168.0.15
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    plen 24 (255.255.255.0)
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    gateway 192.168.0.1
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    server identifier 192.168.0.1
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    lease time 86400
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    nameserver '200.30.192.15'
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    nameserver '190.160.0.11'
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>    nameserver '190.160.0.14'
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>  (wlp3s0): DHCPv4 state changed unknown -> bound
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Dec 23 19:42:58 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now CONNECTED_LOCAL
Dec 23 19:42:58 iacobus-t avahi-daemon[842]: Joining mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 23 19:42:58 iacobus-t avahi-daemon[842]: New relevant interface wlp3s0.IPv4 for mDNS.
Dec 23 19:42:58 iacobus-t avahi-daemon[842]: Registering new address record for 192.168.0.15 on wlp3s0.IPv4.
Dec 23 19:42:59 iacobus-t dhclient[4633]: bound to 192.168.0.15 -- renewal in 35561 seconds.
Dec 23 19:42:59 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Dec 23 19:42:59 iacobus-t NetworkManager[852]: <info>  Policy set 'casa' (wlp3s0) as default for IPv4 routing and DNS.
Dec 23 19:42:59 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: successful, device activated.
Dec 23 19:42:59 iacobus-t dbus[853]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec 23 19:42:59 iacobus-t systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 23 19:42:59 iacobus-t dbus[853]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 23 19:42:59 iacobus-t systemd[1]: Started Network Manager Script Dispatcher Service.
Dec 23 19:42:59 iacobus-t nm-dispatcher: Dispatching action 'up' for wlp3s0
Dec 23 19:43:00 iacobus-t systemd[1]: Reloading OpenBSD Secure Shell server.
Dec 23 19:43:00 iacobus-t systemd[1]: Reloaded OpenBSD Secure Shell server.
Dec 23 19:43:00 iacobus-t systemd[1]: Reloading OpenBSD Secure Shell server.
Dec 23 19:43:00 iacobus-t systemd[1]: Reloaded OpenBSD Secure Shell server.
Dec 23 19:43:00 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:00 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:02 iacobus-t org.kde.kwalletd[1820]: kwalletd(4806): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 19:43:02 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 19:43:06 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:06 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:07 iacobus-t org.kde.kwalletd[1820]: kwalletd(4829): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 19:43:07 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 19:43:18 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:18 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:20 iacobus-t org.kde.kwalletd[1820]: kwalletd(4835): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 19:43:20 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 19:43:27 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:27 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 19:43:28 iacobus-t org.kde.kwalletd[1820]: kwalletd(4840): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 19:43:28 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 20:16:56 iacobus-t systemd-timesyncd[496]: Synchronized to time server 200.89.75.197:123 (0.debian.pool.ntp.org).
Dec 23 20:17:01 iacobus-t CRON[4918]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 23 20:23:03 iacobus-t wpa_supplicant[1332]: wlp3s0: WPA: Group rekeying completed with 70:54:d2:c9:b1:65 [GTK=CCMP]
Dec 23 20:31:53 iacobus-t kernel: [ 7668.800379] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 23 20:32:32 iacobus-t kernel: [ 7707.710392] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=106.1.182.88 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=49 ID=1773 DF PROTO=UDP SPT=8538 DPT=7881 LEN=273 
Dec 23 20:32:39 iacobus-t kernel: [ 7714.891402] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=85.227.131.234 DST=192.168.0.15 LEN=1500 TOS=0x00 PREC=0x00 TTL=109 ID=8330 DF PROTO=TCP SPT=64896 DPT=58890 WINDOW=195 RES=0x00 ACK PSH URGP=0 
Dec 23 20:32:43 iacobus-t kernel: [ 7718.989602] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=87.217.161.210 DST=192.168.0.15 LEN=1492 TOS=0x00 PREC=0x00 TTL=113 ID=9634 DF PROTO=TCP SPT=33095 DPT=35690 WINDOW=258 RES=0x00 ACK PSH URGP=0 
Dec 23 20:33:12 iacobus-t kernel: [ 7747.572306] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=200.13.137.66 DST=192.168.0.15 LEN=1500 TOS=0x00 PREC=0x00 TTL=112 ID=20336 DF PROTO=TCP SPT=62369 DPT=48220 WINDOW=260 RES=0x00 ACK PSH URGP=0 
Dec 23 20:33:59 iacobus-t kernel: [ 7794.629526] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 23 20:34:07 iacobus-t kernel: [ 7802.302308] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=203.153.72.195 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=50 ID=9206 PROTO=UDP SPT=24694 DPT=7881 LEN=273 
Dec 23 20:34:40 iacobus-t wpa_supplicant[1332]: rfkill: WLAN soft blocked
Dec 23 20:34:40 iacobus-t systemd[1]: Starting Load/Save RF Kill Switch Status...
Dec 23 20:34:40 iacobus-t kernel: [ 7835.672399] wlp3s0: deauthenticating from 70:54:d2:c9:b1:65 by local choice (Reason: 3=DEAUTH_LEAVING)
Dec 23 20:34:40 iacobus-t systemd[1]: Started Load/Save RF Kill Switch Status.
Dec 23 20:34:43 iacobus-t kernel: [ 7838.670694] ath10k_pci 0000:03:00.0: failed to install key for vdev 0 peer 70:54:d2:c9:b1:65: -110
Dec 23 20:34:43 iacobus-t kernel: [ 7838.670699] wlp3s0: failed to remove key (0, 70:54:d2:c9:b1:65) from hardware (-110)
Dec 23 20:34:43 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=70:54:d2:c9:b1:65 reason=3 locally_generated=1
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Interface wlp3s0.IPv6 no longer relevant for mDNS.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Leaving mDNS multicast group on interface wlp3s0.IPv6 with address fe80::ba86:87ff:fe31:b153.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Withdrawing address record for fe80::ba86:87ff:fe31:b153 on wlp3s0.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Withdrawing address record for 192.168.0.15 on wlp3s0.
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <info>  WiFi hardware radio set disabled
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Joining mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: New relevant interface wlp3s0.IPv4 for mDNS.
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Registering new address record for 192.168.0.15 on wlp3s0.IPv4.
Dec 23 20:34:43 iacobus-t wpa_supplicant[1332]: rfkill: WLAN soft blocked
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <info>  (wlp3s0): canceled DHCP transaction, DHCP client pid 4633
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <info>  (wlp3s0): DHCPv4 state changed bound -> done
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Withdrawing address record for 192.168.0.15 on wlp3s0.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Leaving mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 23 20:34:43 iacobus-t avahi-daemon[842]: Interface wlp3s0.IPv4 no longer relevant for mDNS.
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now CONNECTED_LOCAL
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now DISCONNECTED
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791609] cfg80211: World regulatory domain updated:
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791611] cfg80211:  DFS Master region: unset
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791612] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791614] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791615] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791616] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791618] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791619] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791620] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791621] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:34:43 iacobus-t kernel: [ 7838.791622] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <info>  WiFi now disabled by radio killswitch
Dec 23 20:34:43 iacobus-t dbus[853]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <warn>  Failed to GDBus.Error:fi.w1.wpa_supplicant1.NotConnected: This interface is not connected: disconnect.
Dec 23 20:34:43 iacobus-t NetworkManager[852]: <warn>  Failed to GDBus.Error:fi.w1.wpa_supplicant1.NotConnected: This interface is not connected: disconnect.
Dec 23 20:34:43 iacobus-t systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 23 20:34:43 iacobus-t dbus[853]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 23 20:34:43 iacobus-t systemd[1]: Started Network Manager Script Dispatcher Service.
Dec 23 20:34:43 iacobus-t nm-dispatcher: Dispatching action 'down' for wlp3s0
Dec 23 20:34:55 iacobus-t dbus[853]: [system] Activating service name='gufw.Daemon' (using servicehelper)
Dec 23 20:34:55 iacobus-t dbus[853]: [system] Successfully activated service 'gufw.Daemon'
Dec 23 20:34:59 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:34:59 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:35:00 iacobus-t org.kde.kwalletd[1820]: kwalletd(5488): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 20:35:00 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 20:35:11 iacobus-t NetworkManager[852]: <info>  WiFi hardware radio set enabled
Dec 23 20:35:11 iacobus-t systemd[1]: Starting Load/Save RF Kill Switch Status...
Dec 23 20:35:11 iacobus-t systemd[1]: Started Load/Save RF Kill Switch Status.
Dec 23 20:35:13 iacobus-t NetworkManager[852]: <info>  WiFi now enabled by radio killswitch
Dec 23 20:35:13 iacobus-t kernel: [ 7868.799547] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Dec 23 20:35:13 iacobus-t NetworkManager[852]: <info>  (wlp3s0) supports 5 scan SSIDs
Dec 23 20:35:13 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: starting -> ready
Dec 23 20:35:13 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
Dec 23 20:35:13 iacobus-t kernel: [ 7868.836451] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
Dec 23 20:35:16 iacobus-t wpa_supplicant[1332]: wlp3s0: Reject scan trigger since one is already pending
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: ready -> inactive
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Auto-activating connection 'casa'.
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: starting connection 'casa' (dc76fe49-d5c5-468f-b681-2bbe363634a1)
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now CONNECTING
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: (wifi) access point 'casa' has security, but secrets are required.
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: (wifi) connection 'casa' has security, and secrets exist.  No new secrets needed.
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Config: added 'ssid' value 'casa'
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Config: added 'scan_ssid' value '1'
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Config: added 'auth_alg' value 'OPEN'
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Config: added 'psk' value '<omitted>'
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Config: set interface ap_scan to 1
Dec 23 20:35:18 iacobus-t wpa_supplicant[1332]: wlp3s0: SME: Trying to authenticate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 23 20:35:18 iacobus-t kernel: [ 7873.542798] wlp3s0: authenticate with 70:54:d2:c9:b1:65
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: inactive -> authenticating
Dec 23 20:35:18 iacobus-t wpa_supplicant[1332]: wlp3s0: Trying to associate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 23 20:35:18 iacobus-t kernel: [ 7873.579476] wlp3s0: send auth to 70:54:d2:c9:b1:65 (try 1/3)
Dec 23 20:35:18 iacobus-t kernel: [ 7873.581193] wlp3s0: authenticated
Dec 23 20:35:18 iacobus-t kernel: [ 7873.581717] wlp3s0: associate with 70:54:d2:c9:b1:65 (try 1/3)
Dec 23 20:35:18 iacobus-t kernel: [ 7873.584906] wlp3s0: RX AssocResp from 70:54:d2:c9:b1:65 (capab=0x431 status=0 aid=13)
Dec 23 20:35:18 iacobus-t wpa_supplicant[1332]: wlp3s0: Associated with 70:54:d2:c9:b1:65
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: authenticating -> associated
Dec 23 20:35:18 iacobus-t kernel: [ 7873.586382] wlp3s0: associated
Dec 23 20:35:18 iacobus-t kernel: [ 7873.586406] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
Dec 23 20:35:18 iacobus-t wpa_supplicant[1332]: wlp3s0: WPA: Key negotiation completed with 70:54:d2:c9:b1:65 [PTK=CCMP GTK=CCMP]
Dec 23 20:35:18 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 70:54:d2:c9:b1:65 completed [id=0 id_str=]
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: (wifi) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'casa'.
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  Activation (wlp3s0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 23 20:35:18 iacobus-t NetworkManager[852]: <info>  dhclient started with pid 5758
Dec 23 20:35:18 iacobus-t dhclient[5758]: DHCPREQUEST of 192.168.0.15 on wlp3s0 to 255.255.255.255 port 67
Dec 23 20:35:20 iacobus-t avahi-daemon[842]: Joining mDNS multicast group on interface wlp3s0.IPv6 with address fe80::ba86:87ff:fe31:b153.
Dec 23 20:35:20 iacobus-t avahi-daemon[842]: New relevant interface wlp3s0.IPv6 for mDNS.
Dec 23 20:35:20 iacobus-t avahi-daemon[842]: Registering new address record for fe80::ba86:87ff:fe31:b153 on wlp3s0.*.
Dec 23 20:35:22 iacobus-t dhclient[5758]: DHCPREQUEST of 192.168.0.15 on wlp3s0 to 255.255.255.255 port 67
Dec 23 20:35:23 iacobus-t dhclient[5758]: DHCPACK of 192.168.0.15 from 192.168.0.1
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    address 192.168.0.15
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    plen 24 (255.255.255.0)
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    gateway 192.168.0.1
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    server identifier 192.168.0.1
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    lease time 86400
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    nameserver '200.30.192.15'
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    nameserver '190.160.0.11'
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>    nameserver '190.160.0.14'
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  (wlp3s0): DHCPv4 state changed unknown -> bound
Dec 23 20:35:23 iacobus-t avahi-daemon[842]: Joining mDNS multicast group on interface wlp3s0.IPv4 with address 192.168.0.15.
Dec 23 20:35:23 iacobus-t avahi-daemon[842]: New relevant interface wlp3s0.IPv4 for mDNS.
Dec 23 20:35:23 iacobus-t avahi-daemon[842]: Registering new address record for 192.168.0.15 on wlp3s0.IPv4.
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  (wlp3s0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now CONNECTED_LOCAL
Dec 23 20:35:23 iacobus-t dhclient[5758]: bound to 192.168.0.15 -- renewal in 39366 seconds.
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  NetworkManager state is now CONNECTED_GLOBAL
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  Policy set 'casa' (wlp3s0) as default for IPv4 routing and DNS.
Dec 23 20:35:23 iacobus-t NetworkManager[852]: <info>  (wlp3s0): Activation: successful, device activated.
Dec 23 20:35:23 iacobus-t dbus[853]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
Dec 23 20:35:23 iacobus-t systemd[1]: Starting Network Manager Script Dispatcher Service...
Dec 23 20:35:23 iacobus-t dbus[853]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Dec 23 20:35:23 iacobus-t systemd[1]: Started Network Manager Script Dispatcher Service.
Dec 23 20:35:23 iacobus-t nm-dispatcher: Dispatching action 'up' for wlp3s0
Dec 23 20:35:24 iacobus-t systemd[1]: Reloading OpenBSD Secure Shell server.
Dec 23 20:35:24 iacobus-t systemd[1]: Reloaded OpenBSD Secure Shell server.
Dec 23 20:35:25 iacobus-t systemd[1]: Reloading OpenBSD Secure Shell server.
Dec 23 20:35:25 iacobus-t systemd[1]: Reloaded OpenBSD Secure Shell server.
Dec 23 20:35:26 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:35:26 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:35:27 iacobus-t org.kde.kwalletd[1820]: kwalletd(5927): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 20:35:27 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 20:35:34 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:35:34 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:35:35 iacobus-t org.kde.kwalletd[1820]: kwalletd(5943): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 20:35:35 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 20:35:39 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:35:39 iacobus-t org.kde.kwalletd[1820]: QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Dec 23 20:35:40 iacobus-t org.kde.kwalletd[1820]: kwalletd(5949): Communication problem with  "kwalletd" , it probably crashed.
Dec 23 20:35:40 iacobus-t org.kde.kwalletd[1820]: Error message was:  "org.freedesktop.DBus.Error.NoReply" : " "Message recipient disconnected from message bus without replying" "
Dec 23 20:46:30 iacobus-t kernel: [ 8545.089926] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=184.170.99.26 DST=192.168.0.15 LEN=129 TOS=0x00 PREC=0x00 TTL=109 ID=22460 PROTO=UDP SPT=6881 DPT=7881 LEN=109 
Dec 23 20:47:38 iacobus-t kernel: [ 8612.661119] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=85.227.131.234 DST=192.168.0.15 LEN=1500 TOS=0x00 PREC=0x00 TTL=109 ID=7310 DF PROTO=TCP SPT=64896 DPT=33430 WINDOW=195 RES=0x00 ACK PSH URGP=0 
Dec 23 20:48:07 iacobus-t kernel: [ 8642.180504] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=66.102.87.81 DST=192.168.0.15 LEN=344 TOS=0x00 PREC=0x00 TTL=114 ID=16165 PROTO=UDP SPT=53371 DPT=7881 LEN=324 
Dec 23 20:48:29 iacobus-t kernel: [ 8664.120592] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=171.5.247.35 DST=192.168.0.15 LEN=293 TOS=0x00 PREC=0x00 TTL=107 ID=25662 PROTO=UDP SPT=22031 DPT=7881 LEN=273 
Dec 23 20:48:41 iacobus-t kernel: [ 8675.835708] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 23 20:50:47 iacobus-t kernel: [ 8801.171842] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=119.188.12.9 DST=192.168.0.15 LEN=86 TOS=0x00 PREC=0x00 TTL=48 ID=58007 PROTO=UDP SPT=65005 DPT=7881 LEN=66 
Dec 23 20:50:47 iacobus-t kernel: [ 8801.663906] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 23 20:51:54 iacobus-t kernel: [ 8868.527039] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=117.217.177.233 DST=192.168.0.15 LEN=323 TOS=0x00 PREC=0x00 TTL=111 ID=19761 PROTO=UDP SPT=17005 DPT=7881 LEN=303 
Dec 23 20:52:53 iacobus-t kernel: [ 8927.594533] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 23 20:55:40 iacobus-t kernel: [ 9094.073275] [UFW BLOCK] IN=wlp3s0 OUT= MAC=b8:86:87:31:b1:53:10:5f:49:c7:b3:b7:08:00 SRC=119.188.12.9 DST=192.168.0.15 LEN=86 TOS=0x00 PREC=0x00 TTL=48 ID=0 DF PROTO=UDP SPT=65005 DPT=7881 LEN=66 
Dec 23 20:57:05 iacobus-t kernel: [ 9179.353400] [UFW BLOCK] IN=wlp3s0 OUT= MAC=01:00:5e:00:00:01:10:5f:49:c7:b3:b7:08:00 SRC=192.168.0.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 PROTO=2 
Dec 23 20:57:58 iacobus-t kernel: [ 9232.037827] wlp3s0: AP 70:54:d2:c9:b1:65 tries to chanswitch to same channel, ignore
Dec 23 20:57:58 iacobus-t kernel: [ 9232.038906] wlp3s0: cannot understand ECSA IE operating class 32, disconnecting
Dec 23 20:57:58 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-DISCONNECTED bssid=70:54:d2:c9:b1:65 reason=4 locally_generated=1
Dec 23 20:57:58 iacobus-t NetworkManager[852]: <warn>  Connection disconnected (reason -4)
Dec 23 20:57:58 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: completed -> disconnected
Dec 23 20:57:58 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: disconnected -> scanning
Dec 23 20:57:58 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=CORE type=WORLD
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251496] cfg80211: World regulatory domain updated:
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251499] cfg80211:  DFS Master region: unset
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251500] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251502] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251503] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251504] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251505] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251507] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251508] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251509] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
Dec 23 20:57:58 iacobus-t kernel: [ 9232.251510] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
Dec 23 20:58:02 iacobus-t wpa_supplicant[1332]: wlp3s0: SME: Trying to authenticate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 23 20:58:02 iacobus-t kernel: [ 9236.035615] wlp3s0: authenticate with 70:54:d2:c9:b1:65
Dec 23 20:58:02 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: scanning -> authenticating
Dec 23 20:58:02 iacobus-t kernel: [ 9236.065266] wlp3s0: send auth to 70:54:d2:c9:b1:65 (try 1/3)
Dec 23 20:58:02 iacobus-t kernel: [ 9236.069765] wlp3s0: authenticated
Dec 23 20:58:02 iacobus-t kernel: [ 9236.070890] wlp3s0: associate with 70:54:d2:c9:b1:65 (try 1/3)
Dec 23 20:58:02 iacobus-t kernel: [ 9236.074260] wlp3s0: RX AssocResp from 70:54:d2:c9:b1:65 (capab=0x431 status=0 aid=11)
Dec 23 20:58:02 iacobus-t kernel: [ 9236.075845] wlp3s0: associated
Dec 23 20:58:02 iacobus-t wpa_supplicant[1332]: wlp3s0: Trying to associate with 70:54:d2:c9:b1:65 (SSID='casa' freq=2417 MHz)
Dec 23 20:58:02 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: authenticating -> associating
Dec 23 20:58:02 iacobus-t wpa_supplicant[1332]: wlp3s0: Associated with 70:54:d2:c9:b1:65
Dec 23 20:58:02 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: associating -> associated
Dec 23 20:58:02 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: associated -> 4-way handshake
Dec 23 20:58:02 iacobus-t wpa_supplicant[1332]: wlp3s0: WPA: Key negotiation completed with 70:54:d2:c9:b1:65 [PTK=CCMP GTK=CCMP]
Dec 23 20:58:02 iacobus-t wpa_supplicant[1332]: wlp3s0: CTRL-EVENT-CONNECTED - Connection to 70:54:d2:c9:b1:65 completed [id=0 id_str=]
Dec 23 20:58:02 iacobus-t NetworkManager[852]: <info>  (wlp3s0): supplicant interface state: 4-way handshake -> completed
<

```

---

