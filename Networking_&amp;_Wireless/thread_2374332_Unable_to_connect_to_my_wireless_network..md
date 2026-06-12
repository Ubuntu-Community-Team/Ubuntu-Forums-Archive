---
title: "Unable to connect to my wireless network."
date: 2017-10-14
forum: Networking &amp; Wireless
---

### Post by srobison62 on 2017-10-14
I moved my computer into my office so I could hardwire it and follow the info on the sticky.  WHen I try to connect to wireless it just times out.  Wifi info below:

```
########## wireless info START ##########

Report from: 14 Oct 2017 11:27 CDT -0500

Booted last: 14 Oct 2017 00:00 CDT -0500

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty

##### kernel ############################

Linux 4.10.0-19-generic #21-Ubuntu SMP Thu Apr 6 17:04:57 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:14.0 Bridge [0680]: NVIDIA Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MCP51 Ethernet Controller [1462:7350]
    Kernel driver in use: forcedeth

##### lsusb #############################

Bus 001 Device 005: ID 148f:7601 Ralink Technology, Corp. MT7601U Wireless Adapter
Bus 001 Device 004: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

mac80211              782336  1 mt7601u
cfg80211              602112  2 mac80211,mt7601u

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s20: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp0s20' [IF1]> brd <MAC address>
    inet 192.168.1.203/24 brd 192.168.1.255 scope global dynamic enp0s20
       valid_lft 85574sec preferred_lft 85574sec
    inet6 fe80::127b:1f28:2e32:e414/64 scope link 
       valid_lft forever preferred_lft forever
3: wlxc83a35dc81ad: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether <MAC 'wlxc83a35dc81ad' [IF2]> brd <MAC address>

##### iwconfig ##########################

enp0s20   no wireless extensions.

lo        no wireless extensions.

wlxc83a35dc81ad  IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

default via 192.168.1.1 dev enp0s20 proto static metric 100 
169.254.0.0/16 dev enp0s20 scope link metric 1000 
192.168.1.0/24 dev enp0s20 proto kernel scope link src 192.168.1.203 metric 100 

##### resolv.conf #######################

nameserver 127.0.0.53

##### network managers ##################

Installed:

    NetworkManager

Running:

root       622     1  0 11:12 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp0s20
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         NVIDIA Corporation
GENERAL.PRODUCT:                        MCP51 Ethernet Controller
GENERAL.DRIVER:                         forcedeth
GENERAL.DRIVER-VERSION:                 0.64
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp0s20' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.0/net/enp0s20
GENERAL.IP-IFACE:                       enp0s20
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       9a5152ce-0213-3c79-b870-0feae7cd69a0
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     1000 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   9a5152ce-0213-3c79-b870-0feae7cd69a0 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.203/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
IP4.DOMAIN[1]:                          tendawifi.com
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.1.1
DHCP4.OPTION[5]:                        ip_address = 192.168.1.203
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = tendawifi.com
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1508084081
DHCP4.OPTION[21]:                       host_name = emma-MS-7350
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 192.168.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400
IP6.ADDRESS[1]:                         fe80::127b:1f28:2e32:e414/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlxc83a35dc81ad
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         MediaTek
GENERAL.PRODUCT:                        802.11 n WLAN
GENERAL.DRIVER:                         mt7601u
GENERAL.DRIVER-VERSION:                 4.10.0-19-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlxc83a35dc81ad' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:0b.1/usb1/1-8/1-8.3/1-8.3:1.0/net/wlxc83a35dc81ad
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
WIFI-PROPERTIES.ADHOC:                  no
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   d3eb6d2d-3882-40f7-96a6-4826f5778589 | Robison1

SSID       BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Robison1   <MAC 'Robison1' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
--         <MAC '--' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  49      &#9602;&#9604;__  WPA2       no        
2WIRE278   <MAC '2WIRE278' [AC2]>  Infra  5     2432 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
NETGEAR46  <MAC 'NETGEAR46' [AC1]>  Infra  8     2447 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA2       no        

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

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Robison1]] (600 root)
[connection] id=Robison1 | type=wifi | permissions=user:emma:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=Robison1
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

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

enp0s20   no frequency information.

lo        no frequency information.

wlxc83a35dc81ad  14 channels in total; available frequencies :
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

enp0s20   Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.447 GHz (Channel 8)

wlxc83a35dc81ad  Scan completed :
          Cell 01 - Address: <MAC 'NETGEAR46' [AC1]>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR46"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000f3d55b3183
                    Extra: Last beacon: 680ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC '2WIRE278' [AC2]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"2WIRE278"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000118c3181
                    Extra: Last beacon: 856ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[mac80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     6FCDB39CB1DCCA0C9A450B2
depends:        cfg80211
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.10.0-19-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     0ADFC23D0B6BCD6916160E7
depends:        
intree:         Y
vermagic:       4.10.0-19-generic SMP mod_unload 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[  202.975415] IPv6: ADDRCONF(NETDEV_UP): wlxc83a35dc81ad: link is not ready
[  204.248630] wlxc83a35dc81ad: authenticate with <MAC 'Robison1' [AN1]>
[  204.292888] wlxc83a35dc81ad: send auth to <MAC 'Robison1' [AN1]> (try 1/3)
[  204.295142] wlxc83a35dc81ad: authenticated
[  209.294853] wlxc83a35dc81ad: aborting authentication with <MAC 'Robison1' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  210.652546] wlxc83a35dc81ad: authenticate with <MAC 'Robison1' [AN1]>
[  210.689416] wlxc83a35dc81ad: send auth to <MAC 'Robison1' [AN1]> (try 1/3)
[  210.693535] wlxc83a35dc81ad: authenticated
[  215.694512] wlxc83a35dc81ad: aborting authentication with <MAC 'Robison1' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  217.456607] wlxc83a35dc81ad: authenticate with <MAC 'Robison1' [AN1]>
[  217.492681] wlxc83a35dc81ad: send auth to <MAC 'Robison1' [AN1]> (try 1/3)
[  217.494676] wlxc83a35dc81ad: authenticated
[  222.497783] wlxc83a35dc81ad: aborting authentication with <MAC 'Robison1' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  224.768506] wlxc83a35dc81ad: authenticate with <MAC 'Robison1' [AN1]>
[  224.800425] wlxc83a35dc81ad: send auth to <MAC 'Robison1' [AN1]> (try 1/3)
[  224.826657] wlxc83a35dc81ad: authenticated
[  228.003025] wlxc83a35dc81ad: aborting authentication with <MAC 'Robison1' [AN1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[  228.028543] IPv6: ADDRCONF(NETDEV_UP): wlxc83a35dc81ad: link is not ready (repeated 4 times)

########## wireless info END ############
```

---

### Post by jeremy31 on 2017-10-14
See if praseodyms advice helps [https://ubuntuforums.org/showthread.php?t=2371002&p=13684949#post13684949](https://ubuntuforums.org/showthread.php?t=2371002&p=13684949#post13684949)

---

### Post by srobison62 on 2017-10-14
THat did it thank you!

---

### Post by jeremy31 on 2017-10-14
Please use the thread tools menu near the top right of the page to mark as solved.
There are 2 problems that exist in Ubuntu 17.04, it enables wifi powersave by default and uses MAC randomization, the MAC randomization causes issues for many ISB wifi devices

---

