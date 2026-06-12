---
title: "Wireless stopped working"
date: 2015-04-18
forum: Networking &amp; Wireless
---

### Post by kkelly77 on 2015-04-18
Hello,

I was trying to fix an issue I'm having with Ubuntu 14.04 (Bluetooth adaptor not being recognised/working).

I was trying a possible fix found here [http://ubuntuforums.org/showthread.php?t=2251009](http://ubuntuforums.org/showthread.php?t=2251009)

Unfortunately, not only did it not resolve my bluetooth issue, but my wireless card seems to have stopped working. It doesn't seem to be recognised now and it is not responding to the hardware on/off button for it on my laptop (HP Compaq nc8430). I have confirmed it is Enabled in the BIOS.

Can anyone please help???

Edit: Wireless module is Intel PRO/Wireless 3945ABG

---

### Post by kkelly77 on 2015-04-18
rfkill list all
```
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

dmesg | grep iwl

```
[   60.488567] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[   60.488575] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[   60.488606] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   60.488609] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   60.488614] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[   60.488617] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   60.488624] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[   60.488626] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[   60.488635] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[   60.488638] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[   60.488657] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   60.488659] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   60.488699] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[   60.488701] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[   60.488723] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[   60.488725] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   60.511833] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[   60.511839] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[   60.511867] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   60.511870] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   60.511875] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[   60.511877] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   60.511884] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[   60.511887] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[   60.511896] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[   60.511898] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[   60.511916] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   60.511918] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   60.511958] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[   60.511960] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[   60.511981] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[   60.511983] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[  858.157730] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[  858.157736] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[  858.157766] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[  858.157768] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[  858.157776] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[  858.157778] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[  858.157788] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[  858.157790] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[  858.157800] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[  858.157803] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[  858.157821] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[  858.157823] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[  858.157862] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[  858.157865] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[  858.157888] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[  858.157891] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
```

---

### Post by chili555 on 2015-04-18
Please do:```
cd ~/Desktop/backports-3.18-rc1-1
sudo make uninstall
```Reboot.

---

### Post by kkelly77 on 2015-04-18
> **chili555 said:**
> Please do:```
cd ~/Desktop/backports-3.18-rc1-1
sudo make uninstall
```Reboot.

Still not working.

Just to mention as well, I "Restored Defaults" in the BIOS. This got my Bluetooth adapter working and the wireless hardware button is working too but only to turn the Bluetooth on/off.

Still no WiFi, which has been working with no issues to date, until I attempted Bluetooth "fix" found in another thread. The wireless hardware button would control the WiFi connection off/on.

---

### Post by chili555 on 2015-04-18
May we see some diagnostics?```
sudo modprobe iwl3945
dmesg | grep iwl
```

---

### Post by kkelly77 on 2015-04-19
sudo modprobe iwl3945

```
modprobe: ERROR: could not insert 'iwl3945': Invalid argument
```

dmesg | grep iwl

```
[   36.782280] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[   36.782287] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[   36.782319] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   36.782322] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   36.782327] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[   36.782330] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   36.782337] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[   36.782339] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[   36.782348] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[   36.782350] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[   36.782366] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   36.782368] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   36.782406] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[   36.782408] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[   36.782427] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[   36.782430] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[   36.785321] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[   36.785326] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[   36.785350] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[   36.785353] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[   36.785358] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[   36.785360] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[   36.785367] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[   36.785369] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[   36.785377] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[   36.785380] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[   36.785393] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[   36.785396] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[   36.785432] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[   36.785434] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[   36.785452] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[   36.785454] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)
[ 2068.976489] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[ 2068.976495] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[ 2068.976525] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[ 2068.976527] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[ 2068.976534] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[ 2068.976536] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[ 2068.976545] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[ 2068.976547] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[ 2068.976557] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[ 2068.976560] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[ 2068.976576] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[ 2068.976579] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[ 2068.976618] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[ 2068.976620] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[ 2068.976642] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[ 2068.976644] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)

```

---

### Post by jeremy31 on 2015-04-19
It may be time to run the script from [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the results

---

### Post by kkelly77 on 2015-04-19
> **jeremy31 said:**
> It may be time to run the script from [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the results

```

########## wireless info START ##########

Report from: 19 Apr 2015 11:01 IST +0100

Booted last: 18 Apr 2015 23:22 IST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-49-generic #83-Ubuntu SMP Fri Apr 10 20:11:33 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express [14e4:16fd] (rev 21)
    Subsystem: Hewlett-Packard Company Compaq nw8440 [103c:30a3]
    Kernel driver in use: tg3

10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135d]

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

mac80211              616571  0 
hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
cfg80211              493859  1 mac80211
compat                 16281  2 cfg80211,mac80211
wmi                    19177  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.40.234  Bcast:192.168.40.255  Mask:255.255.255.0
          inet6 addr: fe80::217:a4ff:fee0:8d38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8402385 (8.4 MB)  TX bytes:948994 (948.9 KB)
          Interrupt:16 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.


##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

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

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[mac80211]
filename:       /lib/modules/3.13.0-49-generic/updates/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
version:        backported from Linux (v3.19-rc1-0-g97bf6af) using backports v3.19-rc1-1-0-g74aaf28
srcversion:     160A70ED2B5AFA688D3BAD5
depends:        cfg80211,compat
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-49-generic/updates/net/wireless/cfg80211.ko
version:        backported from Linux (v3.19-rc1-0-g97bf6af) using backports v3.19-rc1-1-0-g74aaf28
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     DE67EA5A07F19D3DD828D79
depends:        compat
vermagic:       3.13.0-49-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

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
iwl3945

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

[/etc/modprobe.d/iwl3945.conf]
alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

rfkill unblock all
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
# PCI device 0x14e4:0x16fd (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 2068.976489] iwlegacy: disagrees about version of symbol ieee80211_chswitch_done
[ 2068.976495] iwlegacy: Unknown symbol ieee80211_chswitch_done (err -22)
[ 2068.976525] iwlegacy: disagrees about version of symbol __ieee80211_create_tpt_led_trigger
[ 2068.976527] iwlegacy: Unknown symbol __ieee80211_create_tpt_led_trigger (err -22)
[ 2068.976534] iwlegacy: disagrees about version of symbol __ieee80211_get_radio_led_name
[ 2068.976536] iwlegacy: Unknown symbol __ieee80211_get_radio_led_name (err -22)
[ 2068.976545] iwlegacy: disagrees about version of symbol ieee80211_wake_queue
[ 2068.976547] iwlegacy: Unknown symbol ieee80211_wake_queue (err -22)
[ 2068.976557] iwlegacy: disagrees about version of symbol ieee80211_find_sta
[ 2068.976560] iwlegacy: Unknown symbol ieee80211_find_sta (err -22)
[ 2068.976576] iwlegacy: disagrees about version of symbol wiphy_rfkill_set_hw_state
[ 2068.976579] iwlegacy: Unknown symbol wiphy_rfkill_set_hw_state (err -22)
[ 2068.976618] iwlegacy: disagrees about version of symbol ieee80211_scan_completed
[ 2068.976620] iwlegacy: Unknown symbol ieee80211_scan_completed (err -22)
[ 2068.976642] iwlegacy: disagrees about version of symbol ieee80211_beacon_get_tim
[ 2068.976644] iwlegacy: Unknown symbol ieee80211_beacon_get_tim (err -22)

########## wireless info END ############


```

---

### Post by chili555 on 2015-04-19
> using backports v3.19-rc1Ah, haaaaa!! Please do:```
cd ~/Desktop/backports-3.1[COLOR="#FF0000"]9[/COLOR]-rc1-1
sudo make uninstall
```Reboot.

---

### Post by kkelly77 on 2015-04-19
> **chili555 said:**
> Ah, haaaaa!! Please do:```
cd ~/Desktop/backports-3.1[COLOR=#FF0000]9[/COLOR]-rc1-1
sudo make uninstall
```Reboot.

I saw the typo earlier when you asked me to uninstall and reboot. Tried the commands cd ~/Desktop/backports-3.1[COLOR=#FF0000]9[/COLOR]-rc1-1 and sudo make uninstall but it did not resolve the problem.

---

### Post by chili555 on 2015-04-19
Was there a problem with the command sequence? File not found? Errors, warnings, etc.? If you are unsure, please run it again to see the outcome.

How about this?```
sudo updatedb
locate backports-3.19 | head -n5
```

---

### Post by jeremy31 on 2015-04-19
Your bluetooth appears to be soft blocked, could be fixed with
```
rfkill unblock bluetooth
```

---

### Post by kkelly77 on 2015-04-19
> **chili555 said:**
> Was there a problem with the command sequence? File not found? Errors, warnings, etc.? If you are unsure, please run it again to see the outcome.

How about this?```
sudo updatedb
locate backports-3.19 | head -n5
```

It gave a message 'File not found' but that was because name was .8 and not .9, which I changed it to. The command worked and uninstalled successfully.

sudo updatedb
locate backports-3.19 | head -n5

Appeared to do nothing.

```
keitho@HP-nc8430:~$ sudo updatedb
[sudo] password for keitho: 
keitho@HP-nc8430:~$
```

```
keitho@HP-nc8430:~$ locate backports-3.19 | head -n5
keitho@HP-nc8430:~$
```

---

### Post by chili555 on 2015-04-19
> sudo updatedb
locate backports-3.19 | head -n5

Appeared to do nothing.This implies that you have no file named backports-3.19 anywhere; desktop or not. If that is the case, how can you have uninstalled it? Here, for comparison, is my result:```
chili@T410:~$ locate backports-3.19 | head -n5
/home/chili/Desktop/Forum/backports-3.19-rc1-1
/home/chili/Desktop/Forum/backports-3.19-rc1-1.tar.gz
/home/chili/Desktop/Forum/backports-3.19-rc1-1/.blacklist.map
/home/chili/Desktop/Forum/backports-3.19-rc1-1/.config
/home/chili/Desktop/Forum/backports-3.19-rc1-1/.config.old
```

:confused: :confused:

---

### Post by kkelly77 on 2015-04-19
> **chili555 said:**
> This implies that you have no file named backports-3.19 anywhere; desktop or not. If that is the case, how can you have uninstalled it? Here, for comparison, is my result:```
chili@T410:~$ locate backports-3.19 | head -n5
/home/chili/Desktop/Forum/backports-3.19-rc1-1
/home/chili/Desktop/Forum/backports-3.19-rc1-1.tar.gz
/home/chili/Desktop/Forum/backports-3.19-rc1-1/.blacklist.map
/home/chili/Desktop/Forum/backports-3.19-rc1-1/.config
/home/chili/Desktop/Forum/backports-3.19-rc1-1/.config.old
```

:confused: :confused:

I ran the commands you asked: ```
cd ~/Desktop/backports-3.19-rc1-1
sudo make uninstall
```

As well as
```
sudo updatedb
locate backports-3.19 | head -n5
```

backports-3.19-rc1-1 is located on the Desktop. I don't know why it is not listed in search results.

---

### Post by chili555 on 2015-04-19
Let's see it:```
cd ~/Desktop && ls
```

---

### Post by kkelly77 on 2015-04-19
> **chili555 said:**
> Let's see it:```
cd ~/Desktop && ls
```

```
keitho@HP-nc8430:~$ cd ~/Desktop && ls
admin20140904_10253257.pdf
backports-3.19-rc1-1
backports-3.19-rc1-1.tar.xz


```

---

### Post by chili555 on 2015-04-19
Please try:```
cd ~/Desktop/backports-3.19-rc1-1
make clean
make defconfig-wifi
make
sudo make install
exit
```Reboot.

---

### Post by kkelly77 on 2015-04-19
> **chili555 said:**
> Please try:```
cd ~/Desktop/backports-3.19-rc1-1
make clean
make defconfig-wifi
make
sudo make install
exit
```Reboot.

make clean command giving following error

```
keitho@HP-nc8430:~/Desktop/backports-3.19-rc1-1$ make clean
/bin/bash: line 46: .kernel_config_md5: Permission denied
make: *** [clean] Error 1


```

---

### Post by chili555 on 2015-04-19
> **kkelly77 said:**
> make clean command giving following error

```
keitho@HP-nc8430:~/Desktop/backports-3.19-rc1-1$ make clean
/bin/bash: line 46: .kernel_config_md5: Permission denied
make: *** [clean] Error 1


```I believe this suggests you did the original faulty build with sudo or as root. Please try:```
sudo make clean
```...and the remainder as written.

By the way, 'make' takes quite a while; please be patient.

---

### Post by kkelly77 on 2015-04-19
> **chili555 said:**
> I believe this suggests you did the original faulty build with sudo or as root. Please try:```
sudo make clean
```...and the remainder as written.

By the way, 'make' takes quite a while; please be patient.

```
keitho@HP-nc8430:~$ cd ~/Desktop/backports-3.19-rc1-1
keitho@HP-nc8430:~/Desktop/backports-3.19-rc1-1$ sudo make clean
[sudo] password for keitho: 
keitho@HP-nc8430:~/Desktop/backports-3.19-rc1-1$ make defconfig-wifi
/bin/bash: line 46: .kernel_config_md5: Permission denied
make: *** [defconfig-wifi] Error 1
keitho@HP-nc8430:~/Desktop/backports-3.19-rc1-1$
```

---

### Post by chili555 on 2015-04-19
I hate when compile is being difficult to get along with!!! Please sudo everything in sight!

---

### Post by kkelly77 on 2015-04-19
> **chili555 said:**
> I hate when compile is being difficult to get along with!!! Please sudo everything in sight!

You got the wireless connection working again Chili!!!! :p And my bluetooth is finally working again too. Unfortunately at the expense of the wifi problem.

Thanks so much for all your hard work.

Can you explain what was the issue?

---

### Post by chili555 on 2015-04-19
If you followed the thread you linked carefully, you built the driver for ath9k, not iwl3945. Some of the component parts conflict. We simply built the correct parts.

Don't forget to recompile when Update Manager installs a later linux-image:```
cd ~/Desktop/backports-3.19-rc1-1
sudo make clean
sudo make defconfig-wifi
sudo make
sudo make install
exit
```Glad it's working. Have fun!

---

### Post by kkelly77 on 2015-04-20
> **chili555 said:**
> If you followed the thread you linked carefully, you built the driver for ath9k, not iwl3945. Some of the component parts conflict. We simply built the correct parts.

Don't forget to recompile when Update Manager installs a later linux-image:```
cd ~/Desktop/backports-3.19-rc1-1
sudo make clean
sudo make defconfig-wifi
sudo make
sudo make install
exit
```Glad it's working. Have fun!

At least the ath9k resolved my non working bluetooth problem and you were available to fix the subsequent wifi problem it caused :p

I ran Update and all software was already up to date.

Will I need to recompile every time Update Manager updates linux image?

---

### Post by jeremy31 on 2015-04-20
> **kkelly77 said:**
> At least the ath9k resolved my non working bluetooth problem and you were available to fix the subsequent wifi problem it caused :p

I ran Update and all software was already up to date.

Will I need to recompile every time Update Manager updates linux image?

You will have to recompile after every update of linux-image

Strange that wifi backports would fix a bluetooth issue unless it is related to some error in the bluetooth coexistence code

---

