---
title: "Water damaged Dell XPS 13 will not connect to wireless wifi"
date: 2018-10-11
forum: Networking &amp; Wireless
---

### Post by rare HERO on 2018-10-11
Hello,

Last week my partner spilt some water onto the keyboard of my XPS 13 while I was out of the room. Within (less than 5) minutes of this happening I saw the water bottle toppled over the laptop keyboard, removed the water bottle and shut off the laptop by holding down the power button.
I gently shook the laptop while off and open upside down then placed it in a plastic vacuum seal bag with a portable dehumidifer (just a large plastic container with silica gel, they sell these for cars and boats and RVs). 

The following day (yes, too soon) I tried to use the laptop. Everything seemed to work okay except that the wireless connection was dead. I could not access any website using Firefox or Opera and my dropbox account would not connect to sync. I could, however, send and receive messages with the Telegram web client. And the laptop does show up when I use the Fing app on my Android phone.

It will connect to a wireless network but after establishing the connection nothing happens. If I try to use my phone as a USB tether it will not work (I often have had to resort to this because this laptop will not stay connected to some public wifi networks). I have yet to try a USB wifi adapter.

My last resort is to contact Dell for support but it will likely cost me.

Before I do that, what would you recommend for me to do to troubleshoot what has happened? What terminal commands will provide useful info?

**TL;DR: water damage on my Dell XPS 13 and now it won't connect to any wireless networks, what terminal commands should I consider to run to troubleshoot and fix.**

Extra info: I am using Ubuntu 14.04 on this laptop

EDIT: wireless info script results

[https://pastebin.ubuntu.com/p/2hwGPhVr3F/](https://pastebin.ubuntu.com/p/2hwGPhVr3F/)

EDIT 2: wireless info script results with the wifi turned on

[https://pastebin.ubuntu.com/p/Y5QtGPkBTT/](https://pastebin.ubuntu.com/p/Y5QtGPkBTT/)

EDIT 3: wireless info script results with the wifi turned on and connected to PIA VPN

[https://pastebin.ubuntu.com/p/rqjR3m2H76/](https://pastebin.ubuntu.com/p/rqjR3m2H76/)

---

### Post by praseodym on 2018-10-13
Please run the wireless script from the stick thread and show the outputs

---

### Post by rare HERO on 2018-10-15
The wireless info script results is here: 

[https://pastebin.ubuntu.com/p/2hwGPhVr3F/](https://pastebin.ubuntu.com/p/2hwGPhVr3F/)

```


########## wireless info START ##########

Report from: 15 Oct 2018 09:28 MST -0700

Booted last: 11 Oct 2018 08:44 MST -0700

Script from: 06 Oct 2018 06:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.5 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 4.4.0-98-generic #121~14.04.1-Ubuntu SMP Wed Oct 11 11:54:55 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, "acpi_osi=Windows, 2013", vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
	Subsystem: Dell Device [1028:0019]
	Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 0951:1666 Kingston Technology DataTraveler G4
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 0bda:5682 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0a5c:216f Broadcom Corp. BCM20702A0 Bluetooth
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
5: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### secure boot #######################

SecureBoot disabled

##### lsmod #############################

dell_laptop            20480  0 
dcdbas                 16384  1 dell_laptop
dell_wmi               16384  0 
wl                   6365184  0 
cfg80211              561152  1 wl
snd_soc_rt286          36864  0 
snd_soc_rl6347a        16384  1 snd_soc_rt286
snd_soc_core          212992  2 snd_soc_ssm4567,snd_soc_rt286
snd_pcm               106496  7 snd_soc_core,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_soc_rt286,snd_pcm_dmaengine,snd_hda_core
sparse_keymap          16384  3 dell_wmi,intel_hid,intel_vbtn
wmi                    20480  2 dell_led,dell_wmi
video                  40960  3 i915,dell_wmi,dell_laptop

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:842 errors:0 dropped:0 overruns:0 frame:0
          TX packets:842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1199915 (1.1 MB)  TX bytes:1199915 (1.1 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF1]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3504 errors:0 dropped:0 overruns:0 frame:1311
          TX packets:2082 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:291753 (291.7 KB)  TX bytes:225466 (225.4 KB)
          Interrupt:19 

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

[664 root ‘/etc/resolv.conf’]
search forest.usf.edu.
nameserver 131.247.1.1
nameserver 131.247.1.2

##### network managers ##################

Installed:

	NetworkManager

Running:

root      1114     1  0 Oct11 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: asleep

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unmanaged
  Default:           no
  HW Address:        <MAC 'wlan0' [IF1]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=false
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

[[/etc/NetworkManager/system-connections/The_Grand_Guste]] (600 root)
[connection] id=The_Grand_Guste | type=802-11-wireless
[802-11-wireless] ssid=The_Grand_Guste | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Free Airport WIFI]] (600 root)
[connection] id=Free Airport WIFI | type=802-11-wireless
[802-11-wireless] ssid=Free Airport WIFI | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Verizon-791L-3035]] (600 root)
[connection] id=Verizon-791L-3035 | type=802-11-wireless
[802-11-wireless] ssid=Verizon-791L-3035 | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Sheraton_Guest]] (600 root)
[connection] id=Sheraton_Guest | type=802-11-wireless
[802-11-wireless] ssid=Sheraton_Guest | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/9DB923]] (600 root)
[connection] id=9DB923 | type=802-11-wireless
[802-11-wireless] ssid=9DB923 | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TPA]] (600 root)
[connection] id=TPA | type=802-11-wireless
[802-11-wireless] ssid=TPA | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/@Hyatt_WiFi]] (600 root)
[connection] id=@Hyatt_WiFi | type=802-11-wireless
[802-11-wireless] ssid=@Hyatt_WiFi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Google Starbucks]] (600 root)
[connection] id=Google Starbucks | type=802-11-wireless
[802-11-wireless] ssid=Google Starbucks | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/PANERA]] (600 root)
[connection] id=PANERA | type=802-11-wireless
[802-11-wireless] ssid=PANERA | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/attwifi]] (600 root)
[connection] id=attwifi | type=802-11-wireless
[802-11-wireless] ssid=attwifi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Urban Beans Guest]] (600 root)
[connection] id=Urban Beans Guest | type=802-11-wireless
[802-11-wireless] ssid=Urban Beans Guest | mac-address=<MAC 'wlan0' [IF1]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Starbucks@Sheraton ]] (600 root)
[connection] id=Starbucks@Sheraton  | type=802-11-wireless
[802-11-wireless] ssid=Starbucks@Sheraton  | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/SouthwestWiFi]] (600 root)
[connection] id=SouthwestWiFi | type=802-11-wireless
[802-11-wireless] ssid=SouthwestWiFi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/IND PUBLIC WiFi]] (600 root)
[connection] id=IND PUBLIC WiFi | type=802-11-wireless
[802-11-wireless] ssid=IND PUBLIC WiFi | mac-address=<MAC 'wlan0' [IF1]>
[ipv6] method=auto
[ipv4] method=auto

##### Netplan config ####################

##### iw reg get ########################

Region: America/Phoenix (based on set time zone)

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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 150 : 5.75 GHz
          Channel 151 : 5.755 GHz
          Channel 152 : 5.76 GHz
          Channel 153 : 5.765 GHz
          Channel 154 : 5.77 GHz
          Channel 155 : 5.775 GHz
          Channel 156 : 5.78 GHz
          Channel 157 : 5.785 GHz
          Channel 158 : 5.79 GHz
          Channel 159 : 5.795 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

##### module infos ######################

[wl]
filename:       /lib/modules/4.4.0-98-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     3F8570547EE3A2BA3D5D734
depends:        cfg80211
vermagic:       4.4.0-98-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.4.0-98-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     20950513252BA8F4707EF3C
depends:        
intree:         Y
vermagic:       4.4.0-98-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
lp
rtc

coretemp

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

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/video.conf]
options video use_native_backlight=1

##### rc.local ##########################

rfkill block bluetooth

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
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rndis_host)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[15989.776789] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

---

### Post by jeremy31 on 2018-10-15
Click the networking icon in the notification area and enable networking, then see if the wifi works again

---

### Post by rare HERO on 2018-10-16
wireless info script results with the wifi turned on

[https://pastebin.ubuntu.com/p/Y5QtGPkBTT/](https://pastebin.ubuntu.com/p/Y5QtGPkBTT/)

---

### Post by rare HERO on 2018-10-21
The laptop will connect to the wireless network but only passes traffic while connected to VPN

EDIT 3: wireless info script results with the wifi turned on and connected to PIA VPN

[https://pastebin.ubuntu.com/p/rqjR3m2H76/](https://pastebin.ubuntu.com/p/rqjR3m2H76/)

---

### Post by rare HERO on 2018-12-29
Hi, the problem seems to have resolved itself.

To summarize:

- Water was spilt on to the laptop.
- afterwards, the wifi would connect but would not carry any traffic
- the wifi did connect and have full function only when connected with PIA VPN
- now, the wifi seems to work fine without needing to be connected to the PIA VPN

---

