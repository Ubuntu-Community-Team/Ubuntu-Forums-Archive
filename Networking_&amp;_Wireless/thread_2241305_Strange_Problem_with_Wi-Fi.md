---
title: "Strange Problem with Wi-Fi"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by francois6 on 2014-08-25
Hi there.

I am a new Ubuntu (and Linux) user and I have tried to solve a problem with little success. I hope that others have had similiar problems and would be able to either assist me in sorting this out, or possibly direct me to a place that would be able to provide the information I need.

I have an external USB wifi device on my Desktop. Ubuntu picks it up and it recognizes all the wireless networks. From the list I can see a list of networks, including my own Router. I am even able to connect to the router with no problems. The problem comes in when I try to do anything online! It tells me I am connected, but I am not able to browse or download. 

But when I use my phone as a wifi hotspot, I am able to browse the internet and download fine, with no problems at all. 

Normally I would say the problem is lying with the router, or even my ISP. However I am able to use the internet on my laptop and other devices. When I reboot my desktop (with linux on) and boot into Windows 8, I am again able to use the internet when I connect to the router.

Quite frankly, I have no idea what I could be doing wrong, and would appreciate any and all help I can find here.

---

### Post by varunendra on 2014-08-25
Welcome to the forums francois6 !

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by francois6 on 2014-08-25
```


    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


francois-desktop 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
Memory : 3886 MB
Uptime : 19:31:44 up 54 min,  2 users,  load average: 0,92, 2,36, 2,80




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation 82567V-2 Gigabit Network Connection [8086:10ce]
    Subsystem: Intel Corporation Device [8086:0028]
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
--
05:04.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 8b)
    Subsystem: D-Link System Inc DFE-520TX Fast Ethernet PCI Adapter [1186:1405]
    Kernel driver in use: via-rhine




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1038:1320 Ideazon, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 010: ID 1058:1048 Western Digital Technologies, Inc. 
Bus 001 Device 011: ID 03f0:bb07 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"Francois's iPhone"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Francois's iPhone>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:47   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
1: phy1: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              630653  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
============================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [Francois's iPhone] | 802.11 WiFi | rt2800usb | connected   | yes     | 48 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    MartinG:         Infra, <MAC C-02 MartinG>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    AXIM:            Infra, <MAC C-NA AXIM 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    Pandora:         Infra, <MAC C-03 Pandora>, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA2
    *Francois's iPhone: Infra, <MAC C-01 Francois's iPhone>, Freq 2437 MHz, Rate 54 Mb/s, Strength 63 WPA2


    Address:         172.20.10.3
    Prefix:          28 (255.255.255.240)
    Gateway:         172.20.10.1
    DNS:             172.20.10.1
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0                       | Wired       | via-rhine | unavailable | no      |           |              | <MAC eth0>
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


AEBLVW               : ssid=AEBLVW | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Francois's iPhone    : ssid=Francois's iPhone | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Pandora              : ssid=Pandora | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    0      0        0 wlan0
172.20.10.0     0.0.0.0         255.255.255.240 U     9      0        0 wlan0


--- 172.20.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 29.237/29.298/29.360/0.181 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.029/0.031/0.034/0.006 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_ZA.UTF-8")
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
          Cell 01 - Address: <MAC C-01 Francois's iPhone>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Francois's iPhone"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004ecebc5c
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 MartinG>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"MartinG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004b303dd8f6
                    Extra: Last beacon: 288ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Pandora>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Pandora"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005015bd6ea
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rt2800usb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211


[rt2800lib]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt


[rt2x00lib]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     CC69EE39E7D673974A21C0A
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[crc_ccitt]
filename:       /lib/modules/3.13.0-34-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1106:0x3106 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=21affc21-b22f-4779-812b-2bb80b73095c ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    3.679607] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.679922] audit: initializing netlink socket (disabled)
[   14.374870] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   14.405472] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   15.515528] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.460281] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   16.543834] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   16.781778] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.782170] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.012213] wlan0: authenticate with <MAC C-03 Pandora>
[   18.035063] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[   18.036993] wlan0: authenticated
[   18.040077] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[   18.043755] wlan0: RX AssocResp from <MAC C-03 Pandora> (capab=0x31 status=0 aid=4)
[   18.050231] wlan0: associated
[   18.050252] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  585.917417] wlan0: deauthenticating from <MAC C-03 Pandora> by local choice (reason=3)
[  587.756392] wlan0: authenticate with <MAC C-01 Francois's iPhone>
[  587.784861] wlan0: send auth to <MAC C-01 Francois's iPhone> (try 1/3)
[  587.787462] wlan0: authenticated
[  587.787603] wlan0: AP has invalid WMM params (AIFSN=0 for ACI 0), disabling WMM
[  587.788329] wlan0: associate with <MAC C-01 Francois's iPhone> (try 1/3)
[  587.790178] wlan0: RX AssocResp from <MAC C-01 Francois's iPhone> (capab=0x411 status=0 aid=1)
[  587.797070] wlan0: associated
[  779.689265] wlan0: deauthenticating from <MAC C-01 Francois's iPhone> by local choice (reason=3)
[  780.608742] wlan0: authenticate with <MAC C-03 Pandora>
[  780.640888] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[  780.645969] wlan0: authenticated
[  780.648071] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[  780.652197] wlan0: RX AssocResp from <MAC C-03 Pandora> (capab=0x31 status=0 aid=4)
[  780.658692] wlan0: associated
[  911.520527] wlan0: deauthenticating from <MAC C-03 Pandora> by local choice (reason=3)
[  916.742041] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  919.020491] wlan0: authenticate with <MAC C-01 Francois's iPhone>
[  919.052889] wlan0: send auth to <MAC C-01 Francois's iPhone> (try 1/3)
[  919.073082] wlan0: send auth to <MAC C-01 Francois's iPhone> (try 2/3)
[  919.115969] wlan0: send auth to <MAC C-01 Francois's iPhone> (try 3/3)
[  919.149845] wlan0: authentication with <MAC C-01 Francois's iPhone> timed out
[ 1193.660056] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0xffffffff]
[ 1685.338677] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[ 1685.366923] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 5370 detected
[ 1685.438802] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[ 1685.495113] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[ 1685.729852] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1685.730190] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1688.028228] wlan0: authenticate with <MAC C-03 Pandora>
[ 1688.058865] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[ 1688.060824] wlan0: authenticated
[ 1688.064040] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[ 1688.067959] wlan0: RX AssocResp from <MAC C-03 Pandora> (capab=0x31 status=0 aid=5)
[ 1688.074436] wlan0: associated
[ 1688.074459] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1688.082913] wlan0: deauthenticating from <MAC C-03 Pandora> by local choice (reason=2)
[ 1688.125764] wlan0: authenticate with <MAC C-03 Pandora>
[ 1688.144880] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[ 1688.146836] wlan0: authenticated
[ 1688.148033] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[ 1688.151698] wlan0: RX AssocResp from <MAC C-03 Pandora> (capab=0x31 status=0 aid=5)
[ 1688.164195] wlan0: associated
[ 1974.416968] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1974.416989] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1974.416992] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1974.598348] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2039.207016] wlan0: deauthenticating from <MAC C-03 Pandora> by local choice (reason=3)
[ 2040.612553] wlan0: authenticate with <MAC C-01 Francois's iPhone>
[ 2040.640925] wlan0: send auth to <MAC C-01 Francois's iPhone> (try 1/3)
[ 2040.642138] wlan0: authenticated
[ 2040.642270] wlan0: AP has invalid WMM params (AIFSN=0 for ACI 0), disabling WMM
[ 2040.644067] wlan0: associate with <MAC C-01 Francois's iPhone> (try 1/3)
[ 2040.646490] wlan0: RX AssocResp from <MAC C-01 Francois's iPhone> (capab=0x411 status=0 aid=1)
[ 2040.653490] wlan0: associated
[ 2596.684144] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 2596.684157] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 2596.684160] ieee80211 phy1: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[ 2597.359280] ieee80211 phy1: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 3206.777384] wlan0: deauthenticating from <MAC C-01 Francois's iPhone> by local choice (reason=3)
[ 3209.899619] wlan0: authenticate with <MAC C-03 Pandora>
[ 3209.922553] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[ 3209.924503] wlan0: authenticated
[ 3209.928081] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[ 3209.931758] wlan0: RX AssocResp from <MAC C-03 Pandora> (capab=0x31 status=0 aid=4)
[ 3209.938244] wlan0: associated
[ 3277.822844] wlan0: deauthenticating from <MAC C-03 Pandora> by local choice (reason=3)
[ 3278.664100] wlan0: authenticate with <MAC C-01 Francois's iPhone>
[ 3278.692913] wlan0: send auth to <MAC C-01 Francois's iPhone> (try 1/3)
[ 3278.694012] wlan0: authenticated
[ 3278.694117] wlan0: AP has invalid WMM params (AIFSN=0 for ACI 0), disabling WMM
[ 3278.696076] wlan0: associate with <MAC C-01 Francois's iPhone> (try 1/3)
[ 3278.697870] wlan0: RX AssocResp from <MAC C-01 Francois's iPhone> (capab=0x411 status=0 aid=1)
[ 3278.704989] wlan0: associated


    ======== Done ========

```

---

### Post by francois6 on 2014-08-25
I did as you asked. Just one thing to keep in mind is that I had to connect to the internet using my phone as a wireless hotspot (using the same device that I use to connect to my router)

---

### Post by Malcolm_Gaissert on 2014-08-25
Had the same problem. Win 8.1 worked with the USB adapter. But would not work with the Ubuntu distro 13.10. Then it finally dawned on me. The problem was that Ubuntu was actually blocking the original WiFi device that was still in the laptop and therefore not allowing the USB device to function.

What to do? I turned off the computer turned it over, found the door that the internal wifi device was behind and carefully removed it. Remove the screws first then when the device lifts up gently remove the antenna wires. If at some time you wish to replace the device with a new one make note of where the wires were attached.
 
Powered up the laptop and I have had WiFi since the moment I filled in the correct info. (I have a D-Link DWA140 attached to its short USB cord.)

Good luck

---

### Post by francois6 on 2014-08-25
> **Malcolm_Gaissert said:**
> Had the same problem. Win 8.1 worked with the USB adapter. But would not work with the Ubuntu distro 13.10. Then it finally dawned on me. The problem was that Ubuntu was actually blocking the original WiFi device that was still in the laptop and therefore not allowing the USB device to function.

What to do? I turned off the computer turned it over, found the door that the internal wifi device was behind and carefully removed it. Remove the screws first then when the device lifts up gently remove the antenna wires. If at some time you wish to replace the device with a new one make note of where the wires were attached.
 
Powered up the laptop and I have had WiFi since the moment I filled in the correct info. (I have a D-Link DWA140 attached to its short USB cord.)

Good luck

Hey! Thanks for the reply! What you explained actually makes sense, though I never thought of it myself. I will try to disable my onboard wireless device (broken which is why I have a USB thingy). Why would the device work connecting to my phone though?

---

### Post by varunendra on 2014-08-25
> **francois6 said:**
> I will try to disable my onboard wireless device (broken which is why I have a USB thingy). Why would the device work connecting to my phone though?

Because nothing onboard is blocking your wifi. You don't even have an onboard wifi device. Why the regular AP is not working could be due to many reasons. For now, please just try -
```
sudo iwconfig wlan0 power off
```
Then try to reconnect to the AP. Can you browse now? If yes, reboot and see if the "Power Management" remains off in the output of "iwconfig" command. It probably won't, in which case, we can do a few thing to keep it permanently off (the Power Management is supposed to save power when running on battery, I don't think your Desktop runs on battery ;)).

If it doesn't seem to help, please run the script again with -
```
bash ./wireless_script
```
..when you are connected using the USB adapter, not your iPhone. Since the script has already been downloaded, you can run it offline now. Post back the fresh report with "...power off" applied this time.

---

### Post by francois6 on 2014-08-26
```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


francois-desktop 3.13.0-34-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM)2 Quad CPU    Q9400  @ 2.66GHz
Memory : 3886 MB
Uptime : 16:16:28 up 17 min,  3 users,  load average: 1,15, 1,32, 1,22




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


00:19.0 Ethernet controller [0200]: Intel Corporation 82567V-2 Gigabit Network Connection [8086:10ce]
    Subsystem: Intel Corporation Device [8086:0028]
00:1a.0 USB controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
--
05:04.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 8b)
    Subsystem: D-Link System Inc DFE-520TX Fast Ethernet PCI Adapter [1186:1405]
    Kernel driver in use: via-rhine




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 1038:1320 Ideazon, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 006: ID 1058:1048 Western Digital Technologies, Inc. 
Bus 001 Device 009: ID 03f0:bb07 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              630653  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 eth0           | Wired       | via-rhine | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | rt2800usb | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    AXIM:            Infra, <MAC C-02 AXIM>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    MartinG:         Infra, <MAC C-01 MartinG>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    Pandora:         Infra, <MAC C-03 Pandora>, Freq 2457 MHz, Rate 54 Mb/s, Strength 41 WPA2
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


AEBLVW               : ssid=AEBLVW | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Francois's iPhone    : ssid=Francois's iPhone | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Pandora              : ssid=Pandora | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_ZA.UTF-8")
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
          Cell 01 - Address: <MAC C-01 MartinG>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MartinG"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005c951b5d80
                    Extra: Last beacon: 1176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 AXIM>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"AXIM"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ff24a89ec
                    Extra: Last beacon: 1176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Pandora>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Pandora"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000166411b4ba
                    Extra: Last beacon: 1176ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rt2800usb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)


[rt2x00usb]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211


[rt2800lib]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt


[rt2x00lib]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     CC69EE39E7D673974A21C0A
depends:        mac80211,cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-34-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[crc_ccitt]
filename:       /lib/modules/3.13.0-34-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1106:0x3106 (via-rhine)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-34-generic root=UUID=21affc21-b22f-4779-812b-2bb80b73095c ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    3.679599] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.679915] audit: initializing netlink socket (disabled)
[   15.482739] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   15.511862] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   16.633124] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.536605] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   17.650168] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   17.885904] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.886274] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.252333] wlan0: authenticate with <MAC C-03 Pandora>
[   20.286940] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[   20.288879] wlan0: authenticated
[   20.292085] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[   20.296772] wlan0: RX AssocResp from <MAC C-03 Pandora> (capab=0x31 status=0 aid=2)
[   20.303252] wlan0: associated
[   20.303281] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.327605] wlan0: deauthenticating from <MAC C-03 Pandora> by local choice (reason=2)
[   20.365813] wlan0: authenticate with <MAC C-03 Pandora>
[   20.384925] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[   20.386762] wlan0: authenticated
[   20.388071] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[   20.393530] wlan0: RX AssocResp from <MAC C-03 Pandora> (capab=0x31 status=0 aid=2)
[   20.400102] wlan0: associated
[  118.940759] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  118.940781] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  118.940784] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  119.038351] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  119.288974] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  119.288995] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  119.288998] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  120.280999] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  121.041097] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  121.041120] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  121.041123] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  121.042355] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  122.012613] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  122.012634] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  122.012637] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  122.027734] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  122.229001] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  122.230071] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  122.230076] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  123.091189] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  124.261116] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  124.261151] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  124.261156] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  124.358326] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  126.049096] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  126.049116] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  126.049119] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  126.973010] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  127.072452] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  127.072473] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  127.072476] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  127.251499] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.404069] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  127.404093] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  127.404098] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  127.404113] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  127.404117] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  127.404125] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  127.404130] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  127.404135] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  127.404140] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  127.502390] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.502512] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.502631] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.502734] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.502857] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.502983] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.503234] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  127.848072] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  127.848098] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  127.848101] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  128.093300] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  128.272973] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  128.273013] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  128.273018] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  128.370445] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  129.036586] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  129.036609] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  129.036612] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  129.052339] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  129.052364] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  129.052367] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  129.052376] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  129.052380] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  129.057083] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  129.057207] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  129.057327] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  129.057474] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  129.532731] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  129.532752] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  129.532754] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  129.547968] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  130.313075] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  130.313098] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  130.313101] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  130.440894] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  146.056708] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  146.056731] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  146.056734] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  146.062336] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  176.508867] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  176.508889] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  176.508892] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  176.511355] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  178.904041] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  178.904064] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  178.904067] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  178.919781] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  179.120923] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  179.120946] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  179.120949] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  179.135672] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  275.921003] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  275.921024] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  275.921027] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  276.137020] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  276.137039] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  276.137043] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  276.817464] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  276.817565] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  277.032832] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  277.032917] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  277.032920] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  277.047727] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  277.148147] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  277.148171] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  277.148175] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  277.148196] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  277.348675] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  277.348698] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  277.348701] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  277.805458] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  277.805580] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  278.213131] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  279.732233] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  279.732253] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  279.732255] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  280.057382] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  280.256716] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  280.256736] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  280.256739] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  280.956121] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  281.176251] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  281.176272] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  281.176276] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  281.941383] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  283.096055] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  283.096060] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  283.945012] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  284.044573] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  284.044600] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  284.044604] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  284.044627] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  284.044630] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  284.044634] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  284.044640] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  284.142288] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  284.142401] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  284.142517] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  284.142643] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  284.142773] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  284.244476] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  284.244493] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  284.244495] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  285.241240] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  286.440119] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  286.440146] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  286.440149] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  286.793473] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  286.892046] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  286.892051] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  286.916646] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  286.916662] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  286.916664] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  287.414397] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  287.952994] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  288.676385] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  288.676403] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  288.676407] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  288.774607] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  288.876771] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  288.876792] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  288.876795] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  289.725123] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  292.056310] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  292.056326] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  292.056329] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  292.072050] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  292.072071] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  292.072074] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  292.124031] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  292.124051] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  292.124053] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  292.125167] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  292.136519] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  292.136541] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  292.136544] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  292.136556] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  292.168032] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  292.168063] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  292.168067] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  292.177129] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  292.177165] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  292.177168] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  292.199624] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  292.200234] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  292.200366] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  292.200490] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  292.200619] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  292.200734] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  294.504091] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  294.504117] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  294.504122] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  294.511604] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  315.952985] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  315.953007] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  315.953009] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  315.967614] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  317.800816] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  317.800840] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  317.800842] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  317.957744] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  318.773078] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  318.773105] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  318.773108] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  318.860294] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  392.440725] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  392.440746] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  392.440750] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  392.713123] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  405.000082] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  405.000099] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  405.000101] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  405.044951] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  405.144133] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  405.144154] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  405.144157] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  405.345221] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  405.345233] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  405.345236] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  405.792941] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  406.740960] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  445.916490] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  445.916512] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  445.916515] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  446.047806] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  472.996320] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  472.996343] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  472.996346] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  473.013070] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  473.112147] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  473.112176] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  473.112180] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  473.312043] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  473.312060] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  473.312064] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  473.792931] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  474.220980] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  475.072289] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  475.072311] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  475.072314] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  475.975965] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  477.252068] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  477.252090] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  477.252093] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  477.362883] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  478.205096] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  478.205112] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  478.205115] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  478.441221] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  479.040801] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  479.040821] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  479.040824] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 0
[  479.248950] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  479.449082] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  479.449098] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  479.449100] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  479.764941] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  480.972573] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  480.972592] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  480.972595] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  480.972613] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  481.097416] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  481.097528] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  492.225070] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  492.225089] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  492.225092] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  492.322277] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  502.880240] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  502.880259] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  502.880261] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  503.092025] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  503.092059] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  503.092065] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  503.107766] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  503.107889] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  518.072269] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  518.072308] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  518.072312] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  518.170368] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  519.360998] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  519.361019] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  519.361022] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  519.492808] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  519.492826] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  519.492829] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  519.548045] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  519.548062] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  519.548066] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  519.588891] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  519.588915] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  519.588919] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  519.604644] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  519.604676] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  519.604680] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  519.652361] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  519.652605] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  519.652875] ieee80211 phy0: rt2800usb_txdone: Warning - Data pending for entry 2 in queue 2
[  519.653354] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  519.656857] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  525.116876] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  525.116892] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  525.116894] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  525.132000] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  525.804402] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  525.804423] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  525.804425] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  525.820421] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  526.896362] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  526.896376] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  526.896379] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  526.994467] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  527.096257] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  527.096270] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  527.096275] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  527.111758] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  527.212574] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  527.212589] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  527.212593] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  527.236431] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  527.236449] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  527.236452] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  527.292658] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  527.292683] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  527.292689] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  527.492558] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  527.492577] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  527.492580] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  527.781052] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  527.781176] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  527.781297] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  527.928615] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  527.928635] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  527.928638] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  528.078439] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  528.078523] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  528.632739] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  528.632759] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  528.632762] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  528.985591] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  530.008557] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  530.008578] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  530.008584] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  530.023680] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  530.224191] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  530.224211] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  530.224214] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  530.513340] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  531.460477] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  531.460502] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  531.460505] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  531.558285] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  531.660479] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  531.660496] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  531.660500] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  532.012941] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  536.928969] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  536.928988] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  536.928991] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  537.026427] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  537.448713] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  537.448737] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  537.448740] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  537.466830] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  541.012804] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  541.012827] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  541.012832] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  541.413492] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  543.712705] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  543.712727] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  543.712733] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  545.720328] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  549.412122] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  549.412135] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  549.412138] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  549.510301] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  550.017042] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  550.017063] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  550.017066] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[  550.605016] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  550.804655] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  550.804675] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  550.804681] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  552.053033] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  552.252554] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  552.252568] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  552.252573] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  552.936361] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  553.892861] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  553.892881] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  553.892887] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  554.192962] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  554.292038] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  554.292054] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  554.292060] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  554.390302] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  554.492939] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  554.492967] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  554.492970] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  554.589522] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  557.096876] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  557.096898] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  557.096904] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  557.593017] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  559.880360] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  559.880380] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  559.880383] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 0
[  560.011675] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  562.204947] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  562.204967] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  562.204970] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 0
[  562.971349] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  569.764299] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  569.764318] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  569.764321] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  569.797418] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  569.960201] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  569.960222] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  569.960229] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  569.960244] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  569.965828] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  570.016545] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  570.016563] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  570.016569] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  570.050284] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  570.051282] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  605.972580] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  605.972624] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  605.972631] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  605.980701] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  606.220434] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  606.220454] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  606.220457] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  606.228303] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  606.228320] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  606.228323] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  606.268796] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  606.268814] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  606.268817] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[  606.268824] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  606.278909] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  606.293423] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  606.293532] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  606.293654] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  629.408712] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  629.408732] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  629.408735] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 0
[  629.509051] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  632.704065] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  632.704102] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  632.704106] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  632.832384] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  632.960196] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  632.960208] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  632.960212] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  633.193202] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  724.293014] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  724.293031] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  724.293036] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  724.390340] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  781.904319] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  781.904339] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  781.904342] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  782.817143] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  785.020392] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  785.020413] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  785.020419] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  785.171082] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  787.572615] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  787.572637] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  787.572640] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 0
[  789.217074] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  790.009023] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  790.009047] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  790.009052] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  790.052872] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  790.052889] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  790.052892] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  790.072519] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  790.072633] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  790.468541] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  790.468561] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  790.468567] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[  790.626339] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  790.988773] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  790.988792] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  790.988795] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[  791.108595] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  791.108613] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  791.108618] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[  791.108634] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[  791.108638] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[  791.213175] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  791.213294] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  791.213440] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  791.213562] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  791.308113] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  791.308130] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  791.308133] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  791.448952] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  792.772870] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  792.772890] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  792.772896] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  793.004117] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  793.004142] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  793.004147] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 0
[  793.794388] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  793.794497] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  795.156980] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  795.157001] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  795.157004] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 0
[  796.660985] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  796.760104] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  796.760121] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  796.760127] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[  796.790735] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  797.880603] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  797.880619] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  797.880626] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  798.049370] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  799.160728] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  799.160746] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  799.160752] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  799.313006] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  799.892356] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  799.892375] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  799.892381] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  800.016110] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  801.256849] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  801.256868] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  801.256871] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 0
[  801.580980] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  801.893102] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  801.893118] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  801.893125] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  802.793509] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  807.117099] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  807.117121] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  807.117124] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  807.117140] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  807.214503] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  807.214626] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  807.572876] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  807.572909] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  807.572914] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  807.613140] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  812.244482] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  812.244501] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  812.244504] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  812.342354] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  812.704854] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  812.704867] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  812.704871] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  812.816999] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  816.168987] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  816.169015] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  816.169019] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 0
[  816.170116] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  825.880858] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  825.880881] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  825.880885] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  825.990755] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  827.880234] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  827.880255] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  827.880258] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 0
[  828.688989] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  854.916353] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  854.916376] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  854.916380] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 0
[  855.264994] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  861.052870] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  861.052990] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  861.052995] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 0
[  861.067868] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  861.324614] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  861.324638] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  861.324642] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  861.540999] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  864.108112] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  864.108139] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  864.108143] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[  864.206375] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  864.532741] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  864.532763] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  864.532766] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[  864.630373] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  865.180606] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  865.180630] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  865.180634] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[  865.274373] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  871.504748] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  871.504769] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  871.504772] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 0
[  872.021004] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  881.477111] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  881.477128] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  881.477131] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  881.574505] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  882.565119] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  882.565155] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  882.565161] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  882.591753] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  885.468621] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  885.468642] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  885.468645] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  885.617750] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  894.909119] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  894.909141] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  894.909145] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 0
[  896.817002] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  900.232733] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  900.232755] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  900.232758] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 0
[  900.848952] wlan0: deauthenticating from <MAC C-03 Pandora> by local choice (reason=3)
[  900.850381] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[  905.125050] wlan0: authenticate with <MAC C-03 Pandora>
[  905.152952] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[  905.256042] wlan0: send auth to <MAC C-03 Pandora> (try 2/3)
[  905.360051] wlan0: send auth to <MAC C-03 Pandora> (try 3/3)
[  905.464049] wlan0: authentication with <MAC C-03 Pandora> timed out
[  905.524153] wlan0: authenticate with <MAC C-03 Pandora>
[  905.549214] wlan0: send auth to <MAC C-03 Pandora> (try 1/3)
[  905.652070] wlan0: send auth to <MAC C-03 Pandora> (try 2/3)
[  905.756060] wlan0: send auth to <MAC C-03 Pandora> (try 3/3)
[  905.758013] wlan0: authenticated
[  905.760058] wlan0: associate with <MAC C-03 Pandora> (try 1/3)
[  905.864061] wlan0: associate with <MAC C-03 Pandora> (try 2/3)
[  905.968038] wlan0: associate with <MAC C-03 Pandora> (try 3/3)
[  906.072065] wlan0: association with <MAC C-03 Pandora> timed out


    ======== Done ========

```

It has become even stranger... 

Since an hour ago I sometimes randomly can connect to the internet and browse normally (though quite slow). Then when I disconnect I am unable to connect again. Rebooting and reconnecting doesnt work either, yet 5 mins ago I was again able to connect to the internet.

This is not a network issue with my Router or ISP, as I have been connected with 2 laptops and a few mobile devices during the whole time Linux wasnt able to connect.

---

### Post by varunendra on 2014-08-26
Power Management is still "on" -
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:**[COLOR="#FF0000"]on[/COLOR]**
```
Did you turn it off using the "sudo iwconfig wlan0 power off" command? Didn't it help connecting?

**PS:**
And who said anything about your Router or ISP?

---

