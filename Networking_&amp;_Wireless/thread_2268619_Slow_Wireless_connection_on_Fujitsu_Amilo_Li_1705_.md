---
title: "Slow Wireless connection on Fujitsu Amilo Li 1705 laptop running LXLE"
date: 2015-03-10
forum: Networking &amp; Wireless
---

### Post by podmore71 on 2015-03-10
Hi everyone.

I'm somewhat of a newbie when it comes to Linux but I am desperate to learn. At the momemt I have Kubuntu 14.10 running perfectly on my Dell Inspirion 1545 and I love it.

I also have an old Fujitsu Li 1705 laptop which was too slow to run Windows on so I thought I would try and install Linux on that too. As the machine only has 1 gig of ram I decided to try a copy of LXLE as it seemed more suited to lower spec laptops.

Well after spending what felt like forever trying to get it installed (because of a very doggy DVD drive, I finally got it installed last night. The only problem I have with it is the Wireless connection speed is painfully slow. I have a 100 meg cable connection but running a test over at speedtest.net only gave me a download speed of around 5 meg.

I have tried searching for help on this but became stuck so I thought I would ask here. 

I have run the 'wireless-info script' as posted in the sticky and here is the resluts of thsat txt file:
```


########## wireless info START ##########


Report from: 10 Mar 2015 10:10 GMT +0000


Booted last: 10 Mar 2015 09:04 GMT +0000


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise


##### kernel ############################


Linux 3.2.0-78-generic #113-Ubuntu SMP Tue Mar 3 17:33:40 UTC 2015 i686 i686 i386 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


XP-Paradigm


##### lspci #############################


00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 7c)
	Subsystem: Fujitsu Technology Solutions Device [1734:10f7]
	Kernel driver in use: via-rhine


05:01.0 Ethernet controller [0200]: Qualcomm Atheros AR2413/AR2414 Wireless Network Adapter [AR5005G(S) 802.11bg] [168c:001a] (rev 01)
	Subsystem: Qualcomm Atheros Compex Wireless 802.11 b/g  MiniPCI Adapter, Rev A1 [WLM54G] [168c:2052]
	Kernel driver in use: ath5k


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


rtl8192cu              97717  0 
rtl8192c_common        69519  1 rtl8192cu
rtlwifi                95855  1 rtl8192cu
ath5k                 145127  0 
ath                    19387  1 ath5k
mac80211              436493  4 rtl8192cu,rtl8192c_common,rtlwifi,ath5k
cfg80211              178877  4 rtlwifi,ath5k,ath,mac80211


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:bff:fe0e:70c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2914 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3361441 (3.3 MB)  TX bytes:182489 (182.4 KB)
          Interrupt:23 Base address:0x4400 


wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:a8ff:fedd:943c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4986 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4371024 (4.3 MB)  TX bytes:727431 (727.4 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:"VM763233-2G"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: <MAC 'VM763233-2G' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:3023   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0


##### resolv.conf #######################


grep: /etc/resolv.conf: No such file or directory


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: wlan0  [VM763233-2G] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>


  Capabilities:
    Speed:           1 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    VM145045-2G:     Infra, <MAC 'VM145045-2G' [AN1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 4 WPA WPA2
    TALKTALK-7274F8: Infra, <MAC 'TALKTALK-7274F8' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    *VM763233-2G:    Infra, <MAC 'VM763233-2G' [AC1]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 80 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2 Enterprise
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10
    SKY960D0:        Infra, <MAC 'SKY960D0' [AN6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN7]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2 Enterprise
    BTHub3-ZTR3:     Infra, <MAC 'BTHub3-ZTR3' [AN8]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN9]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2 Enterprise
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0
    BTHub5-2Z2P:     Infra, <MAC 'BTHub5-2Z2P' [AN11]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    BTHub4-P6NG:     Infra, <MAC 'BTHub4-P6NG' [AN12]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WPA WPA2
    virginmedia5344121: Infra, <MAC 'virginmedia5344121' [AN13]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2


  IPv4 Settings:
    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            via-rhine
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/VM763233-2G]] (600 root)
[connection] id=VM763233-2G | type=802-11-wireless
[802-11-wireless] ssid=VM763233-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/VM763233-2G 1]] (600 root)
[connection] id=VM763233-2G 1 | type=802-11-wireless
[802-11-wireless] ssid=VM763233-2G | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


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
          Current Frequency:2.452 GHz (Channel 9)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM763233-2G' [AC1]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"VM763233-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000034b9975d459
                    Extra: Last beacon: 244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TALKTALK-7274F8' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-7274F8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ed7f25417f
                    Extra: Last beacon: 800ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'BTWifi-X' [AC3]>


:81:D8:5B:C1:EA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003100722180
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x


##### module infos ######################


[rtl8192cu]
filename:       /lib/modules/3.2.0-78-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     9F5B9066754F20EC5ED1CF9
depends:        rtlwifi,mac80211,rtl8192c-common
intree:         Y
vermagic:       3.2.0-78-generic SMP mod_unload modversions 686 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl8192c_common]
filename:       /lib/modules/3.2.0-78-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C45A418F3DB47147A5BED91
depends:        mac80211
intree:         Y
vermagic:       3.2.0-78-generic SMP mod_unload modversions 686 


[rtlwifi]
filename:       /lib/modules/3.2.0-78-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     95584F2D2B680E159E26850
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.2.0-78-generic SMP mod_unload modversions 686 


[ath5k]
filename:       /lib/modules/3.2.0-78-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     6994626DE437F30E5074A5E
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-78-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           all_channels:Expose all channels the device can use. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)


[ath]
filename:       /lib/modules/3.2.0-78-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8B429DBE4586F4065E2EA2E
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-78-generic SMP mod_unload modversions 686 


[mac80211]
filename:       /lib/modules/3.2.0-78-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E240EFDC3EE774AE3EEA5D1
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-78-generic SMP mod_unload modversions 686 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)


[cfg80211]
filename:       /lib/modules/3.2.0-78-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     3F81584A8E06499FBACA9C1
depends:        
intree:         Y
vermagic:       3.2.0-78-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8192cu]
debug: 0
swenc: N


[ath5k]
all_channels: N
fastchanswitch: N
nohwcrypt: N


[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp
lp


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


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }


##### rc.local ##########################


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


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x1106:/sys/devices/pci0000:00/0000:00:12.0 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:13.1/0000:05:01.0 (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x0bda:0x8176 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


##### dmesg #############################


[  792.564840] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd30000
[  792.564846] rtlwifi: reg 0x824, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x80390004
[  792.567823] rtlwifi: reg 0x820, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x1000100
[  792.567827] rtlwifi: reg 0x8b8, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x100010
[  792.567833] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x40130104
[  792.567836] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x90e1317
[  792.567840] rtlwifi: reg 0x2, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xf0002ace
[  792.567844] rtlwifi: reg 0x44, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x69543434
[  792.567848] rtlwifi: reg 0x42, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x69543434
[  801.171165] wlan0: authenticate with <MAC 'VM763233-2G' [AC1]> (try 1)
[  801.206103] wlan0: authenticated
[  801.206794] wlan0: associate with <MAC 'VM763233-2G' [AC1]> (try 1)
[  801.215546] wlan0: RX ReassocResp from <MAC 'VM763233-2G' [AC1]> (capab=0x411 status=0 aid=4)
[  801.215553] wlan0: associated
[  801.215559] wlan0: No basic rates in AssocResp. Using min supported rate instead.
[  811.456029] wlan0: no IPv6 routers present


########## wireless info END ############



```

I hope that's come out alright.

Can anyone shed any light on the problem I am having??

Thanks

Andy

---

### Post by Vladlenin5000 on 2015-03-10
Change the encryption to WPA2 only. Mixed mode usually results in what you've been experiencing.

---

### Post by podmore71 on 2015-03-10
Ok Vladlenin, I've done that and it's still the same

Andy

---

### Post by Vladlenin5000 on 2015-03-13
> **podmore71 said:**
> Ok Vladlenin, I've done that and it's still the same

Andy

Then probably is how it is...


```
Subsystem: Qualcomm Atheros Compex Wireless 802.11 [COLOR=#ff0000]b/g[/COLOR]  MiniPCI Adapter, Rev A1 [WLM54G] [168c:2052]
    Kernel driver in use: [COLOR=#008000]ath5k[/COLOR]
```

The driver is correct for that old device and it can't do better than 802.11g anyway so...

---

### Post by chili555 on 2015-03-13
Why is rtl8192cu loaded?

---

