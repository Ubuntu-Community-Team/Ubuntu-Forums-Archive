---
title: "Problem with WiFi connection. W/ wireless-info results."
date: 2016-05-23
forum: Networking &amp; Wireless
---

### Post by Chronux on 2016-05-23
I have a problem with my WiFi connection. I can not seem to connect to any WiFi network regardless of the security. 

I've tried connecting to a WPA, WPA2, None, etc WiFi's but it won't work eventhough I can see the list of available WiFis.

I've ran the "wireless-info" script that was posted in a sticky thread in this section and I've attached the results to this thread.

I'm also posting the results here if you don't feel like downloading:

```

########## wireless info START ##########

Report from: 17 Mar 2158 00:31 EDT -0400

Booted last: 07 Feb 2022 16:33 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.18.0-ctx.patch #3 SMP Wed Dec 10 15:36:38 MST 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, tpm_tis.interrupts=0, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Qualcomm Atheros AR9462 Wireless Network Adapter [168c:0034] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e058]
    Kernel driver in use: ath9k

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 046d:c077 Logitech, Inc. 
Bus 001 Device 005: ID 0489:e056 Foxconn / Hon Hai 
Bus 001 Device 002: ID 04f2:b490 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 136715  0 
ath9k_common           25638  1 ath9k
ath9k_hw              455128  2 ath9k_common,ath9k
ath                    29006  3 ath9k_common,ath9k,ath9k_hw
mac80211              674115  1 ath9k
cfg80211              513009  4 ath,ath9k_common,ath9k,mac80211
ath3k                  13331  0 
bluetooth             461507  25 bnep,ath3k,btusb,rfcomm

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1648 (1.6 KB)  TX bytes:4864 (4.8 KB)

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

    NetworkManager

Running:

root       843     1  0 00:01 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    t1242798_2.4GHz: Infra, <MAC 't1242798_2.4GHz' [AC1]>, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    t1242798_5GHz:   Infra, <MAC 't1242798_5GHz' [AC2]>, Freq 5765 MHz, Rate 54 Mb/s, Strength 100
    ASUSBio:         Infra, <MAC 'ASUSBio' [AN3]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 39 WPA2

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

Sorry, try again.
[[/etc/NetworkManager/system-connections/t1242798_5GHz]] (600 root)
[connection] id=t1242798_5GHz | type=802-11-wireless
[802-11-wireless] ssid=t1242798_5GHz | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/t1242798_5GHz~]] (600 root)
[connection] id=t1242798_5GHz | type=802-11-wireless
[802-11-wireless] ssid=t1242798_5GHz | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/t1242798_2.4GHz]] (600 root)
[connection] id=t1242798_2.4GHz | type=802-11-wireless
[802-11-wireless] ssid=t1242798_2.4GHz | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/New_York (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:5.765 GHz

wlan0     Scan completed :
          Cell 01 - Address: <MAC 't1242798_2.4GHz' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"t1242798_2.4GHz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000009ae2bb43
                    Extra: Last beacon: 72ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 't1242798_5GHz' [AC2]>
                    Channel:153
                    Frequency:5.765 GHz
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:off
                    ESSID:"t1242798_5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000009adb3c07
                    Extra: Last beacon: 72ms ago

##### module infos ######################

[ath9k]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     5CA20ABDB2778F3165E3ED9
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     94B4F03FB0E70D4D2C6AD91
depends:        cfg80211,ath9k_hw,ath
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

[ath9k_hw]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     715A6023A3AE8A8FB5869EF
depends:        ath
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

[ath]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     0D7DE85EF15890F115735E2
depends:        cfg80211
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     7EEF5988245D414BA91F27D
depends:        cfg80211
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C8543A08D2650C7BC1B7107
depends:        
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ath3k]
filename:       /lib/modules/3.18.0-ctx.patch/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     C337943CFD92B950F279B89
depends:        bluetooth
intree:         Y
vermagic:       3.18.0-ctx.patch SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        78:40:98:D9:99:62:AD:94:06:29:DB:7D:A4:37:97:3F:64:1B:F7:32
sig_hashalgo:   sha512

##### module parameters #################

[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

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

lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc
lp
rtc

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

[/etc/modprobe.d/snd-hda-intel.conf]
options snd-hda-intel model=,alc283-dac-wcaps

##### rc.local ##########################

chgrp plugdev /sys/class/backlight/intel_backlight/brightness
chmod 664 /sys/class/backlight/intel_backlight/brightness

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/00_screen] (755 root)
getXuser() {
        export user=`pinky -fw | awk '{ if ($2 == ":'$displaynum'" || $(NF) == ":'$displaynum'" ) { print $1; exit; } }'`
}
for x in /tmp/.X11-unix/*; do
    displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
    getXuser;
    case "$1" in
    thaw|resume)
        getXuser;
        sudo -u $user env DISPLAY=":$displaynum" /usr/bin/xrandr --auto
            ;;
    *)
            ;;
    esac
done
exit 0

[/etc/pm/sleep.d/99wifi] (755 root)
case "${1}" in
        hibernate)
        sudo service network-manager stop
        /sbin/rmmod ath9k
                ;;
    resume|thaw)
                /sbin/modprobe ath9k
        sudo service network-manager restart
        ;;
esac
exit 0

[/etc/pm/sleep.d/99zcyapa] (755 root)
getXuser() {
        user=`pinky -fw | awk '{ if ($2 == ":'$displaynum'" || $(NF) == ":'$displaynum'" ) { print $1; exit; } }'`
        if [ x"$user" = x"" ]; then
                startx=`pgrep -n startx`
                if [ x"$startx" != x"" ]; then
                        user=`ps -o user --no-headers $startx`
                fi
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XSESSIONRC=$userhome/.xsessionrc
        else
                export XSESSIONRC=""
        fi
}
case "${1}" in
    hibernate)
    /sbin/rmmod cyapa
        ;;
    resume|thaw)
        COUNTER=0
        while [  $COUNTER -lt 10 ]; do
            date >>/tmp/99_cyapa
            /sbin/modprobe cyapa
        sleep 1
        dmesg | grep cyapa | tail -1 | grep "\(error\|fail\)" >/dev/null
        RES=$?
        if [ ${RES} -ne 1 ] ; then
        /sbin/rmmod cyapa
        sleep 1
        else
        #done
        COUNTER=11
        fi
        
            COUNTER=`expr $COUNTER + 1`
        done
        ;;
esac
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x168c:0x0034 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    4.908726] ath: phy0: ASPM enabled: 0x43
[    4.908732] ath: EEPROM regdomain: 0x6c
[    4.908733] ath: EEPROM indicates we should expect a direct regpair map
[    4.908736] ath: Country alpha2 being used: 00
[    4.908737] ath: Regpair used: 0x6c
[    5.550709] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   75.335748] wlan0: authenticate with <MAC 't1242798_5GHz' [AC2]>
[   75.348333] wlan0: send auth to <MAC 't1242798_5GHz' [AC2]> (try 1/3)
[   75.349190] wlan0: authenticated
[   75.350039] wlan0: associate with <MAC 't1242798_5GHz' [AC2]> (try 1/3)
[   75.351448] wlan0: RX AssocResp from <MAC 't1242798_5GHz' [AC2]> (capab=0x401 status=0 aid=2)
[   75.351521] wlan0: associated
[   75.351532] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   95.990244] wlan0: deauthenticating from <MAC 't1242798_5GHz' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)

########## wireless info END ############


```

any help is appreciated.



File:
[ATTACH]269255[/ATTACH]

---

