---
title: "Wifi problems on my old laptop"
date: 2016-06-03
forum: Networking &amp; Wireless
---

### Post by carlostefano on 2016-06-03
Hello,

I have just installed the last version of Xubuntu on my laptop hp compaq 6710b. I can get the internet connection only with the cable but not using the wifi. 

The system still shows the list of the wifi connections in the area, but if I try to choose one of them and put a password anyway I don't get a connection.

Hope someone can help me about it.

Greetings,

carlostefano

---

### Post by Hadaka on 2016-06-03
Hi ,please post the output of..
```
lspci -nnk | grep 0280
rfkill list all
```
thanks.

---

### Post by carlostefano on 2016-06-03
Hello, thank you!

Here is the result:

10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ rfkill list all

---

### Post by Hadaka on 2016-06-03
Hi , please open a terminal ctrl/alt/t then copy and paste 
one line at a time..ignore any file not found or error..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall linux-firmware
```
boot and test wireless

*If still no wireless then,.,
Please open a terminal ctrl/alt/t then Copy and paste the following command
and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is **wireless-info.txt**
Next.
From your directory please copy,paste and post the **wireless-info.txt**
thanks.

---

### Post by carlostefano on 2016-06-03
```
########## wireless info START ##########

Report from: 03 Jun 2016 19:25 CEST +0200

Booted last: 03 Jun 2016 00:00 CEST +0200

Script from: 26 May 2016 21:56 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company PRO/Wireless 3945ABG [Golan] Network Connection [103c:135c]
    Kernel driver in use: iwl3945

18:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Hewlett-Packard Company 6710b [103c:30c0]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hp-gps: GPS
    Soft blocked: yes
    Hard blocked: yes

##### lsmod #############################

iwl3945                69632  0
iwlegacy              102400  1 iwl3945
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
mac80211              737280  2 iwl3945,iwlegacy
cfg80211              565248  3 iwl3945,iwlegacy,mac80211
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

ens1      Link encap:Ethernet  HWaddr <MAC 'ens1' [IF1]>  
          inet addr:192.168.0.188  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::b3b5:894c:60bd:23eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70630 (70.6 KB)  TX bytes:43132 (43.1 KB)
          Interrupt:18 

wlp16s0   Link encap:Ethernet  HWaddr <MAC 'wlp16s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1130 (1.1 KB)  TX bytes:1550 (1.5 KB)

##### iwconfig ##########################

lo        no wireless extensions.

ens1      no wireless extensions.

wlp16s0   IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 ens1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ens1
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 ens1

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       599     1  0 19:17 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         ens1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetLink BCM5787M Gigabit Ethernet PCI Express (6710b)
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'ens1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:18:00.0/net/ens1
GENERAL.IP-IFACE:                       ens1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       a4a44095-4f5b-4254-81d7-7ac44d8e18d4
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a4a44095-4f5b-4254-81d7-7ac44d8e18d4 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.0.188/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1465061006
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       dhcp_lease_time = 86400
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.0.188
DHCP4.OPTION[16]:                       broadcast_address = 192.168.0.255
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_ntp_servers = 1
DHCP4.OPTION[20]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[21]:                       routers = 192.168.0.1
DHCP4.OPTION[22]:                       domain_name_servers = 192.168.0.1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[25]:                       network_number = 192.168.0.0
DHCP4.OPTION[26]:                       requested_host_name = 1
DHCP4.OPTION[27]:                       dhcp_server_identifier = 192.168.0.1
IP6.ADDRESS[1]:                         fe80::b3b5:894c:60bd:23eb/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlp16s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 3945ABG [Golan] Network Connection
GENERAL.DRIVER:                         iwl3945
GENERAL.DRIVER-VERSION:                 4.4.0-21-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp16s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:10:00.0/net/wlp16s0
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   877a5000-b79c-4204-898a-2558f0bceca1 | NETWORK - ONE

SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
NETWORK - ONE      <MAC 'NETWORK - ONE' [AC1]>  Infra  9     2452 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA2      no        
Vodafone-WiFi      <MAC 'Vodafone-WiFi' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  --        no        
Vodafone-30455040  <MAC 'Vodafone-30455040' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2      no        
Vodafone-WiFi      <MAC 'Vodafone-WiFi' [AC4]>  Infra  100   5500 MHz  54 Mbit/s  34      &#9602;&#9604;__  --        no        
Vodafone-30455040  <MAC 'Vodafone-30455040' [AN5]>  Infra  100   5500 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2      no        

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

[[/etc/NetworkManager/system-connections/NETWORK - ONE]] (600 root)
[connection] id=NETWORK - ONE | type=wifi | permissions=user:hp6710b:;
[wifi] mac-address=<MAC 'wlp16s0' [IF2]> | mac-address-blacklist= | ssid=NETWORK - ONE
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Rome (based on set time zone)

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

lo        no frequency information.

ens1      no frequency information.

wlp16s0   32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

ens1      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:5.5 GHz (Channel 100)

wlp16s0   Scan completed :
          Cell 01 - Address: <MAC 'NETWORK - ONE' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:on
                    ESSID:"NETWORK - ONE"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000115fe936f32
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Vodafone-30455040' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Vodafone-30455040"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006a371cc4
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Vodafone-WiFi' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"Vodafone-WiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006a373297
                    Extra: Last beacon: 40ms ago
          Cell 04 - Address: <MAC 'Vodafone-WiFi' [AC4]>
                    Channel:100
                    Frequency:5.5 GHz (Channel 100)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"Vodafone-WiFi"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000067a4d219
                    Extra: Last beacon: 1208ms ago

##### module infos ######################

[iwl3945]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     E80BE10D520D11A1B26EC87
depends:        iwlegacy,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/4.4.0-21-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     464AE65E4E6FD2825462A97
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

[mac80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     A882F4FE63500846E1C859E
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-21-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     00D8DA6D3B739DDD31FFF50
depends:        
intree:         Y
vermagic:       4.4.0-21-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 1

[iwlegacy]
bt_coex_active: Y
led_mode: 0

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   90.522959] wlp16s0: authenticate with <MAC 'NETWORK - ONE' [AC1]>
[   90.523029] wlp16s0: send auth to <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[   90.524843] wlp16s0: authenticated
[   90.532849] wlp16s0: associate with <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[   90.535953] wlp16s0: RX AssocResp from <MAC 'NETWORK - ONE' [AC1]> (capab=0x431 status=0 aid=2)
[   90.537315] wlp16s0: associated
[  100.539232] wlp16s0: deauthenticating from <MAC 'NETWORK - ONE' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  125.595565] IPv6: ADDRCONF(NETDEV_UP): wlp16s0: link is not ready
[  217.368890] wlp16s0: authenticate with <MAC 'NETWORK - ONE' [AC1]>
[  217.370662] wlp16s0: send auth to <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[  217.372495] wlp16s0: authenticated
[  217.380051] wlp16s0: associate with <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[  217.383250] wlp16s0: RX AssocResp from <MAC 'NETWORK - ONE' [AC1]> (capab=0x431 status=0 aid=2)
[  217.384792] wlp16s0: associated
[  217.384851] IPv6: ADDRCONF(NETDEV_CHANGE): wlp16s0: link becomes ready
[  217.392896] wlp16s0: deauthenticated from <MAC 'NETWORK - ONE' [AC1]> (Reason: 9=STA_REQ_ASSOC_WITHOUT_AUTH)
[  225.840799] wlp16s0: authenticate with <MAC 'NETWORK - ONE' [AC1]>
[  225.843010] wlp16s0: send auth to <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[  225.845058] wlp16s0: authenticated
[  225.852059] wlp16s0: associate with <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[  225.855144] wlp16s0: RX AssocResp from <MAC 'NETWORK - ONE' [AC1]> (capab=0x431 status=0 aid=2)
[  225.856562] wlp16s0: associated
[  225.862472] wlp16s0: deauthenticated from <MAC 'NETWORK - ONE' [AC1]> (Reason: 9=STA_REQ_ASSOC_WITHOUT_AUTH)
[  250.921067] IPv6: ADDRCONF(NETDEV_UP): wlp16s0: link is not ready
[  281.068145] wlp16s0: authenticate with <MAC 'NETWORK - ONE' [AC1]>
[  281.068218] wlp16s0: send auth to <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[  281.069993] wlp16s0: authenticated
[  281.076066] wlp16s0: associate with <MAC 'NETWORK - ONE' [AC1]> (try 1/3)
[  281.079182] wlp16s0: RX AssocResp from <MAC 'NETWORK - ONE' [AC1]> (capab=0x431 status=0 aid=2)
[  281.080524] wlp16s0: associated
[  281.080567] IPv6: ADDRCONF(NETDEV_CHANGE): wlp16s0: link becomes ready
[  281.086654] wlp16s0: deauthenticated from <MAC 'NETWORK - ONE' [AC1]> (Reason: 9=STA_REQ_ASSOC_WITHOUT_AUTH)
[  306.139230] IPv6: ADDRCONF(NETDEV_UP): wlp16s0: link is not ready
[  390.344016] tg3 0000:18:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update (repeated 3 times)
[  390.465076] tg3 0000:18:00.0 eth0: Tigon3 [partno(none) rev b002] (PCI Express) MAC address <MAC 'ens1' [IF1]>
[  390.465081] tg3 0000:18:00.0 eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[  390.465084] tg3 0000:18:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[  390.465087] tg3 0000:18:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[  390.467208] tg3 0000:18:00.0 ens1: renamed from eth0
[  390.490735] IPv6: ADDRCONF(NETDEV_UP): ens1: link is not ready (repeated 4 times)
[  392.802928] tg3 0000:18:00.0 ens1: Link is up at 1000 Mbps, full duplex
[  392.802954] tg3 0000:18:00.0 ens1: Flow control is on for TX and on for RX
[  392.803845] IPv6: ADDRCONF(NETDEV_CHANGE): ens1: link becomes ready

########## wireless info END ############
```

---

### Post by Hadaka on 2016-06-03
Hi, thanks for the wireless report.
Please remove if possible.. hp-gps: GPS

then your wifi ssid has spaces and that creates connection problems..
please access your router and chang your ssid from.. NETWORK - ONE to .. NETWORK-ONE

Next your regulatory country code is not set and currently at 00
please copy and paste to correct..
```
sudo iw reg set IT
sudo sed -i 's/^REG.*=$/&IT/' /etc/default/crda
```
remove wired connection,boot and test wireless

*If still no wireless please run a new wireless diagnostic report..
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```

---

### Post by carlostefano on 2016-06-03
Thank you...sorry, what is hp-gps? How can I find or change it?

---

### Post by carlostefano on 2016-06-04
It works now!!!!!!!  Thank you !!!!!!!!!!!!!!!!!!!))))))))))))

---

### Post by Hadaka on 2016-06-04
Great ! glad it is working. Please take the time
to mark your thread solved...by going to your 
first post,click Thread Tools and then click Solved.
Were you able to remove the GPS or did changing
the router ssid get it working??
thanks.

---

### Post by carlostefano on 2016-06-04
I didn't even understood what was that GPS thing (my laptop has a GPS??). I changed the SSID removing the spaces and also set the country code in the way that you suggested me. After the reboot I was able to make the wifi working ).

---

### Post by bodzio2k on 2016-10-17
Hadaka can You please take a look at my wireless info, unfortunatelly I still cannot connect using wireless connection...
```


########## wireless info START ##########


Report from: 17 Oct 2016 20:47 CEST +0200


Booted last: 17 Oct 2016 00:00 CEST +0200


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 4.4.0-43-generic #63-Ubuntu SMP Wed Oct 12 13:50:36 UTC 2016 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu (from ~/.dmrc)


##### lspci #############################


02:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Hewlett-Packard Company NX7300 laptop [103c:30a2]
    Kernel driver in use: b44


10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company PRO/Wireless 3945ABG [Golan] Network Connection [103c:135c]
    Kernel driver in use: iwl3945


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hp-gps: GPS
    Soft blocked: yes
    Hard blocked: yes
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


iwl3945                65536  0
iwlegacy               90112  1 iwl3945
mac80211              659456  2 iwl3945,iwlegacy
cfg80211              499712  3 iwl3945,iwlegacy,mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
ssb                    57344  1 b44
wmi                    20480  1 hp_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ea84:2aeb:d08c:117b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:272366 (272.3 KB)  TX bytes:74361 (74.3 KB)
          Interrupt:16 


wlp16s0   Link encap:Ethernet  HWaddr <MAC 'wlp16s0' [IF2]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlp16s0   IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search mydomain.example


##### network managers ##################


Installed:


    NetworkManager


Running:


root       678     1  0 20:44 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4401-B0 100Base-TX (NX7300 laptop)
GENERAL.DRIVER:                         b44
GENERAL.DRIVER-VERSION:                 2.0
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/ssb0:0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Pinka-n over the cable
GENERAL.CON-UUID:                       72060874-148c-4b9d-9b57-8356575ad9e3
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   72060874-148c-4b9d-9b57-8356575ad9e3 | Pinka-n over the cable
IP4.ADDRESS[1]:                         192.168.0.15/24
IP4.GATEWAY:                            192.168.0.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.0.1
IP4.DOMAIN[1]:                          mydomain.example
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.0.1
DHCP4.OPTION[5]:                        ip_address = 192.168.0.15
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.0.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.0.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 37800
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.0.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 21600
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = mydomain.example
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1476773179
DHCP4.OPTION[21]:                       host_name = Ealing
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.0.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.0.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 43200
IP6.ADDRESS[1]:                         fe80::ea84:2aeb:d08c:117b/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlp16s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        PRO/Wireless 3945ABG [Golan] Network Connection
GENERAL.DRIVER:                         iwl3945
GENERAL.DRIVER-VERSION:                 4.4.0-43-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp16s0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:10:00.0/net/wlp16s0
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
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   84bf3101-3bc5-472a-b3a3-c21a6029daeb | Pinka-n
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   03d5858d-5abd-4f79-a425-5426e7806d9d | Pinka


SSID                    BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Pinka                   <MAC 'Pinka' [AC5]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
Amedeus Asus            <MAC 'Amedeus Asus' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA2       no        
--                      <MAC '' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  50      &#9602;&#9604;__  --         no        
Internet Domowy-0E4398  <MAC 'Internet Domowy-0E4398' [AC6]>  Infra  12    2467 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
Moje Wifi               <MAC 'Moje Wifi' [AC4]>  Infra  9     2452 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
TP-LINK_B6D703          <MAC 'TP-LINK_B6D703' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  24      &#9602;___  WPA2       no        
Pietruszka              <MAC 'Pietruszka' [AC7]>  Infra  10    2457 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2  no        
WLAN1-000203            <MAC 'WLAN1-000203' [AC8]>  Infra  1     2412 MHz  54 Mbit/s  12      &#9602;___  WPA2       no        


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


[[/etc/NetworkManager/system-connections/fiber_biber]] (600 root)
[connection] id=fiber_biber | type=wifi | permissions=user:bodzio:;
[wifi] mac-address=<MAC 'wlp16s0' [IF2]> | mac-address-blacklist= | ssid=fiber_biber
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Pinka]] (600 root)
[connection] id=Pinka | type=wifi | permissions=user:bodzio:;
[wifi] mac-address=<MAC 'wlp16s0' [IF2]> | mac-address-blacklist= | ssid=Pinka
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Pinka-n]] (600 root)
[connection] id=Pinka-n | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp16s0' [IF2]> | mac-address-blacklist= | mtu=1500 | ssid=Pinka-n
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Warsaw (based on set time zone)


country IT: DFS-ETSI
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 27), (0 ms), DFS
    (57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


wlp16s0   32 channels in total; available frequencies :
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
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


Channel occupancy:


      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)


wlp16s0   Scan completed :
          Cell 01 - Address: <MAC 'Amedeus Asus' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"Amedeus Asus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e55077fc40
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001e550776140
                    Extra: Last beacon: 2852ms ago
          Cell 03 - Address: <MAC 'TP-LINK_B6D703' [AC3]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"TP-LINK_B6D703"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005884a868509
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'Moje Wifi' [AC4]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Moje Wifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b0c5fbe9aa
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Pinka' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-26 dBm  
                    Encryption key:on
                    ESSID:"Pinka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002c68f5ff
                    Extra: Last beacon: 32ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC 'Internet Domowy-0E4398' [AC6]>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Internet Domowy-0E4398"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000931155b14c
                    Extra: Last beacon: 2520ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'Pietruszka' [AC7]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Pietruszka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b2baa780593
                    Extra: Last beacon: 2500ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'WLAN1-000203' [AC8]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"WLAN1-000203"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000014f338c41a
                    Extra: Last beacon: 32ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


[iwl3945]
filename:       /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     E80BE10D520D11A1B26EC87
depends:        iwlegacy,mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)


[iwlegacy]
filename:       /lib/modules/4.4.0-43-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     464AE65E4E6FD2825462A97
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)


[mac80211]
filename:       /lib/modules/4.4.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/4.4.0-43-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-43-generic SMP mod_unload modversions 686 


##### module parameters #################


[iwl3945]
antenna: 0
disable_hw_scan: 1
fw_restart: 1
swcrypto: 0


[iwlegacy]
bt_coex_active: Y
led_mode: 0


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
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


[/etc/modprobe.d/iwl3945.conf]
options iwl3945 swcrypto=0
options iwl3945 disable_hw_scan=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


##### dmesg #############################


[   14.816110] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.816116] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   14.816207] iwl3945 0000:10:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.871022] iwl3945 0000:10:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   14.871031] iwl3945 0000:10:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   15.051093] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.054186] iwl3945 0000:10:00.0 wlp16s0: renamed from wlan0
[   32.343702] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready (repeated 2 times)
[   32.475428] IPv6: ADDRCONF(NETDEV_UP): wlp16s0: link is not ready
[   35.804255] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[   35.804269] b44 ssb0:0 eth0: Flow control is off for TX and off for RX
[   35.804415] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   42.341114] iwl3945 0000:10:00.0: loaded firmware version 15.32.2.9
[   42.412411] IPv6: ADDRCONF(NETDEV_UP): wlp16s0: link is not ready (repeated 2 times)
[   66.804165] b44 ssb0:0 eth0: Link is down
[   74.756316] wlp16s0: authenticate with <MAC 'Pinka' [AC5]>
[   74.758098] wlp16s0: send auth to <MAC 'Pinka' [AC5]> (try 1/3)
[   74.759333] wlp16s0: authenticated
[   74.764144] wlp16s0: associate with <MAC 'Pinka' [AC5]> (try 1/3)
[   74.765864] wlp16s0: RX AssocResp from <MAC 'Pinka' [AC5]> (capab=0x411 status=18 aid=5632)
[   74.765874] wlp16s0: <MAC 'Pinka' [AC5]> denied association (code=18)
[   77.913010] wlp16s0: authenticate with <MAC 'Pinka' [AC5]>
[   77.916227] wlp16s0: send auth to <MAC 'Pinka' [AC5]> (try 1/3)
[   77.917424] wlp16s0: authenticated
[   77.920146] wlp16s0: associate with <MAC 'Pinka' [AC5]> (try 1/3)
[   77.921900] wlp16s0: RX AssocResp from <MAC 'Pinka' [AC5]> (capab=0x411 status=18 aid=5632)
[   77.921904] wlp16s0: <MAC 'Pinka' [AC5]> denied association (code=18)
[   81.473033] wlp16s0: authenticate with <MAC 'Pinka' [AC5]>
[   81.476982] wlp16s0: send auth to <MAC 'Pinka' [AC5]> (try 1/3)
[   81.478609] wlp16s0: authenticated
[   81.480125] wlp16s0: associate with <MAC 'Pinka' [AC5]> (try 1/3)
[   81.482737] wlp16s0: RX AssocResp from <MAC 'Pinka' [AC5]> (capab=0x411 status=18 aid=5632)
[   81.482743] wlp16s0: <MAC 'Pinka' [AC5]> denied association (code=18)
[   85.533010] wlp16s0: authenticate with <MAC 'Pinka' [AC5]>
[   85.534401] wlp16s0: send auth to <MAC 'Pinka' [AC5]> (try 1/3)
[   85.535518] wlp16s0: authenticated
[   85.536176] wlp16s0: associate with <MAC 'Pinka' [AC5]> (try 1/3)
[   85.538199] wlp16s0: RX AssocResp from <MAC 'Pinka' [AC5]> (capab=0x411 status=18 aid=0)
[   85.538205] wlp16s0: <MAC 'Pinka' [AC5]> denied association (code=18)
[  103.351587] IPv6: ADDRCONF(NETDEV_UP): wlp16s0: link is not ready
[  117.804261] b44 ssb0:0 eth0: Link is up at 100 Mbps, full duplex
[  117.804275] b44 ssb0:0 eth0: Flow control is off for TX and off for RX


########## wireless info END ############



```

---

### Post by praseodym on 2016-10-17
Which of the networks do you want to connect to? Try "ignoring" IPv6 in the network-manager settings.

---

