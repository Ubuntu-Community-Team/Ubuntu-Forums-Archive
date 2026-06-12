---
title: "Problem With Wireless Connection"
date: 2016-01-13
forum: Networking &amp; Wireless
---

### Post by HerzeleidMeister on 2016-01-13
Hello, my wireless connection using Ubuntu seems to drop out a lot and I have to reboot the laptop in order to get it restarted again. I've tried just reconnecting and it does not seem to work. I'm not at all sure what info you may need to help me fix this problem, so please let me know. Staying connected is super important to me as i'm a web designer by trade.

---

### Post by Bucky Ball on 2016-01-13
New install? Either way, do this, and use an ethernet cable if possible:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Reboot. Any better? If not, post the output of this between code tags (see the green link in my signature):

```
sudo lshw -C network
```

That might give us enough info, but you should [also read this]("http://ubuntuforums.org/showthread.php?t=370108"). We recommend you do so prior to posting generally. :)

---

### Post by HerzeleidMeister on 2016-01-14
Ok will reboot and see. The connection will sometimes be ok for a couple of hours or days even and then for no reason it drops out. So I may not see if the first part worked right away. I'll go ahead and post the output here:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: f8:a9:63:2f:80:aa
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-3_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:64 ioport:4000(size=256) memory:c0604000-c0604fff memory:c0600000-c0603fff
  *-network
       description: Wireless interface
       product: Wireless 3160
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 93
       serial: d0:7e:35:33:1e:13
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-74-generic firmware=22.24.8.0 ip=192.168.1.115 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:66 memory:c0500000-c0501fff


```

---

### Post by Bucky Ball on 2016-01-14
After updating and rebooting, next time it drops, if it drops, post the output of the Wirelessinfo script in my signature, please.

---

### Post by HerzeleidMeister on 2016-01-14
Ok but I will not be able t do that because I'll have to reboot to be back online. So I very well would not be able to connect at all. How am I supposed to run that command when I&#8217;m not online?

---

### Post by Bucky Ball on 2016-01-14
By plugging an ethernet cable in?

---

### Post by HerzeleidMeister on 2016-01-14
Don't have one and my laptop does not have a port for it anyways.

---

### Post by Bucky Ball on 2016-01-14
Okay. Post it now.

---

### Post by HerzeleidMeister on 2016-01-14
Ok. Upon looking at my laptop it does look like there is a place for an Ethernet cable but its not the standard one, probably newer than a cat5 if that's possible. Either way I don't have a cable for it. :( Here's the output:

```

########## wireless info START ##########

Report from: 14 Jan 2016 02:01 EST -0500

Booted last: 14 Jan 2016 00:08 EST -0500

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-74-generic #118-Ubuntu SMP Thu Dec 17 22:52:10 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

GNOME Flashback (Compiz)

##### lspci #############################

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo Device [17aa:3809]
    Kernel driver in use: r8169

04:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b4] (rev 93)
    Subsystem: Intel Corporation Dual Band Wireless AC 3160 [8086:8270]
    Kernel driver in use: iwlwifi

##### lsusb #############################

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 8087:07dc Intel Corp. 
Bus 002 Device 003: ID 174f:14b1 Syntek 
Bus 002 Device 009: ID 0480:a006 Toshiba America Info. Systems, Inc. 
Bus 002 Device 008: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
Bus 002 Device 007: ID 0480:0200 Toshiba America Info. Systems, Inc. 
Bus 002 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 005: ID 062a:4101 Creative Labs 
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwlmvm                189852  0 
mac80211              630728  1 iwlmvm
iwlwifi               169932  1 iwlmvm
cfg80211              484040  3 iwlwifi,mac80211,iwlmvm
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85875779 (85.8 MB)  TX bytes:5441859 (5.4 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"TheDarkSide"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'TheDarkSide' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-17 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:8  Invalid misc:137   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search knology.net

##### network managers ##################

Installed:

    NetworkManager

Running:

root       859     1  0 00:08 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [TheDarkSide] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TheDarkSide-guest: Infra, <MAC 'TheDarkSide-guest' [AC9]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 100
    TheDarkSide-guest: Infra, <MAC 'TheDarkSide-guest' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100
    TheDarkSide:     Infra, <MAC 'TheDarkSide' [AC8]>, Freq 5745 MHz, Rate 54 Mb/s, Strength 83 WPA WPA2
    *TheDarkSide:    Infra, <MAC 'TheDarkSide' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Wow!0647:        Infra, <MAC 'Wow!0647' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA2

  IPv4 Settings:
    Address:         192.168.1.115
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

[[/etc/NetworkManager/system-connections/TheDarkSide]] (600 root)
[connection] id=TheDarkSide | type=802-11-wireless
[802-11-wireless] ssid=TheDarkSide | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-91D2]] (600 root)
[connection] id=HOME-91D2 | type=802-11-wireless
[802-11-wireless] ssid=HOME-91D2 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/HOME-9119]] (600 root)
[connection] id=HOME-9119 | type=802-11-wireless
[802-11-wireless] ssid=HOME-9119 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/TheDarkSide-guest]] (600 root)
[connection] id=TheDarkSide-guest | type=802-11-wireless
[802-11-wireless] ssid=TheDarkSide-guest | mac-address=<MAC 'wlan0' [IF]>
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

eth0      no frequency information.

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
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      7   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:5.745 GHz

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TheDarkSide' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:on
                    ESSID:"TheDarkSide"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004bbc4a90bf
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'TheDarkSide-guest' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-21 dBm  
                    Encryption key:off
                    ESSID:"TheDarkSide-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004bbc4a5034
                    Extra: Last beacon: 24ms ago
          Cell 03 - Address: <MAC 'HOME-F292' [AC3]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"HOME-F292"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000045efe9f746
                    Extra: Last beacon: 24ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'xfinitywifi' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000045efe9fd80
                    Extra: Last beacon: 24ms ago
          Cell 05 - Address: <MAC 'xfinitywifi' [AC5]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000258fca3180
                    Extra: Last beacon: 4144ms ago
          Cell 06 - Address: <MAC '' [AC6]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000045efe99b95
                    Extra: Last beacon: 4124ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC 'HOME-0A27-2.4' [AC7]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"HOME-0A27-2.4"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000258fca3180
                    Extra: Last beacon: 4092ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC 'TheDarkSide' [AC8]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:on
                    ESSID:"TheDarkSide"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004bbcb1dd66
                    Extra: Last beacon: 24ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC 'TheDarkSide-guest' [AC9]>
                    Channel:149
                    Frequency:5.745 GHz
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:off
                    ESSID:"TheDarkSide-guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004bbcb17cd2
                    Extra: Last beacon: 24ms ago

##### module infos ######################

[iwlmvm]
filename:       /lib/modules/3.13.0-74-generic/kernel/drivers/net/wireless/iwlwifi/mvm/iwlmvm.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    The new Intel(R) wireless AGN driver for Linux
srcversion:     E1740125DB45A064E2455BB
depends:        iwlwifi,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           init_dbg:set to true to debug an ASSERT in INIT fw (default: false (bool)
parm:           power_scheme:power management scheme: 1-active, 2-balanced, 3-low power, default: 2 (int)

[mac80211]
filename:       /lib/modules/3.13.0-74-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C8432FAB97804E8F7A8FB0F
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-74-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
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
srcversion:     797502E088D21C379B35700
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
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

[cfg80211]
filename:       /lib/modules/3.13.0-74-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     695424C2F5CD23A91B67E25
depends:        
intree:         Y
vermagic:       3.13.0-74-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        14:8A:25:3C:CE:F5:E2:9B:7F:50:8A:4C:FE:5D:C1:0E:72:1C:82:1C
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwlmvm]
init_dbg: N
power_scheme: 2

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x08b4 (iwlwifi)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[  335.569122] wlan0: Limiting TX power to 20 (23 - 3) dBm as advertised by <MAC 'TheDarkSide' [AC8]>
[  694.834139] wlan0: authenticate with <MAC 'TheDarkSide' [AC1]>
[  694.840483] wlan0: send auth to <MAC 'TheDarkSide' [AC1]> (try 1/3)
[  694.842749] wlan0: authenticated
[  694.846311] wlan0: associate with <MAC 'TheDarkSide' [AC1]> (try 1/3)
[  694.881638] wlan0: RX AssocResp from <MAC 'TheDarkSide' [AC1]> (capab=0x411 status=0 aid=12)
[  694.889293] wlan0: associated
[ 6048.435411] wlan0: AP <MAC 'TheDarkSide' [AC1]> changed bandwidth, new config is 2437 MHz, width 1 (2437/0 MHz)
[ 6051.011241] iwlwifi 0000:04:00.0: Microcode SW error detected.  Restarting 0x2000000.
[ 6051.011253] iwlwifi 0000:04:00.0: CSR values:
[ 6051.011258] iwlwifi 0000:04:00.0: (2nd byte of CSR_INT_COALESCING is CSR_INT_PERIODIC_REG)
[ 6051.011276] iwlwifi 0000:04:00.0:        CSR_HW_IF_CONFIG_REG: 0X00c89204
[ 6051.011294] iwlwifi 0000:04:00.0:          CSR_INT_COALESCING: 0X8000ff40
[ 6051.011311] iwlwifi 0000:04:00.0:                     CSR_INT: 0X00000000
[ 6051.011328] iwlwifi 0000:04:00.0:                CSR_INT_MASK: 0X00000000
[ 6051.011345] iwlwifi 0000:04:00.0:           CSR_FH_INT_STATUS: 0X00000000
[ 6051.011362] iwlwifi 0000:04:00.0:                 CSR_GPIO_IN: 0X00000000
[ 6051.011378] iwlwifi 0000:04:00.0:                   CSR_RESET: 0X00000000
[ 6051.011394] iwlwifi 0000:04:00.0:                CSR_GP_CNTRL: 0X080403c5
[ 6051.011410] iwlwifi 0000:04:00.0:                  CSR_HW_REV: 0X00000164
[ 6051.011425] iwlwifi 0000:04:00.0:              CSR_EEPROM_REG: 0X00000000
[ 6051.011441] iwlwifi 0000:04:00.0:               CSR_EEPROM_GP: 0X80000000
[ 6051.011457] iwlwifi 0000:04:00.0:              CSR_OTP_GP_REG: 0X803a0000
[ 6051.011472] iwlwifi 0000:04:00.0:                 CSR_GIO_REG: 0X00080042
[ 6051.011488] iwlwifi 0000:04:00.0:            CSR_GP_UCODE_REG: 0X00000000
[ 6051.011504] iwlwifi 0000:04:00.0:           CSR_GP_DRIVER_REG: 0X00000000
[ 6051.011519] iwlwifi 0000:04:00.0:           CSR_UCODE_DRV_GP1: 0X00000000
[ 6051.011535] iwlwifi 0000:04:00.0:           CSR_UCODE_DRV_GP2: 0X00000000
[ 6051.011551] iwlwifi 0000:04:00.0:                 CSR_LED_REG: 0X00000060
[ 6051.011566] iwlwifi 0000:04:00.0:        CSR_DRAM_INT_TBL_REG: 0X8844690c
[ 6051.011582] iwlwifi 0000:04:00.0:        CSR_GIO_CHICKEN_BITS: 0X27800200
[ 6051.011597] iwlwifi 0000:04:00.0:             CSR_ANA_PLL_CFG: 0Xd55555d5
[ 6051.011613] iwlwifi 0000:04:00.0:           CSR_HW_REV_WA_REG: 0X0001001a
[ 6051.011629] iwlwifi 0000:04:00.0:        CSR_DBG_HPET_MEM_REG: 0Xffff0010
[ 6051.011633] iwlwifi 0000:04:00.0: FH register values:
[ 6051.011659] iwlwifi 0000:04:00.0:         FH_RSCSR_CHNL0_STTS_WPTR_REG: 0X4452b200
[ 6051.011685] iwlwifi 0000:04:00.0:        FH_RSCSR_CHNL0_RBDCB_BASE_REG: 0X04452b10
[ 6051.011708] iwlwifi 0000:04:00.0:                  FH_RSCSR_CHNL0_WPTR: 0X00000060
[ 6051.011731] iwlwifi 0000:04:00.0:         FH_MEM_RCSR_CHNL0_CONFIG_REG: 0X80801114
[ 6051.011754] iwlwifi 0000:04:00.0:          FH_MEM_RSSR_SHARED_CTRL_REG: 0X000000fc
[ 6051.011778] iwlwifi 0000:04:00.0:            FH_MEM_RSSR_RX_STATUS_REG: 0X07030000
[ 6051.011801] iwlwifi 0000:04:00.0:    FH_MEM_RSSR_RX_ENABLE_ERR_IRQ2DRV: 0X00000000
[ 6051.011827] iwlwifi 0000:04:00.0:                FH_TSSR_TX_STATUS_REG: 0X07ff0001
[ 6051.011850] iwlwifi 0000:04:00.0:                 FH_TSSR_TX_ERROR_REG: 0X00000000
[ 6051.011972] iwlwifi 0000:04:00.0: Start IWL Error Log Dump:
[ 6051.011977] iwlwifi 0000:04:00.0: Status: 0x00000000, count: 6
[ 6051.011980] iwlwifi 0000:04:00.0: Loaded firmware version: 22.24.8.0
[ 6051.011985] iwlwifi 0000:04:00.0: 0x00002078 | ADVANCED_SYSASSERT          
[ 6051.011989] iwlwifi 0000:04:00.0: 0x00A002B0 | uPc
[ 6051.011993] iwlwifi 0000:04:00.0: 0x00000000 | branchlink1
[ 6051.011997] iwlwifi 0000:04:00.0: 0x00000BEA | branchlink2
[ 6051.012000] iwlwifi 0000:04:00.0: 0x00014218 | interruptlink1
[ 6051.012004] iwlwifi 0000:04:00.0: 0x00260410 | interruptlink2
[ 6051.012007] iwlwifi 0000:04:00.0: 0x00000000 | data1
[ 6051.012011] iwlwifi 0000:04:00.0: 0x00004906 | data2
[ 6051.012014] iwlwifi 0000:04:00.0: 0xDEADBEEF | data3
[ 6051.012018] iwlwifi 0000:04:00.0: 0x09814BAE | beacon time
[ 6051.012022] iwlwifi 0000:04:00.0: 0x8C9232F6 | tsf low
[ 6051.012025] iwlwifi 0000:04:00.0: 0x0000004B | tsf hi
[ 6051.012029] iwlwifi 0000:04:00.0: 0x00000000 | time gp1
[ 6051.012033] iwlwifi 0000:04:00.0: 0x678B79A5 | time gp2
[ 6051.012036] iwlwifi 0000:04:00.0: 0x00000000 | time gp3
[ 6051.012039] iwlwifi 0000:04:00.0: 0x00041618 | uCode version
[ 6051.012043] iwlwifi 0000:04:00.0: 0x00000164 | hw version
[ 6051.012047] iwlwifi 0000:04:00.0: 0x00C89204 | board version
[ 6051.012050] iwlwifi 0000:04:00.0: 0x0934004E | hcmd
[ 6051.012054] iwlwifi 0000:04:00.0: 0x00022084 | isr0
[ 6051.012057] iwlwifi 0000:04:00.0: 0x00000000 | isr1
[ 6051.012060] iwlwifi 0000:04:00.0: 0x0000000B | isr2
[ 6051.012064] iwlwifi 0000:04:00.0: 0x0041ECC0 | isr3
[ 6051.012067] iwlwifi 0000:04:00.0: 0x00000000 | isr4
[ 6051.012071] iwlwifi 0000:04:00.0: 0x01000112 | isr_pref
[ 6051.012074] iwlwifi 0000:04:00.0: 0x00000000 | wait_event
[ 6051.012078] iwlwifi 0000:04:00.0: 0x00004208 | l2p_control
[ 6051.012082] iwlwifi 0000:04:00.0: 0x00010020 | l2p_duration
[ 6051.012085] iwlwifi 0000:04:00.0: 0x0000033F | l2p_mhvalid
[ 6051.012089] iwlwifi 0000:04:00.0: 0x000000E6 | l2p_addr_match
[ 6051.012092] iwlwifi 0000:04:00.0: 0x00000005 | lmpm_pmg_sel
[ 6051.012096] iwlwifi 0000:04:00.0: 0x23021719 | timestamp
[ 6051.012099] iwlwifi 0000:04:00.0: 0x00006070 | flow_handler
[ 6051.066429] iwlwifi 0000:04:00.0: L1 Enabled - LTR Enabled (repeated 2 times)

########## wireless info END ############


```

---

### Post by Bucky Ball on 2016-01-14
You could [give this a bash]("http://ubuntuforums.org/showthread.php?t=2264792&p=13226020&viewfull=1#post13226020").

What is the make/model of your machine? Have you looked for it [here]("http://www.ubuntu.com/certification/catalog/component/pci/8086%3A08b3/")? That might give further clues.

---

### Post by HerzeleidMeister on 2016-01-14
I have a Lenovo Y40 70 laptop. Its not in that list.

---

### Post by Bucky Ball on 2016-01-14
Try the link I supplied in post #10. You have not mentioned your results from that.

---

### Post by HerzeleidMeister on 2016-01-15
The only output I got from the link was this:

```
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
```

I changed the code to my country and rebooted. We will see if it still drops.

---

### Post by Bucky Ball on 2016-01-15
And switch IPv6 to 'Ignore' in the Network Manager IPv6 tab for your wireless connection.

---

### Post by HerzeleidMeister on 2016-01-15
I did. I did everything it said in that post. I'm waiting to see if it drops again.

---

### Post by Bucky Ball on 2016-01-15
Cool. Give it twenty-four hours and see how it goes. The moment it drops, open a terminal and:

> dmesg

The last part of that output should give some clues. Save it, get back online and post it here, please.

---

### Post by HerzeleidMeister on 2016-01-16
Looks like something from that post has worked. :) no drops so far and it was dropping about every couple of hours before. Thanks for the help. If it should drop out again I'll post back.

---

### Post by Bucky Ball on 2016-01-16
Please do.

In the meantime, see the first link in my signature below and mark the thread as solved. If the problem crops up again, you can mark it 'unsolved' the same way. If the issue crops up again in a month or two, better to post a new thread and link to this one if it's relevant.

Enjoy. ;)

---

### Post by HerzeleidMeister on 2016-01-16
Thanks, marked as solved.

---

