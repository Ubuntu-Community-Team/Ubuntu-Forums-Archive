---
title: "Wireless not working"
date: 2019-11-22
forum: Networking &amp; Wireless
---

### Post by evanm11710 on 2019-11-22
I have already visited this thread:

[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

After rebooting this did not solve the issue. I am running 14.04 and had been trying to upgrade to 16.04 when this issue started (after a failed attempt).

In any case, I must note that I could not run the wireless-info script as I can not get text files to run as executables (I know I am supposed to go to files->preferences->behaviors tab to have it ask me to run text files as executables but that menu path is simply NOT THERE at all).

---

### Post by uRock on 2019-11-22
To make the wireless script executable, open a terminal and navigate to where it is using the cd command(if not in the home folder), then run the following,
```
chmod +x filename
```
You should now be able to execute it.

---

### Post by evanm11710 on 2019-11-23
> **uRock said:**
> To make the wireless script executable, open a terminal and navigate to where it is using the cd command(if not in the home folder), then run the following,
```
chmod +x filename
```
You should now be able to execute it.

Ok. Thanks for that. Here is the dump file contents:

```
########## wireless info START ##########

Report from: 15 May 2015 12:44 EDT -0400

Booted last: 15 May 2015 12:35 EDT -0400

Script from: 22 Oct 2018 03:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.6 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-170-generic #220-Ubuntu SMP Thu May 9 12:40:49 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, "acpi_osi=Windows, 2013", vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Dell Device [1028:0019]

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0c45:670c Microdia 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### secure boot #######################

SecureBoot enabled

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18133  0 
dcdbas                 14928  1 dell_laptop
cfg80211              496328  0 
wmi                    19177  1 dell_wmi

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

##### resolv.conf #######################

[777 root &#8216;/etc/resolv.conf&#8217; -> &#8216;../run/resolvconf/resolv.conf&#8217;]

##### network managers ##################

Installed:

    NetworkManager

Running:

root       985     1  0 12:35 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: disconnected

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager config #############

[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Anubis.guests-6401d0ec-3ed1-4930-84e9-6a38a17a6d56]] (600 root)
[connection] id=Anubis.guests | type=802-11-wireless
[802-11-wireless] ssid=Anubis.guests | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MCO Internet]] (600 root)
[connection] id=MCO Internet | type=802-11-wireless
[802-11-wireless] ssid=MCO Internet | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/DXFF1]] (600 root)
[connection] id=DXFF1 | type=802-11-wireless
[802-11-wireless] ssid=DXFF1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Boingo Hotspot]] (600 root)
[connection] id=Boingo Hotspot | type=802-11-wireless
[802-11-wireless] ssid=Boingo Hotspot | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/OC-Premium]] (600 root)
[connection] id=OC-Premium | type=802-11-wireless
[802-11-wireless] ssid=OC-Premium | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/buzzard]] (600 root)
[connection] id=buzzard | type=802-11-wireless
[802-11-wireless] ssid=buzzard | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Engineering]] (600 root)
[connection] id=Engineering | type=802-11-wireless
[802-11-wireless] ssid=Engineering | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Anubis.guests]] (600 root)
[connection] id=Anubis.guests | type=802-11-wireless
[802-11-wireless] ssid=Anubis.guests | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Porter Square Guest]] (600 root)
[connection] id=Porter Square Guest | type=802-11-wireless
[802-11-wireless] ssid=Porter Square Guest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/_Free_ORD_Wi-Fi]] (600 root)
[connection] id=_Free_ORD_Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=_Free_ORD_Wi-Fi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Anubis]] (600 root)
[connection] id=Anubis | type=802-11-wireless
[802-11-wireless] ssid=Anubis | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/hhonors]] (600 root)
[connection] id=hhonors | type=802-11-wireless
[802-11-wireless] ssid=hhonors | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/RENAISSANCE-GUEST]] (600 root)
[connection] id=RENAISSANCE-GUEST | type=802-11-wireless
[802-11-wireless] ssid=RENAISSANCE-GUEST | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NTPS-Guest]] (600 root)
[connection] id=NTPS-Guest | type=802-11-wireless
[802-11-wireless] ssid=NTPS-Guest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HolidaayInnCentralDC]] (600 root)
[connection] id=HolidaayInnCentralDC | type=802-11-wireless
[802-11-wireless] ssid=HolidaayInnCentralDC | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/nasa-guest]] (600 root)
[connection] id=nasa-guest | type=802-11-wireless
[802-11-wireless] ssid=nasa-guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/gogoinflight]] (600 root)
[connection] id=gogoinflight | type=802-11-wireless
[802-11-wireless] ssid=gogoinflight | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/5776]] (600 root)
[connection] id=5776 | type=802-11-wireless
[802-11-wireless] ssid=5776 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/RTCA]] (600 root)
[connection] id=RTCA | type=802-11-wireless
[802-11-wireless] ssid=RTCA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/CaCa HotSpot]] (600 root)
[connection] id=CaCa HotSpot | type=802-11-wireless
[802-11-wireless] ssid=CaCa HotSpot | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/oxfordsuites]] (600 root)
[connection] id=oxfordsuites | type=802-11-wireless
[802-11-wireless] ssid=oxfordsuites | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/concoursep]] (600 root)
[connection] id=concoursep | type=802-11-wireless
[802-11-wireless] ssid=concoursep | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/ACOORD]] (600 root)
[connection] id=ACOORD | type=802-11-wireless
[802-11-wireless] ssid=ACOORD | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AELHQ-BONHAM]] (600 root)
[connection] id=AELHQ-BONHAM | type=802-11-wireless
[802-11-wireless] ssid=AELHQ-BONHAM | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/LAX Free WiFi]] (600 root)
[connection] id=LAX Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=LAX Free WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SM-G900PF8C]] (600 root)
[connection] id=SM-G900PF8C | type=802-11-wireless
[802-11-wireless] ssid=SM-G900PF8C | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Homestead]] (600 root)
[connection] id=Homestead | type=802-11-wireless
[802-11-wireless] ssid=Homestead | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-2C52]] (600 root)
[connection] id=HOME-2C52 | type=802-11-wireless
[802-11-wireless] ssid=HOME-2C52 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Fly Dayton Public Wifi]] (600 root)
[connection] id=Fly Dayton Public Wifi | type=802-11-wireless
[802-11-wireless] ssid=Fly Dayton Public Wifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/boingo hotspot]] (600 root)
[connection] id=boingo hotspot | type=802-11-wireless
[802-11-wireless] ssid=boingo hotspot | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/NASA GUEST]] (600 root)
[connection] id=NASA GUEST | type=802-11-wireless
[802-11-wireless] ssid=NASA GUEST | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/blueStreak]] (600 root)
[connection] id=blueStreak | type=802-11-wireless
[802-11-wireless] ssid=blueStreak | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Reagan National WiFi]] (600 root)
[connection] id=Reagan National WiFi | type=802-11-wireless
[802-11-wireless] ssid=Reagan National WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WestinGuestRooms]] (600 root)
[connection] id=WestinGuestRooms | type=802-11-wireless
[802-11-wireless] ssid=WestinGuestRooms | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/DXFF1 1]] (600 root)
[connection] id=DXFF1 1 | type=802-11-wireless
[802-11-wireless] ssid=DXFF1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HolidayInn]] (600 root)
[connection] id=HolidayInn | type=802-11-wireless
[802-11-wireless] ssid=HolidayInn | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/CLT Free WiFi]] (600 root)
[connection] id=CLT Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=CLT Free WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/wbi wireless]] (600 root)
[connection] id=wbi wireless | type=802-11-wireless
[802-11-wireless] ssid=wbi wireless | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Plaza Ocean Club SKYFY09E]] (600 root)
[connection] id=Plaza Ocean Club SKYFY09E | type=802-11-wireless
[802-11-wireless] ssid=Plaza Ocean Club SKYFY09E | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### Netplan config ####################

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

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-170-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     31968F04B23058DCB1788B5
depends:        
intree:         Y
vermagic:       3.13.0-170-generic SMP mod_unload modversions retpoline 
signer:         Magrathea: Glacier signing key
sig_key:        EB:DD:61:40:14:3C:AD:81:89:B3:8F:E3:2B:A1:47:C6:AC:F9:F0:07
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

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
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/video.conf]
options video use_native_backlight=1

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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############
```

---

### Post by jeremy31 on 2019-11-23
Disable Secure Boot in BIOS/UEFI settings, leave Secure Boot keys alone and then the wifi should work

---

### Post by evanm11710 on 2019-11-23
> **jeremy31 said:**
> Disable Secure Boot in BIOS/UEFI settings, leave Secure Boot keys alone and then the wifi should work

Ok. I have disabled secure boot in BIOS, left keys alone, rebooted, ran the update and dist-upgrade again, rebooted again. I get the same issue on startup "Disconnected - you are now disconnected from internet"

I should note that it is also warning me that Ubuntu has experienced an internal error (this may or may not be related) every time I boot and log in.

---

### Post by jeremy31 on 2019-11-23
Lets see new script results ```
./wireless-info
```

---

### Post by evanm11710 on 2019-11-23
The script results are blank?

---

### Post by praseodym on 2019-11-23
14.04 is outdated. Try installing a LTS version, 16.04 or 18.04

---

### Post by evanm11710 on 2019-11-23
Ive been trying to upgrade to 16.04 from 14.04 without starting with a fresh image and losing everything.

---

### Post by praseodym on 2019-11-23
So, you tried, or you did?! How did you try?

Edit: Deactivate SecureBoot

---

### Post by jeremy31 on 2019-11-23
Ok, run the entire wireless script command again and post results

---

### Post by evanm11710 on 2019-11-23
Using the upgrade manager - but there were some security updates it needed first. It was during that process that I lost wifi and could not get it back. To be clear, the security updates went through. It was a 40GB chrome update that kept failing, and during one of the attempts to get that I lost wifi during a reboot.

---

### Post by evanm11710 on 2019-11-23
> **jeremy31 said:**
> Ok, run the entire wireless script command again and post results

Results in a blank file.

---

### Post by evanm11710 on 2019-11-23
> **jeremy31 said:**
> Ok, run the entire wireless script command again and post results


Okay, I got it now. File got corrupted somehow. 
```

########## wireless info START ##########


Report from: 16 May 2015 11:53 EDT -0400


Booted last: 16 May 2015 08:35 EDT -0400


Script from: 22 Oct 2018 03:34 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.6 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-170-generic #220-Ubuntu SMP Thu May 9 12:40:49 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, "acpi_osi=Windows, 2013", vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Dell Device [1028:0019]


##### lsusb #############################


Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 002: ID 0c45:670c Microdia 
Bus 002 Device 003: ID 0e8d:1887 MediaTek Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


##### secure boot #######################


SecureBoot disabled


##### lsmod #############################


dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18133  0 
dcdbas                 14928  1 dell_laptop
cfg80211              496328  0 
wmi                    19177  1 dell_wmi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


##### iwconfig ##########################


lo        no wireless extensions.


##### route #############################


##### resolv.conf #######################


[777 root &#8216;/etc/resolv.conf&#8217; -> &#8216;../run/resolvconf/resolv.conf&#8217;]


##### network managers ##################


Installed:


	NetworkManager


Running:


root       898     1  0 08:35 ?        00:00:01 NetworkManager


##### NetworkManager info ###############


NetworkManager Tool


State: disconnected


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager config #############


[[/etc/NetworkManager/NetworkManager.conf]]
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq
[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Anubis.guests-6401d0ec-3ed1-4930-84e9-6a38a17a6d56]] (600 root)
[connection] id=Anubis.guests | type=802-11-wireless
[802-11-wireless] ssid=Anubis.guests | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/MCO Internet]] (600 root)
[connection] id=MCO Internet | type=802-11-wireless
[802-11-wireless] ssid=MCO Internet | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DXFF1]] (600 root)
[connection] id=DXFF1 | type=802-11-wireless
[802-11-wireless] ssid=DXFF1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Boingo Hotspot]] (600 root)
[connection] id=Boingo Hotspot | type=802-11-wireless
[802-11-wireless] ssid=Boingo Hotspot | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/OC-Premium]] (600 root)
[connection] id=OC-Premium | type=802-11-wireless
[802-11-wireless] ssid=OC-Premium | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/buzzard]] (600 root)
[connection] id=buzzard | type=802-11-wireless
[802-11-wireless] ssid=buzzard | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Engineering]] (600 root)
[connection] id=Engineering | type=802-11-wireless
[802-11-wireless] ssid=Engineering | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Anubis.guests]] (600 root)
[connection] id=Anubis.guests | type=802-11-wireless
[802-11-wireless] ssid=Anubis.guests | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Porter Square Guest]] (600 root)
[connection] id=Porter Square Guest | type=802-11-wireless
[802-11-wireless] ssid=Porter Square Guest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/_Free_ORD_Wi-Fi]] (600 root)
[connection] id=_Free_ORD_Wi-Fi | type=802-11-wireless
[802-11-wireless] ssid=_Free_ORD_Wi-Fi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Anubis]] (600 root)
[connection] id=Anubis | type=802-11-wireless
[802-11-wireless] ssid=Anubis | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/hhonors]] (600 root)
[connection] id=hhonors | type=802-11-wireless
[802-11-wireless] ssid=hhonors | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/RENAISSANCE-GUEST]] (600 root)
[connection] id=RENAISSANCE-GUEST | type=802-11-wireless
[802-11-wireless] ssid=RENAISSANCE-GUEST | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/NTPS-Guest]] (600 root)
[connection] id=NTPS-Guest | type=802-11-wireless
[802-11-wireless] ssid=NTPS-Guest | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HolidaayInnCentralDC]] (600 root)
[connection] id=HolidaayInnCentralDC | type=802-11-wireless
[802-11-wireless] ssid=HolidaayInnCentralDC | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/nasa-guest]] (600 root)
[connection] id=nasa-guest | type=802-11-wireless
[802-11-wireless] ssid=nasa-guest | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/gogoinflight]] (600 root)
[connection] id=gogoinflight | type=802-11-wireless
[802-11-wireless] ssid=gogoinflight | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/5776]] (600 root)
[connection] id=5776 | type=802-11-wireless
[802-11-wireless] ssid=5776 | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/RTCA]] (600 root)
[connection] id=RTCA | type=802-11-wireless
[802-11-wireless] ssid=RTCA | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/CaCa HotSpot]] (600 root)
[connection] id=CaCa HotSpot | type=802-11-wireless
[802-11-wireless] ssid=CaCa HotSpot | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/oxfordsuites]] (600 root)
[connection] id=oxfordsuites | type=802-11-wireless
[802-11-wireless] ssid=oxfordsuites | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/concoursep]] (600 root)
[connection] id=concoursep | type=802-11-wireless
[802-11-wireless] ssid=concoursep | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/ACOORD]] (600 root)
[connection] id=ACOORD | type=802-11-wireless
[802-11-wireless] ssid=ACOORD | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/AELHQ-BONHAM]] (600 root)
[connection] id=AELHQ-BONHAM | type=802-11-wireless
[802-11-wireless] ssid=AELHQ-BONHAM | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/LAX Free WiFi]] (600 root)
[connection] id=LAX Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=LAX Free WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/SM-G900PF8C]] (600 root)
[connection] id=SM-G900PF8C | type=802-11-wireless
[802-11-wireless] ssid=SM-G900PF8C | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Homestead]] (600 root)
[connection] id=Homestead | type=802-11-wireless
[802-11-wireless] ssid=Homestead | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HOME-2C52]] (600 root)
[connection] id=HOME-2C52 | type=802-11-wireless
[802-11-wireless] ssid=HOME-2C52 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Fly Dayton Public Wifi]] (600 root)
[connection] id=Fly Dayton Public Wifi | type=802-11-wireless
[802-11-wireless] ssid=Fly Dayton Public Wifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/boingo hotspot]] (600 root)
[connection] id=boingo hotspot | type=802-11-wireless
[802-11-wireless] ssid=boingo hotspot | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/NASA GUEST]] (600 root)
[connection] id=NASA GUEST | type=802-11-wireless
[802-11-wireless] ssid=NASA GUEST | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/blueStreak]] (600 root)
[connection] id=blueStreak | type=802-11-wireless
[802-11-wireless] ssid=blueStreak | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/Reagan National WiFi]] (600 root)
[connection] id=Reagan National WiFi | type=802-11-wireless
[802-11-wireless] ssid=Reagan National WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/WestinGuestRooms]] (600 root)
[connection] id=WestinGuestRooms | type=802-11-wireless
[802-11-wireless] ssid=WestinGuestRooms | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/DXFF1 1]] (600 root)
[connection] id=DXFF1 1 | type=802-11-wireless
[802-11-wireless] ssid=DXFF1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/HolidayInn]] (600 root)
[connection] id=HolidayInn | type=802-11-wireless
[802-11-wireless] ssid=HolidayInn | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/CLT Free WiFi]] (600 root)
[connection] id=CLT Free WiFi | type=802-11-wireless
[802-11-wireless] ssid=CLT Free WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto


[[/etc/NetworkManager/system-connections/wbi wireless]] (600 root)
[connection] id=wbi wireless | type=802-11-wireless
[802-11-wireless] ssid=wbi wireless | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/Plaza Ocean Club SKYFY09E]] (600 root)
[connection] id=Plaza Ocean Club SKYFY09E | type=802-11-wireless
[802-11-wireless] ssid=Plaza Ocean Club SKYFY09E | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


##### module infos ######################


[cfg80211]
filename:       /lib/modules/3.13.0-170-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     31968F04B23058DCB1788B5
depends:        
intree:         Y
vermagic:       3.13.0-170-generic SMP mod_unload modversions retpoline 
signer:         Magrathea: Glacier signing key
sig_key:        EB:DD:61:40:14:3C:AD:81:89:B3:8F:E3:2B:A1:47:C6:AC:F9:F0:07
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp
rtc
lp
rtc


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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
options iwlwifi 11n_disable=1


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/video.conf]
options video use_native_backlight=1


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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
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
    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi
exit 0


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


########## wireless info END ############
```

---

### Post by jeremy31 on 2019-11-24
What happens if you ```
sudo modprobe -v wl
```

---

### Post by praseodym on 2019-11-24
Please also show
```

dkms status
```

---

### Post by evanm11710 on 2019-11-24
> **jeremy31 said:**
> What happens if you ```
sudo modprobe -v wl
```

Package not installed. I would get it - but no internet (laptop doesn't have a cable connection).

---

### Post by evanm11710 on 2019-11-24
> **praseodym said:**
> Please also show
```

dkms status
```

```

evan@evan-ubuntu-dell-xps:~$ dkms status
bcmwl, 6.30.223.248+bdcom, 3.13.0-170-generic, x86_64: installed
bcmwl, 6.30.223.248+bdcom, 3.13.0-37-generic, x86_64: installed
bcmwl, 6.30.223.248+bdcom, 3.13.0-61-generic, x86_64: installed
bcmwl, 6.30.223.248+bdcom, 3.13.0-74-generic, x86_64: installed
bcmwl, 6.30.223.248+bdcom, 3.13.0-83-generic, x86_64: installed
i915-3.19-3.13, 3.19.1, 3.13.0-170-generic, x86_64: installed
i915-3.19-3.13, 3.19.1, 3.13.0-37-generic, x86_64: installed
i915-3.19-3.13, 3.19.1, 3.13.0-61-generic, x86_64: installed
i915-3.19-3.13, 3.19.1, 3.13.0-74-generic, x86_64: installed
i915-3.19-3.13, 3.19.1, 3.13.0-83-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-170-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-37-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-61-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-74-generic, x86_64: installed
oem-audio-hda-daily, 0.1, 3.13.0-83-generic, x86_64: installed
synaptic-i2c-hid-3.13.0-32-backport, 1.6.4, 3.13.0-170-generic, x86_64: installed
synaptic-i2c-hid-3.13.0-32-backport, 1.6.4, 3.13.0-37-generic, x86_64: installed
synaptic-i2c-hid-3.13.0-32-backport, 1.6.4, 3.13.0-61-generic, x86_64: installed
synaptic-i2c-hid-3.13.0-32-backport, 1.6.4, 3.13.0-74-generic, x86_64: installed
synaptic-i2c-hid-3.13.0-32-backport, 1.6.4, 3.13.0-83-generic, x86_64: installed
evan@evan-ubuntu-dell-xps:~$ 
```

---

### Post by jeremy31 on 2019-11-24
Can you copy this to the Ubuntu machine Desktop [http://mirrors.kernel.org/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb)
Then in terminal do ```
cd Desktop
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb
```
See if it installs

---

### Post by praseodym on 2019-11-24
Please uninstall the older, buggy driver first:
```

sudo apt-get remove --purge bcmwl-kernel-source
```
The link from Jeremy provides the updated, non-buggy version.

---

### Post by evanm11710 on 2019-11-24
> **jeremy31 said:**
> Can you copy this to the Ubuntu machine Desktop [http://mirrors.kernel.org/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb](http://mirrors.kernel.org/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb)
Then in terminal do ```
cd Desktop
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb
```
See if it installs

It installed. I rebooted. I wasn't sure if you wanted me to run this code:

```

sudo modprobe -v wl

```

So I tried running that. It says 
```

'modprobe: ERROR could not insert 'wl' : Package not installed

```

---

### Post by jeremy31 on 2019-11-24
Reboot and use grub to boot into the 3.13.0-83-generic kernel

---

### Post by evanm11710 on 2019-11-24
> **jeremy31 said:**
> Reboot and use grub to boot into the 3.13.0-83-generic kernel

Safe mode or just generic kernel not safe mode?

---

### Post by jeremy31 on 2019-11-24
Just the generic kernel

---

### Post by evanm11710 on 2019-11-24
> **jeremy31 said:**
> Reboot and use grub to boot into the 3.13.0-83-generic kernel

Ok. I rebooted in that kernel. It is still disconnected. Anything else you want me to do here?

---

### Post by jeremy31 on 2019-11-24
Can you connect a smartphone to your router and use USB tethering to update to 16.04?

---

### Post by evanm11710 on 2019-11-24
> **jeremy31 said:**
> Can you connect a smartphone to your router and use USB tethering to update to 16.04?

I will see what I can do. My reply will be a little bit later.

---

### Post by praseodym on 2019-11-24
Uninstall the old driver. You may need to reinstall the DEB file again now afterwards

---

