---
title: "Problem with Wifi Ubuntu 14.0.4"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by manolis2 on 2015-07-01
Hi to all!
I had a problem because the wifi connection was unstable in my connection and that's why i followed the the second post from [this answer]("http://ubuntuforums.org/showthread.php?t=2219952") and now I don't have wifi connection at all.

This is the outcome from the wireless script that i ran.

Any thoughts?


```
########## wireless info START ##########

Report from: 01 Jul 2015 11:27 EEST +0300

Booted last: 01 Jul 2015 00:00 EEST +0300

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2248]
    Kernel driver in use: r8169

09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]

0a:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Topaz PRO [Radeon R5 M255] [1002:6901]

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 04f2:b477 Chicony Electronics Co., Ltd 
Bus 002 Device 004: ID 138a:003f Validity Sensors, Inc. 
Bus 002 Device 003: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 002 Device 007: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 008: ID 1004:633e LG Electronics, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19177  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:138.4.55.144  Bcast:138.4.55.191  Mask:255.255.255.192
          inet6 addr: fe80::d2bf:9cff:fe63:f33b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1296779 errors:0 dropped:365 overruns:0 frame:0
          TX packets:618204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1146808987 (1.1 GB)  TX bytes:72582726 (72.5 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         138.4.55.129    0.0.0.0         UG    0      0        0 eth0
138.4.55.128    0.0.0.0         255.255.255.192 U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search die.upm.es

##### network managers ##################

Installed:

    NetworkManager

Running:

root       756     1  0 Jun30 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         138.4.55.144
    Prefix:          26 (255.255.255.192)
    Gateway:         138.4.55.129

    DNS:             138.4.55.129

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

[[/etc/NetworkManager/system-connections/ __ORIOCENTER__]] (600 root)
[connection] id=\s__ORIOCENTER__ | type=802-11-wireless
[802-11-wireless] ssid=\s__ORIOCENTER__ | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/L90_4972]] (600 root)
[connection] id=L90_4972 | type=802-11-wireless
[802-11-wireless] ssid=L90_4972 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MOVISTAR_4466]] (600 root)
[connection] id=MOVISTAR_4466 | type=802-11-wireless
[802-11-wireless] ssid=MOVISTAR_4466 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/@FreeLuna]] (600 root)
[connection] id=@FreeLuna | type=802-11-wireless
[802-11-wireless] ssid=@FreeLuna | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/AntonisSom]] (600 root)
[connection] id=AntonisSom | type=802-11-wireless
[802-11-wireless] ssid=AntonisSom | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BGY Public WiFi]] (600 root)
[connection] id=BGY Public WiFi | type=802-11-wireless
[802-11-wireless] ssid=BGY Public WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Athens (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee ips=0 fwlps=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############
```

---

### Post by jeremy31 on 2015-07-01
Wrong driver was installed, to fix
```
cd rtl8188ce-linux-driver
```
```
sudo make uninstall
```
```
sudo rm /etc/modprobe.d/rtl8188ee.conf
```
```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot and run the wireless script again if the wifi doesn't work

---

### Post by manolis2 on 2015-07-01
Nothing again :/

This the last run of the script.

```

########## wireless info START ##########

Report from: 01 Jul 2015 13:21 EEST +0300

Booted last: 01 Jul 2015 13:18 EEST +0300

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-55-generic #94-Ubuntu SMP Thu Jun 18 00:27:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:2248]
    Kernel driver in use: r8168

09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:2231]

0a:00.0 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] Topaz PRO [Radeon R5 M255] [1002:6901]

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 04f2:b477 Chicony Electronics Co., Ltd 
Bus 002 Device 005: ID 138a:003f Validity Sensors, Inc. 
Bus 002 Device 004: ID 0bda:b001 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 1004:633e LG Electronics, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

hp_wmi                 14062  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19177  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:138.4.55.144  Bcast:138.4.55.191  Mask:255.255.255.192
          inet6 addr: fe80::d2bf:9cff:fe63:f33b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16930 errors:0 dropped:2 overruns:0 frame:0
          TX packets:10330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18981102 (18.9 MB)  TX bytes:960017 (960.0 KB)
          Interrupt:62 Base address:0x6000 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         138.4.55.129    0.0.0.0         UG    0      0        0 eth0
138.4.55.128    0.0.0.0         255.255.255.192 U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search die.upm.es

##### network managers ##################

Installed:

    NetworkManager

Running:

root       795     1  0 13:18 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8168
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         138.4.55.144
    Prefix:          26 (255.255.255.192)
    Gateway:         138.4.55.129

    DNS:             138.4.55.129

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

[[/etc/NetworkManager/system-connections/ __ORIOCENTER__]] (600 root)
[connection] id=\s__ORIOCENTER__ | type=802-11-wireless
[802-11-wireless] ssid=\s__ORIOCENTER__ | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/L90_4972]] (600 root)
[connection] id=L90_4972 | type=802-11-wireless
[802-11-wireless] ssid=L90_4972 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/MOVISTAR_4466]] (600 root)
[connection] id=MOVISTAR_4466 | type=802-11-wireless
[802-11-wireless] ssid=MOVISTAR_4466 | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/@FreeLuna]] (600 root)
[connection] id=@FreeLuna | type=802-11-wireless
[802-11-wireless] ssid=@FreeLuna | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/AntonisSom]] (600 root)
[connection] id=AntonisSom | type=802-11-wireless
[802-11-wireless] ssid=AntonisSom | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/BGY Public WiFi]] (600 root)
[connection] id=BGY Public WiFi | type=802-11-wireless
[802-11-wireless] ssid=BGY Public WiFi | mac-address=<MAC address>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/Athens (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

##### module infos ######################

##### module parameters #################

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

[/etc/modprobe.d/r8168-dkms.conf]
blacklist r8169

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be fwlps=N

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.2/0000:08:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

########## wireless info END ############


```

---

### Post by jeremy31 on 2015-07-01
Try ```
sudo apt-get install linux-headers-$(uname -r) build-essential
```
```
[/FONT][/COLOR]wget https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.19-rc1/backports-3.19-rc1-1.tar.gz
```
```
tar -zxvf backports-3.19-rc1-1.tar.gz
```
 ```
cd backports-3.19-rc1-1
```
```
make defconfig-rtlwifi
```
```
make
```
```
sudo make install
```
Reboot

---

### Post by Pilot6 on 2015-07-01
You can install a driver this way

```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
```

---

### Post by Pilot6 on 2015-07-01
3.19 kernel does not have a working driver. But I suggest to upgrade kernel either way by

sudo apt-get install linux-generic-lts-vivid

---

