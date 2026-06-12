---
title: "No WiFi after last update"
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by stavrosian on 2016-08-01
My WiFi was working great for a year on my new Lenovo Yoga Pro 13 and today I did a Software Updater update and when I rebooted I now get "no network devices available".  Does  anyone know what happened? 

Here is my wireless-info.txt:

```


########## wireless info START ##########

Report from: 31 Jul 2016 23:20 MDT -0600

Booted last: 31 Jul 2016 00:00 MDT -0600

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial

##### kernel ############################

Linux 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noprompt, quiet, splash, elevator=deadline, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 5986:0535 Acer, Inc 
Bus 002 Device 005: ID 04f3:016f Elan Microelectronics Corp. 
Bus 002 Device 004: ID 2047:0855 Texas Instruments Invensense Embedded MotionApp HID Sensor
Bus 002 Device 003: ID 8087:07dc Intel Corp. 
Bus 002 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 002 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no

##### lsmod #############################

ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
wmi                    20480  1 ideapad_laptop
video                  40960  2 i915,ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

##### iwconfig ##########################

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #######################

##### network managers ##################

Installed:

	NetworkManager

Running:

root      2492     1  0 22:06 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         ttyACM0
GENERAL.TYPE:                           gsm
GENERAL.NM-TYPE:                        NMDeviceModem
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         cdc_acm
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         (unknown)
GENERAL.MTU:                            0
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /org/freedesktop/ModemManager1/Modem/0
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
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

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

[[/etc/NetworkManager/system-connections/bueycup]] (600 root)
[connection] id=bueycup | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=bueycup
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/INFINITUMBC0FBF]] (600 root)
[connection] id=INFINITUMBC0FBF | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=INFINITUMBC0FBF
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/202b96]] (600 root)
[connection] id=202b96 | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=202b96
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/INFINITUMa435]] (600 root)
[connection] id=INFINITUMa435 | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=INFINITUMa435
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/INFINITUMCC5F46]] (600 root)
[connection] id=INFINITUMCC5F46 | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=INFINITUMCC5F46
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DoceCuarenta]] (600 root)
[connection] id=DoceCuarenta | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DoceCuarenta
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/infinitum movil]] (600 root)
[connection] id=infinitum movil | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=infinitum movil
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/INFINITUM3A7FBF]] (600 root)
[connection] id=INFINITUM3A7FBF | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=INFINITUM3A7FBF
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/INFINITUM]] (600 root)
[connection] id=INFINITUM | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=INFINITUM
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/DEPARTAMENTOS945]] (600 root)
[connection] id=DEPARTAMENTOS945 | type=wifi | permissions=user:stav:;
[wifi] mac-address=<MAC address> | mac-address-blacklist= | ssid=DEPARTAMENTOS945
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Mazatlan (based on set time zone)

country 00: DFS-UNSET
	(2402 - 2472 @ 40), (6, 20), (N/A)
	(2457 - 2482 @ 40), (6, 20), (N/A), PASSIVE-SCAN
	(2474 - 2494 @ 20), (6, 20), (N/A), NO-OFDM, PASSIVE-SCAN
	(5170 - 5250 @ 160), (6, 20), (N/A), PASSIVE-SCAN
	(5250 - 5330 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5490 - 5730 @ 160), (6, 20), (0 ms), DFS, PASSIVE-SCAN
	(5735 - 5835 @ 80), (6, 20), (N/A), PASSIVE-SCAN
	(57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

##### iwlist scan #######################

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

for user in stav; do
  DIR=/tmp/$user/cache/chromium
  sudo -u $user -- sh -c "mkdir -p $DIR && chmod -R 700 /tmp/$user"
done

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/00_check_touchpad_status] (755 root)
LOGFILE="/var/log/sleep.log"
case "$1" in
        resume|thaw)
                echo "Resumed normal from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/check_touchpad_status.py resume
                echo "Touchpad enabled"
                ;;
esac

##### udev rules ########################

##### dmesg #############################

########## wireless info END ############



```

---

### Post by stavrosian on 2016-08-04
The problem was hardware.  I had to replace my wifi card and everything is working now.

---

