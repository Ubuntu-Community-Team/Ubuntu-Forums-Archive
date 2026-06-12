---
title: "Wireless Network Issues"
date: 2014-05-21
forum: Networking &amp; Wireless
---

### Post by Pieman15 on 2014-05-21
Hello All - 

My computer randomly disconnects from my wireless network and although the computer recognizes my wireless network's signal, it will often not reconnect. I am using the same laptop and wireless router for the past several years and have not made any recent changes to either. I have two other devices in close proximity that use the wireless without issue. The issue actually occurred before upgrading to 14.04, but seems to be more frequent since the upgrade. My wireless router is an old Linksys WRT54G.

Any help is appreciated. Please forgive my ignorance, but I am not sure where to start troubleshooting on this one. The issue seems to be more software based than hardware.

---

### Post by oldos2er on 2014-05-21
Moved to Networking & Wireless.

---

### Post by varunendra on 2014-05-22
Please follow the instructions in this post to download and run 'wireless_script' (experimental version), and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by Pieman15 on 2014-05-22
Varun - As requested. Thank you for your assistance.

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Pieman 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz
Memory : 2014 MB
Uptime : 19:30:41 up 1 day,  3:56,  2 users,  load average: 0.97, 0.33, 0.14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
    Subsystem: Dell Device [1028:0228]
    Kernel driver in use: b44
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
    Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 05b8:3155 Agiler, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:"the house"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 the house>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1487  Invalid misc:786   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

dell_wmi               12665  0 
sparse_keymap          13708  1 dell_wmi
wmi                    18673  1 dell_wmi
ssb_hcd                12749  0 
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  3 b43,b44,ssb_hcd


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
====================o=============o========o==============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
====================o=============o========o==============o=========o===========o==============o===========
 eth0               | Wired       | b44    | unavailable  | no      |           |              | <MAC eth0>
--------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0  [the house] | 802.11 WiFi | b43    | connected    | yes     | 48 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *the house:      Infra, <MAC C-01 the house>, Freq 2462 MHz, Rate 54 Mb/s, Strength 53 WPA WPA2

    Address:         192.168.1.105
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
--------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

TallPaulians         : ssid=TallPaulians | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
the house            : ssid=the house | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 
Verizon-890L-73F3    : ssid=Verizon-890L-73F3 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#Static IP for wlan0


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.171/2.127/3.083/0.956 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.110/0.110/0.110/0.000 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency=2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 the house>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"the house"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000073d0df4845
                    Extra: Last beacon: 16ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist iwlwifi

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ssb_hcd]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/usb/host/ssb-hcd.ko
srcversion:     2A4C0EB5791EE9A11133FCB
depends:        ssb

[b43]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
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
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0 (b44)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:0c:00.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modules]
ose# /etc/modules: kernel modules to load at boot time.
b43
coretemp

[/etc/rc.local]
NetworkManager
exit 0

[/etc/modprobe.d]
blacklist.conf~   : blacklist evbug
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
                    Reading package lists...
                    Building dependency tree...Reading package lists...
                    Building dependency tree...
                    Reading state information...
                    Reading state information...
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
iwlwifi.conf.dpkg-old: options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/95hdparm-apm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/disable_wol] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/intel-audio-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/laptop-mode] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pci_devices] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/pcie_aspm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sata_alpm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/sched-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/usb_bluetooth] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0

[/etc/pm/power.d/xfs_buffer] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/

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

    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi

exit 0


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=ed2e5fcc-6dd5-48ef-b2f3-4e25a3bff58c ro quiet splash acpi=force


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[16331.282156] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2588 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16331.282319] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2589 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16352.122324] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2605 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16391.347979] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2629 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16391.348558] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2630 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16412.152081] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2646 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16451.286561] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2667 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16451.286647] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2668 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16472.183994] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2684 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16511.289069] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2705 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16511.289214] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2706 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16532.205253] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2723 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16571.295583] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2744 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16571.297191] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2745 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16592.248826] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2761 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16631.298104] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2789 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16631.298259] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2790 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16652.274504] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2806 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16671.286894] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=2835 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[16691.300919] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2859 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16711.313183] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2880 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16751.367797] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2907 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16761.335062] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2912 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16771.337188] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2920 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16811.305122] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2944 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16811.305566] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2945 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16831.449010] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2959 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16871.309381] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2983 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16871.310353] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2984 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16891.395533] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=2998 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16931.311922] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3024 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16931.312532] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3025 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16951.432915] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3039 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16991.315330] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3062 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[16991.315821] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3063 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17011.458890] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3077 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17051.320854] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3100 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17051.320991] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3101 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17071.485735] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3115 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17111.331451] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3138 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17111.332102] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3139 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17131.528302] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3154 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17171.335619] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3177 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17171.336178] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3178 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17191.564244] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3192 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17231.340405] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3218 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17231.340585] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3219 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17251.591745] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3233 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17271.600984] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=3264 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[17291.344581] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3287 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17311.622232] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3308 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17351.445162] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3334 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17361.664075] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3339 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17371.672488] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3346 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17411.350920] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3369 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17411.352819] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3370 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17431.702105] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3384 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17471.356929] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3407 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17471.357012] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3408 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17491.730025] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3422 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17531.357160] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3445 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17531.357649] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3446 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17551.765564] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3460 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17591.359419] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3483 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17591.359883] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3484 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17611.815432] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3498 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17651.361702] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3521 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17651.362041] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3522 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17671.840854] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3536 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17711.365357] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3559 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17711.366264] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3560 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17731.891006] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3575 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17771.368627] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3598 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17771.369740] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3599 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17791.923865] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3613 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17831.373136] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3639 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17831.374227] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3640 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17851.964647] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3654 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17871.976296] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=3685 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[17891.376317] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3708 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17912.006715] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3729 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17951.419494] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3755 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17962.024687] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3760 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[17972.029810] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3766 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18011.450895] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3790 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18011.451398] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3791 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18032.075559] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3804 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18071.407684] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3829 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18071.409627] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3830 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18092.110465] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3842 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18131.400316] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3866 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18131.400497] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3867 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18152.156808] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3880 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18191.403062] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3904 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18191.403605] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3905 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18212.192996] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3918 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18251.406804] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3942 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18251.407280] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3943 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18272.228883] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3956 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18311.414567] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3980 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18311.428604] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3981 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18332.259849] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=3995 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18371.414128] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4019 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18371.414566] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4020 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18392.277778] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4033 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18431.417314] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4060 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18431.417765] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4061 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18452.284229] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4074 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18471.314929] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=4103 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[18491.422766] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4129 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18512.345446] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4149 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18551.496345] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4180 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18562.378485] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4183 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18572.385238] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4191 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18611.430990] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4216 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18611.431155] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4217 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18632.417685] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4230 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18652.426454] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4248 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18701.439134] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4281 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18701.441194] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4282 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18712.437492] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4287 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18761.439796] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4320 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18761.440385] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4321 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18771.466211] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4327 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18821.442682] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4360 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18821.443046] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4361 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18831.492187] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4366 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18881.446119] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4400 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18881.446749] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4401 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18891.524334] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4406 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18941.450478] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4437 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18941.451445] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4438 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[18951.554224] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4445 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19008.517533] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4482 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19018.584741] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4485 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19018.586424] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4486 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19053.207495] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=4511 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[19054.205755] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=4517 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[19071.600906] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=4536 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[19095.609483] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=4571 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[19128.428116] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4592 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19138.612893] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4601 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19188.433140] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4636 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19188.433614] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4637 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19198.618049] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4642 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19248.437222] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4677 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19248.437710] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4678 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19258.623133] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4683 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19308.441801] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4715 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19308.442388] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4716 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19318.650398] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4721 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19368.444793] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4753 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19368.444875] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4754 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19378.680531] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4759 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19428.448273] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4791 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19428.448997] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4792 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19438.707981] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4797 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19488.451944] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4829 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19488.452083] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4830 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19498.743319] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4835 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19548.456504] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4868 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19548.459251] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4869 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19558.779299] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4874 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19608.458852] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4906 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19608.459470] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4907 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19618.802530] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=4912 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19653.229287] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=4938 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[19654.229690] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=4943 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[19671.828066] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=4963 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[19691.845368] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=4997 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[19728.467763] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5019 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19738.875609] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5025 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19788.469781] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5057 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19788.469861] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5058 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19798.907263] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5063 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19848.471978] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5098 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19848.472235] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5099 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19858.940923] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5104 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19908.475187] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5136 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19908.476118] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5137 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19918.960813] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5142 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19968.479204] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5174 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19968.479806] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5175 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[19978.967280] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5180 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20028.484400] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5212 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20028.485087] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5213 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20038.973855] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5218 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20088.486698] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5250 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20088.487457] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5251 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20098.985756] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5256 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20148.490321] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5287 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20148.490782] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5288 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20158.990985] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5295 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20208.493246] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5325 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20208.493948] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5326 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20219.003662] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5333 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20253.247368] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=5359 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[20254.246901] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=5364 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[20272.004266] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=5384 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[20292.009269] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=5415 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[20328.500427] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5438 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20339.015536] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5446 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20388.506992] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5476 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20388.507882] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5477 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20399.024543] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5484 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20448.509237] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5517 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20448.509992] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5518 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20459.048378] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5525 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20508.514838] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5559 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20508.517855] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5560 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20519.082716] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5568 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20568.517086] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5599 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20568.517998] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5600 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20579.112941] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5607 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20628.523288] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5638 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20628.524159] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5639 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20639.148773] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5646 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20688.526319] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5677 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20688.526576] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5678 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20699.199353] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5686 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20748.530913] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5718 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20748.531856] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5719 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20759.225893] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5726 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20808.534416] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5758 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20808.536361] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5759 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20819.258928] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5766 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20853.267945] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=5792 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[20854.268498] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=5797 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[20871.284156] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=5817 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[20892.288409] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=5848 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[20928.545317] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5871 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20939.316083] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5879 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20988.546862] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5909 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20988.547720] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5910 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[20999.343706] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5917 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21048.550769] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5950 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21048.551624] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5951 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21059.375198] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5958 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21108.556810] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5988 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21108.557482] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5989 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21119.404223] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=5996 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21168.559001] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6026 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21168.560288] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6027 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21179.431349] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6034 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21228.565525] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6064 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21228.568491] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6065 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21239.445002] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6072 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21288.567011] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6102 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21288.567553] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6103 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21299.473418] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6110 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21348.570336] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6141 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21348.570850] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6142 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21359.506384] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6149 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21408.575058] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6179 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21408.576411] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6180 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21419.535988] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6187 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21453.289115] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=6213 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[21454.290056] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=6218 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[21471.562607] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=6238 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[21493.575098] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=6269 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[21518.587571] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6290 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21538.597449] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6302 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21558.587375] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6317 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21578.610162] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6328 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21598.620936] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6340 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21618.591493] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6355 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21638.643687] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6369 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21658.653649] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6381 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21678.594596] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6396 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21698.674009] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6407 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21718.694529] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6419 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21738.598098] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6434 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21758.696790] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6445 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21778.708653] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6457 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21798.602238] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6472 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21818.723771] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6483 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21838.731332] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6495 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21858.605562] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6510 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21878.756189] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6521 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21898.761026] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6533 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21918.609411] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6549 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21938.787122] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6560 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21958.796916] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6572 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21978.612748] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6587 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[21998.823163] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6597 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22018.830623] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6610 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22038.615862] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6625 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22053.313432] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=6634 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[22071.859354] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=6658 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[22094.871768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=6690 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[22118.886347] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6710 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22138.895953] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6723 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22158.622705] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6738 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22178.917060] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6748 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22198.928004] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6761 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22218.630133] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6776 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22238.949307] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6789 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22258.960901] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6802 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22278.631644] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6817 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22298.981424] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6827 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22318.993088] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6840 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22338.636078] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6855 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22359.014940] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6865 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22379.021632] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6878 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22398.639611] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6897 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22419.045008] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6907 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22439.055429] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6921 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22458.643028] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6936 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22479.085089] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6947 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22499.082932] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6960 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22518.649152] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6976 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22539.095754] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=6987 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22559.104707] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7000 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22578.652248] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7016 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22599.115888] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7026 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22619.117554] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7040 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22638.655478] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7055 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22653.330980] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=7064 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[22672.125927] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=7088 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[22696.125104] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=7123 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[22719.129608] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7143 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22739.129115] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7154 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22758.661926] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7171 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22779.208093] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7182 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22799.134423] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7193 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22818.665576] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7210 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22839.142158] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7223 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22859.146513] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7234 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22878.668509] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7251 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22899.160813] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7261 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22919.165001] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7272 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22938.671325] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7289 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22959.178280] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7299 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22979.186237] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7310 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[22998.676877] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7327 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23019.205465] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7337 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23039.215615] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7348 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23058.678347] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7365 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23079.238134] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7375 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23099.248997] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7386 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23118.684799] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7404 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23139.267739] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7414 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23159.279882] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7425 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23178.688612] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7442 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23199.294671] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7452 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23219.306345] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7463 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23238.691819] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7480 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23253.352170] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=7489 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[23272.328529] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=7512 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[23291.338319] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=7540 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[23319.366105] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7565 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23339.392476] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7576 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23358.698928] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7593 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23379.413375] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7603 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23399.422406] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7614 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23418.703372] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7631 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23439.445527] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7644 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23459.457507] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7655 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23478.708128] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7672 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23499.490549] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7682 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23519.503748] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7693 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23538.717350] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7710 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23559.517152] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7720 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23579.520592] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7731 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23598.715543] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7748 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23619.537304] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7758 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23639.539087] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7769 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23658.718806] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7786 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23679.546395] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7796 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23699.548379] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7807 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23718.721894] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7823 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23739.551623] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7835 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23759.553311] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7846 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23778.725169] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7861 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23799.556734] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7873 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23819.558539] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7884 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23838.728710] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7899 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23853.856301] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=7914 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[23872.563948] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=7933 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[23891.566905] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=7959 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[23912.567402] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=7981 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[23939.571345] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=7997 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23958.736994] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8012 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23979.579067] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8024 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[23999.581777] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8035 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24018.738091] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8050 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24039.592867] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8065 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24059.598954] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8076 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24078.741427] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8091 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24099.614673] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8103 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24119.652986] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8114 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24138.749325] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8129 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24159.680893] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8141 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24179.681231] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8152 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24198.755565] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8167 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24219.705562] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8179 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24239.715032] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8190 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24258.758592] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8205 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24279.731291] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8217 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24299.741091] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8228 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24318.761998] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8250 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24339.759837] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8260 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24358.771516] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8272 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24378.765666] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8289 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24398.787431] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8300 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24418.797616] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8311 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24438.771514] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8326 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24453.392812] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=8338 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[24471.816462] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=8361 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[24492.821668] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=8390 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[24511.827172] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=8410 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[24538.833058] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8427 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24558.774699] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8442 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24578.855438] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8455 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24598.859711] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8466 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24618.779392] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8483 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24638.876215] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8498 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24658.887941] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8509 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24678.788398] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8524 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24698.905680] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8536 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24718.917205] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8547 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24738.785271] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8562 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24758.936525] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8574 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24778.946584] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8585 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24798.789406] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8600 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24818.970930] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8612 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24838.981342] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8623 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24858.792464] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8638 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24879.005460] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8650 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24899.018138] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8661 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24918.796154] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8677 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24939.041143] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8689 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24959.053055] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8700 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24978.798762] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8715 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[24999.057318] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8727 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25019.059194] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8738 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25038.801918] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8753 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25053.482315] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=8768 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[25072.063528] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=8787 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[25092.066534] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=8814 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[25113.067213] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=8834 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[25139.069518] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8851 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25158.810818] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8865 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25179.072743] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8878 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25199.074835] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8889 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25218.812283] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8903 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25239.084246] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8919 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25259.085781] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8930 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25278.815774] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8944 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25299.128693] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8957 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25319.103226] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8968 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25338.818170] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8982 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25359.120938] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=8995 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25379.124907] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9006 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25398.821438] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9020 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25419.150078] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9033 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25439.163676] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9044 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25458.832093] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9058 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25479.181505] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9071 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25499.189720] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9082 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25518.830705] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9097 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25539.210252] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9110 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25559.219574] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9121 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25578.832575] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9135 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25599.241581] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9148 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25619.253028] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9159 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25638.839068] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9173 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25653.432708] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=9185 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[25671.433733] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=9206 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[25691.299206] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=9235 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[25713.321408] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=9255 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[25739.327657] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9272 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25758.845184] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9286 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25779.337755] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9299 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25799.345412] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9310 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25818.848381] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9324 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25839.343704] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9340 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25859.345690] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9351 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25878.851725] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9365 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25899.350243] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9378 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25919.372304] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9389 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25938.856978] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9403 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25959.381104] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9416 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25979.359556] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9427 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[25998.858970] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9441 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26019.370971] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9454 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26039.377572] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9465 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26058.862411] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9479 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26079.397252] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9492 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26099.415350] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9503 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26118.866050] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9518 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26139.432639] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9529 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26159.442155] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9542 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[26178.870532] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9556 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[69393.688331] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9571 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[69407.030926] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9639 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[69407.031333] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9640 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[69407.031466] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9641 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[69407.032145] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9642 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95214.830690] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9657 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95238.327988] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9733 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95238.329970] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9734 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95238.332183] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9735 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95238.333510] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9736 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95249.246536] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9745 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95249.247399] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9746 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95249.247591] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9747 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95249.247719] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9748 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95253.023897] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=70 TOS=0x00 PREC=0x00 TTL=128 ID=9756 PROTO=UDP SPT=53033 DPT=161 LEN=50 
[95259.250568] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9759 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95259.250806] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9760 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95283.258611] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=9780 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[95298.331612] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9789 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95319.271866] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9811 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95358.335380] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9834 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95358.335899] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9835 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95379.282382] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9851 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95418.339054] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9874 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95418.340629] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9875 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95439.297301] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9891 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95478.342868] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9914 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95478.345712] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9915 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95498.383267] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9933 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95538.346574] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9958 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95538.347999] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9959 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95558.419727] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9975 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95598.350238] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9996 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95598.350689] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=9997 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95618.447322] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10013 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95658.355233] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10034 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95658.355864] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10035 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95678.471012] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10051 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95718.365539] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10072 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95718.366145] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10073 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95738.511838] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10089 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95778.370908] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10110 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95778.371620] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10111 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95798.534477] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10127 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95838.377086] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10148 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95838.377290] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10149 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95858.559221] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10173 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95878.577508] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=10191 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[95898.380356] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10208 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95918.592981] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10228 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95958.386694] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10249 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95958.386783] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10250 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[95978.618462] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10266 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96018.391006] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10287 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96018.392353] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10288 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96038.636183] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10304 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96078.394904] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10325 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96078.395133] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10326 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96098.665530] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10342 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96138.400368] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10363 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96138.401200] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10364 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96158.707293] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10380 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96198.406565] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10401 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96198.407060] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10402 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96218.742768] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10418 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96258.412214] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10439 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96258.413612] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10440 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96278.794419] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10456 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96318.416945] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10477 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96318.417603] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10478 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96338.826773] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10494 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96378.421090] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10516 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96378.421245] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10517 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96398.836511] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10533 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96438.424690] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10554 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96438.425017] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10555 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96458.881804] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10580 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96478.898907] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=10600 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[96498.430123] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10622 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96518.922903] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10642 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96558.434875] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10663 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96558.440167] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10664 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96578.946300] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10680 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96618.438475] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10701 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96618.439071] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10702 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96638.979203] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10718 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96678.442090] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10737 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96678.443252] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10738 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96699.003505] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10756 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96738.458196] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10775 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96738.458648] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10776 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96759.030100] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10794 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96798.461886] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10814 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96798.462786] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10815 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96819.056192] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10833 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96858.466068] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10852 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96858.466147] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10853 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96879.086013] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10871 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96918.469260] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10890 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96918.474951] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10891 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[96939.113207] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10909 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97876.194309] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=10996 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97887.000996] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11000 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97887.003879] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11001 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97887.004002] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11002 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97887.004252] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11003 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97896.972803] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11014 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97896.973316] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11015 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97896.973502] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11016 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97896.973569] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11017 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97936.110974] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11036 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97936.111430] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11037 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97936.112281] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11038 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97947.013102] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11042 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97957.018433] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11062 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[97981.031004] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=69 TOS=0x00 PREC=0x00 TTL=128 ID=11079 PROTO=UDP SPT=53033 DPT=161 LEN=49 
[98007.047642] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11098 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98017.056063] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11109 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98056.118665] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11131 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98066.111097] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11137 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98126.163890] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11176 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98126.164662] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11177 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98126.164925] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11178 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98176.124881] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11211 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98176.125639] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11212 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98186.199681] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11217 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98196.205063] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11228 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98246.231753] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11255 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98246.232760] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11256 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98256.236107] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11266 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98296.135257] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11285 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98306.264509] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11293 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98316.269499] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11304 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98356.142961] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11323 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98366.297590] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11331 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98376.303155] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11342 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98416.144792] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11361 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98426.331871] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11369 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98436.339050] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11380 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98476.152445] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11399 PROTO=UDP SPT=53033 DPT=161 LEN=86 
[98476.204454] [UFW BLOCK] IN=wlan0 OUT= MAC=<MAC wlan0>:<MAC ID removed>:08:00 SRC=192.168.1.103 DST=192.168.1.105 LEN=106 TOS=0x00 PREC=0x00 TTL=128 ID=11402 PROTO=UDP SPT=53033 DPT=161 LEN=86 

    ======== Done ========

```

---

### Post by varunendra on 2014-05-24
> **Pieman15 said:**
> ```

    *the house:      Infra, <MAC C-01 the house>, Freq 2462 MHz, Rate 54 Mb/s, Strength 53 **[COLOR="#FF0000"]WPA WPA2[/COLOR]**
...
                    ESSID:"the house"
                    ....
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```

First off, please change the encryption type in your router to pure WPA2-PSK with AES (CCMP). No WPA/WPA2 mixed mode, no TKIP. Please refer to your router's user manual to see how to change it (it must be under 'wireless security' section). Reboot the router after saving the change.

Keep it that way even if it doesn't seem to help. If the problem persists, then we'll need to do some experiments to see what works and what doesn't. I'd begin with disabling the power saving script for the wireless, which means running the following command -
```
sudo chmod -x /etc/pm/power.d/wireless
```
Reboot, and see if it works any better. What the above command does is to remove the 'executable' permission from a script (thus disabling it) that tries to save power on wireless when it 'thinks' it should. This may help where aggressive power saving mode (causing weak, unstable signal strength) is the cause of the problem.

Try these for now, and let me know the result.

---

### Post by tgalati4 on 2014-05-24
Try the above, but it may be a simple case of interference from neighbors--as pesky as they can be.

How many wireless networks show up when you click on the network icon?  For me, I'm showing 9 with a pretty strong signal.

These results are telling:

> wlan0     IEEE 802.11bg  ESSID:"the house"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 the house>   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1487  Invalid misc:786   Missed beacon:0


Link quality is average.  You probably want 50/70 or better.  Your link speed should be 54Mb/sec if your signal is clear and you don't have too many other devices in the household.  Because you are down to 36Mb/sec, the wireless router has to throttle-down to maintain the connection.  You are running bg mode.  Try changing to g-only mode.  Transmit retries could indicate an antenna problem with your laptop.  Try reseating the wireless card and antenna connections--be careful, they are delicate.  Because the antenna runs through the hinge, it is subject to twisting and eventual breakdown.  Invalid misc could be mangled packets because of a bad antenna or interference.

Run the following (you don't need to post it) and compare the number of other AP's and their signal strength.  If over 5 have a similar signal strength, then interference is a probable cause.  Get new neighbors.

```
iwlist wlan0 scan
iwlist wlan0 scan | grep Quality 
```

Try installing *wifi-radar* and watch the local wireless signals around you.

Try moving your router antenna to a better location--5 to 6 feet high and away from other electronics.  You want it central to where your wireless devices are used.

---

### Post by varunendra on 2014-05-25
> **tgalati4 said:**
> ....Get new neighbors.

:lolflag:

This aside (or including This ^^ ;)), very nice and useful info!

---

