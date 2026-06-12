---
title: "my wireless driver is RT3290 32 bits"
date: 2016-11-11
forum: Networking &amp; Wireless
---

### Post by rickywy on 2016-11-11
Hello, i'm new to the forum. could anyone help me, how to change the Ralink RT3290 wireless driver from 32 bit to 64 bit
bcos i think it's kinda slower

```

########## wireless info START ##########

Report from: 10 Nov 2016 15:16 WIB +0700

Booted last: 10 Nov 2016 00:00 WIB +0700

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, net.ifnames=0, biosdevname=0, i8042.reset, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/rtlbetcoex.conf line 1: ignoring bad line starting with 'ant_sel=2'

07:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
    DeviceName: Ralink RT3290LE 802.11bgn 1x1 Wi-Fi Adapter
    Subsystem: Hewlett-Packard Company Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter [103c:18ec]

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
    DeviceName: Hanksville Gbe Lan Connection
    Subsystem: Hewlett-Packard Company RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [103c:193e]

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 04f2:b3a6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

cfg80211              565248  0
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rt3290sta            1155072  1
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ra0       Link encap:Ethernet  HWaddr <MAC 'ra0' [IF2]>  
          inet addr:10.42.203.171  Bcast:10.42.203.255  Mask:255.255.252.0
          inet6 addr: fe80::ad02:8f21:cdaf:a41f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:138551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:261748172 (261.7 MB)  TX bytes:15721462 (15.7 MB)
          Interrupt:16 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:"UGM-Hotspot"  Nickname:"RT3290STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: <MAC 'UGM-Hotspot' [AC1]>   
          Bit Rate=48 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=65/100  Signal level:-77 dBm  Noise level:-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.42.200.1     0.0.0.0         UG    600    0        0 ra0
10.42.200.0     0.0.0.0         255.255.252.0   U     600    0        0 ra0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ra0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       961     1  0 13:10 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         ra0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Ralink corp.
GENERAL.PRODUCT:                        RT3290 Wireless 802.11n 1T/1R PCIe (Ralink RT3290LE 802.11bgn 1x1 Wi-Fi and Bluetooth 4.0 Combo Adapter)
GENERAL.DRIVER:                         rt2860
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'ra0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:07:00.0/net/ra0
GENERAL.IP-IFACE:                       ra0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     UGM-Hotspot
GENERAL.CON-UUID:                       4963a56d-e415-4176-a763-e7e7eb7696d2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     48 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4963a56d-e415-4176-a763-e7e7eb7696d2 | UGM-Hotspot
IP4.ADDRESS[1]:                         10.42.203.171/22
IP4.GATEWAY:                            10.42.200.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.42.200.1
IP4.DNS[2]:                             10.13.10.13
IP4.DNS[3]:                             10.18.10.18
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_wpad = 1
DHCP4.OPTION[8]:                        requested_netbios_scope = 1
DHCP4.OPTION[9]:                        next_server = 10.42.200.1
DHCP4.OPTION[10]:                       broadcast_address = 10.42.203.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       expiry = 1478768347
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       ip_address = 10.42.203.171
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       dhcp_message_type = 5
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       subnet_mask = 255.255.252.0
DHCP4.OPTION[22]:                       routers = 10.42.200.1
DHCP4.OPTION[23]:                       domain_name_servers = 10.42.200.1 10.13.10.13 10.18.10.18
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       ntp_servers = 175.111.88.2
DHCP4.OPTION[26]:                       network_number = 10.42.200.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 10.42.200.1
IP6.ADDRESS[1]:                         fe80::ad02:8f21:cdaf:a41f/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8168g-2_0.0.1 02/06/13
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:0e:00.0/net/eth0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID         BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
UGM-Hotspot  <MAC 'UGM-Hotspot' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  --         yes     * 
UGM-Hotspot  <MAC 'UGM-Hotspot' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  44      &#9602;&#9604;__  --         no        
CISCO coba   <MAC 'CISCO coba' [AN3]>  Infra  5     2432 MHz  54 Mbit/s  24      &#9602;___  WPA1 WPA2  no        
pcode        <MAC 'pcode' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
UGM-Hotspot  <MAC 'UGM-Hotspot' [AC3]>  Infra  6     2437 MHz  54 Mbit/s  7       &#9602;___  --         no        

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

[[/etc/NetworkManager/system-connections/pogung_rejo]] (600 root)
[connection] id=pogung_rejo | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'ra0' [IF2]> | mac-address-blacklist= | ssid=pogung_rejo
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vietnam1]] (600 root)
[connection] id=Vietnam1 | type=wifi | permissions=user:ubuntu:;
[wifi] mac-address=<MAC 'ra0' [IF2]> | mac-address-blacklist= | ssid=Vietnam1
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/UGM-Hotspot]] (600 root)
[connection] id=UGM-Hotspot | type=wifi | permissions=user:ricky:;
[wifi] mac-address=<MAC 'ra0' [IF2]> | mac-address-blacklist= | ssid=UGM-Hotspot
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Jakarta (based on set time zone)

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

eth0      no frequency information.

ra0       11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      2   APs on   Frequency:2.437 GHz (Channel 6)

ra0       Scan completed :
          Cell 01 - Address: <MAC 'UGM-Hotspot' [AC1]>
                    Protocol:802.11g/n
                    ESSID:"UGM-Hotspot"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/100  Signal level=-72 dBm  Noise level=-67 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 02 - Address: <MAC 'UGM-Hotspot' [AC2]>
                    Protocol:802.11b/g/n
                    ESSID:"UGM-Hotspot"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/100  Signal level=-74 dBm  Noise level=-69 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 03 - Address: <MAC 'UGM-Hotspot' [AC3]>
                    Protocol:802.11g/n
                    ESSID:"UGM-Hotspot"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=0/100  Signal level=-96 dBm  Noise level=-91 dBm
                    Encryption key:off
                    Bit Rates:54 Mb/s
          Cell 04 - Address: <MAC 'pcode' [AC4]>
                    Protocol:802.11b/g/n
                    ESSID:"pcode"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality=5/100  Signal level=-88 dBm  Noise level=-83 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[cfg80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[rt3290sta]
filename:       /lib/modules/4.4.0-47-generic/updates/dkms/rt3290sta.ko
version:        2.6.0.0_rev1
srcversion:     073AC1AA84019DBCFEC8F58
depends:        
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

##### module parameters #################

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

[/etc/modprobe.d/blacklist-ralink.conf]
blacklist rt2800pci
blacklist rt2x00pci  

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

[/etc/modprobe.d/rtlbetcoex.conf]
ant_sel=2

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIR='/usr/lib/pm-utils'
if [ -d "$LIBDIR/power.d" ]; then
    # pm-utils script dir exists
    blocked="$LIBDIR/power.d/${0##*/}"
    if [ -x "$blocked" ]; then
        # overridable pm-utils script exists --> check if TLP enabled
        if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
            # TLP is enabled --> disable $blocked
            echo "Notice: '${blocked}' disabled by TLP."
        else
            exec "$blocked" $*
        fi
    fi # else: nothing to disable -> don't read $CONFFILE
fi
exit 0

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############


```

[SIZE=4][FONT=arial]and i post my wireless-info.txt there
thanks![/FONT][/SIZE]

---

### Post by wildmanne39 on 2016-11-12
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

Did you set parameters for your driver in the grub at boot up?

---

### Post by rickywy on 2016-11-12
> **Wild Man said:**
> Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

Did you set parameters for your driver in the grub at boot up?

okay, sorry im new here Wild Man..
i havent set it yet.. could you please tell me how to set the parameters?

---

### Post by wildmanne39 on 2016-11-12
I was just asking about the parameters because I see this:
```
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/rtlbetcoex.conf line 1: ignoring bad line starting with 'ant_sel=2'
```which is strange to me.

Are you having issues with your wifi connection? what makes you think you are using a 32bit driver?

---

### Post by rickywy on 2016-11-13
i think i previously changed the line referring to someone post, but i dont know how to resetting it back.
my connection is sometimes delayed, and sometimes the wifi disconnected, other time when starting ubuntu... the driver doesnt work

i saw the driver with command: lshw -C network

---

### Post by chili555 on 2016-11-13
> **Wild Man said:**
> I was just asking about the parameters because I see this:
```
libkmod: ERROR ../libkmod/libkmod-config.c:635 kmod_config_parse: /etc/modprobe.d/rtlbetcoex.conf line 1: ignoring bad line starting with 'ant_sel=2'
```which is strange to me.

Are you having issues with your wifi connection? what makes you think you are using a 32bit driver?Your driver, rt3290sta, doesn't have a parameter ant_sel=2. You can check all the available parameters:```
modinfo rt3290sta
```Once you've verified it, you may as well remove the faulty conf file:```
sudo rm  /etc/modprobe.d/rtlbetcoex.conf
```As for your driver being 32-bit, I see no evidence that it is so. As for it dropping and being unstable, we haven't seen the cause of that either. Please post:```
dmesg | grep -e rt3 -e ra0
```I recommend that you set your regulatory domain explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-*maybe*-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

