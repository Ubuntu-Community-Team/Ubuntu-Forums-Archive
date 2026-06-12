---
title: "WNA3100 Wireless Adapter connection problems"
date: 2014-05-16
forum: Networking &amp; Wireless
---

### Post by nycpunk2012 on 2014-05-16
Hello, I know there have been many threads on this topic already, but it's killing me staying up day and night to try to get this fixed.

The problem is that my WNA3100 Wireless adapter is having trouble connecting. At first, not even this wireless options came up, so I installed ndiswrapper (since I was conveniently near a ethernet at the time) and installed the driver that came with the Windows XP installation disk. 

Here's the main problem: when I boot up my computer, the connection initially works after it attempts to connect to my network a few times. It'll work for a few then completely stop after I've been on for around 3 minutes or if I try to download/install something. At first, it'll still say I'm connected. After about a minute, it tells me I've been disconnected, then it attempts to connect to my network over and over and over while reminding me that I've been disconnected after each attempt.

I really hope someone can help me. I don't want to just give up because of this issue and run back to Windows 7.

I'm running on Ubuntu 14.04.

---

### Post by varunendra on 2014-05-16
Welcome to the forums nycpunk2012 !

Please follow the instructions in this post to provide us a detailed diagnostics report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)
Preferably run the script when the adapter fails to connect.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by nycpunk2012 on 2014-05-16
Thanks for the reply, varunendra. I was minutes away from giving up. Here's the results of the wireless script.

```


	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

YourAniki-MS-7752 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz
Memory : 7864 MB
Uptime : 13:44:17 up 3 min,  1 user,  load average: 0.54, 0.48, 0.23


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7752]
	Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 056a:00b8 Wacom Co., Ltd Intuos4 4x6
Bus 001 Device 004: ID 24f0:0137  
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 003 Device 003: ID 0781:5530 SanDisk Corp. Cruzer
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:117 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ndiswrapper           283985  0 
mxm_wmi                13021  0 
wmi                    19177  1 mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

ndiswrapper   (6): 
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o=============o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver      | State        | Default | Speed     | Support      | HW Addr   
================o=============o=============o==============o=========o===========o==============o===========
 eth0           | Wired       | r8169       | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-------------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | ndiswrapper | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    CH5NJ:           Infra, <MAC C-03 CH5NJ>, Freq 2437 MHz, Rate 54 Mb/s, Strength 84 WPA2
    GetYourOwnWifiChump: Infra, <MAC C-05 GetYourOwnWifiChump>, Freq 2437 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
    LUCKYLION:       Infra, <MAC C-04 LUCKYLION>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    Base Family Network: Infra, <MAC C-06 Base Family Network>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA2
    DIRECT-RC-VIZIOTV: Infra, <MAC C-NA DIRECT-RC-VIZIOTV 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2
    68G2S:           Infra, <MAC C-NA 68G2S 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2
    DKN11:           Infra, <MAC C-02 DKN11>, Freq 2412 MHz, Rate 54 Mb/s, Strength 54 WEP
    LUCKYLION-guest: Infra, <MAC C-09 LUCKYLION-guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80
    CableWiFi:       Infra, <MAC C-11 CableWiFi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 57
    xfinitywifi:     Infra, <MAC C-08 xfinitywifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
    Rhonda Washington: Infra, <MAC C-NA Rhonda Washington 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    optimumwifi:     Infra, <MAC C-10 optimumwifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59
    TWCWiFi:         Infra, <MAC C-07 TWCWiFi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55
    2QRMR:           Infra, <MAC C-01 2QRMR>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA WPA2
----------------+-------------+-------------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 2QRMR>
                    ESSID:"2QRMR"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:85/100  Signal level:-41 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DKN11>
                    ESSID:"DKN11"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: <MAC C-03 CH5NJ>
                    ESSID:"CH5NJ"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 LUCKYLION>
                    ESSID:"LUCKYLION"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 GetYourOwnWifiChump>
                    ESSID:"GetYourOwnWifiChump"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Base Family Network>
                    ESSID:"Base Family Network"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:62/100  Signal level:-56 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 TWCWiFi>
                    ESSID:"TWCWiFi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=102
                    Extra:atim=0
          Cell 08 - Address: <MAC C-08 xfinitywifi>
                    ESSID:"xfinitywifi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:45/100  Signal level:-67 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=102
                    Extra:atim=0
          Cell 09 - Address: <MAC C-09 LUCKYLION-guest>
                    ESSID:"LUCKYLION-guest"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:67/100  Signal level:-53 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 10 - Address: <MAC C-10 optimumwifi>
                    ESSID:"optimumwifi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=102
                    Extra:atim=0
          Cell 11 - Address: <MAC C-11 CableWiFi>
                    ESSID:"CableWiFi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=102
                    Extra:atim=0


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ndiswrapper]
filename:       /lib/modules/3.13.0-24-generic/misc/ndiswrapper.ko
version:        1.59
srcversion:     59359C0B181EE23FBCFCC27
depends:        
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
ndiswrapper

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic.efi.signed root=UUID=1ec7d68f-4a38-4a86-ba70-495730e5e310 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.379344] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.379527] audit: initializing netlink socket (disabled)
[    0.515558] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   11.775577] wmi: Mapper loaded
[   11.953202] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   11.953744] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   13.157347] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[   13.557715] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005590000, 16000, 4
[   13.557717] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005593e80, 16000, 5
[   13.557718] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005597d00, 16000, 5
[   13.557719] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000559bb80, 16000, 5
[   13.557721] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000559fa00, 16000, 5
[   13.557722] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055a3880, 16000, 5
[   13.557723] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055a7700, 16000, 5
[   13.557724] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055ab580, 16000, 5
[   13.557725] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055af400, 16000, 5
[   13.557726] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055b3280, 16000, 5
[   13.557728] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055b7100, 16000, 4
[   13.557729] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055baf80, 16000, 5
[   13.557730] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055bee00, 16000, 5
[   13.557732] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055c2c80, 16000, 5
[   13.557733] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055c6b00, 16000, 5
[   13.557734] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055ca980, 16000, 5
[   13.557735] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055ce800, 16000, 5
[   13.557736] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055d2680, 16000, 5
[   13.557738] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055d6500, 16000, 5
[   13.557739] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055da380, 16000, 5
[   13.557740] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055de200, 16000, 5
[   13.557741] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055e2080, 16000, 4
[   13.557742] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055e5f00, 16000, 5
[   13.557743] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055e9d80, 16000, 5
[   13.557744] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055edc00, 16000, 5
[   13.557745] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055f1a80, 16000, 5
[   13.557746] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055f5900, 16000, 5
[   13.557748] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055f9780, 16000, 5
[   13.557749] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900055fd600, 16000, 5
[   13.557750] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005601480, 16000, 5
[   13.557752] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005605300, 16000, 5
[   13.557753] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005609180, 16000, 4
[   13.557754] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000560d000, 16000, 4
[   13.557755] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005610e80, 16000, 5
[   13.557756] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005614d00, 16000, 5
[   13.557757] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005618b80, 16000, 5
[   13.557758] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000561ca00, 16000, 5
[   13.557759] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005620880, 16000, 5
[   13.557760] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005624700, 16000, 5
[   13.557761] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005628580, 16000, 5
[   13.557762] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000562c400, 16000, 5
[   13.557763] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005630280, 16000, 5
[   13.557764] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005634100, 16000, 4
[   13.557766] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005637f80, 16000, 5
[   13.557767] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000563be00, 16000, 5
[   13.557769] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000563fc80, 16000, 5
[   13.557770] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005643b00, 16000, 5
[   13.557771] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005647980, 16000, 5
[   13.557772] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000564b800, 16000, 5
[   13.557773] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000564f680, 16000, 5
[   13.571738] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[   13.851800] wlan0: ethernet device <MAC wlan0> using NDIS driver: bcmwlhigh5, version: 0x564442e, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[   13.857664] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   17.433323] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.249425] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.249568] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   43.489075] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

	======== Done ========


```

---

### Post by varunendra on 2014-05-17
Which one of the listed Access-Points is yours? The recommended encryption setting for the router/access-point is pure WPA2-PSK with AES (CCMP). No WPA/WPA2 mixed mode, no TKIP. So if your router/access-point is using the mixed mode or TKIP, please change it to the recommended WPA2 only with AES.

Also try fixing the channel to channel - 1 or 11 (if it is currently set to 'Auto' or some other channel). Usually they offer better signal quality. As per the report, channels 6 and 11 seem to be quite congested (many APs already using them), so I think channel 1 should be best for you, but also try channel 11 if 1 doesn't seem to help. Reboot the router/AP after saving any changes.

---

