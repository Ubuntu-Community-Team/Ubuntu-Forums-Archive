---
title: "Ubuntu 16.04 - Configuring Internet over Wifi instead of Ethernet?"
date: 2017-01-02
forum: Networking &amp; Wireless
---

### Post by jsk2017 on 2017-01-02
[COLOR=#111111][FONT=Ubuntu]I am setting up networking on my ODROID C1 running Ubuntu 16.04.1 LTS (GNU/Linux 3.10.104-181 armv7l) . Internet access over WiFi works fine but when I plug-in the ethernet cable (which has no internet) the internet stops working. 

 Output of **wireless-info.txt**[COLOR=#222222][FONT=Verdana] and [/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana]wireless-info.tar.gz[/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana] is provided below.[/FONT][/COLOR][/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]```


########## wireless info START ##########


Report from: 02 Jan 2017 05:39 UTC +0000


Booted last: 02 Jan 2017 00:00 UTC +0000


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial


##### kernel ############################


Linux 3.10.104-181 #1 SMP PREEMPT Fri Dec 23 13:18:53 UTC 2016 armv7l armv7l armv7l GNU/Linux


, rootwait, ro, console=tty0, console=ttyS0,115200n8, no_console_suspend, vdaccfg=0xa000, logo=osd1,loaded,0x7900000,720p,full, dmfc=3, cvbsmode=576cvbs, hdmimode=1080p, m_bpp=32, vout=hdmi, disableuhs, disablehpd=true, monitor_onoff=false, max_freq=1536


##### desktop ###########################


MATE (from ~/.dmrc)


##### lspci #############################


pcilib: Cannot open /proc/bus/pci
lspci: Cannot find any working access method.


##### lsusb #############################


Bus 001 Device 003: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 004: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### lsmod #############################


r8712u                157175  0


##### interfaces ########################


source-directory /etc/network/interfaces.d


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF1]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:276533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1301725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48899285 (48.8 MB)  TX bytes:1951335686 (1.9 GB)
          Interrupt:40 


ip6tnl0   Link encap:UNSPEC  HWaddr <MAC 'ip6tnl0' [IF2]>  
          NOARP  MTU:1452  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlx<IF from MAC [IF3]> Link encap:Ethernet  HWaddr <MAC 'wlx<IF from MAC [IF3]>' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2919 errors:0 dropped:296 overruns:0 frame:0
          TX packets:8129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:251295 (251.2 KB)  TX bytes:931283 (931.2 KB)


##### iwconfig ##########################


sit0      no wireless extensions.


lo        no wireless extensions.


eth0      no wireless extensions.


ip6tnl0   no wireless extensions.


wlx<IF from MAC [IF3]>  unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


    NetworkManager


Running:


root      2409     1  0  2016 ?        00:02:15 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         meson-eth
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/platform/meson-eth/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       bfc675ec-878a-40da-9c22-b4d09537b9b2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bfc675ec-878a-40da-9c22-b4d09537b9b2 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.1.101/24
IP4.GATEWAY:                            
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP6.ADDRESS[1]:                         fe80::<IP6 'eth0' [IF1]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         wlx<IF from MAC [IF3]>
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Manufacturer Realtek 
GENERAL.PRODUCT:                        RTL8191S WLAN Adapter 
GENERAL.DRIVER:                         r8712u
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlx<IF from MAC [IF3]>' [IF3]>
GENERAL.MTU:                            0
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/lm1/usb1/1-1/1-1.3/1-1.3:1.0/net/wlx<IF from MAC [IF3]>
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
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0,4,3}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   15d84fa3-9ddb-4edc-827f-f4a78be93efe | @dj_abu#
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   ce33a174-1b4e-40a4-ac3d-e75969d897cf | Dlink
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   60315439-350e-4af6-a444-c0d04740309f | JioFi3_6F26A3


GENERAL.DEVICE:                         ip6tnl0
GENERAL.TYPE:                           ip6tnl
GENERAL.NM-TYPE:                        NMDeviceGeneric
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         ip6tnl
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00
GENERAL.MTU:                            1452
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/0
GENERAL.IP-IFACE:                       ip6tnl0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            


GENERAL.DEVICE:                         sit0
GENERAL.TYPE:                           iptunnel
GENERAL.NM-TYPE:                        NMDeviceIPTunnel
GENERAL.VENDOR:                         
GENERAL.PRODUCT:                        
GENERAL.DRIVER:                         sit
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            1480
GENERAL.STATE:                          10 (unmanaged)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /virtual/device/placeholder/3
GENERAL.IP-IFACE:                       sit0
GENERAL.IS-SOFTWARE:                    yes
GENERAL.NM-MANAGED:                     no
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
CAPABILITIES.IS-SOFTWARE:               yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
IP4.GATEWAY:                            
IP6.GATEWAY:                            


SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Dlink           <MAC 'Dlink' [AC1]>  Infra  1     2412 MHz  54 Mbit/s  100     &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
JioFi3_6F26A3   <MAC 'JioFi3_6F26A3' [AC3]>  Infra  5     2432 MHz  54 Mbit/s  98      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
MAC-PC_Network  <MAC 'MAC-PC_Network' [AC4]>  Infra  11    2462 MHz  54 Mbit/s  74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
@dj_abu#        <MAC '@dj_abu#' [AC2]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/ADYYc291bmRkYXJiYXI]] (600 root)
[connection] id=ADYYc291bmRkYXJiYXI | type=wifi | permissions=user:odroid:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF3]>' [IF3]> | mac-address-blacklist= | ssid=ADYYc291bmRkYXJiYXI
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/JioFi3_6F26A3]] (600 root)
[connection] id=JioFi3_6F26A3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF3]>' [IF3]> | mac-address-blacklist= | ssid=JioFi3_6F26A3
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/@dj_abu#]] (600 root)
[connection] id=@dj_abu# | type=wifi | permissions=user:root:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF3]>' [IF3]> | mac-address-blacklist= | ssid=@dj_abu#
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Dlink]] (600 root)
[connection] id=Dlink | type=wifi | permissions=user:odroid:;
[wifi] mac-address=<MAC 'wlx<IF from MAC [IF3]>' [IF3]> | mac-address-blacklist= | ssid=Dlink
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Etc/UTC (based on set time zone)


country 00: DFS-UNSET
    (2402 - 2472 @ 40), (6, 20), (N/A)
    (2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN


##### iwlist channels ###################


sit0      no frequency information.


lo        no frequency information.


eth0      no frequency information.


ip6tnl0   no frequency information.


wlx<IF from MAC [IF3]>  14 channels in total; available frequencies :
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


sit0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


ip6tnl0   Interface doesn't support scanning.


Channel occupancy:


      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.462 GHz (Channel 11)


wlx<IF from MAC [IF3]>  Scan completed :
          Cell 01 - Address: <MAC 'Dlink' [AC1]>
                    ESSID:"Dlink"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 02 - Address: <MAC '@dj_abu#' [AC2]>
                    ESSID:"@dj_abu#"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd1a0050f20101000050f20202000050f2020050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac02000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 03 - Address: <MAC 'JioFi3_6F26A3' [AC3]>
                    ESSID:"JioFi3_6F26A3"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=98/100  
          Cell 04 - Address: <MAC 'MAC-PC_Network' [AC4]>
                    ESSID:"MAC-PC_Network"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:wpa_ie=dd160050f20101000050f20401000050f20401000050f202
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac020000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=74/100  


##### module infos ######################


[r8712u]
filename:       /lib/modules/3.10.104-181/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
author:         Larry Finger
description:    rtl871x wireless lan driver
license:        GPL
depends:        
staging:        Y
intree:         Y
vermagic:       3.10.104-181 SMP preempt mod_unload ARMv7 
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


##### module parameters #################


[r8712u]
ampdu_enable: 1
busy_thresh: 40
cbw40_enable: 1
channel: 1
chip_version: 2
hci: 1
ht_enable: 1
ifname: wlan%d
initmac: (null)
lbkmode: 0
low_power: 0
mp_mode: 0
network_mode: 0
power_mgnt: 0
rf_config: 1
rfintfs: 2
vcs_type: 1
video_mode: 1
vrtl_carrier_sense: 2
wifi_test: 0
wmm_enable: 0


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


[/etc/modprobe.d/blacklist-odroid.conf]
blacklist w1_gpio
blacklist wire


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


if [ -f /aafirstboot ]; then /aafirstboot start ; fi


exit 0


##### pm-utils ##########################


[/etc/pm/power.d/disable_wol] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/laptop-mode] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pci_devices] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/pcie_aspm] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/sched-powersave] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/usb_bluetooth] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/wireless] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


[/etc/pm/power.d/xfs_buffer] (777 root)
CONFFILE=/etc/default/tlp
LIBDIRS='/usr/lib /usr/lib64'
for d in ${LIBDIRS}; do
    if [ -d "${d}/pm-utils/power.d" ]; then
        blocked="${d}/pm-utils/power.d/${0##*/}"
        break
    fi
done
if [ -n "$blocked" ] && [ -x "$blocked" ]; then
    # else nothing to disable -> don't read $CONFFILE
    if [ -e "$CONFFILE" ] && . "$CONFFILE" && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


##### dmesg #############################


[   36.102605] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF3]>: link becomes ready
[   37.504976] r8712u 1-1.3:1.0 wlx<IF from MAC [IF3]>: r8712_got_addbareq_event_callback: mac = <MAC 'JioFi3_6F26A3' [AC3]>, seq = 48, tid = 6
[  103.960590] r8712u 1-1.3:1.0 wlx<IF from MAC [IF3]>: r8712_got_addbareq_event_callback: mac = <MAC 'JioFi3_6F26A3' [AC3]>, seq = 0, tid = 0
[16244.548097] r8712u 1-1.3:1.0 wlx<IF from MAC [IF3]>: r8712_got_addbareq_event_callback: mac = <MAC 'JioFi3_6F26A3' [AC3]>, seq = 0, tid = 1
[16245.584773] r8712u 1-1.3:1.0 wlx<IF from MAC [IF3]>: r8712_got_addbareq_event_callback: mac = <MAC 'JioFi3_6F26A3' [AC3]>, seq = 0, tid = 2
[16542.452050] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF3]>: link becomes ready
[16565.430526] r8712u 1-1.3:1.0 wlx<IF from MAC [IF3]>: r8712_got_addbareq_event_callback: mac = <MAC 'JioFi3_6F26A3' [AC3]>, seq = 48, tid = 0
[16662.842947] IPv6: ADDRCONF(NETDEV_CHANGE): wlx<IF from MAC [IF3]>: link becomes ready
[16694.780233] r8712u 1-1.3:1.0 wlx<IF from MAC [IF3]>: r8712_got_addbareq_event_callback: mac = <MAC 'JioFi3_6F26A3' [AC3]>, seq = 192, tid = 6
[16711.619001] r8712u 1-1.3:1.0 wlx<IF from MAC [IF3]>: r8712_got_addbareq_event_callback: mac = <MAC 'JioFi3_6F26A3' [AC3]>, seq = 64, tid = 0


########## wireless info END ############



```[COLOR=#111111][FONT=Ubuntu][FONT=Verdana]

[/FONT][/FONT][/COLOR][ATTACH]272976[/ATTACH]

---

### Post by jsk2017 on 2017-01-02
Managed to fix this, updated DNS to wifi adapter via Network Manager and it worked :)

---

### Post by Keith_Helms on 2017-01-02
What messages come up in syslog/dmesg when you're connected to wifi and then plug in ethernet?  Is there anything about why wifi was disconnected?

Never mind.  I see you figured it out.

---

### Post by bluepearlsky on 2017-07-26
How to update DNS and where to write? Ethernet is getting connected but no interenet access. But inserting a WiFi USB adapter works perfectly to browse internet. Please help me. :-)

---

