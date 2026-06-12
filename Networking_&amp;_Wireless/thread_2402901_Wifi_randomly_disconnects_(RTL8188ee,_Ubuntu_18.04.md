---
title: "Wifi randomly disconnects (RTL8188ee, Ubuntu 18.04)"
date: 2018-10-05
forum: Networking &amp; Wireless
---

### Post by kingnorth20 on 2018-10-05
Hello! This is yet another case of Wifi connection issues. I'm using an HP 14 with a Realtek RTL8188ee wireless network adapter and Ubuntu 18.04. The problem is that sometimes the wifi adapter and the Network Manager turn off out of the blue, and the only way to turn them on again is to restart the computer. This happens after the wifi signal is lost and the computer tries to reconnect again. The issue is rather unpredictable - sometimes I can spend the whole day without it happening, and sometimes it disconnects every few minutes and it takes me several tries to get the wifi working again.

I have looked for other solutions online but the threads I've found are rather old and nothing has worked. I reinstalled the OS a couple of weeks ago. I even took the computer to the repair shop and they told me there was nothing wrong with the wireless adapter. So I'm at my wit's end, and would greatly appreciate your help. 

[COLOR=#000000]Here's the info outcome of the “wireless-info” script:

```
[/COLOR]

########## wireless info START ##########


Report from: 04 Oct 2018 21:32 CST -0600


Booted last: 04 Oct 2018 00:00 CST -0600


Script from: 10 Jan 2018 20:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic


##### kernel ############################


Linux 4.15.0-36-generic #39-Ubuntu SMP Mon Sep 24 16:19:09 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, i915.modeset=1, quiet, splash, vt.handoff=1


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company RTL810xE PCI Express Fast Ethernet controller [103c:218b]
	Kernel driver in use: r8169


02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company RTL8188EE mini-PCIe card [103c:197d]
	Kernel driver in use: rtl8188ee


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
rtl8188ee             131072  0
rtl_pci                32768  1 rtl8188ee
rtlwifi               163840  2 rtl_pci,rtl8188ee
wmi_bmof               16384  0
mac80211              778240  3 rtl_pci,rtl8188ee,rtlwifi
cfg80211              622592  2 mac80211,rtlwifi
wmi                    24576  2 wmi_bmof,hp_wmi


##### interfaces ########################


[/etc/network/interfaces]
auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 808  bytes 57615 (57.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 808  bytes 57615 (57.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlan0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1303498  bytes 1861221522 (1.8 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 696494  bytes 74062418 (74.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


wlan0     IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #######################


nameserver 127.0.0.53


##### network managers ##################


Installed:


	NetworkManager


Running:


root      1120     1  0 14:01 ?        00:00:05 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8188EE Wireless Network Adapter (RTL8188EE mini-PCIe card)
GENERAL.DRIVER:                         rtl8188ee
GENERAL.DRIVER-VERSION:                 4.15.0-36-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          30 (disconnected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0
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
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL810xE PCI Express Fast Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               rtl8106e-1_0.0.1 06/29/12
GENERAL.HWADDR:                         <MAC address>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --


SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  IN-USE 


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile


[ifupdown]
managed=true


[device]
wifi.scan-rand-mac-address=no


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/MLRed_3.1]] (600 root)
[connection] id=MLRed_3.1 | type=wifi | permissions=
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=MLRed_3.1
[ipv4] method=auto
[ipv6] method=ignore


[[/etc/NetworkManager/system-connections/VALDEZ-AD]] (600 root)
[connection] id=VALDEZ-AD | type=wifi | permissions=user:ce:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=VALDEZ-AD
[ipv4] method=manual
[ipv6] method=auto


[[/etc/NetworkManager/system-connections/arris54g]] (600 root)
[connection] id=arris54g | type=802-11-wireless
[802-11-wireless] ssid=arris54g | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### Netplan config ####################


##### iw reg get ########################


Region: America/El_Salvador (based on set time zone)


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


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


wlan0     No scan results


##### module infos ######################


[rtl8188ee]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     EA573807C4651A894C223BD
depends:        rtlwifi,rtl_pci,mac80211
retpoline:      Y
name:           rtl8188ee
vermagic:       4.15.0-36-generic SMP mod_unload 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 1)
 (bool)
parm:           aspm:Set to 1 to enable ASPM (default 1)
 (int)
parm:           debug_level:Set debug level (0-5) (default 0) (int)
parm:           debug_mask:Set debug mask (default 0) (ullong)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)


[rtl_pci]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     F1DE1F093B181758DE4640E
depends:        mac80211,rtlwifi
retpoline:      Y
name:           rtl_pci
vermagic:       4.15.0-36-generic SMP mod_unload 


[rtlwifi]
filename:       /lib/modules/4.15.0-36-generic/kernel/drivers/net/wireless/realtek/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B7ECEE846CE5B14E0566D06
depends:        mac80211,cfg80211
retpoline:      Y
name:           rtlwifi
vermagic:       4.15.0-36-generic SMP mod_unload 


[mac80211]
filename:       /lib/modules/4.15.0-36-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     76870094CC01F4AC06240B7
depends:        cfg80211
retpoline:      Y
intree:         Y
name:           mac80211
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.15.0-36-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-36-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[rtl8188ee]
aspm: 1
debug_level: 0
debug_mask: 0
disable_watchdog: N
fwlps: N
ips: N
msi: Y
swenc: N
swlps: N


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


lp
lp
disable_mmc
disable_mmc
disable_mmc
disable_mmc
disable_mmc
disable_mmc
disable_mmc


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
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-opensource-graphics.conf]
blacklist nouveau
blacklist radeon 
blacklist lbm-nouveau
blacklist lbm-radeon 
alias radeon off
alias lbm-radeon off


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/disable-mmc.conf]
install rtsx_pci /sbin/modprobe disable_mmc; /sbin/modprobe --ignore-install rtsx_pci


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee fwlps=N swlps=N ips=N ant_sel=2


[/etc/modprobe.d/snd-hda-intel.conf]
options snd-hda-intel power_save_controller=N


##### rc.local ##########################


/usr/sbin/workaround_r8169
echo 0 > /sys/module/video/parameters/brightness_switch_enabled
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


[/etc/pm/sleep.d/90GlidePoint] (755 root)
case "$1" in
    hibernate|suspend)
		killall -s SIGUSR1 glided
		exit 0
        ;;
    resume|thaw)
        killall -s SIGCONT glided
	exit 0
        ;;
    *) exit 0
        ;;
    esac


[/etc/pm/sleep.d/oem-video-workaround-1176735] (755 root)
workaround()
{
	tty=$1
	printf '\033[?25l' > $tty # hide the cursor
	printf '\033[0;30m' > $tty # make the text color to be black
	#clear > $tty # clear all the message dumped on the screen
}
case $1 in
     suspend|suspend_hybrid|hibernate)
        workaround /dev/tty63
        ;;
esac


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #############################


[24256.178480] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:9248:9aff:fe2b:d945 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=917294 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[24256.178542] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:9248:9aff:fe2b:d945 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=134142 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[24300.982775] rtlwifi: AP off, try to reconnect now
[24300.982807] wlan0: Connection to AP <MAC address> lost
[24302.105008] wlan0: authenticate with <MAC address>
[24302.123941] wlan0: send auth to <MAC address> (try 1/3)
[24302.133820] wlan0: authenticated
[24302.135869] wlan0: associate with <MAC address> (try 1/3)
[24302.139410] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24302.139682] wlan0: associated
[24325.174149] rtlwifi: AP off, try to reconnect now
[24325.174179] wlan0: Connection to AP <MAC address> lost
[24326.295925] wlan0: authenticate with <MAC address>
[24326.315445] wlan0: send auth to <MAC address> (try 1/3)
[24326.319055] wlan0: authenticated
[24326.322987] wlan0: associate with <MAC address> (try 1/3)
[24326.336033] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24326.336373] wlan0: associated
[24343.317707] rtlwifi: AP off, try to reconnect now
[24343.317735] wlan0: Connection to AP <MAC address> lost
[24344.463719] wlan0: authenticate with <MAC address>
[24344.483087] wlan0: send auth to <MAC address> (try 1/3)
[24344.484959] wlan0: authenticated
[24344.490507] wlan0: associate with <MAC address> (try 1/3)
[24344.493824] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24344.494159] wlan0: associated
[24373.675767] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:9248:9aff:fe2b:d945 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=917294 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[24373.675808] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:9248:9aff:fe2b:d945 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=134142 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[24373.686101] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:9248:9aff:fe2b:d945 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=917294 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[24373.686142] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:9248:9aff:fe2b:d945 DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=134142 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[24387.668535] rtlwifi: AP off, try to reconnect now
[24387.668558] wlan0: Connection to AP <MAC address> lost
[24388.807228] wlan0: authenticate with <MAC address>
[24388.825681] wlan0: send auth to <MAC address> (try 1/3)
[24388.828005] wlan0: authenticated
[24388.829458] wlan0: associate with <MAC address> (try 1/3)
[24388.840433] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24388.840737] wlan0: associated
[24409.844022] rtlwifi: AP off, try to reconnect now
[24409.844076] wlan0: Connection to AP <MAC address> lost
[24410.990109] wlan0: authenticate with <MAC address>
[24411.009144] wlan0: send auth to <MAC address> (try 1/3)
[24411.028719] wlan0: authenticated
[24411.032787] wlan0: associate with <MAC address> (try 1/3)
[24411.044938] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24411.045226] wlan0: associated
[24514.673323] rtlwifi: AP off, try to reconnect now
[24514.673344] wlan0: Connection to AP <MAC address> lost
[24515.787307] wlan0: authenticate with <MAC address>
[24515.806656] wlan0: send auth to <MAC address> (try 1/3)
[24515.808665] wlan0: authenticated
[24515.814158] wlan0: associate with <MAC address> (try 1/3)
[24515.817465] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24515.817799] wlan0: associated
[24538.864739] rtlwifi: AP off, try to reconnect now
[24538.864762] wlan0: Connection to AP <MAC address> lost
[24540.007027] wlan0: authenticate with <MAC address>
[24540.025959] wlan0: send auth to <MAC address> (try 1/3)
[24540.027951] wlan0: authenticated
[24540.030582] wlan0: associate with <MAC address> (try 1/3)
[24540.033981] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24540.034251] wlan0: associated
[24688.045112] rtlwifi: AP off, try to reconnect now
[24688.045171] wlan0: Connection to AP <MAC address> lost
[24689.147702] wlan0: authenticate with <MAC address>
[24689.166311] wlan0: send auth to <MAC address> (try 1/3)
[24689.167855] wlan0: authenticated
[24689.169924] wlan0: associate with <MAC address> (try 1/3)
[24689.175752] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=1)
[24689.176089] wlan0: associated
[25524.665099] rtlwifi: AP off, try to reconnect now
[25524.665126] wlan0: Connection to AP <MAC address> lost
[25534.744882] rtlwifi: AP off, try to reconnect now
[25541.540929] wlan0: Connection to AP <MAC address> lost
[25557.587304] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


########## wireless info END ############


[COLOR=#000000]
```
[/COLOR]
Thank you in advance!

---

### Post by kingnorth20 on 2018-10-06
This is the log output when the wifi stops working:

```
Oct  4 13:32:57 centralia kernel: [ 7493.909129] wlan0: Connection to AP 00:00:00:00:00:00 lost
Oct  4 13:32:58 centralia wpa_supplicant[1097]: wlan0: CTRL-EVENT-DISCONNECTED bssid=c8:3a:35:3b:50:28 reason=4 locally_generated=1
Oct  4 13:32:59 centralia dhcpcd[1194]: wlan0: deleting address fe80::5bc9:1a92:3475:aaa3
Oct  4 13:33:09 centralia dhcpcd[1194]: wlan0: deleting default route via 192.168.0.1
Oct  4 13:33:10 centralia dhcpcd[1194]: wlan0: deleting route to 192.168.0.0/24
Oct  4 13:33:10 centralia NetworkManager[1092]: <warn>  [1538681590.2502] sup-iface[0x55d3df460190,wlan0]: connection disconnected (reason -4)
Oct  4 13:33:10 centralia avahi-daemon[1121]: Withdrawing address record for 192.168.0.102 on wlan0.
Oct  4 13:33:11 centralia NetworkManager[1092]: <info>  [1538681590.7768] device (wlan0): supplicant interface state: completed -> scanning
Oct  4 13:33:11 centralia avahi-daemon[1121]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.102.
Oct  4 13:33:11 centralia avahi-daemon[1121]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct  4 13:33:11 centralia NetworkManager[1092]: <info>  [1538681591.8137] manager: NetworkManager state is now CONNECTED_SITE
Oct  4 13:33:12 centralia dbus-daemon[1091]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=1092 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct  4 13:33:13 centralia gsd-sharing[2216]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit rygel.service not loaded.
Oct  4 13:33:13 centralia gsd-sharing[2216]: Failed to StopUnit service: GDBus.Error:org.freedesktop.systemd1.NoSuchUnit: Unit gnome-remote-desktop.service not loaded.
Oct  4 13:33:14 centralia systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct  4 13:33:16 centralia dbus-daemon[1091]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  4 13:33:16 centralia systemd[1]: Started Network Manager Script Dispatcher Service.
Oct  4 13:33:16 centralia nm-dispatcher: req:1 'connectivity-change': new request (1 scripts)
Oct  4 13:33:16 centralia nm-dispatcher: req:1 'connectivity-change': start running ordered scripts...
```

And this is the log output when I try to restart network manager (sorry it's a bit long, I don't know exactly what can be useful here)

```
 Oct  4 13:35:00 centralia NetworkManager[1092]: <info>  [1538681700.5315] manager: NetworkManager state is now DISCONNECTING
Oct  4 13:35:00 centralia NetworkManager[1092]: <info>  [1538681700.7935] device (wlan0): state change: deactivating -> unmanaged (reason 'removed', sys-iface-state: 'managed')
Oct  4 13:35:00 centralia NetworkManager[1092]: <info>  [1538681700.8577] dhcp4 (wlan0): canceled DHCP transaction, DHCP client pid 1301
Oct  4 13:35:00 centralia NetworkManager[1092]: <info>  [1538681700.8578] dhcp4 (wlan0): state changed bound -> done
Oct  4 13:35:00 centralia avahi-daemon[1121]: Withdrawing address record for fe80::9248:9aff:fe2b:d945 on wlan0.
Oct  4 13:35:00 centralia avahi-daemon[1121]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::9248:9aff:fe2b:d945.
Oct  4 13:35:00 centralia avahi-daemon[1121]: Interface wlan0.IPv6 no longer relevant for mDNS.
Oct  4 13:35:01 centralia systemd[1]: Starting resolvconf-pull-resolved.service...
Oct  4 13:35:01 centralia systemd[1]: Started resolvconf-pull-resolved.service.
Oct  4 13:35:03 centralia kernel: [ 7619.709705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 13:35:03 centralia NetworkManager[1092]: <info>  [1538681703.7149] manager: NetworkManager state is now DISCONNECTED
Oct  4 13:35:03 centralia dbus-daemon[1091]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested by ':1.12' (uid=0 pid=1092 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct  4 13:35:03 centralia systemd[1]: Starting Network Manager Script Dispatcher Service...
Oct  4 13:35:03 centralia dbus-daemon[1091]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Oct  4 13:35:03 centralia systemd[1]: Started Network Manager Script Dispatcher Service.
Oct  4 13:35:03 centralia nm-dispatcher: req:1 'down' [wlan0]: new request (1 scripts)
Oct  4 13:35:03 centralia nm-dispatcher: req:1 'down' [wlan0]: start running ordered scripts...
Oct  4 13:35:04 centralia NetworkManager[1092]: <info>  [1538681704.0807] exiting (success)
Oct  4 13:35:04 centralia wpa_supplicant[1097]: nl80211: deinit ifname=wlan0 disabled_11b_rates=0
Oct  4 13:35:06 centralia systemd[1]: Stopped Network Manager.
Oct  4 13:35:06 centralia systemd[1]: Starting Network Manager...
Oct  4 13:35:06 centralia gnome-shell[2069]: Removing a network device that was not added
Oct  4 13:35:06 centralia gnome-shell[2069]: JS WARNING: [resource:///org/gnome/shell/ui/status/network.js 1204]: reference to undefined property "_strengthChangedId"
Oct  4 13:35:06 centralia gnome-shell[1585]: Removing a network device that was not added
Oct  4 13:35:07 centralia gnome-shell[1585]: JS WARNING: [resource:///org/gnome/shell/ui/status/network.js 1204]: reference to undefined property "_strengthChangedId"
Oct  4 13:35:07 centralia NetworkManager[5309]: <info>  [1538681707.9188] NetworkManager (version 1.10.6) is starting... (after a restart)
Oct  4 13:35:07 centralia NetworkManager[5309]: <info>  [1538681707.9190] Read config: /etc/NetworkManager/NetworkManager.conf (lib: 10-dns-resolved.conf, 20-connectivity-ubuntu.conf, no-mac-addr-change.conf) (etc: 10-globally-managed-devices.conf, default-wifi-powersave-on.conf)
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.1053] manager[0x565167f9b060]: monitoring kernel firmware directory '/lib/firmware'.
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.1053] monitoring ifupdown state file '/run/network/ifstate'.
Oct  4 13:35:08 centralia dbus-daemon[1091]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.116' (uid=0 pid=5309 comm="/usr/sbin/NetworkManager --no-daemon " label="unconfined")
Oct  4 13:35:08 centralia systemd[1]: Starting Hostname Service...
Oct  4 13:35:08 centralia dbus-daemon[1091]: [system] Successfully activated service 'org.freedesktop.hostname1'
Oct  4 13:35:08 centralia systemd[1]: Started Hostname Service.
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.8703] hostname: hostname: using hostnamed
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.8704] hostname: hostname changed from (none) to "centralia"
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.8710] dns-mgr[0x565167fb7940]: init: dns=systemd-resolved, rc-manager=symlink, plugin=systemd-resolved
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.9597] rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/ieee80211/phy0/rfkill0) (driver rtl8188ee)
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.9601] manager[0x565167f9b060]: rfkill: WiFi hardware radio set enabled
Oct  4 13:35:08 centralia NetworkManager[5309]: <info>  [1538681708.9601] manager[0x565167f9b060]: rfkill: WWAN hardware radio set enabled
Oct  4 13:35:08 centralia systemd[1]: Started Network Manager.
Oct  4 13:35:08 centralia systemd[1]: Starting Network Manager Wait Online...
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.0511] init!
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.0513]       interface-parser: parsing file /etc/network/interfaces
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1174]       interface-parser: finished parsing file /etc/network/interfaces
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1175] management mode: managed
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1185] devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1186] device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1187] devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1187] device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1188] devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1188] device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1188] end _init.
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1188] settings: loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list. (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-settings-plugin-ifupdown.so)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1189] settings: loaded plugin keyfile: (c) 2007 - 2016 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1189] (1744656704) ... get_connections.
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1190] (1744656704) connections count: 0
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1683] keyfile: new connection /etc/NetworkManager/system-connections/VALDEZ-AD (d53ca53f-7bcd-43ca-9977-7cff38cc3b15,"VALDEZ-AD")
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.1910] keyfile: new connection /etc/NetworkManager/system-connections/MLRed_3.1 (44fb88d8-8ab6-4394-80f2-e56e4a7c491e,"MLRed_3.1")
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2198] keyfile: new connection /etc/NetworkManager/system-connections/arris54g (b2107373-c318-46e6-895d-49bfef15d27d,"arris54g")
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2376] manager: rfkill: WiFi enabled by radio killswitch; enabled by state file
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2377] manager: rfkill: WWAN enabled by radio killswitch; enabled by state file
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2378] manager: Networking is enabled by state file
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2380] dhcp-init: Using DHCP client 'dhclient'
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2381] Loaded device plugin: NMBondDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2382] Loaded device plugin: NMBridgeDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2382] Loaded device plugin: NMDummyDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2383] Loaded device plugin: NMEthernetDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2383] Loaded device plugin: NMInfinibandDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2384] Loaded device plugin: NMIPTunnelDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2385] Loaded device plugin: NMMacsecDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2385] Loaded device plugin: NMMacvlanDeviceFactory (internal)
Oct  4 13:35:09 centralia nm-dispatcher: req:2 'hostname': new request (1 scripts)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2386] Loaded device plugin: NMPppDeviceFactory (internal)
Oct  4 13:35:09 centralia nm-dispatcher: req:2 'hostname': start running ordered scripts...
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2386] Loaded device plugin: NMTunDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2387] Loaded device plugin: NMVethDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2387] Loaded device plugin: NMVlanDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2388] Loaded device plugin: NMVxlanDeviceFactory (internal)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2836] Loaded device plugin: NMWwanFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2844] Loaded device plugin: NMTeamFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-team.so)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2867] Loaded device plugin: NMWifiFactory (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.2871] Loaded device plugin: NMAtmManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3004] Loaded device plugin: NMBluezManager (/usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3014] device (lo): carrier: link connected
Oct  4 13:35:09 centralia kernel: [ 7625.334289] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  4 13:35:09 centralia kernel: [ 7625.339530] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3022] manager: (lo): new Generic device (/org/freedesktop/NetworkManager/Devices/1)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3038] manager: (eth0): new Ethernet device (/org/freedesktop/NetworkManager/Devices/2)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3056] keyfile: add connection in-memory (606c107c-2beb-3b0e-b58c-892a652d61cb,"Conexión cableada 1")
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3062] settings: (eth0): created default wired connection 'Conexión cableada 1'
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3078] device (eth0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3095] wifi-nl80211: (wlan0): using nl80211 for WiFi device control
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3098] device (wlan0): driver supports Access Point (AP) mode
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3117] manager: (wlan0): new 802.11 WiFi device (/org/freedesktop/NetworkManager/Devices/3)
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.3132] device (wlan0): state change: unmanaged -> unavailable (reason 'managed', sys-iface-state: 'external')
Oct  4 13:35:09 centralia kernel: [ 7625.400390] rtl8188ee: Init MAC failed
Oct  4 13:35:09 centralia NetworkManager[5309]: <warn>  [1538681709.3847] device (wlan0): device not up after timeout!
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.6148] supplicant: wpa_supplicant running
Oct  4 13:35:09 centralia NetworkManager[5309]: <info>  [1538681709.6149] device (wlan0): supplicant interface state: init -> starting
Oct  4 13:35:09 centralia kernel: [ 7625.787055] rtl8188ee: Init MAC failed
```

---

