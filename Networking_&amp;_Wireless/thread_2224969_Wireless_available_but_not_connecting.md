---
title: "Wireless available but not connecting"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by asearle on 2014-05-19
Hallo Everyone,

LUbuntu has revived a laptop that I thought was well past it.  Bravo to LUbuntu!

I have tried several Wireless adaptors (USB and PCMCIA) and each one of these is detected and displays available wireless connections.  But then I put in the password and the pop-up diappears but nothing happends.  No connection but also no error message.

Can anyone help me with this?  I've fished around in the network settings and have googled a lot but haven't found a solution.

Many thanks for any tips or links that you can send.

Yours,
Alan Searle,
Cologne, Germany

---

### Post by varunendra on 2014-05-21
Please follow the instructions in this post to provide us a detailed report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by asearle on 2014-06-01
Dear Varunedra,

Below is the output of the of the diagnostic script.

As you can see a number of Wireless networks are visible (including my own "chezalan") but, even though the passcode seems to be recognised (i.e. there is no error message) no connection is made.  I have double-checked the code and indeed this is the same wireless connection as I use with a number of other PCs.

Any help or diagnostic advice that you could give would be more welcome.

Regards and many thanks,
Alan


```
	======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

LatitudeC400 3.13.0-27-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Pentium(R) III Mobile CPU      1200MHz
Memory : 747 MB
Uptime : 13:46:27 up 13 min,  2 users,  load average: 0,30, 0,34, 0,31


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
	Subsystem: Dell Device [1028:00c8]
	Kernel driver in use: 3c59x
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)
	Subsystem: Dell Wireless 1470 Dual Band WLAN Mini-PCI Card [1028:0005]
	Kernel driver in use: b43-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 004 Device 003: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
1: phy2: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12627  1 rt2800lib
b43                   356470  0 
bcma                   42043  1 b43
mac80211              546013  4 b43,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  3 b43,mac80211,rt2x00lib
ssb                    51854  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | rt2800usb | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    chezalan:        Infra, <MAC C-03 chezalan>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Lohrbert:        Infra, <MAC C-02 Lohrbert>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    UPC0897950:      Infra, <MAC C-01 UPC0897950>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2
    WLAN-001A4F00497D: Infra, <MAC C-06 WLAN-001A4F00497D>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    ia99kQEf:        Infra, <MAC C-08 ia99kQEf>, Freq 2467 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Lohrberg-Netz:   Infra, <MAC C-NA Lohrberg-Netz 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    Mupfelhausen:    Infra, <MAC C-04 Mupfelhausen>, Freq 2422 MHz, Rate 54 Mb/s, Strength 32 WPA2
    FRITZ!Box Fon WLAN 7570 vDSL: Infra, <MAC C-07 FRITZ!Box Fon WLAN 7570 vDSL>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    EasyBox-6A1801_EXT: Infra, <MAC C-05 EasyBox-6A1801_EXT>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Brotwerk:        Infra, <MAC C-NA Brotwerk 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    FRITZ!Box Fon WLAN 7170: Infra, <MAC C-NA FRITZ!Box Fon WLAN 7170 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    TP-LINK_9DEE7A:  Infra, <MAC C-NA TP-LINK_9DEE7A 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 25 WPA2
    EasyBox-6A1801:  Infra, <MAC C-NA EasyBox-6A1801 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    HuettgesG:       Infra, <MAC C-NA HuettgesG 1>, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | 3c59x     | unavailable  | no      | 100 Mb/s  |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "de_DE.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 UPC0897950>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"UPC0897950"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002da59b985a
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Lohrbert>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Lohrbert"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000111f5560dc01
                    Extra: Last beacon: 1192ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 03 - Address: <MAC C-03 chezalan>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:on
                    ESSID:"chezalan"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000189d58884
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Mupfelhausen>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Mupfelhausen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005c96947af35
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 EasyBox-6A1801_EXT>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-6A1801_EXT"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002eb91fa11b4
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 WLAN-001A4F00497D>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"WLAN-001A4F00497D"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003defd6e24d
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 FRITZ!Box Fon WLAN 7570 vDSL>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 7570 vDSL"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000065cd09180
                    Extra: Last beacon: 428ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 ia99kQEf>
                    Channel:12
                    Frequency:2.467 GHz (Channel 12)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ia99kQEf"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000cf79351cd7
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2800usb]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211

[rt2800lib]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211

[crc_ccitt]
filename:       /lib/modules/3.13.0-27-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[b43]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

[mac80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B09A94F74DCA60EBD06A6B6
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-27-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10b7:0x9200 (3c59x)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x1814:0x0401 (rt61pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-27-generic root=UUID=2fc3265a-510b-4081-8ea5-51eef10f343a ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.462385] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.463458] audit: initializing netlink socket (disabled)
[    2.403177] ssb: Found chip with id 0x4318, rev 0x02 and package 0x02
[    2.403197] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x0D, vendor 0x4243)
[    2.403238] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x09, vendor 0x4243)
[    2.403247] ssb: Core 2 found: PCI (cc 0x804, rev 0x0C, vendor 0x4243)
[    2.403256] ssb: Core 3 found: PCMCIA (cc 0x80D, rev 0x07, vendor 0x4243)
[    2.444290] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    7.540515] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0b, buttons: 2/3
[   20.092670] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.176809] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   20.264532] b43-phy0: Found PHY: Analog 3, Type 2 (G), Revision 7
[   20.311163] b43 ssb0:0: Direct firmware load failed with error -2
[   20.311178] b43 ssb0:0: Falling back to user helper
[   22.251964] b43 ssb0:0: Direct firmware load failed with error -2
[   22.251977] b43 ssb0:0: Falling back to user helper
[   22.364214] b43 ssb0:0: Direct firmware load failed with error -2
[   22.364228] b43 ssb0:0: Falling back to user helper
[   22.366387] b43 ssb0:0: Direct firmware load failed with error -2
[   22.366398] b43 ssb0:0: Falling back to user helper
[   22.402674] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   22.402824] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   22.402954] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[  438.983323] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[  439.020978] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 5370 detected
[  439.167775] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  439.196834] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  439.544051] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  439.545995] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  666.063313] ieee80211 phy2: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[  666.100129] ieee80211 phy2: rt2x00_set_rf: Info - RF chipset 5370 detected
[  666.242892] ieee80211 phy2: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  666.243049] ieee80211 phy2: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  666.595705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  666.597897] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

	======== Done ========

```

---

### Post by varunendra on 2014-06-01
Here's your problem -
> **asearle said:**
> ```

[   22.402674] b43-phy0 ERROR: **Firmware file "b43/ucode5.fw" [COLOR="#FF0000"]not found[/COLOR]**
[   22.402824] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   22.402954] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

Solution - Please open a terminal (Ctrl-Alt-T), and while being connected to internet via cable or other means, run the following command in the terminal -
```
sudo apt-get install linux-firmware-nonfree
```
Reboot, and enjoy your wireless.

---

### Post by asearle on 2014-06-07
I installed network manager "nm" and then found that NM handled connection.  It works perfectly now.  Am very pleased.  Thanks for your tips.  Rgds, Alan

---

