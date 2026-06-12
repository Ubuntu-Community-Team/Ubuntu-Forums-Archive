---
title: "Unable to detect WiFi after kernel update to 3.16.0-36 on X1 Carbon 3rd Gen"
date: 2015-05-02
forum: Networking &amp; Wireless
---

### Post by BuffaloBuffalo on 2015-05-02
I'm  running Ubuntu 14.04 and Windows 8 dual boot on a Lenovo X1 Carbon 3rd Gen. After updating from 3.16.0-34 to 3.16.0-36, several things happened:

- Booting into 3.16.0-36 gets stuck at purple screen. This is a known issue ([https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1450156](https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1450156)), so I am currently using 3.16.0-34. However...
- WiFi universally doesn't work in any kernel (currently using 3.16.0-34). I can't see any networks at all, and no longer have the soft option to turn WiFi on/off from the connections menu. Ethernet is fine. 

Everything was OK before the update. The wifi works when I boot into Windows so my connection and hardware are OK, but I would prefer to be using Ubuntu. 

Here is the output of the wireless script:

```


########## wireless info START ##########

Report from: 02 May 2015 13:59 CDT -0500

Booted last: 01 May 2015 15:05 CDT -0500

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection (3) I218-V [8086:15a3] (rev 03)
    Subsystem: Lenovo Device [17aa:2227]
    Kernel driver in use: e1000e

04:00.0 Network controller [0280]: Intel Corporation Wireless 7265 [8086:095b] (rev 59)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7265 [8086:5210]

##### lsusb #############################

Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b45d Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 138a:0017 Validity Sensors, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

iwlwifi               179412  0 
cfg80211              494362  1 iwlwifi
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.100.104  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::56ee:75ff:fe44:6ed0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:363383 errors:0 dropped:1 overruns:0 frame:0
          TX packets:271703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:462160224 (462.1 MB)  TX bytes:24933933 (24.9 MB)
          Interrupt:20 Memory:f1100000-f1120000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.100.254 0.0.0.0         UG    0      0        0 eth0
192.168.100.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search gateway.mts.net

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.100.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.100.254

    DNS:             192.168.100.254

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

[[/etc/NetworkManager/system-connections/datavalet]] (600 root)
[connection] id=datavalet | type=802-11-wireless
[802-11-wireless] ssid=datavalet | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Second Cup - WiFi]] (600 root)
[connection] id=Second Cup - WiFi | type=802-11-wireless
[802-11-wireless] ssid=Second Cup - WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/MTS803]] (600 root)
[connection] id=MTS803 | type=802-11-wireless
[802-11-wireless] ssid=MTS803 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Blatm]] (600 root)
[connection] id=Blatm | type=802-11-wireless
[802-11-wireless] ssid=Blatm | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MTS Wi-Fi Hotspot]] (600 root)
[connection] id=MTS Wi-Fi Hotspot | type=802-11-wireless
[802-11-wireless] ssid=MTS Wi-Fi Hotspot | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/maple]] (600 root)
[connection] id=maple | type=802-11-wireless
[802-11-wireless] ssid=maple | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FYI_TC1]] (600 root)
[connection] id=FYI_TC1 | type=802-11-wireless
[802-11-wireless] ssid=FYI_TC1 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/loup pacifique]] (600 root)
[connection] id=loup pacifique | type=802-11-wireless
[802-11-wireless] ssid=loup pacifique | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/uofm-wpa]] (600 root)
[ipv6] method=auto
[connection] id=uofm-wpa | type=802-11-wireless
[802-11-wireless] ssid=uofm-wpa | mac-address=<MAC address>
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/WPG-Wifi]] (600 root)
[connection] id=WPG-Wifi | type=802-11-wireless
[802-11-wireless] ssid=WPG-Wifi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/VnL]] (600 root)
[connection] id=VnL | type=802-11-wireless
[802-11-wireless] ssid=VnL | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/AERO WI-FI]] (600 root)
[connection] id=AERO WI-FI | type=802-11-wireless
[802-11-wireless] ssid=AERO WI-FI | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: America/[city removed] (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

[iwlwifi]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2014 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-9.ucode
firmware:       iwlwifi-3160-9.ucode
firmware:       iwlwifi-7260-9.ucode
firmware:       iwlwifi-8000-8.ucode
srcversion:     93D664267873827B22C4309
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable (default: 1) (int)
parm:           nvm_file:NVM file name (charp)
parm:           uapsd_disable:disable U-APSD functionality (default: Y) (bool)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_monitor: N
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/touchpad.conf]
options psmouse proto=imps

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/00_check_touchpad_status] (644 root)
LOGFILE="/var/log/sleep.log"
case "$1" in
        resume|thaw)
                echo "Resumed from suspend at `date`" >> "$LOGFILE"
                /usr/bin/python3 /opt/extras.ubuntu.com/touchpad-indicator/share/touchpad-indicator/check_touchpad_status.py
                echo "Touchpad enabled"
                ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x15a3 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x095b (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############


```

I am a fairly new user and not sure where to go from here, so any info or suggestions would be appreciated, thanks.

---

### Post by chili555 on 2015-05-02
Please open a terminal and let's load the driver:```
sudo modprobe iwlwifi
```If this produces an error or warning, please post it. Otherwise, check the log for informative messages:```
dmesg | grep iwl
```My colleagues in the back room suspect firmware; let's see.

---

### Post by BuffaloBuffalo on 2015-05-02
No error or warning, here's the log: 

```

user@computer:~$ sudo modprobe iwlwifi
user@computer:~$ dmesg | grep iwl
[    3.186625] iwlwifi 0000:04:00.0: irq 60 for MSI/MSI-X
[    3.217456] iwlwifi 0000:04:00.0: Direct firmware load failed with error -2
[    3.217459] iwlwifi 0000:04:00.0: Falling back to user helper
[    3.299155] iwlwifi 0000:04:00.0: request for firmware file 'iwlwifi-7265-9.ucode' failed.
[    3.316193] iwlwifi 0000:04:00.0: Direct firmware load failed with error -2
[    3.316196] iwlwifi 0000:04:00.0: Falling back to user helper
[    3.316691] iwlwifi 0000:04:00.0: request for firmware file 'iwlwifi-7265-8.ucode' failed.
[    3.316696] iwlwifi 0000:04:00.0: no suitable firmware found! 

```

---

### Post by chili555 on 2015-05-02
> [    3.316691] iwlwifi 0000:04:00.0: request for firmware file 'iwlwifi-7265-8.ucode' failed.
[    3.316696] iwlwifi 0000:04:00.0: no suitable firmware found!I don't know how those guys do it! They're magic!

Let's get some firmware. Please get this: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.228.9.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-25.228.9.0.tgz) and this: [https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-22.24.8.0.tgz](https://wireless.wiki.kernel.org/_media/en/users/drivers/iwlwifi-7265-ucode-22.24.8.0.tgz) Download both to your desktop. Right-click each and select 'Extract Here.' Now, to the terminal:```
cd ~/Desktop/iwlwifi-7265-ucode-22.24.8.0
sudo cp iwl*  /lib/firmware
cd ~/Desktop/iwlwifi-7265-ucode-25.228.9.0
sudo cp iwl*  /lib/firmware
sudo modprobe -r iwlwifi && sudo modprobe iwlwifi
```Your wireless should be working, but it might take a reboot.

---

### Post by BuffaloBuffalo on 2015-05-02
Amazing!!!! It worked effortlessly - no reboot needed even! Thank you so much!

If I can ask, what tipped you off that it was firmware (before the obvious "no suitable firmware found!")? Also, why would the firmware disappear after the kernel upgrade? (I assume I had firmware before that made my wifi work?)

Thanks again!

---

### Post by chili555 on 2015-05-02
>  what tipped you off that it was firmware The 7265 is a pretty new device and 3.16 is a somewhat older kernel version. I suspect that the 7265 was introduced after 3.16 first was released. Absence of 7265 firmware is therefore a possibility.

As to why it worked once and then didn't, I haven't even a guess! I'm just glad it's working now. Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

