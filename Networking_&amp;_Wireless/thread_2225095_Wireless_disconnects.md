---
title: "Wireless disconnects"
date: 2014-05-19
forum: Networking &amp; Wireless
---

### Post by papa.jinzu on 2014-05-19
Hello,

I have 14.04 and the wireless adapter keeps losing connection. The wifi adapter is Netgear WN111v2. It loses connection few times every 10 minutes while plugged into USB slots. Sometimes it will not reconnect and I have to reboot computer. How to fix?

---

### Post by varunendra on 2014-05-21
When it is connected, please follow the instructions in this post to generate a detailed report of the wireless setup : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222) and post back the report file or its contents here.

If posting the contents, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by papa.jinzu on 2014-06-04
I copy and pasted the lines into a terminal. The text file is empty.

---

### Post by varunendra on 2014-06-04
Please try that again, and copy-paste the entire output of the terminal here. That would let me see which steps completed successfully. If you are sure you ran the script correctly, please also show me the output of (from the same terminal) -
```
ls -lh wireless*
```

---

### Post by papa.jinzu on 2014-06-05
got it to run successfully this time terminal output:





```
    ########################################################################


    DONE! All results saved in -


                 File Name:     "wireless-info.tar.gz" 
                 Directory:     "/home/justin"


    Please upload the above file or its contents where you are seeking help.


    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------


    ########################################################################





```




```
	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


justin-U56E 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
Memory : 5872 MB
Uptime : 12:44:26 up 18:59,  3 users,  load average: 0.64, 0.89, 1.00




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 1a)
	Subsystem: Intel Corporation Device [8086:0000]
03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 003: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9170+AR9101]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"bluesky2"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC C-01 bluesky2>   
          Bit Rate=65 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:35  Invalid misc:109   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: hci0: Bluetooth                no            no
6: phy3: Wireless LAN             no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


carl9170               91161  0 
ath                    28698  1 carl9170
mac80211              626489  1 carl9170
cfg80211              484040  3 ath,mac80211,carl9170
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
carl9170      (2): noht=0 | nohwcrypt=N
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
===================o=============o==========o==============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver   | State        | Default | Speed     | Support      | HW Addr   
===================o=============o==========o==============o=========o===========o==============o===========
 wlan0  [bluesky2] | 802.11 WiFi | carl9170 | connected    | yes     | 65 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>


    NETGEAR33:       Infra, <MAC C-05 NETGEAR33>, Freq 2437 MHz, Rate 54 Mb/s, Strength 85 WPA2
    Luis70:          Infra, <MAC C-04 Luis70>, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2
    andy1978:        Infra, <MAC C-07 andy1978>, Freq 2437 MHz, Rate 54 Mb/s, Strength 64 WPA2
    ATT6511:         Infra, <MAC C-03 ATT6511>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA2
    NETGEAR33:       Infra, <MAC C-02 NETGEAR33>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    DIRECT-OP-VIZIOTV: Infra, <MAC C-11 DIRECT-OP-VIZIOTV>, Freq 2447 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Sanay 2.5:       Infra, <MAC C-06 Sanay 2.5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    LowKey1760:      Infra, <MAC C-09 LowKey1760>, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    Kaveti home:     Infra, <MAC C-NA Kaveti home 1>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA2
    NETGEAR53:       Infra, <MAC C-NA NETGEAR53 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA2
    *bluesky2:       Infra, <MAC C-01 bluesky2>, Freq 2422 MHz, Rate 54 Mb/s, Strength 81 WPA2
    Pretty Fly For a WIFI: Infra, <MAC C-08 Pretty Fly For a WIFI>, Freq 2437 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    Starfleet Headquarters: Infra, <MAC C-10 Starfleet Headquarters>, Freq 2447 MHz, Rate 54 Mb/s, Strength 30 WPA2
    Kaveti-Home:     Infra, <MAC C-NA Kaveti-Home 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    HOME-B912:       Infra, <MAC C-NA HOME-B912 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    HOME-B5BF:       Infra, <MAC C-NA HOME-B5BF 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    HawksGA:         Infra, <MAC C-NA HawksGA 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    HOME-68F9:       Infra, <MAC C-NA HOME-68F9 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    knahnetwork:     Infra, <MAC C-NA knahnetwork 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    dazzy:           Infra, <MAC C-NA dazzy 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Larry's Wi-Fi airprt: Infra, <MAC C-NA Larry's Wi-Fi airprt 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Pretty Fly For a WIFI-guest: Infra, <MAC C-NA Pretty Fly For a WIFI-guest 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25


    Address:         192.168.1.133
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-------------------+-------------+----------+--------------+---------+-----------+--------------+-----------
 eth0              | Wired       | atl1c    | unavailable  | no      |           |              | <MAC eth0>
-------------------+-------------+----------+--------------+---------+-----------+--------------+-----------




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


bluesky2             : ssid=bluesky2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Justin's iPhone      : ssid=Justin's | permissions=user:justin:; iPhone | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.878/3.647/4.417/0.771 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.023/0.045/0.068/0.023 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


          Current Frequency:2.422 GHz (Channel 3)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 bluesky2>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"bluesky2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000235d14047c
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 NETGEAR33>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003c950b46bd
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 ATT6511>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"ATT6511"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000211da06c24f
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Luis70>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Luis70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d30847521d
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 NETGEAR33>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001136437d26b8
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Sanay 2.5>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Sanay 2.5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000fbbb64a559
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 andy1978>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"andy1978"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002145be5cea
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 08 - Address: <MAC C-08 Pretty Fly For a WIFI>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Pretty Fly For a WIFI"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000023d1844a217
                    Extra: Last beacon: 2232ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 LowKey1760>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"LowKey1760"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001bb1666d23f
                    Extra: Last beacon: 2208ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 Starfleet Headquarters>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Starfleet Headquarters"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000b82d2d29183
                    Extra: Last beacon: 1376ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 11 - Address: <MAC C-11 DIRECT-OP-VIZIOTV>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"DIRECT-OP-VIZIOTV"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000041d49b07a
                    Extra: Last beacon: 1368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[carl9170]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
firmware:       carl9170-1.fw
srcversion:     F69F7AA6A1CF9E52DDE89FD
depends:        mac80211,ath,cfg80211
parm:           nohwcrypt:Disable hardware crypto offload. (bool)
parm:           noht:Disable MPDU aggregation. (int)


[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (carl9170)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/95hdparm-apm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/disable_wol] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/intel-audio-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/laptop-mode] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pci_devices] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pcie_aspm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sata_alpm] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sched-powersave] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/usb_bluetooth] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/wireless] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/xfs_buffer] [executable]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=UUID=1816a148-f38b-4b75-b7b4-2918b8a2b81d ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.939128] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.939503] audit: initializing netlink socket (disabled)
[    1.208794] wmi: Mapper loaded
[   11.065368] asus_wmi: ASUS WMI generic driver loaded
[   11.066956] asus_wmi: Initialization: 0x1
[   11.066995] asus_wmi: BIOS WMI version: 7.6
[   11.067046] asus_wmi: SFUN value: 0xa0877
[   11.070731] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input16
[   11.168593] asus_wmi: Backlight controlled by ACPI video driver
[   11.791986] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   12.845641] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[   13.195217] ath: EEPROM regdomain: 0x0
[   13.195220] ath: EEPROM indicates default country code should be used
[   13.195222] ath: doing EEPROM country->regdmn map search
[   13.195225] ath: country maps to regdmn code: 0x3a
[   13.195227] ath: Country alpha2 being used: US
[   13.195228] ath: Regpair used: 0x3a
[   14.501514] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.193800] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.195604] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.990887] wlan0: authenticate with <MAC C-01 bluesky2>
[   18.076690] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[   18.082129] wlan0: send auth to <MAC C-01 bluesky2> (try 2/3)
[   18.089183] wlan0: send auth to <MAC C-01 bluesky2> (try 3/3)
[   18.093978] wlan0: authenticated
[   18.095581] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[   18.100626] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[   18.106264] wlan0: associated
[   18.106289] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15575.060568] wlan0: authenticate with <MAC C-01 bluesky2>
[15575.149808] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[15575.151588] wlan0: authenticated
[15575.155548] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[15575.159634] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[15575.164704] wlan0: associated
[16531.293223] usb 2-1.2: firmware upload failed (-22).
[16532.319830] wlan0: deauthenticating from <MAC C-01 bluesky2> by local choice (reason=3)
[16532.893349] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[16533.241499] ath: EEPROM regdomain: 0x0
[16533.241508] ath: EEPROM indicates default country code should be used
[16533.241512] ath: doing EEPROM country->regdmn map search
[16533.241516] ath: country maps to regdmn code: 0x3a
[16533.241520] ath: Country alpha2 being used: US
[16533.241523] ath: Regpair used: 0x3a
[16533.459512] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[16533.462181] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[16536.707010] wlan0: authenticate with <MAC C-01 bluesky2>
[16536.796358] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[16536.797946] wlan0: authenticated
[16536.801518] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[16536.805580] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[16536.810584] wlan0: associated
[16536.810624] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[16536.853405] wlan0: deauthenticating from <MAC C-01 bluesky2> by local choice (reason=2)
[16536.946074] wlan0: authenticate with <MAC C-01 bluesky2>
[16537.032356] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[16537.037885] wlan0: authenticated
[16537.041547] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[16537.045974] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[16537.050997] wlan0: associated
[17155.838912] net_ratelimit: 1 callbacks suppressed
[21132.799070] wlan0: authenticate with <MAC C-01 bluesky2>
[21132.884842] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[21132.893503] wlan0: authenticated
[21132.894804] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[21132.898974] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[21132.903560] wlan0: associated
[22037.767687] wlan0: AP <MAC C-01 bluesky2> changed bandwidth, new config is 2422 MHz, width 2 (2432/0 MHz)
[22337.634986] wlan0: AP <MAC C-01 bluesky2> changed bandwidth, new config is 2422 MHz, width 1 (2422/0 MHz)
[46584.671995] wlan0: authenticate with <MAC C-01 bluesky2>
[46584.758631] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[46584.760507] wlan0: authenticated
[46584.761885] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[46584.765982] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[46584.771706] wlan0: associated
[51724.586570] wlan0: authenticate with <MAC C-01 bluesky2>
[51724.672684] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[51724.675677] wlan0: authenticated
[51724.679301] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[51724.683556] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[51724.688527] wlan0: associated
[51824.623110] wlan0: authenticate with <MAC C-01 bluesky2>
[51824.709377] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[51824.811922] wlan0: send auth to <MAC C-01 bluesky2> (try 2/3)
[51824.816776] wlan0: send auth to <MAC C-01 bluesky2> (try 3/3)
[51824.820654] wlan0: authentication with <MAC C-01 bluesky2> timed out
[51827.083252] wlan0: authenticate with <MAC C-01 bluesky2>
[51827.168768] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[51827.170690] wlan0: authenticated
[51827.171052] wlan0: waiting for beacon from <MAC C-01 bluesky2>
[51827.190764] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[51827.194796] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[51827.199105] wlan0: associated
[53317.713430] wlan0: authenticate with <MAC C-01 bluesky2>
[53317.805089] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[53317.821554] wlan0: authenticated
[53317.825515] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[53317.831239] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[53317.836310] wlan0: associated
[61595.382698] usb 2-1.2: firmware upload failed (-22).
[61596.402305] wlan0: deauthenticating from <MAC C-01 bluesky2> by local choice (reason=3)
[61596.997343] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[61597.346247] ath: EEPROM regdomain: 0x0
[61597.346251] ath: EEPROM indicates default country code should be used
[61597.346252] ath: doing EEPROM country->regdmn map search
[61597.346254] ath: country maps to regdmn code: 0x3a
[61597.346256] ath: Country alpha2 being used: US
[61597.346257] ath: Regpair used: 0x3a
[61597.575110] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[61597.579780] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[61599.469259] wlan0: authenticate with <MAC C-01 bluesky2>
[61599.567927] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[61599.573266] wlan0: authenticated
[61599.574256] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[61599.587593] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[61599.592586] wlan0: associated
[61599.592705] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[67903.500844] usb 2-1.2: firmware upload failed (-22).
[67904.521846] wlan0: deauthenticating from <MAC C-01 bluesky2> by local choice (reason=3)
[67905.090788] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[67905.441964] ath: EEPROM regdomain: 0x0
[67905.441972] ath: EEPROM indicates default country code should be used
[67905.441976] ath: doing EEPROM country->regdmn map search
[67905.441990] ath: country maps to regdmn code: 0x3a
[67905.441993] ath: Country alpha2 being used: US
[67905.441996] ath: Regpair used: 0x3a
[67905.667924] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[67905.670650] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[67908.957059] wlan0: authenticate with <MAC C-01 bluesky2>
[67909.043147] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[67909.044884] wlan0: authenticated
[67909.047853] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[67909.051814] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=2)
[67909.056932] wlan0: associated
[67909.056992] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[67909.098079] wlan0: deauthenticating from <MAC C-01 bluesky2> by local choice (reason=2)
[67909.189022] wlan0: authenticate with <MAC C-01 bluesky2>
[67909.277295] wlan0: send auth to <MAC C-01 bluesky2> (try 1/3)
[67909.280341] wlan0: authenticated
[67909.283551] wlan0: associate with <MAC C-01 bluesky2> (try 1/3)
[67909.288218] wlan0: RX AssocResp from <MAC C-01 bluesky2> (capab=0x431 status=0 aid=1)
[67909.293278] wlan0: associated
[67995.296314] net_ratelimit: 2 callbacks suppressed


	======== Done ========



```

```
-rw-rw-r-- 1 justin justin 6.9K Jun  5 12:44 wireless-info.tar.gz
-rwxrwxr-x 1 justin justin  16K Jun  4 16:27 wireless_script

```

---

### Post by varunendra on 2014-06-06
You are using a power saving package "TLP". Please read my comments on it that I just posted here : [http://ubuntuforums.org/showpost.php?p=13042596](http://ubuntuforums.org/showpost.php?p=13042596) and try a Live DVD/USB as suggested to see if it performs better without TLP.

Additionally, you may try a driver parameter -
```
sudo modprobe -rv carl9170
sudo modprobe -v carl9170 nohwcrypt=Y
```
The first command will remove the driver thus disabling the adapter. The second one will reload it with the 'nohwcrypt=Y' parameter. It will be a temporary change that would be lost on next boot. If it helps, we can make it permanent.

---

### Post by papa.jinzu on 2014-06-06
Will doing the actions in the other thread you mentioned disable powersave on wireless? I need my wireless on at all time because I am using a dongle and work from the Internet.

---

### Post by varunendra on 2014-06-06
I hope it does, not sure if it really will.

But if you are confusing 'powersave' with enabling/disabling of wireless adapter, then let me clarify that these are different things. Power Management is a feature that tries to save power on a device (wireless adapter here) when it *thinks* the device is idle, it does not really turn it off completely. Disabling this feature means there will be no attempts to save power, and the device will work on full power all the time.

---

### Post by papa.jinzu on 2014-06-06
for this: [http://ubuntuforums.org/showpost.php?p=13042596](http://ubuntuforums.org/showpost.php?p=13042596)

When doing what was suggested here the wireless adapter still disconnects.

When doing what was suggested below my wireless does not connect at all

```

sudo modprobe -rv carl9170
sudo modprobe -v carl9170 nohwcrypt=Y

```

---

### Post by varunendra on 2014-06-06
> **papa.jinzu said:**
> When doing what was suggested below my wireless does not connect at all

```

sudo modprobe -rv carl9170
sudo modprobe -v carl9170 nohwcrypt=Y

```

Can we see the output on the terminal when running the above code? Neither reloading of a module, nor that parameter should have any adverse effect on performance.

---

### Post by papa.jinzu on 2014-06-06
```
justin@justin-U56E:~$ sudo modprobe -rv carl9170
[sudo] password for justin: 
rmmod carl9170
rmmod mac80211
rmmod ath
rmmod cfg80211
justin@justin-U56E:~$ sudo modprobe -v carl9170 nohwcrypt=Y
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko nohwcrypt=Y
justin@justin-U56E:~$ 



```

---

### Post by varunendra on 2014-06-07
Looks good to me, please run the wireless_script after running above commands, and post back the report generated in that condition.

---

### Post by papa.jinzu on 2014-06-07
The wireless usb adapter does allow me to connect to a wifi network after running the commands.
Here is the output after running ./wireless_script in Konsole.



```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


justin-U56E 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty


CPU    : Intel(R) Core(TM) i5-2410M CPU @ 2.30GHz
Memory : 5872 MB
Uptime : 14:51:02 up  1:30,  3 users,  load average: 0.48, 0.52, 0.77




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 1a)
	Subsystem: Intel Corporation Device [8086:0000]
03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]
--
04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 004: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9170+AR9101]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 05ac:12a8 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: asus-wlan: Wireless LAN        no            no
1: asus-bluetooth: Bluetooth      no            no
2: hci0: Bluetooth                no            no
5: phy0: Wireless LAN             no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


carl9170               91161  0 
ath                    28698  1 carl9170
mac80211              626489  1 carl9170
cfg80211              484040  3 ath,mac80211,carl9170
asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  2 i915,asus_wmi




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
carl9170      (2): noht=0 | nohwcrypt=Y
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connecting
================o=============o==========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver   | State        | Default | Speed     | Support      | HW Addr   
================o=============o==========o==============o=========o===========o==============o===========
 wlan0  [vespa] | 802.11 WiFi | carl9170 | connecting (configuring)| no      |           | WEP/WPA/WPA2 | <MAC wlan0>


    ghc:             Infra, <MAC C-27 ghc>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    vespa:           Infra, <MAC C-04 vespa>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77 WPA2 Enterprise
    ghc:             Infra, <MAC C-12 ghc>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    vespa:           Infra, <MAC C-14 vespa>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64 WPA2 Enterprise
    ghc:             Infra, <MAC C-NA ghc 4>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    vespa:           Infra, <MAC C-09 vespa>, Freq 2437 MHz, Rate 54 Mb/s, Strength 60 WPA2 Enterprise
    vespa:           Infra, <MAC C-17 vespa>, Freq 2462 MHz, Rate 54 Mb/s, Strength 55 WPA2 Enterprise
    ghc:             Infra, <MAC C-11 ghc>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA2 Enterprise
    vespa:           Infra, <MAC C-NA vespa 5>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA2 Enterprise
    ghc:             Infra, <MAC C-13 ghc>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    vespa:           Infra, <MAC C-02 vespa>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    ghc:             Infra, <MAC C-05 ghc>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2 Enterprise
    ghc:             Infra, <MAC C-06 ghc>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    guest:           Infra, <MAC C-15 guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 64
    guest:           Infra, <MAC C-10 guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59
    hpsetup:         Ad-Hoc, <MAC C-07 hpsetup>, Freq 2437 MHz, Rate 11 Mb/s, Strength 65
    guest:           Infra, <MAC C-08 guest>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50
    guest:           Infra, <MAC C-16 guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 50
    guest:           Infra, <MAC C-01 guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 37
    ghc:             Infra, <MAC C-20 ghc>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA2 Enterprise
    ghc:             Infra, <MAC C-18 ghc>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA2 Enterprise
    guest:           Infra, <MAC C-21 guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 77
    guest:           Infra, <MAC C-19 guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 49
    guest:           Infra, <MAC C-22 guest>, Freq 2412 MHz, Rate 54 Mb/s, Strength 49
    vespa:           Infra, <MAC C-03 vespa>, Freq 2412 MHz, Rate 54 Mb/s, Strength 35 WPA2 Enterprise
    vespa:           Infra, <MAC C-26 vespa>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WPA2 Enterprise
    vespa:           Infra, <MAC C-24 vespa>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2 Enterprise
    ghc:             Infra, <MAC C-23 ghc>, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2 Enterprise
    guest:           Infra, <MAC C-25 guest>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | atl1c    | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------
 eth1           | Wired       | ipheth   | unavailable  | no      |           |              | <MAC ID removed>
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~


bluesky2             : ssid=bluesky2 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Justin's iPhone      : ssid=Justin's | permissions=user:justin:; iPhone | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
vespa                : ssid=vespa | permissions=user:justin:; | ipv4=auto 




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
country US:
	(2402 - 2472 @ 40), (3, 27)
	(5170 - 5250 @ 40), (3, 17)
	(5250 - 5330 @ 40), (3, 20), DFS
	(5490 - 5600 @ 40), (3, 20), DFS
	(5650 - 5710 @ 40), (3, 20), DFS
	(5735 - 5835 @ 40), (3, 30)
	(57240 - 63720 @ 2160), (N/A, 40)




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b19473180
                    Extra: Last beacon: 21984ms ago
          Cell 02 - Address: <MAC C-02 vespa>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000239637644
                    Extra: Last beacon: 6824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: <MAC C-03 vespa>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b1948c180
                    Extra: Last beacon: 21960ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 04 - Address: <MAC C-04 vespa>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000016676aeec2
                    Extra: Last beacon: 1424ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 05 - Address: <MAC C-05 ghc>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000002396310ca
                    Extra: Last beacon: 21952ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC C-06 ghc>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b1a814180
                    Extra: Last beacon: 1456ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 07 - Address: <MAC C-07 hpsetup>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:off
                    ESSID:"hpsetup"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000011af2a7efdb
                    Extra: Last beacon: 756ms ago
          Cell 08 - Address: <MAC C-08 guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000035006b996
                    Extra: Last beacon: 6668ms ago
          Cell 09 - Address: <MAC C-09 vespa>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000104966d58f
                    Extra: Last beacon: 6668ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 10 - Address: <MAC C-10 guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001047927571
                    Extra: Last beacon: 756ms ago
          Cell 11 - Address: <MAC C-11 ghc>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000029dba25e91
                    Extra: Last beacon: 6984ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 12 - Address: <MAC C-12 ghc>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017191f986a
                    Extra: Last beacon: 6980ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 13 - Address: <MAC C-13 ghc>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f727e0180
                    Extra: Last beacon: 6976ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 14 - Address: <MAC C-14 vespa>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000171c2faef6
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 15 - Address: <MAC C-15 guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001719f3d8da
                    Extra: Last beacon: 22084ms ago
          Cell 16 - Address: <MAC C-16 guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b83704e8c
                    Extra: Last beacon: 6960ms ago
          Cell 17 - Address: <MAC C-17 vespa>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000029dc8c036e
                    Extra: Last beacon: 21864ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 18 - Address: <MAC C-18 ghc>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b83710de0
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 19 - Address: <MAC C-19 guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f72e6b180
                    Extra: Last beacon: 64ms ago
          Cell 20 - Address: <MAC C-20 ghc>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000350077e75
                    Extra: Last beacon: 764ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 21 - Address: <MAC C-21 guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000166769a180
                    Extra: Last beacon: 1448ms ago
          Cell 22 - Address: <MAC C-22 guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000023a4a4b3f
                    Extra: Last beacon: 1420ms ago
          Cell 23 - Address: <MAC C-23 ghc>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000169f56d180
                    Extra: Last beacon: 22260ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 24 - Address: <MAC C-24 vespa>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000016a0445180
                    Extra: Last beacon: 6672ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 25 - Address: <MAC C-25 guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000029dc8b39ee
                    Extra: Last beacon: 44ms ago
          Cell 26 - Address: <MAC C-26 vespa>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003b845bd180
                    Extra: Last beacon: 22088ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 27 - Address: <MAC C-27 ghc>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"ghc"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001667186180
                    Extra: Last beacon: 6824ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
          Cell 28 - Address: <MAC C-28 guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:off
                    ESSID:"guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000016a09d6180
                    Extra: Last beacon: 784ms ago
          Cell 29 - Address: <MAC C-29 vespa>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"vespa"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000f72e84180
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[carl9170]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
firmware:       carl9170-1.fw
srcversion:     F69F7AA6A1CF9E52DDE89FD
depends:        mac80211,ath,cfg80211
parm:           nohwcrypt:Disable hardware crypto offload. (bool)
parm:           noht:Disable MPDU aggregation. (int)


[ath]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (carl9170)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


[/etc/pm/power.d/95hdparm-apm]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/disable_wol]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/intel-audio-powersave]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/laptop-mode]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pci_devices]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/pcie_aspm]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sata_alpm]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/sched-powersave]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/usb_bluetooth]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/wireless]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0


[/etc/pm/power.d/xfs_buffer]
#!/bin/sh
# tlp - if tlp is enabled, override corresponding script
#       in /usr/lib*/pm-utils/power.d/


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


    if [ -e "$CONFFILE" ] && . "$CONFFILE" -- && [ "$TLP_ENABLE" = '1' ]; then
        # TLP is enabled -> disable $blocked
        echo "Notice: '${blocked}' disabled by TLP."
    else
        exec "$blocked" $*
    fi
fi


exit 0




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/vmlinuz-3.13.0-24-generic root=UUID=1816a148-f38b-4b75-b7b4-2918b8a2b81d ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.950709] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.951086] audit: initializing netlink socket (disabled)
[    1.220259] wmi: Mapper loaded
[   11.161168] asus_wmi: ASUS WMI generic driver loaded
[   11.163703] asus_wmi: Initialization: 0x1
[   11.163739] asus_wmi: BIOS WMI version: 7.6
[   11.164292] asus_wmi: SFUN value: 0xa0877
[   11.165920] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input13
[   11.260394] asus_wmi: Backlight controlled by ACPI video driver
[   11.869175] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   12.787343] usb 2-1.1: firmware API: 1.9.6 2012-07-07
[   12.809877] ipheth 3-1:4.2: Apple iPhone USB Ethernet device attached
[   13.135160] ath: EEPROM regdomain: 0x0
[   13.135169] ath: EEPROM indicates default country code should be used
[   13.135172] ath: doing EEPROM country->regdmn map search
[   13.135177] ath: country maps to regdmn code: 0x3a
[   13.135181] ath: Country alpha2 being used: US
[   13.135184] ath: Regpair used: 0x3a
[   15.120758] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.472828] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.475450] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   16.717245] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.719347] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  899.987013] wlan0: authenticate with <MAC C-04 vespa>
[  900.073933] wlan0: send auth to <MAC C-04 vespa> (try 1/3)
[  900.075575] wlan0: authenticated
[  900.078415] wlan0: associate with <MAC C-04 vespa> (try 1/3)
[  900.080820] wlan0: RX AssocResp from <MAC C-04 vespa> (capab=0x411 status=0 aid=5)
[  900.085831] wlan0: associated
[  900.085885] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3687.433401] wlan0: deauthenticating from <MAC C-04 vespa> by local choice (reason=3)
[ 4844.747838] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[ 4845.094235] ath: EEPROM regdomain: 0x0
[ 4845.094239] ath: EEPROM indicates default country code should be used
[ 4845.094240] ath: doing EEPROM country->regdmn map search
[ 4845.094242] ath: country maps to regdmn code: 0x3a
[ 4845.094243] ath: Country alpha2 being used: US
[ 4845.094244] ath: Regpair used: 0x3a
[ 4845.511064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4845.512842] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4848.735437] wlan0: authenticate with <MAC C-04 vespa>
[ 4848.824100] wlan0: send auth to <MAC C-04 vespa> (try 1/3)
[ 4848.825356] wlan0: authenticated
[ 4848.829219] wlan0: associate with <MAC C-04 vespa> (try 1/3)
[ 4848.831303] wlan0: RX AssocResp from <MAC C-04 vespa> (capab=0x411 status=0 aid=1)
[ 4848.836303] wlan0: associated
[ 4848.836336] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5385.902951] wlan0: deauthenticating from <MAC C-04 vespa> by local choice (reason=3)
[ 5394.533277] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[ 5394.889540] ath: EEPROM regdomain: 0x0
[ 5394.889549] ath: EEPROM indicates default country code should be used
[ 5394.889553] ath: doing EEPROM country->regdmn map search
[ 5394.889558] ath: country maps to regdmn code: 0x3a
[ 5394.889562] ath: Country alpha2 being used: US
[ 5394.889565] ath: Regpair used: 0x3a
[ 5395.114053] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5395.116547] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5405.276201] wlan0: authenticate with <MAC C-04 vespa>
[ 5405.362648] wlan0: send auth to <MAC C-04 vespa> (try 1/3)
[ 5405.363832] wlan0: authenticated
[ 5410.360710] wlan0: deauthenticating from <MAC C-04 vespa> by local choice (reason=3)
[ 5420.464730] wlan0: authenticate with <MAC C-14 vespa>
[ 5420.551494] wlan0: send auth to <MAC C-14 vespa> (try 1/3)
[ 5420.552816] wlan0: authenticated
[ 5425.549598] wlan0: deauthenticating from <MAC C-14 vespa> by local choice (reason=3)
[ 5435.648509] wlan0: authenticate with <MAC C-09 vespa>
[ 5435.736765] wlan0: send auth to <MAC C-09 vespa> (try 1/3)
[ 5435.738567] wlan0: authenticated
[ 5440.827342] wlan0: deauthenticating from <MAC C-09 vespa> by local choice (reason=3)


	======== Done ========



```

---

### Post by varunendra on 2014-06-07
> **papa.jinzu said:**
> The wireless usb adapter **[COLOR="#0000CD"]does allow me[/COLOR]** to connect to a wifi network after running the commands.
Please clarify - does or doesn't? Because earlier you wrote -
> **papa.jinzu said:**
> When doing what was suggested below my wireless **[COLOR="#FF0000"]does not connect at all[/COLOR]**

```

sudo modprobe -rv carl9170
sudo modprobe -v carl9170 nohwcrypt=Y

```

If it helps, making it permanent is easy. If it doesn't we can try a few more things.

---

### Post by papa.jinzu on 2014-06-07
That was a typo. I meant this: [COLOR=#000000]*The wireless usb adapter *[/COLOR]**[COLOR=#0000CD]does NOT allow me[/COLOR] to connect to a wifi network after running the commands.**

---

### Post by varunendra on 2014-06-08
It is scanning networks means the card is working at least to some extent. Please describe what happens when you click on a network in nm-applet's menu. From the report it seems it was trying to connect to one of the APs with SSID "vespa", and since there are many of them around, it is also hopping from one to another.

Try binding the connection to one particular AP among these. Use the command -
```
sudo iwlist scan
```
to see which one has the strongest signal and save its MAC address ("Address" in the output) into the "BSSID" field of the connection profile under "Wireless" tab in Network Manager (nm-applet > Edit Connection > Wireless tab > Edit the connection).

If that doesn't help, some other things to try -

**1)** Try another available parameter which is worth trying in certain setups -
```
sudo modprobe -rv carl9170
sudo modprobe -v carl9170 nohwcrypt=Y **noht=1**
```

**2)** If you have admin access to the router, try disabling 'N' mode (set it to b/g mode only) in it. Although seeing the nature of the AP, doesn't look like you have that option.

**3)** As a desperate, probably last experimental attempt, try replacing the driver's firmware with (apparently) the latest one from github -
```
wget http://git.kernel.org/cgit/linux/kernel/git/firmware/linux-firmware.git/plain/carl9170-1.fw
sudo mv /lib/firmware/carl9170-1.fw carl9170-1.fw.bak
sudo mv carl9170-1.fw /lib/firmware
```
..followed by a reboot. The driver may or may not accept this new firmware. So if you still can't connect (with the "nohwcrypt=Y" and "noht=1" parameters applied), check dmesg to see if there is a firmware error -
```
dmesg | egrep -i 'firm|carl'
```
If there is, post back the error here. You can restore the older firmware that we backed up (but I suggest you do so only if it is confirmed that the new one is not working) -
```
sudo mv /lib/firmware/carl9170-1.fw carl9170-1.fw.new
sudo mv carl9170-1.fw.bak /lib/firmware
```
Followed by a reboot.

**PS:**
For reference : [http://wireless.kernel.org/en/users/Drivers/carl9170](http://wireless.kernel.org/en/users/Drivers/carl9170)

---

### Post by papa.jinzu on 2014-06-08
The reason for there being so many "vespa" connections is that I was at school on campus when I ran the wireless script. Now I am at home and the wireless connection I use is "bluesky2". I can post the log of the wireless script here. Unfortunately the file "wireless-info.txt" is not saving to the computer. It is a 1 Byte file with nothing in it. This is the output from Konsole terminal:

```
justin@justin-U56E:~$ sudo ./wireless_script


        **** PLEASE WAIT WHILE THE SCRIPT GENERATES THE REPORT ****
  
  If this takes more than 1 minute, you may abort the script by pressing
  "Ctrl+Z" on your keyboard.
  
  (Type your Login Password when asked, then press 'Enter')


sed: -e expression #1, char 133: unknown command: `C'




    ########################################################################


    DONE! All results saved in -


                 File Name:     "wireless-info.txt" 
                 Directory:     "/home/justin"


    Please upload the above file or its contents where you are seeking help.


    ------------------------------------------------------------------------
    NOTE: Although we have taken full precaution to filter out all sensitive
          information, it is recommended to take a look at the file yourself
          to be double sure that it contains no sensitive data.
    ------------------------------------------------------------------------


    ########################################################################



```


I ran the commands you suggested only to have the adapter still disconnecting. I do not know how to fix this problem. I most likely will have to get another adapter because of the problems with this one.

Here is the output after checking for firmware errors:

```

justin@justin-U56E:~$ dmesg | egrep -i 'firm|carl'
[    0.177181] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[   11.513757] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   12.537559] usbcore: registered new interface driver carl9170
[   12.581766] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[ 9096.093029] usb 2-1.2: firmware upload failed (-22).
[ 9097.703260] usb 2-1.2: firmware API: 1.9.6 2012-07-07

```

---

### Post by papa.jinzu on 2014-06-11
Should I get another adapter? Can this adapter be fixed?

---

### Post by varunendra on 2014-06-11
Sorry for my inability to respond sooner, my work routine has become too exhaustive to let me indulge here. In fact I am responding even now because I forgot my diary in the office, so have nothing to do for about an hour or so.

On to the problem - If you wish to seek help on the current one, please post the report of the regular **wireless_script** which you can find in the 'Wireless Script' link in my signature below. The experimental one seems to have a bug apparently triggered by abnormal AP names, the regular one should confirm that.

However, unless the problem turns out to be something obvious and easy to fix, or unless someone else picks up your thread and is able to help you out, I think getting a new, supported adapter would be the best idea at this point. Although this one should have been supported as well, so I'm not sure if the problem is the adapter (or driver) or something else.

**PS:**
I don't get time to even check the responses these days, so if anyone watching this thread has any ideas, please join us. Thanks!

---

### Post by papa.jinzu on 2014-06-12
```



########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux justin-U56E 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


##### lspci #####


02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 1a)
	Subsystem: Intel Corporation Device [8086:0000]
03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042]


04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
	Kernel driver in use: atl1c


##### lsusb #####


Bus 002 Device 005: ID 0846:9001 NetGear, Inc. WN111(v2) RangeMax Next Wireless [Atheros AR9170+AR9101]
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA Card Info #####


##### rfkill #####


0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
11: phy8: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


wlan0     IEEE 802.11bgn  ESSID:"bluesky2"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: <MAC address removed>   
          Bit Rate=58.5 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:46   Missed beacon:0


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


##### resolv.conf #####


nameserver 127.0.1.1


##### nm-tool #####


NetworkManager Tool


State: connected (global)


- Device: wlan0  [bluesky2] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            carl9170
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           58 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    ATT6511:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70 WPA2
    NETGEAR33:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 92 WPA2
    DesiBoyz:        Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    andy1978:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 65 WPA2
    Luis70:          Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA2
    Sanay 2.5:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    Kalpana Arora:   Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Cisco17982-guest:Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100
    Pretty Fly For a WIFI-guest: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 34
    NETGEAR33:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA2
    LowKey1760:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Pretty Fly For a WIFI: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 15 WPA2
    NETGEAR81:       Infra, <MAC address removed>, Freq 2427 MHz, Rate 54 Mb/s, Strength 27 WPA2
    DIRECT-OP-VIZIOTV: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 54 WPA2
    dazzy:           Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Starfleet Headquarters: Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 20 WPA2
    Kaveti home:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    HOME-B5BF:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WEP
    *bluesky2:       Infra, <MAC address removed>, Freq 2422 MHz, Rate 54 Mb/s, Strength 84 WPA2
    Kaveti-Home:     Infra, <MAC address removed>, Freq 2462 MHz, Rate 56 Mb/s, Strength 20 WEP
    NETGEAR81:       Infra, <MAC address removed>, Freq 2427 MHz, Rate 0 Mb/s, Strength 20 WEP


  IPv4 Settings:
    Address:         192.168.1.133
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1


    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false
WimaxEnabled=true
WiMAXEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"bluesky2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000cf35339
                    Extra: Last beacon: 232ms ago
                    IE: Unknown: 0008626C7565736B7932
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101830003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3403080800000000000000000000000000000000000000
                    IE: Unknown: 3D1603080800000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001000000000000010000000C43DC79CEA83102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"LowKey1760"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000771150335c
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000A4C6F774B657931373630
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD910050F204104A0001101044000102103B0001031047001035BDE523D316F2D271F6275656FD3F2910210013436973636F2053797374656D732C20496E632E1023000E4C696E6B737973204541323730301024000645413237303010420001311054000800060050F20400011011000D4C6F774B657931373630204150100800022008103C0001021049000600372A000120
                    IE: Unknown: DD090010180201F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c6bcbe007e
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00094E4554474541523333
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601081500000000000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B000103104700103D7A0BAAEE781235115D52BBE1313D2C1021000D4E4554474541522C20496E632E10230009574E5231303030763310240009574E523130303076331042000538333235381054000800060050F204000110110009574E52313030307633100800020084
                    IE: Unknown: DD090010180206F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C336C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401081500000000000000000000000000000000000000
          Cell 04 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"ATT6511"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000029c01c363d8
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000741545436353131
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 331AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001100000000000000000000000000000000000000
                    IE: Unknown: 341601001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
          Cell 05 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"Luis70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000058594f4180
                    Extra: Last beacon: 1516ms ago
                    IE: Unknown: 00064C7569733730
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B24
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD26000C42000000011E000000001F660902FF0F416972526F757465720000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F202010185000364000027A4000041435E0061322F00
                    IE: Unknown: DD1E00904C33CC111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 2D1ACC111BFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401001D00000000000000000000000000000000000000
                    IE: Unknown: 3D1601001D00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD0E00156D0000000102A2E402021400
          Cell 06 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"andy1978"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000b756bc027
                    Extra: Last beacon: 1760ms ago
                    IE: Unknown: 0008616E647931393738
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD0900037F0101001FFF7F
                    IE: Unknown: DD0C00037F020101000002A34000
                    IE: Unknown: DD1A00037F0301000000001CF0E8A245021CF0E8A24564002C011F08
          Cell 07 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000011c097221c1e
                    Extra: Last beacon: 1772ms ago
                    IE: Unknown: 00094E4554474541523333
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606001500000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33AD0103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: DD1A00904C3406001500000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD900050F204104A0001101044000102103B00010310470010427974EECF6C52788C94000000000000102100046E6F6E65102300046E6F6E65102400046E6F6E651042001253657269616C204E756D62657220486572651054000800060050F204000110110016574E5232303030763428576972656C65737320415029100800022008103C0001011049000600372A000120
          Cell 08 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Sanay 2.5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000185f755e3c7
                    Extra: Last beacon: 1804ms ago
                    IE: Unknown: 000953616E617920322E35
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010100
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF1103FFFF0000000000000000000000000000000406E6E70D00
                    IE: Unknown: 3D1606051700000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101850003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD260050F204104A0001101044000102104900140024E26002000101600000020001600100020001
          Cell 09 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:off
                    ESSID:"Cisco17982-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000045845a6657
                    Extra: Last beacon: 940ms ago
                    IE: Unknown: 0010436973636F31373938322D6775657374
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1017FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1608070400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C336E1017FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408070400000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 10 - Address: <MAC address removed>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"DesiBoyz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000045845b1edf
                    Extra: Last beacon: 936ms ago
                    IE: Unknown: 000844657369426F797A
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030108
                    IE: Unknown: 0406000200000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A6E1017FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1608070400000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A00B400C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD1E00904C336E1017FFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3408070400000000000000000000000000000000000000
                    IE: Unknown: DD06005043030000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD740050F204104A0001101044000102103B0001031047001082883490697F47EAAF3D2D91D9B7264410210005436973636F10230003574150102400033132331042000531323334351054000800060050F20400011011000844657369426F797A10080002200C103C0001011049000600372A000120
          Cell 11 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Kaveti-Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000832bdee2ac
                    Extra: Last beacon: 96ms ago
                    IE: Unknown: 000B4B61766574692D486F6D65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E95
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD0E0017F2070001010620C9D027402B
                    IE: Unknown: DD0B0017F20100010100000007


##### iwlist channel #####


wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.422 GHz (Channel 3)


##### lsmod #####


carl9170               91161  0 
ath                    28698  1 carl9170
mac80211              626489  1 carl9170
cfg80211              484040  3 ath,mac80211,carl9170


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/carl9170/carl9170.ko
alias:          arusb_lnx
alias:          ar9170usb
firmware:       carl9170-1.fw
description:    Atheros AR9170 802.11n USB wireless
license:        GPL
author:         Christian Lamparter <chunkeey@googlemail.com>
author:         Johannes Berg <johannes@sipsolutions.net>
srcversion:     F69F7AA6A1CF9E52DDE89FD
alias:          usb:v1B75p9170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1668p1200d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8402d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p02B4d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0409p0249d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp093Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0026d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3417d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0326d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1435p0804d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0ACEp1221d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3A09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C10d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:vCACEp0300d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p1001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CF3p9170d*dc*dsc*dp*ic*isc*ip*in*
depends:        mac80211,ath,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware crypto offload. (bool)
parm:           noht:Disable MPDU aggregation. (int)


filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D9:06:21:70:6E:8D:06:60:4D:73:0B:35:9F:C0
sig_hashalgo:   sha512


##### modules #####


lp
rtc


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (carl9170)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


##### dmesg #####


[   13.842395] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   14.862639] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[   15.209590] ath: EEPROM regdomain: 0x0
[   15.209599] ath: EEPROM indicates default country code should be used
[   15.209602] ath: doing EEPROM country->regdmn map search
[   15.209607] ath: country maps to regdmn code: 0x3a
[   15.209610] ath: Country alpha2 being used: US
[   15.209613] ath: Regpair used: 0x3a
[   19.663300] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.665045] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.397099] wlan0: authenticate with <MAC address removed>
[   21.492367] wlan0: send auth to <MAC address removed> (try 1/3)
[   21.493957] wlan0: authenticated
[   21.496436] wlan0: associate with <MAC address removed> (try 1/3)
[   21.502137] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[   21.507200] wlan0: associated
[   21.507259] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  834.783649] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  836.063629] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[  836.407637] ath: EEPROM regdomain: 0x0
[  836.407641] ath: EEPROM indicates default country code should be used
[  836.407642] ath: doing EEPROM country->regdmn map search
[  836.407643] ath: country maps to regdmn code: 0x3a
[  836.407644] ath: Country alpha2 being used: US
[  836.407645] ath: Regpair used: 0x3a
[  836.812591] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  836.814327] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  838.504626] wlan0: authenticate with <MAC address removed>
[  838.607646] wlan0: send auth to <MAC address removed> (try 1/3)
[  838.609231] wlan0: authenticated
[  838.609739] wlan0: associate with <MAC address removed> (try 1/3)
[  838.613612] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[  838.620598] wlan0: associated
[  838.620631] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1401.827786] usb 2-1.2: firmware upload failed (-22).
[ 1402.857352] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 1403.450527] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[ 1403.797144] ath: EEPROM regdomain: 0x0
[ 1403.797147] ath: EEPROM indicates default country code should be used
[ 1403.797148] ath: doing EEPROM country->regdmn map search
[ 1403.797150] ath: country maps to regdmn code: 0x3a
[ 1403.797151] ath: Country alpha2 being used: US
[ 1403.797152] ath: Regpair used: 0x3a
[ 1404.021088] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1404.022954] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1407.384847] wlan0: authenticate with <MAC address removed>
[ 1407.474759] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1407.478117] wlan0: send auth to <MAC address removed> (try 2/3)
[ 1407.481586] wlan0: send auth to <MAC address removed> (try 3/3)
[ 1407.483107] wlan0: authenticated
[ 1407.486999] wlan0: associate with <MAC address removed> (try 1/3)
[ 1407.499108] wlan0: associate with <MAC address removed> (try 2/3)
[ 1407.506961] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1407.511937] wlan0: associated
[ 1407.511963] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1410.743523] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[ 1410.836905] wlan0: authenticate with <MAC address removed>
[ 1410.924464] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1410.926175] wlan0: authenticated
[ 1410.929310] wlan0: associate with <MAC address removed> (try 1/3)
[ 1410.933432] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 1410.938424] wlan0: associated
[ 4215.464595] wlan0: authenticate with <MAC address removed>
[ 4215.552096] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4215.638181] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4215.644176] wlan0: authenticated
[ 4215.648478] wlan0: associate with <MAC address removed> (try 1/3)
[ 4215.657562] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4215.662278] wlan0: associated
[ 4273.578488] wlan0: authenticate with <MAC address removed>
[ 4273.664557] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4273.709882] wlan0: authenticated
[ 4273.710658] wlan0: associate with <MAC address removed> (try 1/3)
[ 4273.714717] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4273.720161] wlan0: associated
[ 4290.450385] wlan0: authenticate with <MAC address removed>
[ 4290.538662] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4290.543823] wlan0: send auth to <MAC address removed> (try 2/3)
[ 4290.549733] wlan0: send auth to <MAC address removed> (try 3/3)
[ 4290.558464] wlan0: authentication with <MAC address removed> timed out
[ 4292.816183] wlan0: authenticate with <MAC address removed>
[ 4292.911611] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4292.934349] wlan0: authenticated
[ 4292.936853] wlan0: associate with <MAC address removed> (try 1/3)
[ 4292.941475] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4292.946558] wlan0: associated
[ 4302.194805] wlan0: deauthenticated from <MAC address removed> (Reason: 2)
[ 4302.296953] wlan0: deauthenticating from <MAC address removed> by local choice (reason=1)
[ 4304.016593] wlan0: authenticate with <MAC address removed>
[ 4304.103252] wlan0: send auth to <MAC address removed> (try 1/3)
[ 4304.105210] wlan0: authenticated
[ 4304.107082] wlan0: associate with <MAC address removed> (try 1/3)
[ 4304.111482] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[ 4304.116482] wlan0: associated
[10011.778896] usb 2-1.2: firmware upload failed (-22).
[10012.801478] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[10013.402788] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[10013.751234] ath: EEPROM regdomain: 0x0
[10013.751243] ath: EEPROM indicates default country code should be used
[10013.751247] ath: doing EEPROM country->regdmn map search
[10013.751251] ath: country maps to regdmn code: 0x3a
[10013.751255] ath: Country alpha2 being used: US
[10013.751259] ath: Regpair used: 0x3a
[10013.980391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10013.982905] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10015.720787] wlan0: authenticate with <MAC address removed>
[10015.848233] wlan0: send auth to <MAC address removed> (try 1/3)
[10015.851691] wlan0: authenticated
[10015.855802] wlan0: associate with <MAC address removed> (try 1/3)
[10015.874467] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[10015.879440] wlan0: associated
[10015.879494] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[10578.664581] usb 2-1.2: firmware upload failed (-22).
[10579.682087] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[10580.259588] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[10580.611887] ath: EEPROM regdomain: 0x0
[10580.611893] ath: EEPROM indicates default country code should be used
[10580.611895] ath: doing EEPROM country->regdmn map search
[10580.611898] ath: country maps to regdmn code: 0x3a
[10580.611900] ath: Country alpha2 being used: US
[10580.611902] ath: Regpair used: 0x3a
[10580.836296] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10580.839784] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[10582.680976] wlan0: authenticate with <MAC address removed>
[10582.773116] wlan0: send auth to <MAC address removed> (try 1/3)
[10582.775587] wlan0: authenticated
[10582.776261] wlan0: associate with <MAC address removed> (try 1/3)
[10582.783804] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[10582.788723] wlan0: associated
[10582.788801] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11382.395193] usb 2-1.2: firmware upload failed (-22).
[11382.424963] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[11384.013430] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[11384.360031] ath: EEPROM regdomain: 0x0
[11384.360035] ath: EEPROM indicates default country code should be used
[11384.360037] ath: doing EEPROM country->regdmn map search
[11384.360039] ath: country maps to regdmn code: 0x3a
[11384.360041] ath: Country alpha2 being used: US
[11384.360042] ath: Regpair used: 0x3a
[11384.589212] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11384.591115] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11387.884636] wlan0: authenticate with <MAC address removed>
[11387.971376] wlan0: send auth to <MAC address removed> (try 1/3)
[11388.077291] wlan0: authenticated
[11388.078097] wlan0: associate with <MAC address removed> (try 1/3)
[11388.082347] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11388.087669] wlan0: associated
[11388.087736] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11418.759491] wlan0: authenticate with <MAC address removed>
[11418.849199] wlan0: send auth to <MAC address removed> (try 1/3)
[11418.851013] wlan0: authenticated
[11418.851961] wlan0: associate with <MAC address removed> (try 1/3)
[11418.857023] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11418.861976] wlan0: associated
[11477.575277] wlan0: authenticate with <MAC address removed>
[11477.663056] wlan0: send auth to <MAC address removed> (try 1/3)
[11477.665034] wlan0: authenticated
[11477.668379] wlan0: associate with <MAC address removed> (try 1/3)
[11477.672406] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11477.677396] wlan0: associated
[11574.534315] wlan0: authenticate with <MAC address removed>
[11574.687465] wlan0: send auth to <MAC address removed> (try 1/3)
[11574.704672] wlan0: authenticated
[11574.707395] wlan0: associate with <MAC address removed> (try 1/3)
[11574.711838] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11574.716959] wlan0: associated
[11954.375823] wlan0: authenticate with <MAC address removed>
[11954.461537] wlan0: send auth to <MAC address removed> (try 1/3)
[11954.464127] wlan0: authenticated
[11954.464724] wlan0: associate with <MAC address removed> (try 1/3)
[11954.468776] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[11954.474497] wlan0: associated
[12251.154123] wlan0: authenticate with <MAC address removed>
[12251.242559] wlan0: send auth to <MAC address removed> (try 1/3)
[12251.245539] wlan0: authenticated
[12251.248652] wlan0: associate with <MAC address removed> (try 1/3)
[12251.290893] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[12251.296211] wlan0: associated
[12289.161543] wlan0: authenticate with <MAC address removed>
[12289.250439] wlan0: send auth to <MAC address removed> (try 1/3)
[12289.258155] wlan0: send auth to <MAC address removed> (try 2/3)
[12289.264480] wlan0: send auth to <MAC address removed> (try 3/3)
[12289.269676] wlan0: authentication with <MAC address removed> timed out
[12291.511411] wlan0: authenticate with <MAC address removed>
[12291.597561] wlan0: send auth to <MAC address removed> (try 1/3)
[12291.599249] wlan0: authenticated
[12291.599995] wlan0: associate with <MAC address removed> (try 1/3)
[12291.604137] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[12291.610556] wlan0: associated
[13265.278106] wlan0: authenticate with <MAC address removed>
[13265.369412] wlan0: send auth to <MAC address removed> (try 1/3)
[13265.375235] wlan0: authenticated
[13265.376992] wlan0: associate with <MAC address removed> (try 1/3)
[13265.381155] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[13265.386498] wlan0: associated
[13579.480042] wlan0: authenticate with <MAC address removed>
[13579.566833] wlan0: send auth to <MAC address removed> (try 1/3)
[13579.568723] wlan0: authenticated
[13579.571917] wlan0: associate with <MAC address removed> (try 1/3)
[13579.576166] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[13579.581264] wlan0: associated
[13721.437978] wlan0: authenticate with <MAC address removed>
[13721.526911] wlan0: send auth to <MAC address removed> (try 1/3)
[13721.612214] wlan0: send auth to <MAC address removed> (try 2/3)
[13721.614455] wlan0: authenticated
[13721.615090] wlan0: associate with <MAC address removed> (try 1/3)
[13721.619315] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[13721.624544] wlan0: associated
[14232.473368] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[14233.769572] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[14234.118029] ath: EEPROM regdomain: 0x0
[14234.118034] ath: EEPROM indicates default country code should be used
[14234.118035] ath: doing EEPROM country->regdmn map search
[14234.118037] ath: country maps to regdmn code: 0x3a
[14234.118039] ath: Country alpha2 being used: US
[14234.118040] ath: Regpair used: 0x3a
[14234.520048] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14234.521957] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[14237.952432] wlan0: authenticate with <MAC address removed>
[14238.065090] wlan0: send auth to <MAC address removed> (try 1/3)
[14238.066904] wlan0: authenticated
[14238.070728] wlan0: associate with <MAC address removed> (try 1/3)
[14238.074660] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14238.079834] wlan0: associated
[14238.079872] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[14238.125034] wlan0: deauthenticating from <MAC address removed> by local choice (reason=2)
[14238.215549] wlan0: authenticate with <MAC address removed>
[14238.303258] wlan0: send auth to <MAC address removed> (try 1/3)
[14238.371840] wlan0: authenticated
[14238.374261] wlan0: associate with <MAC address removed> (try 1/3)
[14238.378554] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14238.383337] wlan0: associated
[14349.092256] wlan0: authenticate with <MAC address removed>
[14349.259949] wlan0: send auth to <MAC address removed> (try 1/3)
[14349.358378] wlan0: authenticated
[14349.358968] wlan0: associate with <MAC address removed> (try 1/3)
[14349.363123] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14349.368089] wlan0: associated
[14385.026417] wlan0: authenticate with <MAC address removed>
[14385.115314] wlan0: send auth to <MAC address removed> (try 1/3)
[14385.152527] wlan0: authenticated
[14385.156512] wlan0: associate with <MAC address removed> (try 1/3)
[14385.160608] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14385.165603] wlan0: associated
[14416.049313] wlan0: authenticate with <MAC address removed>
[14416.136297] wlan0: send auth to <MAC address removed> (try 1/3)
[14416.188709] wlan0: send auth to <MAC address removed> (try 2/3)
[14416.194189] wlan0: send auth to <MAC address removed> (try 3/3)
[14416.199410] wlan0: authentication with <MAC address removed> timed out
[14418.430806] wlan0: authenticate with <MAC address removed>
[14418.516748] wlan0: send auth to <MAC address removed> (try 1/3)
[14418.518532] wlan0: authenticated
[14418.519559] wlan0: associate with <MAC address removed> (try 1/3)
[14418.523539] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14418.530280] wlan0: associated
[14445.123593] wlan0: authenticate with <MAC address removed>
[14445.223829] wlan0: send auth to <MAC address removed> (try 1/3)
[14445.225593] wlan0: authenticated
[14445.229770] wlan0: associate with <MAC address removed> (try 1/3)
[14445.238169] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14445.243201] wlan0: associated
[14493.957308] wlan0: authenticate with <MAC address removed>
[14494.043511] wlan0: send auth to <MAC address removed> (try 1/3)
[14494.082768] wlan0: authenticated
[14494.084774] wlan0: associate with <MAC address removed> (try 1/3)
[14494.131257] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14494.138506] wlan0: associated
[14718.842585] wlan0: authenticate with <MAC address removed>
[14718.931950] wlan0: send auth to <MAC address removed> (try 1/3)
[14718.933836] wlan0: authenticated
[14718.937501] wlan0: associate with <MAC address removed> (try 1/3)
[14718.947629] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[14718.952483] wlan0: associated
[19576.566231] wlan0: authenticate with <MAC address removed>
[19576.655249] wlan0: send auth to <MAC address removed> (try 1/3)
[19576.659864] wlan0: authenticated
[19576.663888] wlan0: associate with <MAC address removed> (try 1/3)
[19576.668055] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[19576.673090] wlan0: associated
[21338.464451] wlan0: authenticate with <MAC address removed>
[21338.561481] wlan0: send auth to <MAC address removed> (try 1/3)
[21338.580738] wlan0: send auth to <MAC address removed> (try 2/3)
[21338.590889] wlan0: send auth to <MAC address removed> (try 3/3)
[21338.611823] wlan0: authenticated
[21338.612878] wlan0: associate with <MAC address removed> (try 1/3)
[21338.617099] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21338.622265] wlan0: associated
[21355.510537] wlan0: authenticate with <MAC address removed>
[21355.595769] wlan0: send auth to <MAC address removed> (try 1/3)
[21355.597634] wlan0: authenticated
[21355.600183] wlan0: associate with <MAC address removed> (try 1/3)
[21355.604249] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21355.609370] wlan0: associated
[21383.557951] wlan0: authenticate with <MAC address removed>
[21383.643359] wlan0: send auth to <MAC address removed> (try 1/3)
[21383.645002] wlan0: authenticated
[21383.649821] wlan0: associate with <MAC address removed> (try 1/3)
[21383.657535] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21383.662800] wlan0: associated
[21495.074211] wlan0: authenticate with <MAC address removed>
[21495.159322] wlan0: send auth to <MAC address removed> (try 1/3)
[21495.164001] wlan0: send auth to <MAC address removed> (try 2/3)
[21495.171925] wlan0: send auth to <MAC address removed> (try 3/3)
[21495.175397] wlan0: authentication with <MAC address removed> timed out
[21497.386484] wlan0: authenticate with <MAC address removed>
[21497.472260] wlan0: send auth to <MAC address removed> (try 1/3)
[21497.475630] wlan0: send auth to <MAC address removed> (try 2/3)
[21497.483479] wlan0: send auth to <MAC address removed> (try 3/3)
[21497.485374] wlan0: authenticated
[21497.487467] wlan0: associate with <MAC address removed> (try 1/3)
[21497.491487] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21497.496051] wlan0: associated
[21630.322986] wlan0: authenticate with <MAC address removed>
[21630.416883] wlan0: send auth to <MAC address removed> (try 1/3)
[21630.419701] wlan0: authenticated
[21630.423363] wlan0: associate with <MAC address removed> (try 1/3)
[21630.429371] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21630.433984] wlan0: associated
[21790.260486] wlan0: authenticate with <MAC address removed>
[21790.348520] wlan0: send auth to <MAC address removed> (try 1/3)
[21790.352289] wlan0: authenticated
[21790.353378] wlan0: associate with <MAC address removed> (try 1/3)
[21790.357506] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21790.362522] wlan0: associated
[21903.206388] wlan0: authenticate with <MAC address removed>
[21903.303862] wlan0: send auth to <MAC address removed> (try 1/3)
[21903.384402] wlan0: send auth to <MAC address removed> (try 2/3)
[21903.435707] wlan0: authenticated
[21903.439493] wlan0: associate with <MAC address removed> (try 1/3)
[21903.563433] wlan0: associate with <MAC address removed> (try 2/3)
[21903.568688] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21903.574009] wlan0: associated
[21993.215219] wlan0: authenticate with <MAC address removed>
[21993.302099] wlan0: send auth to <MAC address removed> (try 1/3)
[21993.305441] wlan0: authenticated
[21993.309346] wlan0: associate with <MAC address removed> (try 1/3)
[21993.315602] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[21993.319851] wlan0: associated
[22301.942330] wlan0: authenticate with <MAC address removed>
[22302.028135] wlan0: send auth to <MAC address removed> (try 1/3)
[22302.033006] wlan0: authenticated
[22302.035160] wlan0: associate with <MAC address removed> (try 1/3)
[22302.041543] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[22302.046614] wlan0: associated
[22348.125781] wlan0: authenticate with <MAC address removed>
[22348.226079] wlan0: send auth to <MAC address removed> (try 1/3)
[22348.227871] wlan0: authenticated
[22348.231463] wlan0: associate with <MAC address removed> (try 1/3)
[22348.240749] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[22348.245198] wlan0: associated
[22484.638778] wlan0: authenticate with <MAC address removed>
[22484.739068] wlan0: send auth to <MAC address removed> (try 1/3)
[22484.740939] wlan0: authenticated
[22484.741564] wlan0: associate with <MAC address removed> (try 1/3)
[22484.746902] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[22484.751372] wlan0: associated
[22591.787989] wlan0: authenticate with <MAC address removed>
[22591.873956] wlan0: send auth to <MAC address removed> (try 1/3)
[22591.978625] wlan0: send auth to <MAC address removed> (try 2/3)
[22591.980575] wlan0: authenticated
[22591.982554] wlan0: associate with <MAC address removed> (try 1/3)
[22591.986659] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[22591.991759] wlan0: associated
[22625.842533] wlan0: authenticate with <MAC address removed>
[22625.931812] wlan0: send auth to <MAC address removed> (try 1/3)
[22625.933725] wlan0: authenticated
[22625.937134] wlan0: associate with <MAC address removed> (try 1/3)
[22625.946115] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[22625.951220] wlan0: associated
[22634.988800] wlan0: deauthenticated from <MAC address removed> (Reason: 2)
[22636.815557] wlan0: authenticate with <MAC address removed>
[22636.903395] wlan0: send auth to <MAC address removed> (try 1/3)
[22636.905146] wlan0: authenticated
[22636.907534] wlan0: associate with <MAC address removed> (try 1/3)
[22636.913427] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[22636.918347] wlan0: associated
[22762.341565] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[30673.113291] usb 2-1.2: firmware upload failed (-22).
[30675.677674] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[30676.031919] ath: EEPROM regdomain: 0x0
[30676.031922] ath: EEPROM indicates default country code should be used
[30676.031923] ath: doing EEPROM country->regdmn map search
[30676.031925] ath: country maps to regdmn code: 0x3a
[30676.031926] ath: Country alpha2 being used: US
[30676.031927] ath: Regpair used: 0x3a
[30676.252653] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[30676.254861] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[42623.953214] wlan0: authenticate with <MAC address removed>
[42624.038488] wlan0: send auth to <MAC address removed> (try 1/3)
[42624.042148] wlan0: authenticated
[42624.044043] wlan0: associate with <MAC address removed> (try 1/3)
[42624.048226] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[42624.053111] wlan0: associated
[42624.053179] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[44740.165340] wlan0: authenticate with <MAC address removed>
[44740.258028] wlan0: send auth to <MAC address removed> (try 1/3)
[44740.260443] wlan0: authenticated
[44740.263418] wlan0: associate with <MAC address removed> (try 1/3)
[44740.267593] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[44740.272551] wlan0: associated
[44890.160404] wlan0: authenticate with <MAC address removed>
[44890.248929] wlan0: send auth to <MAC address removed> (try 1/3)
[44890.350521] wlan0: send auth to <MAC address removed> (try 2/3)
[44890.357973] wlan0: send auth to <MAC address removed> (try 3/3)
[44890.361938] wlan0: authentication with <MAC address removed> timed out
[44899.215451] wlan0: authenticate with <MAC address removed>
[44899.301983] wlan0: send auth to <MAC address removed> (try 1/3)
[44899.405864] wlan0: send auth to <MAC address removed> (try 2/3)
[44899.509850] wlan0: send auth to <MAC address removed> (try 3/3)
[44899.515405] wlan0: authentication with <MAC address removed> timed out
[44902.242729] wlan0: authenticate with <MAC address removed>
[44902.333034] wlan0: send auth to <MAC address removed> (try 1/3)
[44902.334775] wlan0: authenticated
[44902.336389] wlan0: associate with <MAC address removed> (try 1/3)
[44902.340425] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[44902.345474] wlan0: associated
[45209.959745] wlan0: authenticate with <MAC address removed>
[45210.044939] wlan0: send auth to <MAC address removed> (try 1/3)
[45210.050335] wlan0: authenticated
[45210.050658] wlan0: associate with <MAC address removed> (try 1/3)
[45210.054955] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[45210.059547] wlan0: associated
[45654.460130] wlan0: authenticate with <MAC address removed>
[45654.547833] wlan0: send auth to <MAC address removed> (try 1/3)
[45654.549710] wlan0: authenticated
[45654.550892] wlan0: associate with <MAC address removed> (try 1/3)
[45654.554852] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[45654.560691] wlan0: associated
[46552.049891] wlan0: authenticate with <MAC address removed>
[46552.136029] wlan0: send auth to <MAC address removed> (try 1/3)
[46552.137789] wlan0: authenticated
[46552.138956] wlan0: associate with <MAC address removed> (try 1/3)
[46552.143046] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[46552.148140] wlan0: associated
[47403.439271] wlan0: authenticate with <MAC address removed>
[47403.529787] wlan0: send auth to <MAC address removed> (try 1/3)
[47403.537104] wlan0: send auth to <MAC address removed> (try 2/3)
[47403.543658] wlan0: authenticated
[47403.546520] wlan0: associate with <MAC address removed> (try 1/3)
[47403.565627] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[47403.570620] wlan0: associated
[47646.368151] usb 2-1.2: firmware upload failed (-22).
[47647.389666] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47648.970695] usb 2-1.2: firmware API: 1.9.6 2012-07-07
[47649.320700] ath: EEPROM regdomain: 0x0
[47649.320703] ath: EEPROM indicates default country code should be used
[47649.320704] ath: doing EEPROM country->regdmn map search
[47649.320706] ath: country maps to regdmn code: 0x3a
[47649.320707] ath: Country alpha2 being used: US
[47649.320708] ath: Regpair used: 0x3a
[47649.545705] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[47649.548839] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[47651.235843] wlan0: authenticate with <MAC address removed>
[47651.330812] wlan0: send auth to <MAC address removed> (try 1/3)
[47651.335150] wlan0: authenticated
[47651.335482] wlan0: associate with <MAC address removed> (try 1/3)
[47651.341019] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[47651.346006] wlan0: associated
[47651.346038] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[47725.399900] wlan0: disassociated from <MAC address removed> (Reason: 8)
[47725.524479] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47727.235718] wlan0: authenticate with <MAC address removed>
[47727.323076] wlan0: send auth to <MAC address removed> (try 1/3)
[47727.326847] wlan0: send auth to <MAC address removed> (try 2/3)
[47727.330362] wlan0: send auth to <MAC address removed> (try 3/3)
[47727.333704] wlan0: authentication with <MAC address removed> timed out
[47741.512360] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[47769.760251] wlan0: authenticate with <MAC address removed>
[47769.847258] wlan0: send auth to <MAC address removed> (try 1/3)
[47769.851055] wlan0: authenticated
[47769.852286] wlan0: associate with <MAC address removed> (try 1/3)
[47769.856727] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=1)
[47769.861951] wlan0: associated
[47769.862011] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############



```

---

### Post by varunendra on 2014-06-15
I'm a bit skeptical about these errors -
> **papa.jinzu said:**
> ```

[47403.570620] wlan0: associated
[47646.368151] usb 2-1.2: **[COLOR="#FF0000"]firmware upload failed[/COLOR]** (-22).
[47647.389666] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[47648.970695] usb 2-1.2: firmware API: 1.9.6 2012-07-07

```
..but as long as the adapter is working, I can't point my finger on it with confidence.

But there is another question - Why can't/don't you use the native pci wireless card when it seems supported -
```
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak] [8086:008a] (rev 1a)
	Subsystem: Intel Corporation Device [8086:0000]
```
Although the device ID of its subsystem is also suspicious (0000), and I'm also mystified at why the expected driver "iwlwifi" isn't loading for that card.

Are you aware that your notebook has an inbuilt wireless card? Is it broken? If not, or if unsure, please try -
```
sudo modprobe -v iwlwifi
```
..and see if it jumps to life.

If for whatever reasons you can't use the inbuilt card, and the usb one is the only option, please try what may be my yet another 'last' shot -
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall linux-firmware
```
..reboot, and let me know that it improved nothing, so that I can keep quite now. :|

---

### Post by papa.jinzu on 2014-06-15
> **varunendra said:**
> 

But there is another question - Why can't/don't you use the native pci wireless card when it seems supported -

Are you aware that your notebook has an inbuilt wireless card? Is it broken? If not, or if unsure, please try -
```
sudo modprobe -v iwlwifi
```
..and see if it jumps to life.

If for whatever reasons you can't use the inbuilt card, and the usb one is the only option, please try what may be my yet another 'last' shot -
```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall linux-firmware
```
..reboot, and let me know that it improved nothing, so that I can keep quite now. :|

The pci wifi card does not work for some reason. Not in Kubuntu, nor Windows 7. The status shows up, saying it is installed, but I cannot get it to work.

I tried
```
sudo modprobe -v iwlwifi
```
but it did not work. 

Also it is a replacement pci wifi card. I had to replace the card it came with. Maybe something is just wrong with the computer, I don't know.

Also the adapter seems to be working without disconnects for now. I will repost if it starts disconnecting again. I did the following:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall linux-firmware
```

---

### Post by varunendra on 2014-06-15
I suspect the weird product ID of the wireless subsystem for the disability of internal card. Maybe check BIOS to confirm it is enabled there, and if it is, then reset the BIOS (if it is NOT a UEFI based setup).

> **papa.jinzu said:**
> Also the adapter seems to be working without disconnects for now. I will repost if it starts disconnecting again. I did the following:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install --reinstall linux-firmware
```

If reinstalling the firmware pack got rid of those "**firmware upload failed**" messages from dmesg, there is hope. If they are still occuring, there is almost none. You can check the errors with -
```
dmesg | grep firmware
```
..and hope to see no errors related to firmware, at least not the above one.

---

### Post by papa.jinzu on 2014-06-15
Now, the wireless adapter is disconnecting again. Oh well, at least it works most of the time.

This is what I got from running

```
dmesg | grep firmware
```

```
[    2.214152] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
[   14.781492] usb 2-1.2: firmware API: 1.9.6 2012-07-07

```

Also, I reset the BIOS to default, but the pci wireless card still doesn't work.

---

