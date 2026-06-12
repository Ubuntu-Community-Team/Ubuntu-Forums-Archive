---
title: "nm-applet not showing up + other network issues"
date: 2015-02-02
forum: Networking &amp; Wireless
---

### Post by chawinski on 2015-02-02
Hi all,

I've been having a lot of network issues recently. I'll post details that may be relevant and things I have tried.

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


chawinski-laptop 3.13.0-45-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
Memory : 16025 MB
Uptime : 16:39:29 up 7 min,  3 users,  load average: 1.62, 2.20, 1.17




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop [1043:16d5]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 003: ID 046d:c246 Logitech, Inc. Gaming Mouse G300
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 003: ID 174f:1718 Syntek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: phy0: Wireless LAN             no            no
1: hci0: Bluetooth                no            no
2: asus-wlan: Wireless LAN        no            no
3: asus-bluetooth: Bluetooth      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  1 asus_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: unknown
================o======o========o========o========  =o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o========  =o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------




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


ATC WiFi             : ssid=ATC WiFi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto Liv             : ssid=Liv | ipv4=auto | ipv6=ignore 
Auto uniwide         : ssid=uniwide | permissions=user:chawinski:; 
Auto uniwide_guest   : ssid=uniwide_guest | permissions=user:chawinski:; 
BigPond15E7          : ssid=BigPond15E7 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
BigPond474B          : ssid=BigPond474B | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Elliott Koch's iMac  : ssid=Elliott Koch's iMac | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Full Metal Gremlin   : ssid=Full Metal Gremlin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Glebevt              : ssid=Glebevt | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Le petit tarte cafe  : ssid=Le petit tarte cafe | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Liv                  : ssid=Liv | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
MrFalcons            : ssid=MrFalcons | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NETGEAR60            : ssid=NETGEAR60 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NETGEAR_GCP          : ssid=NETGEAR_GCP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Unwired Free Internet : ssid=Unwired Free Internet | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WellConnected        : ssid=WellConnected | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


auto lo
iface lo inet loopback




resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 129.94.162.96
nameserver 149.171.96.2
nameserver 149.171.56.6
search phys.unsw.edu.au




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         129.94.162.1    0.0.0.0         UG    0      0        0 eth0
129.94.162.0    0.0.0.0         255.255.254.0   U     0      0        0 eth0


--- 129.94.162.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.560/0.562/0.564/0.002 ms


--- 129.94.162.96 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 3.666/4.030/4.395/0.369 ms


--- 149.171.96.2 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.147/0.160/0.173/0.013 ms


--- 149.171.56.6 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1008ms






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




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 eduroam>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dcdba83
                    Extra: Last beacon: 916ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 02 - Address: <MAC C-02 uniwide_guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"uniwide_guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dcd5ba1
                    Extra: Last beacon: 916ms ago
          Cell 03 - Address: <MAC C-03 uniwide>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"uniwide"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dce962a
                    Extra: Last beacon: 892ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 04 - Address: <MAC C-04 uniwide_guest>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"uniwide_guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000767443ee359
                    Extra: Last beacon: 912ms ago
          Cell 05 - Address: <MAC C-05 uniwide>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"uniwide"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000017470b7cb06
                    Extra: Last beacon: 908ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 06 - Address: <MAC C-06 uniwide>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"uniwide"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=00000767443ea822
                    Extra: Last beacon: 904ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 07 - Address: <MAC C-07 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008e7481faed6
                    Extra: Last beacon: 660ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 08 - Address: <MAC C-08 eduroam>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008550afe034
                    Extra: Last beacon: 656ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 09 - Address: <MAC C-09 uniwide>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"uniwide"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be80ac4d5c
                    Extra: Last beacon: 632ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 10 - Address: <MAC C-10 uniwide_guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:off
                    ESSID:"uniwide_guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008e7481f7f3a
                    Extra: Last beacon: 620ms ago
          Cell 11 - Address: <MAC C-11 >
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be80adab28
                    Extra: Last beacon: 620ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 12 - Address: <MAC C-12 eduroam>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000008e75b829822
                    Extra: Last beacon: 612ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 13 - Address: <MAC C-13 KK>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"KK"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000015a2e3758
                    Extra: Last beacon: 556ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dfd2822
                    Extra: Last beacon: 368ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 15 - Address: <MAC C-15 eduroam>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"eduroam"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dfcdc11
                    Extra: Last beacon: 336ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 16 - Address: <MAC C-16 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dfd2822
                    Extra: Last beacon: 356ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 17 - Address: <MAC C-17 uniwide_guest>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"uniwide_guest"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dfc8757
                    Extra: Last beacon: 352ms ago
          Cell 18 - Address: <MAC C-18 uniwide>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"uniwide"
                    Bit Rates:12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s
                              54 Mb/s
                    Mode:Master
                    Extra:tsf=000004be7dfdc97c
                    Extra: Last beacon: 352ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                       Preauthentication Supported
          Cell 19 - Address: <MAC C-19 Daniel Cotton&#8217;s iMac>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Daniel Cotton&#8217;s iMac"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003d7fc13a81f
                    Extra: Last beacon: 304ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[asus_nb_wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video


[wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/acpi/video.ko
srcversion:     FD364E86295EDCA7831C8FB
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


[ath9k]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     94B3813AF84C49B115229AD
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modules]
coretemp
nouveau
nouveau
nouveau
nouveau
nouveau
ath9k
r8169
ath9k


[/etc/rc.local]
echo 0x00050021 > /sys/kernel/debug/asus-nb-wmi/dev_id
echo 0x82 > /sys/kernel/debug/asus-nb-wmi/ctrl_param
cat /sys/kernel/debug/asus-nb-wmi/devs
exit 0


[/etc/modprobe.d]
blacklist.conf    : blacklist evbug
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
                     blacklist vga16fb
                     blacklist rivafb
                     blacklist nvidiafb
                     blacklist rivatv
blacklist.conf~   : blacklist evbug
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
                     blacklist vga16fb
                     blacklist nouveau
                     blacklist rivafb
                     blacklist nvidiafb
                     blacklist rivatv
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
old.blacklist.conf: blacklist evbug
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
                     blacklist vga16fb
                     blacklist nouveau
                     blacklist rivafb
                     blacklist nvidiafb
                     blacklist rivatv
old.nvidia-installer-disable-nouveau.conf: blacklist nouveau
                    options nouveau modeset=0


[/etc/pm/power.d/00-jupiter-cpu] [executable]
#!/bin/bash
# 
# CPU mode change on power state
#


JUPITER_PATH="/usr/lib/jupiter/scripts"
JUPITER_KERNEL="/usr/lib/jupiter/kernel"
JUPITER_HW="/usr/lib/jupiter/vendors"
JUPITER_VAR="/var/jupiter"


DEFAULT_MODE="high"


VENDOR=$(cat /sys/devices/virtual/dmi/id/sys_vendor)


AC_DEVICE=$(ls /sys/class/power_supply | grep "ADP\|AC")
ACPI_AC_PROC=/sys/class/power_supply/$AC_DEVICE/online


function save_ac_state {
  if [ ! -d "$JUPITER_VAR" ]; then
    mkdir $JUPITER_VAR 2>/dev/null
  fi
}


function set_cpu {
    if [ -e "$ACPI_AC_PROC" ]; then
      if [ "$(cat $ACPI_AC_PROC)" = "1" ]; then
        if [ -e "$JUPITER_VAR/power" ]; then
          RESTORE_MODE=$(cat $JUPITER_VAR/power)
        else
          RESTORE_MODE=$DEFAULT_MODE
        fi
        $JUPITER_PATH/cpu-control $RESTORE_MODE
        $JUPITER_KERNEL/power
        if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
          "$JUPITER_HW/$VENDOR/power"
        fi
      else
        if [ -e "$JUPITER_VAR/battery" ]; then
          RESTORE_MODE=$(cat $JUPITER_VAR/battery)
        else
          RESTORE_MODE="powersave"
        fi
        $JUPITER_PATH/cpu-control $RESTORE_MODE
        $JUPITER_KERNEL/battery
        if [ -e "$JUPITER_HW/$VENDOR/battery" ]; then
          "$JUPITER_HW/$VENDOR/battery" 
        fi
      fi
    else
      if [ -e "$JUPITER_VAR/power" ]; then
        RESTORE_MODE=$(cat $JUPITER_VAR/power)
      else
        RESTORE_MODE=$DEFAULT_MODE
      fi
      $JUPITER_PATH/cpu-control $RESTORE_MODE
      $JUPITER_KERNEL/power
      if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
        "$JUPITER_HW/$VENDOR/power"
      fi
    fi
}


case "$1" in
  *) set_cpu
    ;;
esac


[/etc/pm/sleep.d/00-jupiter-restore] [executable]
#!/bin/bash
#
# Jupiter restore settings on resume
#
#


JUPITER_PATH="/usr/lib/jupiter/scripts"
JUPITER_VAR="/var/jupiter"


if [ ! -d "$JUPITER_VAR" ]; then
  mkdir -p $JUPITER_VAR >/dev/null 2>&1 || true
  chown -R root:jupiter $JUPITER_VAR >/dev/null 2>&1 || true
  chmod 775 $JUPITER_VAR >/dev/null 2>&1 || true
  chmod ug+s $JUPITER_VAR >/dev/null 2>&1 || true
  setfacl -Rm g:jupiter:rwX,d:g:jupiter:rwX . >/dev/null 2>&1 || true
fi


case "$1" in
  hibernate|suspend|sleep)
    ;;
  thaw|resume)
    USER=$(who | sed -n '/ (:0[\.0]*)$\| :0 /{s/ .*//p;q}')
    if [ -e "$JUPITER_VAR/bt_saved" ]; then
      sudo $JUPITER_PATH/bluetooth restore 2>/dev/null &
    fi


    if [ -e "$JUPITER_VAR/wifi_saved" ]; then
      sudo $JUPITER_PATH/wifi restore silent 2>/dev/null
    fi


    if [ -e "$JUPITER_VAR/touchpad_saved" ]; then
      su $USER -l -c "DISPLAY=:0.0 $JUPITER_PATH/touchpad restore silent" 2>/dev/null &
    fi


    ;;
  *) exit $NA
    ;;
esac


[/etc/pm/sleep.d/20_custom-ehci_hcd] [executable]
#!/bin/sh
#inspired by http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19
#...and http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug    
# tidied by tqzzaa :)


VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1


unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}


bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}


case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac


Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/vmlinuz-3.13.0-45-generic root=UUID=b2372af5-e96b-4bf9-b4f3-caf0e156be37 ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.553838] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.554275] audit: initializing netlink socket (disabled)
[    1.825795] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   24.880818] ath: phy0: Enable LNA combining
[   24.882413] ath: EEPROM regdomain: 0x60
[   24.882416] ath: EEPROM indicates we should expect a direct regpair map
[   24.882418] ath: Country alpha2 being used: 00
[   24.882420] ath: Regpair used: 0x60
[   25.155314] wmi: Mapper loaded
[   25.302710] asus_wmi: ASUS WMI generic driver loaded
[   25.386392] asus_wmi: Initialization: 0x1
[   25.386422] asus_wmi: BIOS WMI version: 7.6
[   25.386456] asus_wmi: SFUN value: 0xa0877
[   25.386973] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input17
[   25.420702] asus_wmi: Backlight controlled by ACPI video driver
[   52.910731] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   53.490620] init: network-manager main process (1369) killed by SEGV signal
[   53.490630] init: network-manager main process ended, respawning
[   53.499477] init: network-manager main process (1373) killed by SEGV signal
[   53.499487] init: network-manager main process ended, respawning
[   53.507529] init: network-manager main process (1377) killed by SEGV signal
[   53.507540] init: network-manager main process ended, respawning
[   53.516087] init: network-manager main process (1381) killed by SEGV signal
[   53.516098] init: network-manager main process ended, respawning
[   53.525027] init: network-manager main process (1387) killed by SEGV signal
[   53.525038] init: network-manager main process ended, respawning
[   53.534465] init: network-manager main process (1391) killed by SEGV signal
[   53.534476] init: network-manager main process ended, respawning
[   53.543465] init: network-manager main process (1395) killed by SEGV signal
[   53.543475] init: network-manager main process ended, respawning
[   53.552214] init: network-manager main process (1399) killed by SEGV signal
[   53.552224] init: network-manager main process ended, respawning
[   53.560935] init: network-manager main process (1403) killed by SEGV signal
[   53.560946] init: network-manager main process ended, respawning
[   53.569720] init: network-manager main process (1407) killed by SEGV signal
[   53.569734] init: network-manager main process ended, respawning
[   53.578305] init: network-manager main process (1411) killed by SEGV signal
[   53.578315] init: network-manager respawning too fast, stopped
[  126.385156] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready


    ======== Done ========

```

I changed a few things before getting to this state while troubleshooting. Originally when I would boot up my ifconfig showed:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

```

and I could only connect to my university internet service (by ethernet cable) via:

sudo ifconfig eth0 up && sudo dhclient eth0

I edited  /etc/NetworkManager/NetworkManager.conf from:
```

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false

```

to:
```

[main]
plugins=ifupdown,keyfile,
dns=dnsmasq


[ifupdown]
managed=true

```

and /etc/network/interfaces from:

```

auto lo
iface lo inet loopback

```

to:
```

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp

```

which would auto-start my ethernet.

I have re-installed network-manager & network-manager-gnome to no avail. Currently I am tethered to my smartphone (which required "sudo ifconfig usb0 && sudo dhclient usb0") because I have no net access at my new residence.

Errors I encounter:

sudo nm-applet
```

** (nm-applet:11651): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files


(nm-applet:11651): nm-applet-WARNING **: Error connecting to ModemManager: Error calling StartServiceByName for org.freedesktop.ModemManager1: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecF  ailed: Cannot launch daemon, file not found or permissions invalid


(nm-applet:11651): nm-applet-WARNING **: Failed to register as an agent: (2) The name org.freedesktop.NetworkManager was not provided by any .service files
nm-applet-Message: using fallback from indicator to GtkStatusIcon

```

nm-tool
```

** (process:11803): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files


NetworkManager Tool


State: unknown




** (process:11803): WARNING **: error: could not connect to NetworkManager

```

sudo service network-manager restart
```

stop: Unknown instance: 
network-manager start/spawned, process 11924

```

sudo NetworkManager
```

(NetworkManager:12030): GLib-WARNING **: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Key file does not have group 'connectivity'

```

[COLOR=#000000]Also, if I check in 'Network' in 'System Settings' I get the message "The System network services are not compatible with this version."[/COLOR]

Not sure if this should go in the newbie section as i'm pretty lost.

Any help would be much appreciated.

---

### Post by chawinski on 2015-02-14
Bump.

```



    ======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


chawinski-laptop 3.13.0-45-generic x86_64,  Ubuntu 14.04.2 LTS, trusty


CPU    : Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
Memory : 16025 MB
Uptime : 16:41:03 up 3 min,  2 users,  load average: 0.50, 0.77, 0.35




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


03:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. U6V/U31J laptop [1043:16d5]
    Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 003: ID 046d:c246 Logitech, Inc. Gaming Mouse G300
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04e8:6863 Samsung Electronics Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 003: ID 174f:1718 Syntek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface               Soft blocked  Hard blocked
0: phy0: Wireless LAN             no            no
1: asus-wlan: Wireless LAN        no            no
2: asus-bluetooth: Bluetooth      no            no
3: hci0: Bluetooth                no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


asus_nb_wmi            16990  0 
asus_wmi               24191  1 asus_nb_wmi
sparse_keymap          13948  1 asus_wmi
wmi                    19177  1 asus_wmi
video                  19476  1 asus_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630669  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211




module parameters ~~~~~~~~~~~~~~~~~~


asus_nb_wmi   (1): wapf=0
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: unknown
================o======o========o========o========  =o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o========  =o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------




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


ATC WiFi             : ssid=ATC WiFi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Auto Liv             : ssid=Liv | ipv4=auto | ipv6=ignore 
Auto uniwide         : ssid=uniwide | permissions=user:chawinski:; 
Auto uniwide_guest   : ssid=uniwide_guest | permissions=user:chawinski:; 
BigPond15E7          : ssid=BigPond15E7 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
BigPond474B          : ssid=BigPond474B | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Elliott Koch's iMac  : ssid=Elliott Koch's iMac | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Full Metal Gremlin   : ssid=Full Metal Gremlin | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Glebevt              : ssid=Glebevt | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Le petit tarte cafe  : ssid=Le petit tarte cafe | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Liv                  : ssid=Liv | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
MrFalcons            : ssid=MrFalcons | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NETGEAR60            : ssid=NETGEAR60 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
NETGEAR_GCP          : ssid=NETGEAR_GCP | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Unwired Free Internet : ssid=Unwired Free Internet | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
WellConnected        : ssid=WellConnected | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


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




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[asus_nb_wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/asus-nb-wmi.ko
srcversion:     67514DF02FC4A206C47D0F5
depends:        asus-wmi
parm:           wapf:WAPF value (uint)


[asus_wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/asus-wmi.ko
srcversion:     222BD5E26B3EE82CC433FF2
depends:        sparse-keymap,wmi,video


[wmi]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


[video]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/acpi/video.ko
srcversion:     FD364E86295EDCA7831C8FB
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


[ath9k]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     EABAC052C3DF339FA6E716C
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     5ED2DF2BD124A3813829DA8
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     94B3813AF84C49B115229AD
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-45-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/mac80211/mac80211.ko
srcversion:     385697223F8285F67C93A06
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-45-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default


[/etc/modules]
coretemp
nouveau
nouveau
nouveau
nouveau
nouveau
ath9k
r8169
ath9k


[/etc/rc.local]
echo 0x00050021 > /sys/kernel/debug/asus-nb-wmi/dev_id
echo 0x82 > /sys/kernel/debug/asus-nb-wmi/ctrl_param
cat /sys/kernel/debug/asus-nb-wmi/devs
exit 0


[/etc/modprobe.d]
blacklist.conf    : blacklist evbug
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
                     blacklist vga16fb
                     blacklist rivafb
                     blacklist nvidiafb
                     blacklist rivatv
blacklist.conf~   : blacklist evbug
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
                     blacklist vga16fb
                     blacklist nouveau
                     blacklist rivafb
                     blacklist nvidiafb
                     blacklist rivatv
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
old.blacklist.conf: blacklist evbug
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
                     blacklist vga16fb
                     blacklist nouveau
                     blacklist rivafb
                     blacklist nvidiafb
                     blacklist rivatv
old.nvidia-installer-disable-nouveau.conf: blacklist nouveau
                    options nouveau modeset=0


[/etc/pm/power.d/00-jupiter-cpu] [executable]
#!/bin/bash
# 
# CPU mode change on power state
#


JUPITER_PATH="/usr/lib/jupiter/scripts"
JUPITER_KERNEL="/usr/lib/jupiter/kernel"
JUPITER_HW="/usr/lib/jupiter/vendors"
JUPITER_VAR="/var/jupiter"


DEFAULT_MODE="high"


VENDOR=$(cat /sys/devices/virtual/dmi/id/sys_vendor)


AC_DEVICE=$(ls /sys/class/power_supply | grep "ADP\|AC")
ACPI_AC_PROC=/sys/class/power_supply/$AC_DEVICE/online


function save_ac_state {
  if [ ! -d "$JUPITER_VAR" ]; then
    mkdir $JUPITER_VAR 2>/dev/null
  fi
}


function set_cpu {
    if [ -e "$ACPI_AC_PROC" ]; then
      if [ "$(cat $ACPI_AC_PROC)" = "1" ]; then
        if [ -e "$JUPITER_VAR/power" ]; then
          RESTORE_MODE=$(cat $JUPITER_VAR/power)
        else
          RESTORE_MODE=$DEFAULT_MODE
        fi
        $JUPITER_PATH/cpu-control $RESTORE_MODE
        $JUPITER_KERNEL/power
        if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
          "$JUPITER_HW/$VENDOR/power"
        fi
      else
        if [ -e "$JUPITER_VAR/battery" ]; then
          RESTORE_MODE=$(cat $JUPITER_VAR/battery)
        else
          RESTORE_MODE="powersave"
        fi
        $JUPITER_PATH/cpu-control $RESTORE_MODE
        $JUPITER_KERNEL/battery
        if [ -e "$JUPITER_HW/$VENDOR/battery" ]; then
          "$JUPITER_HW/$VENDOR/battery" 
        fi
      fi
    else
      if [ -e "$JUPITER_VAR/power" ]; then
        RESTORE_MODE=$(cat $JUPITER_VAR/power)
      else
        RESTORE_MODE=$DEFAULT_MODE
      fi
      $JUPITER_PATH/cpu-control $RESTORE_MODE
      $JUPITER_KERNEL/power
      if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
        "$JUPITER_HW/$VENDOR/power"
      fi
    fi
}


case "$1" in
  *) set_cpu
    ;;
esac


[/etc/pm/sleep.d/00-jupiter-restore] [executable]
#!/bin/bash
#
# Jupiter restore settings on resume
#
#


JUPITER_PATH="/usr/lib/jupiter/scripts"
JUPITER_VAR="/var/jupiter"


if [ ! -d "$JUPITER_VAR" ]; then
  mkdir -p $JUPITER_VAR >/dev/null 2>&1 || true
  chown -R root:jupiter $JUPITER_VAR >/dev/null 2>&1 || true
  chmod 775 $JUPITER_VAR >/dev/null 2>&1 || true
  chmod ug+s $JUPITER_VAR >/dev/null 2>&1 || true
  setfacl -Rm g:jupiter:rwX,d:g:jupiter:rwX . >/dev/null 2>&1 || true
fi


case "$1" in
  hibernate|suspend|sleep)
    ;;
  thaw|resume)
    USER=$(who | sed -n '/ (:0[\.0]*)$\| :0 /{s/ .*//p;q}')
    if [ -e "$JUPITER_VAR/bt_saved" ]; then
      sudo $JUPITER_PATH/bluetooth restore 2>/dev/null &
    fi


    if [ -e "$JUPITER_VAR/wifi_saved" ]; then
      sudo $JUPITER_PATH/wifi restore silent 2>/dev/null
    fi


    if [ -e "$JUPITER_VAR/touchpad_saved" ]; then
      su $USER -l -c "DISPLAY=:0.0 $JUPITER_PATH/touchpad restore silent" 2>/dev/null &
    fi


    ;;
  *) exit $NA
    ;;
esac


[/etc/pm/sleep.d/20_custom-ehci_hcd] [executable]
#!/bin/sh
#inspired by http://art.ubuntuforums.org/showpost.php?p=9744970&postcount=19
#...and http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug    
# tidied by tqzzaa :)


VERSION=1.1
DEV_LIST=/tmp/usb-dev-list
DRIVERS_DIR=/sys/bus/pci/drivers
DRIVERS="ehci xhci" # ehci_hcd, xhci_hcd
HEX="[[:xdigit:]]"
MAX_BIND_ATTEMPTS=2
BIND_WAIT=0.1


unbindDev() {
  echo -n > $DEV_LIST 2>/dev/null
  for driver in $DRIVERS; do
    DDIR=$DRIVERS_DIR/${driver}_hcd
    for dev in `ls $DDIR 2>/dev/null | egrep "^$HEX+:$HEX+:$HEX"`; do
      echo -n "$dev" > $DDIR/unbind
      echo "$driver $dev" >> $DEV_LIST
    done
  done
}


bindDev() {
  if [ -s $DEV_LIST ]; then
    while read driver dev; do
      DDIR=$DRIVERS_DIR/${driver}_hcd
      while [ $((MAX_BIND_ATTEMPTS)) -gt 0 ]; do
          echo -n "$dev" > $DDIR/bind
          if [ ! -L "$DDIR/$dev" ]; then
            sleep $BIND_WAIT
          else
            break
          fi
          MAX_BIND_ATTEMPTS=$((MAX_BIND_ATTEMPTS-1))
      done  
    done < $DEV_LIST
  fi
  rm $DEV_LIST 2>/dev/null
}


case "$1" in
  hibernate|suspend) unbindDev;;
  resume|thaw)       bindDev;;
esac


Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/vmlinuz-3.13.0-45-generic root=UUID=b2372af5-e96b-4bf9-b4f3-caf0e156be37 ro quiet splash




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.553995] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.554425] audit: initializing netlink socket (disabled)
[    1.827013] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   22.863518] ath: phy0: Enable LNA combining
[   22.865106] ath: EEPROM regdomain: 0x60
[   22.865108] ath: EEPROM indicates we should expect a direct regpair map
[   22.865110] ath: Country alpha2 being used: 00
[   22.865111] ath: Regpair used: 0x60
[   23.489564] wmi: Mapper loaded
[   23.666875] asus_wmi: ASUS WMI generic driver loaded
[   23.742399] asus_wmi: Initialization: 0x1
[   23.742452] asus_wmi: BIOS WMI version: 7.6
[   23.742519] asus_wmi: SFUN value: 0xa0877
[   23.743063] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input15
[   23.782993] asus_wmi: Backlight controlled by ACPI video driver
[   36.046021] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   36.707109] init: network-manager main process (1113) killed by SEGV signal
[   36.707119] init: network-manager main process ended, respawning
[   36.715766] init: network-manager main process (1117) killed by SEGV signal
[   36.715776] init: network-manager main process ended, respawning
[   36.725501] init: network-manager main process (1121) killed by SEGV signal
[   36.725511] init: network-manager main process ended, respawning
[   36.736384] init: network-manager main process (1125) killed by SEGV signal
[   36.736398] init: network-manager main process ended, respawning
[   36.745044] init: network-manager main process (1129) killed by SEGV signal
[   36.745056] init: network-manager main process ended, respawning
[   36.755675] init: network-manager main process (1140) killed by SEGV signal
[   36.755685] init: network-manager main process ended, respawning
[   36.773107] init: network-manager main process (1145) killed by SEGV signal
[   36.773117] init: network-manager main process ended, respawning
[   36.782458] init: network-manager main process (1149) killed by SEGV signal
[   36.782468] init: network-manager main process ended, respawning
[   36.793155] init: network-manager main process (1153) killed by SEGV signal
[   36.793165] init: network-manager main process ended, respawning
[   36.803072] init: network-manager main process (1157) killed by SEGV signal
[   36.803082] init: network-manager main process ended, respawning
[   36.812300] init: network-manager main process (1161) killed by SEGV signal
[   36.812311] init: network-manager respawning too fast, stopped


    ======== Done ========

```

---

