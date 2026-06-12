---
title: "Setting up AP, no eth0 connection"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by russ12 on 2014-08-24
I have a lenovo w530 with an Intel centrino ultimate-n 6300 WLAN card. I am running ubuntu 14.04. 

 I am moving to Germany in a week and I am fairly certain I will only have a wired connection - hence why I am trying to set this up in the first place.  I followed a few tutorials on how to set up an AP, including using hostapd which didn't install with a .conf file. I tried setting up the AP through network connections and that didnt work.  I eventually was able to produce a response that said my card does not support access points.  So, last night I went and bought a netgear n600 and had the same resutls.  After all of this, I ashamed to say I didn't take notice of iwconig when it told me I had no eth0 connection even though a popup told me I was connected.  

It looks like my issue now is my computer will not allow a wired connection. I have tried a couple things I found from searching, but I still have no connection.  Any thoughts?

---

### Post by russ12 on 2014-08-25
Any thoughts?

---

### Post by Ksiencha on 2014-08-25
I think you should give the experts (who will visit this thread) more info, go in terminal and run this command:

```

wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script

```

The command will download a script and create a file named  (**wireless-info.txt** or **wireless-info.txt.tar.gz**) depending on the size of  the file. It will be placed in your home folder. Please, attach this file here or copy/paste its content and wrap it with **```

```** tags ([http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)).

---

### Post by russ12 on 2014-08-25
I have changed out my WLAN card and now it is showing as a wlan1 when my original was a wlan0.  Still no eth0.

Get ready, this is a big'un.

```

########## wireless info START ##########

Report from: 25 Aug 2014 19:51 EDT -0400

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:45:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21f3]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Intel Corporation Centrino Ultimate-N 6300 [8086:4238] (rev 35)
    Subsystem: Intel Corporation Centrino Ultimate-N 6300 3x3 AGN [8086:1111]
    Kernel driver in use: iwlwifi

##### lsusb #####

Bus 002 Device 003: ID 0765:5010 X-Rite, Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b2ea Chicony Electronics Co., Ltd Integrated Camera [ThinkPad]
Bus 001 Device 003: ID 147e:2020 Upek TouchChip Fingerprint Coprocessor (WBF advanced mode)
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: tpacpi_bluetooth_sw: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #####

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3e97:eff:fe54:5b90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:491 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46594 (46.5 KB)  TX bytes:29348 (29.3 KB)
          Interrupt:20 Memory:f3a00000-f3a20000 

wlan1     Link encap:Ethernet  HWaddr <MAC addr wlan1>  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:d7ff:febb:c2b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8018 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5360 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7194232 (7.1 MB)  TX bytes:811953 (811.9 KB)

##### iwconfig #####

eth0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11abgn  ESSID:"YJP3D"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC addr YJP3D>   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-20 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:118   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
10.42.0.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1

##### resolv.conf #####

nameserver 127.0.0.1
search home

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan1  [YJP3D 1] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC addr wlan1>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-8792:       Infra, <MAC addr HOME-8792>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    xfinitywifi:     Infra, <MAC addr xfinitywifi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    Q1E72:           Infra, <MAC addr Q1E72>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WEP
    08W11:           Infra, <MAC addr 08W11>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP
    Frank Pearson:   Infra, <MAC addr Frank Pearson>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    *YJP3D:          Infra, <MAC addr YJP3D>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WEP

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           no
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.42.0.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

no-auto-default=<MAC addr eth0>,

[ifupdown]
managed=false

##### iw reg get #####

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### iwlist channels #####

eth0      no frequency information.

lo        no frequency information.

wlan1     32 channels in total; available frequencies :
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
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #####

Channel occupancy:

     1   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan1     Scan completed :
          Cell 01 - Address: <MAC addr YJP3D>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"YJP3D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002aa5e72642
                    Extra: Last beacon: 20ms ago
          Cell 02 - Address: <MAC addr 08W11>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"08W11"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000644ca64ef5
                    Extra: Last beacon: 20ms ago

##### module infos #####

[iwldvm]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     C000699B57577A9A45666BA
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512

[iwlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
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
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     5AA2E0FDE335B45C3F44AE0
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        50:0B:C5:C8:7D:4B:11:5C:F3:C1:50:4F:7A:92:E2:33:C6:14:3D:58
sig_hashalgo:   sha512
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

##### module parameters #####

[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
wd_disable: 1

##### /etc/modules #####

lp
rtc

##### blacklists #####

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

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4238 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:0x4238 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    1.860833] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    2.149116] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    6.933907] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   32.184974] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   32.185036] iwlwifi 0000:03:00.0: irq 49 for MSI/MSI-X
[   32.283301] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   32.283308] iwlwifi 0000:03:00.0: Falling back to user helper
[   32.994054] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[   32.994057] iwlwifi 0000:03:00.0: Falling back to user helper
[   33.577995] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   34.032116] usb 1-1.4: Direct firmware load failed with error -2
[   34.032660] Bluetooth: can't load firmware, may not work correctly
[   34.132420] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   34.132423] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   34.132424] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   34.132425] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   34.132474] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   34.268425] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   34.701984] systemd-udevd[584]: renamed network interface wlan0 to wlan1
[   45.773564] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   45.776525] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   45.996000] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[   46.003020] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[   46.153438] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready (repeated 2 times)
[  135.498647] wlan1: authenticate with <MAC addr YJP3D>
[  135.555855] wlan1: send auth to <MAC addr YJP3D> (try 1/3)
[  135.558511] wlan1: authenticated
[  135.558753] iwlwifi 0000:03:00.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  135.559933] wlan1: associate with <MAC addr YJP3D> (try 1/3)
[  135.562975] wlan1: RX AssocResp from <MAC addr YJP3D> (capab=0x431 status=0 aid=4)
[  135.566895] wlan1: associated
[  135.566946] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  300.013691] wlan1: deauthenticating from <MAC addr YJP3D> by local choice (reason=3)
[  319.526007] wlan1: Trigger new scan to find an IBSS to join (repeated 3 times)
[  328.035187] wlan1: Creating new IBSS network, BSSID <MAC address>
[  328.103008] iwlwifi 0000:03:00.0: Unable to find TIM Element in beacon (repeated 2 times)
[  357.512085] wlan1: No active IBSS STAs - trying to scan for other IBSS networks with same SSID (merge) (repeated 3 times)
[  423.268712] iwlwifi 0000:03:00.0: L1 Enabled; Disabling L0S
[  423.275722] iwlwifi 0000:03:00.0: Radio type=0x0-0x3-0x1
[  423.418742] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  447.731721] wlan1: authenticate with <MAC addr YJP3D>
[  447.789463] wlan1: send auth to <MAC addr YJP3D> (try 1/3)
[  447.893856] wlan1: send auth to <MAC addr YJP3D> (try 2/3)
[  447.895805] wlan1: authenticated
[  447.896124] iwlwifi 0000:03:00.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  447.897853] wlan1: associate with <MAC addr YJP3D> (try 1/3)
[  447.900920] wlan1: RX AssocResp from <MAC addr YJP3D> (capab=0x431 status=0 aid=1)
[  447.904837] wlan1: associated
[  447.904855] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready

########## wireless info END ############
```

I deleted the original ethernet connect and made another.  Now it seems to be working, but still shows no connection with iwconfig.  Cant create an access point through netweork settings.

---

### Post by jeremy31 on 2014-08-25
I would say, post again once you are in Germany and connected via wired ethernet.  It isn't difficult setting up the wifi hotspot using network manager

---

### Post by grahammechanical on 2014-08-25
Do you see the ifconfig part? It shows that eth0 is UP BROADCAST RUNNING MULTICAST. That means the ethernet adapter is working and is connected. Rx Bytes = Bytes of data received. Tx Bytes = Bytes of data transmitted. And do not notice you have the same report for wlan1.

iwconfig shows that wlan1 is connected to wireless access point ESSID YJP3D with a signal strenth of 20 dBm

network manager tool shows wlan1 to be connected and it has a driver and is detecting wireless access point in range.

What is the problem? Do you want to use this machine as a wireless access point or hot spot. Try System Settings>Network>Use as Hotspot again.

Regards.

---

### Post by ian-weisser on 2014-08-25
[edit] grahammechanical beat me to it...

---

### Post by russ12 on 2014-08-26
I am trying to create an access point for my other devices in my apartment - both droids.  I see now that wlan1 is broadcasting, but when I try to set up the ap in network settings, both my phone and tablet can't see the network I just created.  YJP3D is the home wifi network so we don't want to go on that.  I was naming my ap something like trial or dodobird.

Isn't there a setting to create the ap in infrastructure and not ad hoc?  I ask because it seems droid devices will not recognize ad hoc.

---

### Post by Ksiencha on 2014-08-26
I hope [**this article**](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html) on how to set up hotspot that supports android will help you. I use this app myself, however I haven't tried it on smartphones.

---

### Post by russ12 on 2014-08-26
I will add that to the list of things to try when I get home from work today.  Thanks!

---

### Post by russ12 on 2014-08-26
Ethernet is working!

All this work to try to get an AP set up and its telling me access points are not supported by this device.  I have been reading that software could change this?  The internal car is an intel centrino ultimate n 6300.  I also have on hand a netgear n600 if that would be easier to work.

edit: have tried ndiswrapper in multiple ways, I am sure I am doing something wrong.  When using [#29 as chili555]("http://ubuntuforums.org/showthread.php?t=1695036&highlight=bcmwlhigh5&page=3") says, the wrong driver is being used.  When I look further into it, that is the more up to date driver.  

Which device will be easier to use?  Where to now?

---

