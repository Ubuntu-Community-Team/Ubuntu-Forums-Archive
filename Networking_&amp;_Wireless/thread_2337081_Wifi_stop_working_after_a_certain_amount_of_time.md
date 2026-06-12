---
title: "Wifi stop working after a certain amount of time"
date: 2016-09-14
forum: Networking &amp; Wireless
---

### Post by avisaziz123 on 2016-09-14
Hello, my wifi on lubuntu is very strange it stop working after 5-30 minutes usually when i surf the web using firefox the server cannot connected and i have to click the wifi icon for the wifi works again and that happens too when i download application (playonlinux) on the software center the download failed in the middle and i have to click the wifi icon again
```

########## wireless info START ##########

Report from: 14 Sep 2016 08:07 EDT -0400

Booted last: 14 Sep 2016 00:00 EDT -0400

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller [11ab:4357] (rev 10)
    Subsystem: Hewlett-Packard Company 88E8042 PCI-E Fast Ethernet Controller [103c:308c]
    Kernel driver in use: sky2

06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4312 802.11b/g LP-PHY [103c:1508]
    Kernel driver in use: b43-pci-bridge

##### lsusb #############################

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:b159 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  1 b43
cfg80211              565248  2 b43,mac80211
ssb                    65536  1 b43
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::34a8:9323:7fcd:a2f/64 Scope:Link
          inet6 addr: fe80::bcdc:5f3e:3419:fbb0/64 Scope:Link
          inet6 addr: fe80::5bc:2156:d2c9:ace2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:105865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65165 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:130142805 (130.1 MB)  TX bytes:6189902 (6.1 MB)

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"@wifi.id"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC '@wifi.id' [AC1]>   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    600    0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root      2290     1  0 06:52 ?        00:00:02 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4312 802.11b/g LP-PHY
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.4.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:09.0/0000:06:00.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     @wifi.id
GENERAL.CON-UUID:                       ef642a99-f8c2-42cb-bf13-96ed14f03f21
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/4
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     24 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   ef642a99-f8c2-42cb-bf13-96ed14f03f21 | @wifi.id
IP4.ADDRESS[1]:                         192.168.1.6/24
IP4.GATEWAY:                            192.168.1.254
IP4.DNS[1]:                             192.168.1.254
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        server_name = ZTE
DHCP4.OPTION[5]:                        domain_name_servers = 192.168.1.254
DHCP4.OPTION[6]:                        ip_address = 192.168.1.6
DHCP4.OPTION[7]:                        requested_static_routes = 1
DHCP4.OPTION[8]:                        dhcp_server_identifier = 192.168.1.254
DHCP4.OPTION[9]:                        requested_time_offset = 1
DHCP4.OPTION[10]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       dhcp_rebinding_time = 226800
DHCP4.OPTION[13]:                       requested_domain_name_servers = 1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       requested_broadcast_address = 1
DHCP4.OPTION[16]:                       routers = 192.168.1.254
DHCP4.OPTION[17]:                       dhcp_renewal_time = 129600
DHCP4.OPTION[18]:                       requested_domain_name = 1
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1474113931
DHCP4.OPTION[21]:                       requested_wpad = 1
DHCP4.OPTION[22]:                       host_name = dhcppc4
DHCP4.OPTION[23]:                       requested_netbios_scope = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       requested_ntp_servers = 1
DHCP4.OPTION[29]:                       next_server = 192.168.1.254
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 259200
IP6.ADDRESS[1]:                         fe80::5bc:2156:d2c9:ace2/64
IP6.ADDRESS[2]:                         fe80::34a8:9323:7fcd:a2f/64
IP6.ADDRESS[3]:                         fe80::bcdc:5f3e:3419:fbb0/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Marvell Technology Group Ltd.
GENERAL.PRODUCT:                        88E8042 PCI-E Fast Ethernet Controller
GENERAL.DRIVER:                         sky2
GENERAL.DRIVER-VERSION:                 1.30
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/enp2s0
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

SSID      BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
@wifi.id  <MAC '@wifi.id' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  98      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  yes     * 
omah2     <MAC 'omah2' [AN2]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA1 WPA2  no        
ulhaqayu  <MAC 'ulhaqayu' [AC2]>  Infra  10    2457 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2  no        

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

[[/etc/NetworkManager/system-connections/@wifi.id]] (600 root)
[connection] id=@wifi.id | type=wifi | permissions=user:avis:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=@wifi.id
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country ID: DFS-JP
    (2402 - 2482 @ 20), (N/A, 20), (N/A)
    (5735 - 5815 @ 20), (N/A, 23), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.457 GHz (Channel 10)

wlan0     Scan completed :
          Cell 01 - Address: <MAC '@wifi.id' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"@wifi.id"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002c1009ac9b
                    Extra: Last beacon: 20ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ulhaqayu' [AC2]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"ulhaqayu"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010588ee1c8
                    Extra: Last beacon: 1192ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     C5CB08F60A0C6A00FBF57B0
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B10AF1CD828D26173EA0378
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     25A45701AAA64DAC1E47D9D
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.4.0-36-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-36-generic SMP mod_unload modversions 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

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

[ 4011.559167] wlan0: deauthenticating from <MAC '@wifi.id' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4013.541617] wlan0: authenticate with <MAC '@wifi.id' [AC1]>
[ 4013.564398] wlan0: send auth to <MAC '@wifi.id' [AC1]> (try 1/3)
[ 4013.566122] wlan0: authenticated
[ 4013.572152] wlan0: associate with <MAC '@wifi.id' [AC1]> (try 1/3)
[ 4013.575418] wlan0: RX AssocResp from <MAC '@wifi.id' [AC1]> (capab=0x411 status=0 aid=4)
[ 4013.575677] wlan0: associated
[ 4015.406067] IPv6: wlan0: IPv6 duplicate address fe80::34a8:9323:7fcd:a2f detected!
[ 4016.257865] IPv6: wlan0: IPv6 duplicate address fe80::5bc:2156:d2c9:ace2 detected!
[ 4016.342280] IPv6: wlan0: IPv6 duplicate address fe80::bcdc:5f3e:3419:fbb0 detected!
[ 4223.990747] wlan0: deauthenticating from <MAC '@wifi.id' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4225.013636] wlan0: authenticate with <MAC '@wifi.id' [AC1]>
[ 4225.036436] wlan0: send auth to <MAC '@wifi.id' [AC1]> (try 1/3)
[ 4225.039379] wlan0: authenticated
[ 4225.040180] wlan0: associate with <MAC '@wifi.id' [AC1]> (try 1/3)
[ 4225.043438] wlan0: RX AssocResp from <MAC '@wifi.id' [AC1]> (capab=0x411 status=0 aid=4)
[ 4225.043946] wlan0: associated
[ 4225.450289] IPv6: wlan0: IPv6 duplicate address fe80::34a8:9323:7fcd:a2f detected!
[ 4226.473052] IPv6: wlan0: IPv6 duplicate address fe80::5bc:2156:d2c9:ace2 detected!
[ 4227.531523] IPv6: wlan0: IPv6 duplicate address fe80::bcdc:5f3e:3419:fbb0 detected!
[ 4416.106736] wlan0: deauthenticating from <MAC '@wifi.id' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 4417.161919] wlan0: authenticate with <MAC '@wifi.id' [AC1]>
[ 4417.184517] wlan0: send auth to <MAC '@wifi.id' [AC1]> (try 1/3)
[ 4417.186718] wlan0: authenticated
[ 4417.192131] wlan0: associate with <MAC '@wifi.id' [AC1]> (try 1/3)
[ 4417.195400] wlan0: RX AssocResp from <MAC '@wifi.id' [AC1]> (capab=0x411 status=0 aid=4)
[ 4417.196402] wlan0: associated
[ 4418.805087] IPv6: wlan0: IPv6 duplicate address fe80::34a8:9323:7fcd:a2f detected!
[ 4419.848442] IPv6: wlan0: IPv6 duplicate address fe80::5bc:2156:d2c9:ace2 detected!
[ 4420.663121] IPv6: wlan0: IPv6 duplicate address fe80::bcdc:5f3e:3419:fbb0 detected!

########## wireless info END ############

```

---

### Post by avisaziz123 on 2016-09-14
the signal is fine and strong but after a certaint amount of times it stop working

---

### Post by wildmanne39 on 2016-09-14
First it would be best to remove all special characters from your network name.

Second, check the settings in the router. WPA2-AES (CCMP) is best; not WPA and WPA2 mixed mode and definitely not TKIP. 

Third, if your router is capable of N speeds, You should have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. 

Also set a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly, the information says you are in the United States but your regulatory domain is set to ID which is not the United States.

Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Now go into network manager and change your wireless setting to match the screenshots and you will have better performance it usually stops disconnections and speeds up the connection.
Reboot computer
Thanks

---

### Post by avisaziz123 on 2016-09-16
Hi, sorry for the late reply
I did all the things you say but today i encounter the same problem, the wifi is still connected but wont work i have to click the wifi icon for the wifi to work usually happens every 5-30 minutes

---

### Post by wildmanne39 on 2016-09-16
Please run the wireless script again and post the file it creates so we can see if the changes you made stuck.

---

