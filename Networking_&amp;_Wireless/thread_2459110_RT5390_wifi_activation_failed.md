---
title: "RT5390 wifi activation failed"
date: 2021-03-10
forum: Networking &amp; Wireless
---

### Post by carabian on 2021-03-10
Hi,

Just installed Ubuntu on a old laptop. Everything was working well until the wifi suddenly whent down. Now I'm not able to get connection via wireless, but Ethernet is still working.

I ran the script from the attached post, here it is the results:
```


########## wireless info START ##########

Report from: 11 Mar 2021 00:08 CET +0100

Booted last: 11 Mar 2021 00:00 CET +0100

Script from: 25 Jan 2020 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal

##### kernel ############################

Linux 5.8.0-44-generic #50~20.04.1-Ubuntu SMP Wed Feb 10 21:07:30 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL810xE PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    DeviceName: Realtek Gbe Lan Connection
    Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:1670]

##### lsusb #############################

Bus 002 Device 003: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### secure boot #######################

'mokutil' is not installed (package "mokutil").

##### lsmod #############################

rt2800pci              16384  0
rt2800mmio             24576  1 rt2800pci
rt2800lib             131072  2 rt2800mmio,rt2800pci
rt2x00pci              16384  1 rt2800pci
rt2x00mmio             16384  2 rt2800mmio,rt2800pci
rt2x00lib              65536  5 rt2x00mmio,rt2x00pci,rt2800mmio,rt2800pci,rt2800lib
mac80211              905216  3 rt2x00pci,rt2x00lib,rt2800lib
cfg80211              778240  2 rt2x00lib,mac80211
eeprom_93cx6           16384  1 rt2800pci
libarc4                16384  1 mac80211
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi_bmof               16384  0
wmi                    32768  2 hp_wmi,wmi_bmof

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'eno1' [IF1]> brd <MAC address>
    altname enp3s0
    inet 192.168.1.42/24 brd 192.168.1.255 scope global dynamic noprefixroute eno1
       valid_lft 85808sec preferred_lft 85808sec
    inet6 fe80::64f8:c433:63ff:52cd/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlp2s0' [IF2]> brd <MAC address>

##### iwconfig ##########################

lo        no wireless extensions.

eno1      no wireless extensions.

wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

default via 192.168.1.1 dev eno1 proto dhcp metric 100 
169.254.0.0/16 dev eno1 scope link metric 1000 
192.168.1.0/24 dev eno1 proto kernel scope link src 192.168.1.42 metric 100 

##### resolv.conf #######################

[777 root '/etc/resolv.conf' -> '../run/systemd/resolve/stub-resolv.conf']

nameserver 127.0.0.53
options edns0 trust-ad
search home

##### network managers ##################

Installed:

    NetworkManager

Running:

root         672       1  0 Mar10 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         eno1
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/2
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 5.8.0-44-generic
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'eno1' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               4 (full)
GENERAL.IP6-CONNECTIVITY:               3 (limited)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/eno1
GENERAL.IP-IFACE:                       eno1
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       5ac03147-8098-3b2b-adc9-85e1b60c790f
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/5
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               yes
INTERFACE-FLAGS.CARRIER:                yes
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.1.42/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.1.1, mt = 100
IP4.ROUTE[2]:                           dst = 192.168.1.0/24, nh = 0.0.0.0, mt = 100
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          home
DHCP4.OPTION[1]:                        dhcp_lease_time = 86400
DHCP4.OPTION[2]:                        domain_name = home
DHCP4.OPTION[3]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[4]:                        expiry = 1615503493
DHCP4.OPTION[5]:                        host_name = pau-PC
DHCP4.OPTION[6]:                        ip_address = 192.168.1.42
DHCP4.OPTION[7]:                        next_server = 192.168.1.1
DHCP4.OPTION[8]:                        requested_broadcast_address = 1
DHCP4.OPTION[9]:                        requested_domain_name = 1
DHCP4.OPTION[10]:                       requested_domain_name_servers = 1
DHCP4.OPTION[11]:                       requested_domain_search = 1
DHCP4.OPTION[12]:                       requested_host_name = 1
DHCP4.OPTION[13]:                       requested_interface_mtu = 1
DHCP4.OPTION[14]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[15]:                       requested_nis_domain = 1
DHCP4.OPTION[16]:                       requested_nis_servers = 1
DHCP4.OPTION[17]:                       requested_ntp_servers = 1
DHCP4.OPTION[18]:                       requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[19]:                       requested_root_path = 1
DHCP4.OPTION[20]:                       requested_routers = 1
DHCP4.OPTION[21]:                       requested_static_routes = 1
DHCP4.OPTION[22]:                       requested_subnet_mask = 1
DHCP4.OPTION[23]:                       requested_time_offset = 1
DHCP4.OPTION[24]:                       requested_wpad = 1
DHCP4.OPTION[25]:                       routers = 192.168.1.1
DHCP4.OPTION[26]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[27]:                       wpad = 

IP6.ADDRESS[1]:                         fe80::64f8:c433:63ff:52cd/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = fe80::/64, nh = ::, mt = 100
IP6.ROUTE[2]:                           dst = ff00::/8, nh = ::, mt = 256, table=255
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/1
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   5ac03147-8098-3b2b-adc9-85e1b60c790f | Wired connection 1

GENERAL.DEVICE:                         wlp2s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.DBUS-PATH:                      /org/freedesktop/NetworkManager/Devices/3
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT5390 Wireless 802.11n 1T/1R PCIe (U98Z077.00 Half-size Mini PCIe Card)
GENERAL.DRIVER:                         rt2800pci
GENERAL.DRIVER-VERSION:                 5.8.0-44-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp2s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.IP4-CONNECTIVITY:               1 (none)
GENERAL.IP6-CONNECTIVITY:               1 (none)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlp2s0
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
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
INTERFACE-FLAGS.UP:                     yes
INTERFACE-FLAGS.LOWER-UP:               no
INTERFACE-FLAGS.CARRIER:                no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
WIFI-PROPERTIES.MESH:                   yes
WIFI-PROPERTIES.IBSS-RSN:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/2
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   3ad33c13-118f-4860-968b-283cb757f02b | MiFibra-BE9A

SSID          BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 
MiFibra-BE9A  <MAC 'MiFibra-BE9A' [AC2]>  Infra  1     2412 MHz  130 Mbit/s  49      &#9602;&#9604;__  WPA2      no             
MiFibra-BE9A  <MAC 'MiFibra-BE9A' [AC1]>  Infra  1     2412 MHz  130 Mbit/s  22      &#9602;___  WPA2      no             
MiFibra-6C7E  <MAC 'MiFibra-6C7E' [AC3]>  Infra  11    2462 MHz  130 Mbit/s  15      &#9602;___  WPA2      no             

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager config #############

[[/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf]]
[connection]
wifi.powersave = 3

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile
[ifupdown]
managed=false
[device]
wifi.scan-rand-mac-address=no

[[/usr/lib/NetworkManager/conf.d/10-dns-resolved.conf]]
[main]
dns=systemd-resolved

[[/usr/lib/NetworkManager/conf.d/10-globally-managed-devices.conf]]
[keyfile]
unmanaged-devices=*,except:type:wifi,except:type:gsm,except:type:cdma

[[/usr/lib/NetworkManager/conf.d/20-connectivity-ubuntu.conf]]
[connectivity]
uri=http://connectivity-check.ubuntu.com/

[[/usr/lib/NetworkManager/conf.d/no-mac-addr-change.conf]]
[device-mac-addr-change-wifi]
match-device=driver:rtl8723bs,driver:rtl8189es,driver:r8188eu,driver:8188eu,driver:eagle_sdio,driver:wl
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/MiFibra-BE9A.nmconnection]] (600 root)
[connection] id=MiFibra-BE9A | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=MiFibra-BE9A
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Europe/Madrid (based on set time zone)

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

eno1      no frequency information.

wlp2s0    14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eno1      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp2s0    Scan completed :
          Cell 01 - Address: <MAC 'MiFibra-BE9A' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"MiFibra-BE9A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000f3e5814d
                    Extra: Last beacon: 27976ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC 'MiFibra-BE9A' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"MiFibra-BE9A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000063081e3183
                    Extra: Last beacon: 1132ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MiFibra-6C7E' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"MiFibra-6C7E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000075792ff183
                    Extra: Last beacon: 452ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rt2800pci]
filename:       /lib/modules/5.8.0-44-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800pci.ko
license:        GPL
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
retpoline:      Y
intree:         Y
name:           rt2800pci
vermagic:       5.8.0-44-generic SMP mod_unload 
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2800mmio]
filename:       /lib/modules/5.8.0-44-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
depends:        rt2x00mmio,rt2x00lib,rt2800lib
retpoline:      Y
intree:         Y
name:           rt2800mmio
vermagic:       5.8.0-44-generic SMP mod_unload 

[rt2800lib]
filename:       /lib/modules/5.8.0-44-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2800lib
vermagic:       5.8.0-44-generic SMP mod_unload 
parm:           watchdog:Enable watchdog to detect tx/rx hangs and reset hardware if detected (bool)

[rt2x00pci]
filename:       /lib/modules/5.8.0-44-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
depends:        rt2x00lib,mac80211
retpoline:      Y
intree:         Y
name:           rt2x00pci
vermagic:       5.8.0-44-generic SMP mod_unload 

[rt2x00mmio]
filename:       /lib/modules/5.8.0-44-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
depends:        rt2x00lib
retpoline:      Y
intree:         Y
name:           rt2x00mmio
vermagic:       5.8.0-44-generic SMP mod_unload 

[rt2x00lib]
filename:       /lib/modules/5.8.0-44-generic/kernel/drivers/net/wireless/ralink/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
depends:        mac80211,cfg80211
retpoline:      Y
intree:         Y
name:           rt2x00lib
vermagic:       5.8.0-44-generic SMP mod_unload 

[mac80211]
filename:       /lib/modules/5.8.0-44-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
depends:        cfg80211,libarc4
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       5.8.0-44-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/5.8.0-44-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       5.8.0-44-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rt2800pci]
nohwcrypt: N

[rt2800lib]
watchdog: N

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

[ 1477.594055] r8169 0000:03:00.0 eno1: Link is Down
[ 1649.890216] wlp2s0: authenticate with <MAC 'MiFibra-BE9A' [AC2]>
[ 1649.894920] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 1/3)
[ 1649.927346] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 2/3)
[ 1649.958800] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 3/3)
[ 1649.987843] wlp2s0: authentication with <MAC 'MiFibra-BE9A' [AC2]> timed out
[ 1650.138764] wlp2s0: authenticate with <MAC 'MiFibra-BE9A' [AC1]>
[ 1650.142871] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 1/3)
[ 1650.180776] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 2/3)
[ 1650.236223] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 3/3)
[ 1650.268941] wlp2s0: authentication with <MAC 'MiFibra-BE9A' [AC1]> timed out
[ 1651.475161] wlp2s0: authenticate with <MAC 'MiFibra-BE9A' [AC2]>
[ 1651.481660] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 1/3)
[ 1651.516864] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 2/3)
[ 1651.553593] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 3/3)
[ 1651.594475] wlp2s0: authentication with <MAC 'MiFibra-BE9A' [AC2]> timed out
[ 1652.650641] wlp2s0: authenticate with <MAC 'MiFibra-BE9A' [AC1]>
[ 1652.655656] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 1/3)
[ 1652.686169] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 2/3)
[ 1652.727180] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 3/3)
[ 1652.763928] wlp2s0: authentication with <MAC 'MiFibra-BE9A' [AC1]> timed out
[ 1654.866788] wlp2s0: authenticate with <MAC 'MiFibra-BE9A' [AC2]>
[ 1654.874850] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 1/3)
[ 1654.902382] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 2/3)
[ 1654.951210] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 3/3)
[ 1655.042799] wlp2s0: authentication with <MAC 'MiFibra-BE9A' [AC2]> timed out
[ 1899.976404] r8169 0000:03:00.0 eno1: Link is Up - 100Mbps/Full - flow control rx/tx
[ 2285.850914] wlp2s0: authenticate with <MAC 'MiFibra-BE9A' [AC2]>
[ 2285.855071] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 1/3)
[ 2285.893158] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 2/3)
[ 2285.942152] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC2]> (try 3/3)
[ 2285.976455] wlp2s0: authentication with <MAC 'MiFibra-BE9A' [AC2]> timed out
[ 2297.095406] wlp2s0: authenticate with <MAC 'MiFibra-BE9A' [AC1]>
[ 2297.102610] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 1/3)
[ 2297.152609] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 2/3)
[ 2297.193166] wlp2s0: send auth to <MAC 'MiFibra-BE9A' [AC1]> (try 3/3)
[ 2297.216115] wlp2s0: authentication with <MAC 'MiFibra-BE9A' [AC1]> timed out

########## wireless info END ############

```

I can provide the .txt file if needed.

I'm really new using linux, so be patient and thanks!

---

