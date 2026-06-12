---
title: "Wifi does not work on Broadcom BCM4313 [14e4:4727] (rev1)"
date: 2015-07-11
forum: Networking &amp; Wireless
---

### Post by ivan91 on 2015-07-11
I spent a day following numerous tutorials how to install drivers for this but none of them worked.
Some say its problem with bcma/b43 and that the one that should work is brcsmac.

When I go to Software & Updates > Additional Drivers, it says Broadcom Corporation:BCM4313 802.11b/g/n Wireless LAN Controller - This device is not working, and its selected Do Not use the device, other option is Using Broadcom 802.11 Linux STA Wireless driver source from bcmwl-kernel-source (proprietary)

$ lspci -nn -d 14e4:
[HTML]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
[/HTML]


$ lspci -k
[HTML]
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Hewlett-Packard Company Device 1894
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: mei_me
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: lpc_ich
00:1f.2 RAID bus controller: Intel Corporation 82801 Mobile SATA Controller [RAID mode] (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Hewlett-Packard Company Device 1894
01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: rtsx_pci
01:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
    Subsystem: Hewlett-Packard Company Device 1894
    Kernel driver in use: r8169
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)
    Subsystem: Hewlett-Packard Company Device 1795
    Kernel driver in use: bcma-pci-bridge
[/HTML]

---

### Post by Vladlenin5000 on 2015-07-11
Hi and welcome.
We have a sticky for Broadcom devices: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
Please read it and proceed accordingly. Your device is featured in the "special cases".

---

### Post by ivan91 on 2015-07-11
> **Vladlenin5000 said:**
> Hi and welcome.
We have a sticky for Broadcom devices: [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)
Please read it and proceed accordingly. Your device is featured in the "special cases".

If you are reffering to this, I already tried it and it does not work, also that is pci.id 4727, mine is 4727 (rev 01)
14e4:4727                  Special case #3                       Special case #1

---

### Post by Vladlenin5000 on 2015-07-11
Rev refers to the model, the ID is unique. Meaning, rev 01 refers to "BCM4313 rev 01", other eventual BCM4313 revisions - the Broadcom model number for marketing purposes only - will have different IDs whenever the hardware had been changed.
So, assuming you're running 14.04 or later that would be "special case #1". Is that was you did?
Please check carefully. Even so, whatever you did before may now prevent this easy solution to work.

---

### Post by ivan91 on 2015-07-11
> **Vladlenin5000 said:**
> Rev refers to the model, the ID is unique. Meaning, rev 01 refers to "BCM4313 rev 01", other eventual BCM4313 revisions - the Broadcom model number for marketing purposes only - will have different IDs whenever the hardware had been changed.
So, assuming you're running 14.04 or later that would be "special case #1". Is that was you did?
Please check carefully. Even so, whatever you did before may now prevent this easy solution to work.

Thanks for clarification about rev.
I did special case #1 on a clean ubuntu 14.04 installation and rebooted, still does not work (I connect with my wifi but when I try to connect on internet it doesnt work)
[HTML]sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit[/HTML]

---

### Post by Vladlenin5000 on 2015-07-11
Now - without further changes - it's time to follow the instruction in the other sticky - [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) -, run the wireless script and post the results.
Dr. Chilli may come around ;-)

PS - You may need an Ethernet connection (the easy way).

---

### Post by ivan91 on 2015-07-11
> **Vladlenin5000 said:**
> Now - without further changes - it's time to follow the instruction in the other sticky - [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) -, run the wireless script and post the results.
Dr. Chilli may come around ;-)

PS - You may need an Ethernet connection (the easy way).

Result of wireless-info
[HTML]
########## wireless info START ##########

Report from: 11 Jul 2015 17:41 CEST +0200

Booted last: 11 Jul 2015 17:33 CEST +0200

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-43-generic #58~14.04.1-Ubuntu SMP Mon Jun 22 10:21:20 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
    Subsystem: Hewlett-Packard Company Device [103c:1894]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: bcma-pci-bridge

##### lsusb #############################

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:c336 Suyin Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

brcmsmac              563061  0 
cordic                 12574  1 brcmsmac
brcmutil               15579  1 brcmsmac
mac80211              652777  1 brcmsmac
cfg80211              494362  2 brcmsmac,mac80211
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
bcma                   52320  2 brcmsmac
wmi                    19193  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.137.81  Bcast:192.168.137.255  Mask:255.255.255.0
          inet6 addr: fe80::2a92:4aff:fe1b:f610/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3800056 (3.8 MB)  TX bytes:311632 (311.6 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.6.11  Bcast:192.168.6.255  Mask:255.255.255.0
          inet6 addr: fe80::864b:f5ff:fe76:e538/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49035 (49.0 KB)  TX bytes:36760 (36.7 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"KebWlan"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'KebWlan' [AC1]>   
          Bit Rate=9 Mb/s   Tx-Power=19 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=37/70  Signal level=-73 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10  Invalid misc:42   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.137.1   0.0.0.0         UG    0      0        0 eth0
192.168.6.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
192.168.137.0   0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search mshome.net lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       820     1  0 17:33 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [KebWlan] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           9 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *KebWlan:        Infra, <MAC 'KebWlan' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 51 WPA WPA2
    Xperia E_ccef:   Infra, <MAC 'Xperia E_ccef' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    jckorn:          Infra, <MAC 'jckorn' [AN3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Nikola1:         Infra, <MAC 'Nikola1' [AN4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Airlive:         Infra, <MAC 'Airlive' [AC2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Homeinternet:    Infra, <MAC 'Homeinternet' [AC3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WEP
    Mihic2:          Infra, <MAC 'Mihic2' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA2

  IPv4 Settings:
    Address:         192.168.6.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.6.1

    DNS:             192.168.6.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.137.81
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.137.1

    DNS:             192.168.137.1

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

[[/etc/NetworkManager/system-connections/KebWlan]] (600 root)
[connection] id=KebWlan | type=802-11-wireless
[802-11-wireless] ssid=KebWlan | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Zagreb (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'KebWlan' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"KebWlan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000076eee717d3
                    Extra: Last beacon: 88ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'Airlive' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Airlive"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000412b56232
                    Extra: Last beacon: 14052ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Homeinternet' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Homeinternet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002fc433c337
                    Extra: Last beacon: 14052ms ago
          Cell 04 - Address: <MAC 'Mihic2' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Mihic2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000026bdce1b187
                    Extra: Last beacon: 14732ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Xperia E_ccef' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Xperia E_ccef"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000316381980
                    Extra: Last beacon: 368ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[brcmsmac]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     21EC7461BC4D6521DBDCA51
depends:        bcma,mac80211,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[brcmutil]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     A0783053E3D218C552A3D06
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     315DCE1E2614AE1F38132D3
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/3.16.0-43-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     D52E980A55E0AC3C372382C
depends:        
intree:         Y
vermagic:       3.16.0-43-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        B9:68:43:D5:33:87:3C:28:09:11:67:45:21:94:7A:04:B9:74:2E:72
sig_hashalgo:   sha512

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
blacklist b43
blacklist ssb

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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.122719] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 17
[   13.756935] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   20.826794] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   20.826808] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   20.827442] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.117223] wlan0: authenticate with <MAC 'KebWlan' [AC1]>
[   23.119861] wlan0: send auth to <MAC 'KebWlan' [AC1]> (try 1/3)
[   23.121372] wlan0: authenticated
[   23.124173] wlan0: associate with <MAC 'KebWlan' [AC1]> (try 1/3)
[   23.126535] wlan0: RX AssocResp from <MAC 'KebWlan' [AC1]> (capab=0x411 status=0 aid=4)
[   23.127083] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   23.127088] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   23.127098] wlan0: associated
[   23.127109] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   23.214898] wlan0: deauthenticating from <MAC 'KebWlan' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   23.215952] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[   23.215961] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   23.216545] wlan0: authenticate with <MAC 'KebWlan' [AC1]>
[   23.216648] wlan0: send auth to <MAC 'KebWlan' [AC1]> (try 1/3)
[   23.218497] wlan0: authenticated
[   23.220167] wlan0: associate with <MAC 'KebWlan' [AC1]> (try 1/3)
[   23.224766] wlan0: RX AssocResp from <MAC 'KebWlan' [AC1]> (capab=0x411 status=0 aid=4)
[   23.225374] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   23.225379] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   23.225386] wlan0: associated
[   23.557039] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

########## wireless info END ############

[/HTML]

---

### Post by Vladlenin5000 on 2015-07-11
Quoting Dr. Chilli, there's a few thing you might try:

1. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not  TKIP. 
2. If your router is capable of N speeds, you may have  better connectivity with a channel width of 20 MHz in the 2.4 GHz band  instead of automatic 20/40 MHz, although it is likely to affect N  speeds. 
3. A fixed channel, either 1, 6 or 11,  rather than automatic channel selection, usually gives better results.
Also, be certain the router is  not set to use N speeds only; auto B, G and N is preferred.
After  making these changes, reboot the router.

---

### Post by ivan91 on 2015-07-11
> **Vladlenin5000 said:**
> Quoting Dr. Chilli, there's a few thing you might try:

1. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not  TKIP. 
2. If your router is capable of N speeds, you may have  better connectivity with a channel width of 20 MHz in the 2.4 GHz band  instead of automatic 20/40 MHz, although it is likely to affect N  speeds. 
3. A fixed channel, either 1, 6 or 11,  rather than automatic channel selection, usually gives better results.
Also, be certain the router is  not set to use N speeds only; auto B, G and N is preferred.
After  making these changes, reboot the router.


I dont have WPA2-AES option, only WPA, WPA2, and WPA-WPA2, I cant find anywhere in modem configuration anything about N speeds, and channel is fixed 1
EDIT #1: after checking details I can see now that my wpa-psk encryption is AES, and version is WPA2, so that should be the one right?
EDIT #2: on channel 1 I managed to load a webpage in 5 minutes twice, going to try channel 11 now, however what is this BGN thing?
EDIT #3: writing this edit from chanel 11 !!! Will mark this solved if it works for the next 24 hours.

---

### Post by Vladlenin5000 on 2015-07-11
WPA2-AES means WPA2 only with AES encryption method, Again, avoid WPA or any form of WPA/WPA2 mixed mode.
A, B, G, N and now also C (or AC) are WiFi standards that determine frequency and maximum speed. Your device: ```
Broadcom Corporation BCM4313 802.11[COLOR=#ff0000]bgn[/COLOR] Wireless Network Adapter
```

---

