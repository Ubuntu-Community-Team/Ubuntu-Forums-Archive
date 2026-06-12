---
title: "Lubuntu 12.04 Atheros AR9485 ath9k Driver - Wifi Not Found"
date: 2016-06-16
forum: Networking &amp; Wireless
---

### Post by eulerian.prime on 2016-06-16
Hi, 

I have a laptop [ ASUS Eee pc Flare Series 1025c ] dual-booting Lubuntu 12.04 and Windows. 

The wi-fi signal is not found while on Lubuntu but I have no problems connecting to wifi on Windows. 

The network adapter is [COLOR=#505050][FONT=sans-serif]Atheros AR9485 and the ath9k driver is installed.

I've been searching for threads that also had this problem but haven't been able to use their solutions to fix this. In particular, a fix I've seen a few times involving turning off encryption on the driver had no effect. I think the problem might have something to do with the network controller being "unmanaged" but I am not sure. 
[/FONT][/COLOR]
I'm including the experimental version of the wireless-script that Varunendra likes, but a link to a pastebin of the standard version is at the end of this post.

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


ATOM26 3.4.0-030400-generic i686,  


CPU    : Intel(R) Atom(TM) CPU N2600   @ 1.60GHz
Memory : 991 MB
Uptime : 23:23:59 up 1 day,  9:18,  1 user,  load average: 0.45, 0.55, 0.62




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6627]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
	Kernel driver in use: atl1c




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 002: ID 13d3:5711 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"FFJ64"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-03 FFJ64>   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:163   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface             Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN      no            no
2: phy0: Wireless LAN           no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


ath9k                 122031  0 
mac80211              455908  1 ath9k
ath9k_common           13781  1 ath9k
ath9k_hw              383904  2 ath9k,ath9k_common
ath                    19435  3 ath9k,ath9k_common,ath9k_hw
cfg80211              176297  3 ath9k,mac80211,ath
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
wmi                    18744  1 asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


ath9k         (3): blink=0 | btcoex_enable=0 | nohwcrypt=1
ath9k_hw      (1): force_new_ani=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
eeepc_wmi     (1): hotplug_wireless=N
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=============o========o===========o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=============o========o===========o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | ath9k  | unmanaged | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
----------------------------+-------------+--------+-----------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | atl1c  | connected | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.1.14
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------------+--------+-----------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC eth0>,


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto wlan0
iface wlan0 inet dhcp
	wpa-ssid FFJ64
	wpa-psk  RSTNTDJBL3DG2D2C


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 192.168.1.1
nameserver 127.0.0.1
search home




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.582/13.887/26.192/12.305 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


          Current Frequency=2.412 GHz (Channel 1)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 HP-Print-8D-ENVY 4500 series>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-8D-ENVY 4500 series"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000007622360aa9
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DIRECT-roku-0FE295>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-roku-0FE295"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000024766aefdf
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 FFJ64>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"FFJ64"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000170dad43d4
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000006a50e503a
                    Extra: Last beacon: 212ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 FiOS-27X79>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"FiOS-27X79"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000761fd22b8c
                    Extra: Last beacon: 1144ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 TG1672G42>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"TG1672G42"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000076185e20fc
                    Extra: Last beacon: 100ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 WIFIF32476>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"WIFIF32476"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007626ba818e
                    Extra: Last beacon: 808ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 NETGEAR24>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=17/70  Signal level=-93 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000610ef12d80
                    Extra: Last beacon: 2244ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 Eggie_FiOSj>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Eggie_FiOSj"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005402a4032b
                    Extra: Last beacon: 416ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/libpisock9.conf]
blacklist visor




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ath9k]
filename:       /lib/modules/3.4.0-030400-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     672258AD9591447C62B69DB
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)


[mac80211]
filename:       /lib/modules/3.4.0-030400-generic/kernel/net/mac80211/mac80211.ko
srcversion:     25B76B491D484B865D4D064
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[ath9k_common]
filename:       /lib/modules/3.4.0-030400-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     C96A18C18D58C8FEB170600
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.4.0-030400-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     B21FF7F11622BC8444BF774
depends:        ath
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)


[ath]
filename:       /lib/modules/3.4.0-030400-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     1FE1A669FB4BEE8587F9688
depends:        cfg80211


[cfg80211]
filename:       /lib/modules/3.4.0-030400-generic/kernel/net/wireless/cfg80211.ko
srcversion:     9B63E88DE347ACC7B732128
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[eeepc_wmi]
filename:       /lib/modules/3.4.0-030400-generic/kernel/drivers/platform/x86/eeepc-wmi.ko
srcversion:     4E8B82B5E9DA23D4B017B35
depends:        asus-wmi
parm:           hotplug_wireless:Enable hotplug for wireless device. If your laptop needs that, please report to acpi4asus-user@lists.sourceforge.net. (bool)


[asus_wmi]
filename:       /lib/modules/3.4.0-030400-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     B8E19F35C2ECEF03679A459
depends:        sparse-keymap,wmi


[wmi]
filename:       /lib/modules/3.4.0-030400-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     E6D2183F1F271B3545B1E5C
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modules]
loop




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/vmlinuz-3.4.0-030400-generic root=UUID=98c0ecec-100f-40ec-8ce6-3677ecd01cfb ro splash quiet vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.590900] audit: initializing netlink socket (disabled)
[   13.955325] wmi: Mapper loaded
[   14.844667] asus_wmi: ASUS WMI generic driver loaded
[   14.857193] asus_wmi: Initialization: 0x0
[   14.857292] asus_wmi: BIOS WMI version: 0.9
[   14.857486] asus_wmi: SFUN value: 0x0
[   14.859464] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input6
[   14.873266] asus_wmi: Backlight controlled by ACPI video driver
[   14.980166] ath: EEPROM regdomain: 0x60
[   14.980176] ath: EEPROM indicates we should expect a direct regpair map
[   14.980193] ath: Country alpha2 being used: 00
[   14.980200] ath: Regpair used: 0x60
[   15.064703] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.147828] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.148721] Registered led device: ath9k-phy0
[   15.251074] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.502902] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f00)
[   18.511478] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[32966.257958] asus_wmi: Unknown key 57 pressed
[32966.388438] asus_wmi: Unknown key 58 pressed
[104141.435992] asus_wmi: Unknown key 57 pressed
[104141.950828] asus_wmi: Unknown key 58 pressed
[104142.084652] asus_wmi: Unknown key 57 pressed
[105630.001927] ath9k: Driver unloaded
[105630.355522] type=1400 audit(1466048385.721:25): apparmor="DENIED" operation="capable" parent=4458 profile="/sbin/dhclient" pid=4459 comm="dhclient3" capability=12  capname="net_admin"
[105674.368610] ath: EEPROM regdomain: 0x60
[105674.368618] ath: EEPROM indicates we should expect a direct regpair map
[105674.368627] ath: Country alpha2 being used: 00
[105674.368632] ath: Regpair used: 0x60
[105674.373963] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[105674.383995] Registered led device: ath9k-phy0
[105674.388424] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[105674.503498] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[105675.584644] wlan0: authenticate with <MAC C-03 FFJ64>
[105675.592830] wlan0: send auth to <MAC C-03 FFJ64> (try 1/3)
[105675.595020] wlan0: authenticated
[105675.602257] wlan0: associate with <MAC C-03 FFJ64> (try 1/3)
[105675.605925] wlan0: RX AssocResp from <MAC C-03 FFJ64> (capab=0x431 status=0 aid=8)
[105675.605946] wlan0: associated
[105675.612465] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[105675.642660] ath: regdomain 0x8348 updated by CountryIE
[105675.642665] ath: EEPROM regdomain: 0x8348
[105675.642669] ath: EEPROM indicates we should expect a country code
[105675.642675] ath: doing EEPROM country->regdmn map search
[105675.642680] ath: country maps to regdmn code: 0x3a
[105675.642685] ath: Country alpha2 being used: US
[105675.642689] ath: Regpair used: 0x3a
[105685.986968] wlan0: no IPv6 routers present
[111233.080319] asus_wmi: Unknown key 58 pressed
[111233.455377] asus_wmi: Unknown key 57 pressed
[111242.619888] asus_wmi: Unknown key 58 pressed
[111246.895678] asus_wmi: Unknown key 57 pressed
[111262.402851] asus_wmi: Unknown key 58 pressed
[111269.539473] asus_wmi: Unknown key 57 pressed
[111272.781598] asus_wmi: Unknown key 58 pressed
[111274.995938] asus_wmi: Unknown key 57 pressed
[111410.624538] asus_wmi: Unknown key 58 pressed
[111410.793488] asus_wmi: Unknown key 57 pressed
[111411.018068] asus_wmi: Unknown key 58 pressed
[111412.355833] asus_wmi: Unknown key 57 pressed
[111428.292379] asus_wmi: Unknown key 58 pressed
[111432.737979] asus_wmi: Unknown key 57 pressed
[111435.391780] asus_wmi: Unknown key 58 pressed
[111436.817608] asus_wmi: Unknown key 57 pressed
[111452.490927] asus_wmi: Unknown key 58 pressed
[111456.041051] asus_wmi: Unknown key 57 pressed
[111458.102573] asus_wmi: Unknown key 58 pressed
[111459.201211] asus_wmi: Unknown key 57 pressed
[111465.431048] asus_wmi: Unknown key 58 pressed
[111465.707651] asus_wmi: Unknown key 57 pressed
[111481.175656] asus_wmi: Unknown key 58 pressed
[111481.369260] asus_wmi: Unknown key 57 pressed
[111481.606268] asus_wmi: Unknown key 58 pressed
[111481.762917] asus_wmi: Unknown key 57 pressed
[111855.959078] asus_wmi: Unknown key 58 pressed
[111856.205543] asus_wmi: Unknown key 57 pressed
[111871.199242] asus_wmi: Unknown key 58 pressed
[111871.361527] asus_wmi: Unknown key 57 pressed
[111876.148406] asus_wmi: Unknown key 58 pressed
[111878.781707] asus_wmi: Unknown key 57 pressed
[111880.993921] asus_wmi: Unknown key 58 pressed
[111881.156624] asus_wmi: Unknown key 57 pressed
[111884.851050] asus_wmi: Unknown key 58 pressed
[111924.497676] asus_wmi: Unknown key 57 pressed
[111927.411776] asus_wmi: Unknown key 58 pressed
[111930.175061] asus_wmi: Unknown key 57 pressed
[111931.819836] asus_wmi: Unknown key 58 pressed
[111933.449175] asus_wmi: Unknown key 57 pressed
[111939.305554] asus_wmi: Unknown key 58 pressed
[111943.397218] asus_wmi: Unknown key 57 pressed
[112039.320086] asus_wmi: Unknown key 58 pressed
[112062.529490] asus_wmi: Unknown key 57 pressed
[116182.799305] asus_wmi: Unknown key 58 pressed
[116188.228568] asus_wmi: Unknown key 57 pressed
[116189.988003] asus_wmi: Unknown key 58 pressed
[116399.168599] asus_wmi: Unknown key 57 pressed
[116402.658828] asus_wmi: Unknown key 58 pressed
[116484.269139] asus_wmi: Unknown key 57 pressed
[116484.377622] asus_wmi: Unknown key 58 pressed
[116500.111680] asus_wmi: Unknown key 57 pressed
[116500.338564] asus_wmi: Unknown key 58 pressed
[116537.447334] asus_wmi: Unknown key 57 pressed
[116537.540199] asus_wmi: Unknown key 58 pressed
[116601.103558] asus_wmi: Unknown key 57 pressed
[116603.478563] asus_wmi: Unknown key 58 pressed
[116604.751571] asus_wmi: Unknown key 57 pressed
[116608.000974] asus_wmi: Unknown key 58 pressed
[116840.872503] asus_wmi: Unknown key 57 pressed
[116845.036861] asus_wmi: Unknown key 58 pressed
[116847.530003] asus_wmi: Unknown key 57 pressed
[116856.649761] asus_wmi: Unknown key 58 pressed
[116856.899577] asus_wmi: Unknown key 57 pressed
[116860.864729] asus_wmi: Unknown key 58 pressed
[116940.191957] asus_wmi: Unknown key 57 pressed
[116944.992047] asus_wmi: Unknown key 58 pressed
[116945.836846] asus_wmi: Unknown key 57 pressed
[116948.755796] asus_wmi: Unknown key 58 pressed
[116949.096313] asus_wmi: Unknown key 57 pressed
[116951.559071] asus_wmi: Unknown key 58 pressed
[116951.950796] asus_wmi: Unknown key 57 pressed
[116953.179485] asus_wmi: Unknown key 58 pressed
[116953.319120] asus_wmi: Unknown key 57 pressed
[116955.238108] asus_wmi: Unknown key 58 pressed
[116962.037228] asus_wmi: Unknown key 57 pressed
[116964.281296] asus_wmi: Unknown key 58 pressed
[116970.895833] asus_wmi: Unknown key 57 pressed
[117033.574573] asus_wmi: Unknown key 58 pressed
[117037.447779] asus_wmi: Unknown key 57 pressed
[117037.657626] asus_wmi: Unknown key 58 pressed
[117041.278662] asus_wmi: Unknown key 57 pressed
[117048.476290] asus_wmi: Unknown key 58 pressed
[117052.040363] asus_wmi: Unknown key 57 pressed
[117052.179460] asus_wmi: Unknown key 58 pressed
[117052.329065] asus_wmi: Unknown key 57 pressed
[117061.735599] asus_wmi: Unknown key 58 pressed
[117063.369773] asus_wmi: Unknown key 57 pressed
[117074.480368] asus_wmi: Unknown key 58 pressed
[117074.954560] asus_wmi: Unknown key 57 pressed
[117079.959002] asus_wmi: Unknown key 58 pressed
[117080.321004] asus_wmi: Unknown key 57 pressed
[117080.487732] asus_wmi: Unknown key 58 pressed
[117080.639374] asus_wmi: Unknown key 57 pressed
[117082.943039] asus_wmi: Unknown key 58 pressed
[117098.786032] asus_wmi: Unknown key 57 pressed
[117099.310390] asus_wmi: Unknown key 58 pressed
[117105.583790] asus_wmi: Unknown key 57 pressed
[117124.437505] asus_wmi: Unknown key 58 pressed
[117143.036853] asus_wmi: Unknown key 57 pressed
[117143.127728] asus_wmi: Unknown key 58 pressed
[117166.443378] asus_wmi: Unknown key 57 pressed
[117166.535050] asus_wmi: Unknown key 58 pressed
[117166.809597] asus_wmi: Unknown key 57 pressed
[117167.941980] asus_wmi: Unknown key 58 pressed
[117170.037209] asus_wmi: Unknown key 57 pressed
[117171.044176] asus_wmi: Unknown key 58 pressed
[117192.677352] asus_wmi: Unknown key 57 pressed
[117192.752748] asus_wmi: Unknown key 58 pressed
[117209.244448] asus_wmi: Unknown key 57 pressed
[117210.108710] asus_wmi: Unknown key 58 pressed
[117211.460521] asus_wmi: Unknown key 57 pressed
[117211.819518] asus_wmi: Unknown key 58 pressed
[117214.522773] asus_wmi: Unknown key 57 pressed
[117217.250625] asus_wmi: Unknown key 58 pressed
[117231.707195] asus_wmi: Unknown key 57 pressed
[117233.130752] asus_wmi: Unknown key 58 pressed
[117233.964729] asus_wmi: Unknown key 57 pressed
[117241.932338] asus_wmi: Unknown key 58 pressed
[117242.611373] asus_wmi: Unknown key 57 pressed
[117244.213617] asus_wmi: Unknown key 58 pressed
[117246.337342] asus_wmi: Unknown key 57 pressed
[117246.811001] asus_wmi: Unknown key 58 pressed
[117249.047384] asus_wmi: Unknown key 57 pressed
[117250.212603] asus_wmi: Unknown key 58 pressed
[117261.842418] asus_wmi: Unknown key 57 pressed
[117263.624835] asus_wmi: Unknown key 58 pressed
[117303.497358] asus_wmi: Unknown key 57 pressed
[117311.172401] asus_wmi: Unknown key 58 pressed
[117325.822352] asus_wmi: Unknown key 57 pressed
[117328.655033] asus_wmi: Unknown key 58 pressed
[117334.079563] asus_wmi: Unknown key 57 pressed
[117334.846521] asus_wmi: Unknown key 58 pressed
[117334.992849] asus_wmi: Unknown key 57 pressed
[117336.347769] asus_wmi: Unknown key 58 pressed
[117340.940780] asus_wmi: Unknown key 57 pressed
[117345.054738] asus_wmi: Unknown key 58 pressed
[117350.396755] asus_wmi: Unknown key 57 pressed
[117350.701988] asus_wmi: Unknown key 58 pressed
[117350.827227] asus_wmi: Unknown key 57 pressed
[117351.829726] asus_wmi: Unknown key 58 pressed
[117355.635616] asus_wmi: Unknown key 57 pressed
[117361.162158] asus_wmi: Unknown key 58 pressed
[117367.961505] asus_wmi: Unknown key 57 pressed
[117369.131746] asus_wmi: Unknown key 58 pressed
[117371.781743] asus_wmi: Unknown key 57 pressed
[117372.255044] asus_wmi: Unknown key 58 pressed
[117376.172421] asus_wmi: Unknown key 57 pressed
[117422.667679] asus_wmi: Unknown key 58 pressed
[117423.220201] asus_wmi: Unknown key 57 pressed
[117425.363028] asus_wmi: Unknown key 58 pressed
[117428.053956] asus_wmi: Unknown key 57 pressed
[117428.459511] asus_wmi: Unknown key 58 pressed
[117443.012578] asus_wmi: Unknown key 57 pressed
[117443.161067] asus_wmi: Unknown key 58 pressed
[117459.227345] asus_wmi: Unknown key 57 pressed
[117459.298042] asus_wmi: Unknown key 58 pressed
[117459.673190] asus_wmi: Unknown key 57 pressed
[117470.082687] asus_wmi: Unknown key 58 pressed
[117476.074670] asus_wmi: Unknown key 57 pressed
[117476.178191] asus_wmi: Unknown key 58 pressed
[117484.732570] asus_wmi: Unknown key 57 pressed
[117484.804126] asus_wmi: Unknown key 58 pressed
[117486.932007] asus_wmi: Unknown key 57 pressed
[117487.180652] asus_wmi: Unknown key 58 pressed
[117492.199622] asus_wmi: Unknown key 57 pressed
[117494.848535] asus_wmi: Unknown key 58 pressed
[117497.863409] asus_wmi: Unknown key 57 pressed
[118044.428761] asus_wmi: Unknown key 58 pressed
[118045.368296] asus_wmi: Unknown key 57 pressed
[118048.177869] asus_wmi: Unknown key 58 pressed
[118048.321761] asus_wmi: Unknown key 57 pressed
[118058.498891] asus_wmi: Unknown key 58 pressed
[118061.906046] asus_wmi: Unknown key 57 pressed
[118062.463054] asus_wmi: Unknown key 58 pressed
[118067.365637] asus_wmi: Unknown key 57 pressed
[118141.449302] asus_wmi: Unknown key 58 pressed
[118141.944180] asus_wmi: Unknown key 57 pressed
[118144.046117] asus_wmi: Unknown key 58 pressed
[118158.294544] asus_wmi: Unknown key 57 pressed
[118166.249122] asus_wmi: Unknown key 58 pressed
[118168.690665] asus_wmi: Unknown key 57 pressed
[118179.665236] asus_wmi: Unknown key 58 pressed
[118186.859891] asus_wmi: Unknown key 57 pressed
[118345.010199] asus_wmi: Unknown key 58 pressed
[118354.026814] asus_wmi: Unknown key 57 pressed
[118432.217928] asus_wmi: Unknown key 58 pressed
[118433.410868] asus_wmi: Unknown key 57 pressed
[118439.523004] asus_wmi: Unknown key 58 pressed
[118441.317953] asus_wmi: Unknown key 57 pressed
[118442.416580] asus_wmi: Unknown key 58 pressed
[118445.359596] asus_wmi: Unknown key 57 pressed
[118455.881404] asus_wmi: Unknown key 58 pressed
[118477.019792] asus_wmi: Unknown key 57 pressed
[118479.755520] asus_wmi: Unknown key 58 pressed
[118479.880811] asus_wmi: Unknown key 57 pressed
[118479.974205] asus_wmi: Unknown key 58 pressed
[118480.206833] asus_wmi: Unknown key 57 pressed
[118480.398074] asus_wmi: Unknown key 58 pressed
[118480.717671] asus_wmi: Unknown key 57 pressed
[118480.917773] asus_wmi: Unknown key 58 pressed
[118481.046706] asus_wmi: Unknown key 57 pressed
[118481.273210] asus_wmi: Unknown key 58 pressed
[118482.359703] asus_wmi: Unknown key 57 pressed
[118819.731948] asus_wmi: Unknown key 58 pressed
[118820.103073] asus_wmi: Unknown key 57 pressed
[118824.664604] asus_wmi: Unknown key 58 pressed
[118825.295277] asus_wmi: Unknown key 57 pressed
[119140.331831] asus_wmi: Unknown key 58 pressed
[119142.317621] asus_wmi: Unknown key 57 pressed
[119152.093708] asus_wmi: Unknown key 58 pressed
[119153.332932] asus_wmi: Unknown key 57 pressed
[119153.849684] asus_wmi: Unknown key 58 pressed
[119153.965574] asus_wmi: Unknown key 57 pressed
[119154.109509] asus_wmi: Unknown key 58 pressed
[119154.383621] asus_wmi: Unknown key 57 pressed
[119157.936728] asus_wmi: Unknown key 58 pressed
[119158.084776] asus_wmi: Unknown key 57 pressed
[119188.945687] asus_wmi: Unknown key 58 pressed
[119258.704701] asus_wmi: Unknown key 57 pressed
[119264.024138] asus_wmi: Unknown key 58 pressed
[119264.133171] asus_wmi: Unknown key 57 pressed
[119268.765715] asus_wmi: Unknown key 57 pressed
[119268.856450] asus_wmi: Unknown key 57 pressed
[119269.120847] asus_wmi: Unknown key 58 pressed
[119269.732864] asus_wmi: Unknown key 57 pressed
[119273.657242] asus_wmi: Unknown key 58 pressed
[119275.956862] asus_wmi: Unknown key 57 pressed
[119278.475312] asus_wmi: Unknown key 58 pressed
[119279.540101] asus_wmi: Unknown key 57 pressed
[119290.704573] asus_wmi: Unknown key 58 pressed
[119291.129619] asus_wmi: Unknown key 57 pressed
[119296.207122] asus_wmi: Unknown key 58 pressed
[119298.039098] asus_wmi: Unknown key 57 pressed
[119608.587651] asus_wmi: Unknown key 58 pressed
[119610.350835] asus_wmi: Unknown key 57 pressed
[119610.489793] asus_wmi: Unknown key 58 pressed
[119611.052985] asus_wmi: Unknown key 57 pressed
[119614.711678] asus_wmi: Unknown key 58 pressed
[119614.966614] asus_wmi: Unknown key 57 pressed
[119615.158233] asus_wmi: Unknown key 58 pressed


	======== Done ========



```

Standard version of wireless-script:
[http://pastebin.ubuntu.com/17391606/](http://pastebin.ubuntu.com/17391606/)

---

### Post by eulerian.prime on 2016-06-17
Should I try upgrading to the newest version of Lubuntu?

---

### Post by howefield on 2016-06-17
> **eulerian.prime said:**
> Should I try upgrading to the newest version of Lubuntu?

It is usually a good idea to try with the Live media of a recent release, in this case 16.04

There are a few threads on this wireless card in the forums that you can search out if you haven't already.

---

