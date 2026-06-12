---
title: "RealTek RTL8187L, Wifi Connects but no internet"
date: 2014-09-04
forum: Networking &amp; Wireless
---

### Post by karim2 on 2014-09-04
Hi there
I have just installed 14.04 LTS, everything seems fine except one thing, internet connectivity through WiFi. 
I have a RealTek RTL8187L, it's a USB wireless adapter which I have always used conveniently under Windows and also under several WiFi audit Live CD Linux such as Beini and Xiaopan. 
I have connected through Ethernet with no problem, internet worked fine, but when I connect through WiFi the connection is established and I get a valid IP address but internet is out, no page would load.
 > karim@Linux-Asus:~$ ifconfig -a
eth3      Link encap:Ethernet  HWaddr 28:ff:87:26:02:00  
          inet6 addr: fe80::2aff:87ff:fe26:200/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:91441 errors:0 dropped:0 overruns:0 frame:0
          TX packets:71356 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000 
          RX bytes:118768427 (118.7 MB)  TX bytes:7704394 (7.7 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2289 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228127 (228.1 KB)  TX bytes:228127 (228.1 KB)


mon.wlan0 Link encap:UNSPEC  HWaddr 1C-4B-D6-99-61-64-3A-30-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64648 (64.6 KB)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr 1c:4b:d6:99:61:64  
          inet addr:192.168.150.1  Bcast:192.168.150.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5976 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:744730 (744.7 KB)  TX bytes:7922679 (7.9 MB)


[B][COLOR=#b22222]wlan1     Link encap:Ethernet  HWaddr 00:87:32:3a:1f:61  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::287:32ff:fe3a:1f61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9909 (9.9 KB)  TX bytes:26597 (26.5 KB)[/COLOR][/B]


karim@Linux-Asus:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1
192.168.150.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0
karim@Linux-Asus:~$ ping -c3 91.189.94.12
PING 91.189.94.12 (91.189.94.12) 56(84) bytes of data.


--- 91.189.94.12 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms


karim@Linux-Asus:~$ ping -c3 ubuntuforums.org

---

### Post by varunendra on 2014-09-04
Welcome to the forums Karim!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by karim2 on 2014-09-04
Thank you for your quick reply. I have generated this report while connected with the card I'm having trouble with (RTL8187).

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


Linux-Asus 3.13.0-35-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM)2 Duo CPU     T8300  @ 2.40GHz
Memory : 3918 MB
Uptime : 05:57:12 up  2:48,  1 user,  load average: 0.87, 0.36, 0.28




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
	Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:14f5]
	Kernel driver in use: ATL1E




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 006: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 002 Device 002: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


mon.wlan0  IEEE 802.11bgn  Mode:Monitor  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:"Allah Is Great"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 Allah Is Great>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0


wlan0     IEEE 802.11bgn  Mode:Master  Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          




rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface             Soft blocked  Hard blocked
0: asus-wwan: Wireless WAN      no            no
1: asus-wimax: WiMAX            no            no
2: phy0: Wireless LAN           no            no
5: phy3: Wireless LAN           no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8187                64909  0 
eeprom_93cx6           13344  1 rtl8187
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  2 ath9k,rtl8187
cfg80211              484040  4 ath,ath9k,mac80211,rtl8187




module parameters ~~~~~~~~~~~~~~~~~~


ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
=========================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID          | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
=========================o=============o=========o==============o=========o===========o==============o===========
 wlan1  [Allah Is Great] | 802.11 WiFi | rtl8187 | connected    | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan1>


    TNCAPA38AB8:     Infra, <MAC C-04 TNCAPA38AB8>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    DLink:           Infra, <MAC C-02 DLink>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA
    TNCAP2753FA:     Infra, <MAC C-NA TNCAP2753FA 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 60 WPA WPA2
    Thomson573D38:   Infra, <MAC C-03 Thomson573D38>, Freq 2412 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    *Allah Is Great: Infra, <MAC C-01 Allah Is Great>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA
    PROGFID_TOTAL_2013: Infra, <MAC C-NA PROGFID_TOTAL_2013 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 62 WPA WPA2
    SAGEM_9D70:      Infra, <MAC C-NA SAGEM_9D70 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA


    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
-------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 eth3                    | Wired       | ATL1E   | disconnected | no      | 100 Mb/s  |              | <MAC eth3>
-------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0                   | 802.11 WiFi | ath9k   | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>
-------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------




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


nameserver 127.0.1.1
search Home




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan1
192.168.150.0   0.0.0.0         255.255.255.0   U     0      0        0 wlan0


--- 192.168.1.1 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2010ms
rtt min/avg/max/mdev = 2.508/7.372/12.236/4.864 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.053/0.056/0.060/0.008 ms




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_GB.UTF-8")
country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


mon.wlan0  14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


          wlan1     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


          Current Frequency:2.437 GHz (Channel 6)
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan1     Scan completed :
          Cell 01 - Address: <MAC C-01 Allah Is Great>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"Allah Is Great"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010240b27f1
                    Extra: Last beacon: 260ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 DLink>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"DLink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000004f518b620
                    Extra: Last beacon: 3988ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Thomson573D38>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"Thomson573D38"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ce0a3a680
                    Extra: Last beacon: 6368ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 TNCAPA38AB8>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"TNCAPA38AB8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000b8fb637316
                    Extra: Last beacon: 2096ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


wlan0     No scan results




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8187]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
srcversion:     A707FEC6B464A70F7A04C69
depends:        mac80211,eeprom_93cx6,cfg80211


[eeprom_93cx6]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/misc/eeprom/eeprom_93cx6.ko
version:        1.0
srcversion:     215D8C1284A3C33B4A5A1C5
depends:        


[ath9k]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     DF02272C2FA4678C49046E5
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)


[ath9k_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw


[ath9k_hw]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath


[ath]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211


[mac80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/mac80211/mac80211.ko
srcversion:     D491AB7C521706DA5F4BE7C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.13.0-35-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:0x002b (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (rtl8187)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth2>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"


# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth3>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/rc.local]
service wifi_access_point stop
exit 0


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=f4f46b76-c884-4783-a420-6055f4defd32 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.532058] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.532354] audit: initializing netlink socket (disabled)
[    1.810766] psmouse serio4: elantech: assuming hardware version 2 (with firmware version 0x040101)
[    9.192142] systemd-udevd[395]: renamed network interface eth0 to eth3
[   10.680885] ath: phy0: Enable LNA combining
[   10.682416] ath: EEPROM regdomain: 0x60
[   10.682418] ath: EEPROM indicates we should expect a direct regpair map
[   10.682420] ath: Country alpha2 being used: 00
[   10.682422] ath: Regpair used: 0x60
[   12.359496] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.776095] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.777142] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.779232] ATL1E 0000:03:00.0 eth3: NIC Link is Up <100 Mbps Full Duplex>
[   24.681909] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.430268] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[   25.809676] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.809927] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.811986] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[   25.812318] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[   25.812480] ATL1E 0000:03:00.0 eth3: NIC Link is Up <100 Mbps Full Duplex>
[   25.812495] IPv6: ADDRCONF(NETDEV_CHANGE): eth3: link becomes ready
[ 1941.364309] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1941.369470] ath: phy0: TX while HW is in FULL_SLEEP mode
[ 1941.448146] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5708.076138] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6605.802096] ATL1E 0000:03:00.0 eth3: NIC Link is Down
[ 6617.898570] ieee80211 phy1: hwaddr <MAC wlan1>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 6617.915863] rtl8187: Customer ID is 0x00
[ 6617.917413] rtl8187: wireless switch is on
[ 6620.209422] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6620.210250] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 6623.937193] wlan1: authenticate with <MAC C-01 Allah Is Great>
[ 6624.171285] wlan1: send auth to <MAC C-01 Allah Is Great> (try 1/3)
[ 6624.175409] wlan1: authenticated
[ 6624.175770] rtl8187 2-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[ 6624.175779] rtl8187 2-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 6624.175784] rtl8187 2-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[ 6624.176474] wlan1: associate with <MAC C-01 Allah Is Great> (try 1/3)
[ 6624.179886] wlan1: RX AssocResp from <MAC C-01 Allah Is Great> (capab=0x411 status=0 aid=1)
[ 6624.180604] wlan1: associated
[ 6624.180643] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 6633.236793] wlan1: deauthenticating from <MAC C-01 Allah Is Great> by local choice (reason=2)
[ 6633.300940] wlan1: authenticate with <MAC C-01 Allah Is Great>
[ 6633.359573] wlan1: send auth to <MAC C-01 Allah Is Great> (try 1/3)
[ 6633.364076] wlan1: authenticated
[ 6633.364486] rtl8187 2-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[ 6633.364495] rtl8187 2-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 6633.364500] rtl8187 2-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[ 6633.368094] wlan1: associate with <MAC C-01 Allah Is Great> (try 1/3)
[ 6633.373376] wlan1: RX AssocResp from <MAC C-01 Allah Is Great> (capab=0x411 status=0 aid=1)
[ 6633.374878] wlan1: associated
[ 6784.396087] wlan1: deauthenticating from <MAC C-01 Allah Is Great> by local choice (reason=3)
[ 6813.374191] ATL1E 0000:03:00.0 eth3: NIC Link is Up <100 Mbps Full Duplex>
[ 7469.335314] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7469.364257] ath: phy0: TX while HW is in FULL_SLEEP mode
[ 7469.403774] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8796.925488] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8802.236704] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8802.244118] ath: phy0: TX while HW is in FULL_SLEEP mode
[ 8802.274277] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9198.815814] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 9343.149314] ieee80211 phy2: hwaddr <MAC wlan1>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[ 9343.170838] rtl8187: Customer ID is 0x00
[ 9343.171848] rtl8187: wireless switch is on
[ 9345.629504] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 9345.630507] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 9349.445656] wlan1: authenticate with <MAC C-01 Allah Is Great>
[ 9349.691252] wlan1: send auth to <MAC C-01 Allah Is Great> (try 1/3)
[ 9349.694495] wlan1: authenticated
[ 9349.694939] rtl8187 2-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[ 9349.694948] rtl8187 2-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 9349.694954] rtl8187 2-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[ 9349.696593] wlan1: associate with <MAC C-01 Allah Is Great> (try 1/3)
[ 9349.700854] wlan1: RX AssocResp from <MAC C-01 Allah Is Great> (capab=0x411 status=0 aid=1)
[ 9349.702218] wlan1: associated
[ 9349.702285] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 9349.755266] wlan1: deauthenticating from <MAC C-01 Allah Is Great> by local choice (reason=2)
[ 9349.821405] wlan1: authenticate with <MAC C-01 Allah Is Great>
[ 9349.879145] wlan1: send auth to <MAC C-01 Allah Is Great> (try 1/3)
[ 9349.881440] wlan1: authenticated
[ 9349.882354] rtl8187 2-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[ 9349.882361] rtl8187 2-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 9349.882365] rtl8187 2-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[ 9349.884692] wlan1: associate with <MAC C-01 Allah Is Great> (try 1/3)
[ 9349.891477] wlan1: RX AssocResp from <MAC C-01 Allah Is Great> (capab=0x411 status=0 aid=1)
[ 9349.892643] wlan1: associated
[ 9359.272226] wlan1: deauthenticating from <MAC C-01 Allah Is Great> by local choice (reason=3)
[ 9372.085068] wlan1: authenticate with <MAC C-01 Allah Is Great>
[ 9372.267250] wlan1: send auth to <MAC C-01 Allah Is Great> (try 1/3)
[ 9372.271631] wlan1: authenticated
[ 9372.272084] rtl8187 2-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[ 9372.272093] rtl8187 2-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[ 9372.272099] rtl8187 2-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[ 9372.276051] wlan1: associate with <MAC C-01 Allah Is Great> (try 1/3)
[ 9372.282946] wlan1: RX AssocResp from <MAC C-01 Allah Is Great> (capab=0x411 status=0 aid=1)
[ 9372.283810] wlan1: associated
[ 9463.736273] wlan1: deauthenticating from <MAC C-01 Allah Is Great> by local choice (reason=3)
[10014.390559] ieee80211 phy3: hwaddr <MAC wlan1>, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[10014.412044] rtl8187: Customer ID is 0x00
[10014.413016] rtl8187: wireless switch is on
[10016.821388] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[10016.822339] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[10018.688644] wlan1: authenticate with <MAC C-01 Allah Is Great>
[10018.902078] wlan1: send auth to <MAC C-01 Allah Is Great> (try 1/3)
[10018.906153] wlan1: authenticated
[10018.906409] rtl8187 2-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[10018.906415] rtl8187 2-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[10018.906419] rtl8187 2-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[10018.912382] wlan1: associate with <MAC C-01 Allah Is Great> (try 1/3)
[10018.915513] wlan1: RX AssocResp from <MAC C-01 Allah Is Great> (capab=0x411 status=0 aid=1)
[10018.916632] wlan1: associated
[10018.916977] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[10056.457841] wlan1: deauthenticating from <MAC C-01 Allah Is Great> by local choice (reason=3)
[10058.349393] wlan1: authenticate with <MAC C-01 Allah Is Great>
[10058.531213] wlan1: send auth to <MAC C-01 Allah Is Great> (try 1/3)
[10058.533860] wlan1: authenticated
[10058.535804] rtl8187 2-3:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[10058.535813] rtl8187 2-3:1.0 wlan1: disabling HT as WMM/QoS is not supported by the AP
[10058.535819] rtl8187 2-3:1.0 wlan1: disabling VHT as WMM/QoS is not supported by the AP
[10058.536540] wlan1: associate with <MAC C-01 Allah Is Great> (try 1/3)
[10058.539287] wlan1: RX AssocResp from <MAC C-01 Allah Is Great> (capab=0x411 status=0 aid=1)
[10058.540530] wlan1: associated


	======== Done ========

```

---

### Post by varunendra on 2014-09-04
Two questions -

1) Why aren't you using your internal Atheros wifi card?
2) What are you using this computer, especially its networking for? I'm asking this because your udev rules file looks like a mess, which, unless a valid reason exists, I would suggest to delete to let a fresh, clean one be generated.

Two suggestions, for now -

1) Please change the encryption in your router to WPA2-PSK with AES (CCMP) if it supports that. Currently it is using WPA which requires TKIP, and TKIP may be a problem sometimes. Reboot the router after saving the change.

2) If the above alone doesn't solve the issue, please try explicitly setting your country code for RegDomain settings -
```
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
sudo iw reg set GB
```
..assuming you are in UK. If not, please refer to this table to find out correct country code and replace "GB" with it : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

Just try these, and post back the result with answers to the questions I asked first. The internal card should be good enough (even better) for most of wireless requirements.

---

### Post by karim2 on 2014-09-04
Thanks again. 
Asking your question first. I believe the reason behind that mess is because I have installed a WiFi sharing software which creates a virtual access point, so I use the Atheros as an access point and I share the Ethernet's internet with the aforementioned card. 
Returning to the problem. I never got the RealTek to get an active internet connection even before installing that virtual AP software ([SIZE=2][COLOR=#333333][FONT=TertreExtraBold]AP-Hotspot[/FONT][/COLOR][/SIZE]), you might have a look at what I have done here [http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html](http://www.webupd8.org/2013/06/how-to-set-up-wireless-hotspot-access.html) 
My router doesn't have any advanced wireless security settings, it only has WEP/WPA encryptions, and it actually performs remarkably with every network card including the USB RealTek under both Windows and Tiny Core Linux such as Xiaopan and BEINI, so there is no doubt that there is a problem at the router's end nor the RealTek, but Ubuntu.
By the way I don't live in GB, I live in Morocco and I believe it has generic Europeans norms 
And the reason why I use the RealTek over the more capable Atheros (wlan0) is because the RealTek has a signal booster because it's a USB adapter, while the integrated Atheros doesn't detect any distant APs including mine, which the RealTek does effortlessly.

---

### Post by karim2 on 2014-09-04
I have just tested the code you gave me with no success, after having replaced GB with MA.

---

### Post by karim2 on 2014-09-04
Please help guys. I have just tested the same card in Backtrack 5 r3 and the same problem occurred because they share the same driver, I'm now sure that it's a driver issue, how can I use another driver, probably an older one.

---

