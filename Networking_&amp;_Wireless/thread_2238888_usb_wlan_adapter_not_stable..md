---
title: "usb wlan adapter not stable."
date: 2014-08-10
forum: Networking &amp; Wireless
---

### Post by sti.que.c.pas.faci on 2014-08-10
ok, I got a PC in my garage with a rtl8188cus usb to wifi adapter attached to it running ubuntu 14.04 which is located at 40 to 50 ft. from my router (crossing 2 walls). _**Running winXP it won't even see my network.But running ubuntu it shows 2 out of 4 bars**_ and connects at 150mb/s and I get speeds up to 1500 to 2000 kb/s so I guest it's a strong connection and XP driver just isn't as good as the linux one?

Here's my problem. Here and there, the connection seems to drop (or sleep) randomly. It show as its connected but in fact I got no internet and no local network either. The status bar still is at 2 out of 4 bar but no network. I need to unplug - re-plug my rtl8188cus adapter or disable - enable wi-fi in setting. The network comes to life again and It can be good for 10min to 1 hour. it's never the same.

should I look for a poor connection dropping due to the distance or just the adapter becoming dead ? I don't know where to start.

help would be appreciated here. thanks!

P.S. my android phone stay connected in the same area without issue.
P.P.S I tried an android tablet with the same wifi adapter in the same area and no issue either.

---

### Post by varunendra on 2014-08-12
To provide a detailed report about your overall wireless setup, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by sti.que.c.pas.faci on 2014-08-14
> **varunendra said:**
> To provide a detailed report about your overall wireless setup, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

here it is when working:
```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


pc2 3.13.0-24-generic i686,  Linux Mint 17 Qiana, qiana


CPU    : Intel(R) Pentium(R) D CPU 3.20GHz
Memory : 2013 MB
Uptime : 22:09:21 up 1 min,  2 users,  load average: 2.28, 0.78, 0.28




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell OptiPlex GX620 [1028:01ad]
	Kernel driver in use: tg3




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"dlink5445"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 dlink5445>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8192cu              66675  0 
rtl_usb                18072  1 rtl8192cu
rtlwifi                52835  2 rtl_usb,rtl8192cu
rtl8192c_common        47340  1 rtl8192cu
mac80211              545990  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              409394  2 mac80211,rtlwifi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192cu     (2): debug=0 | swenc=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
====================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
====================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [dlink5445] | 802.11 WiFi | rtl8192cu | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    *dlink5445:      Infra, <MAC C-01 dlink5445>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2


    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0               | Wired       | tg3       | unavailable | no      |           |              | <MAC eth0>
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


dlink5445            : ssid=dlink5445 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search Belkin




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 7.418/8.036/8.654/0.618 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.036/0.038/0.040/0.002 ms




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


          Current Frequency=2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 dlink5445>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"dlink5445"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c11c6b9ffe
                    Extra: Last beacon: 232ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8192cu]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
srcversion:     7CF9B14C5E7812D872691FA
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
srcversion:     CE332F200EA30B201483F4F
depends:        rtlwifi,mac80211


[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211


[rtl8192c_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        


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


# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=607cc82d-62be-4b26-929d-23b231b228dc ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.280156] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.280611] audit: initializing netlink socket (disabled)
[    5.943998] tg3 0000:02:00.0 eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   15.616666] intel_rng: don't want to disable this in firmware setup, and if
[   16.154259] rtl8192cu: Chip version 0x10
[   16.247630] rtl8192cu: MAC address: <MAC wlan0>
[   16.247639] rtl8192cu: Board Type 0
[   16.247859] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   16.247906] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   16.536813] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.537489] rtlwifi: wireless switch is on
[   17.653651] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.565737] rtl8192cu: MAC auto ON okay!
[   19.599003] rtl8192cu: Tx queue select: 0x05
[   19.967254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.969094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.518771] wlan0: authenticate with <MAC C-01 dlink5445>
[   21.530833] wlan0: send auth to <MAC C-01 dlink5445> (try 1/3)
[   21.537516] wlan0: authenticated
[   21.540029] wlan0: associate with <MAC C-01 dlink5445> (try 1/3)
[   21.605894] wlan0: RX AssocResp from <MAC C-01 dlink5445> (capab=0x411 status=0 aid=6)
[   21.605944] wlan0: associated
[   21.606008] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


	======== Done ========
```

here it is when I get no network

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


pc2 3.13.0-24-generic i686,  Linux Mint 17 Qiana, qiana


CPU    : Intel(R) Pentium(R) D CPU 3.20GHz
Memory : 2013 MB
Uptime : 22:12:44 up 4 min,  2 users,  load average: 0.40, 0.65, 0.33




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell OptiPlex GX620 [1028:01ad]
	Kernel driver in use: tg3




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 004: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"dlink5445"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 dlink5445>   
          Bit Rate=15 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8192cu              66675  0 
rtl_usb                18072  1 rtl8192cu
rtlwifi                52835  2 rtl_usb,rtl8192cu
rtl8192c_common        47340  1 rtl8192cu
mac80211              545990  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              409394  2 mac80211,rtlwifi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192cu     (2): debug=0 | swenc=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
====================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
====================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [dlink5445] | 802.11 WiFi | rtl8192cu | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    *dlink5445:      Infra, <MAC C-01 dlink5445>, Freq 2437 MHz, Rate 54 Mb/s, Strength 52 WPA2


    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0               | Wired       | tg3       | unavailable | no      |           |              | <MAC eth0>
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


dlink5445            : ssid=dlink5445 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search Belkin




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.2.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3022ms




--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.040/0.047/0.055/0.010 ms




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


          Current Frequency=2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 dlink5445>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"dlink5445"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c12874cec0
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8192cu]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
srcversion:     7CF9B14C5E7812D872691FA
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
srcversion:     CE332F200EA30B201483F4F
depends:        rtlwifi,mac80211


[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211


[rtl8192c_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        


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


# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=607cc82d-62be-4b26-929d-23b231b228dc ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.280156] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.280611] audit: initializing netlink socket (disabled)
[    5.943998] tg3 0000:02:00.0 eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   15.616666] intel_rng: don't want to disable this in firmware setup, and if
[   16.154259] rtl8192cu: Chip version 0x10
[   16.247630] rtl8192cu: MAC address: <MAC wlan0>
[   16.247639] rtl8192cu: Board Type 0
[   16.247859] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   16.247906] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   16.536813] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.537489] rtlwifi: wireless switch is on
[   17.653651] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.565737] rtl8192cu: MAC auto ON okay!
[   19.599003] rtl8192cu: Tx queue select: 0x05
[   19.967254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.969094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.518771] wlan0: authenticate with <MAC C-01 dlink5445>
[   21.530833] wlan0: send auth to <MAC C-01 dlink5445> (try 1/3)
[   21.537516] wlan0: authenticated
[   21.540029] wlan0: associate with <MAC C-01 dlink5445> (try 1/3)
[   21.605894] wlan0: RX AssocResp from <MAC C-01 dlink5445> (capab=0x411 status=0 aid=6)
[   21.605944] wlan0: associated
[   21.606008] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


	======== Done ========
```

then again, I unplug / plug nmy adapter and it's working again

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


pc2 3.13.0-24-generic i686,  Linux Mint 17 Qiana, qiana


CPU    : Intel(R) Pentium(R) D CPU 3.20GHz
Memory : 2013 MB
Uptime : 22:14:46 up 6 min,  2 users,  load average: 1.66, 0.98, 0.48




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
	Subsystem: Dell OptiPlex GX620 [1028:01ad]
	Kernel driver in use: tg3




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     IEEE 802.11bgn  ESSID:"dlink5445"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 dlink5445>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface        Soft blocked  Hard blocked
1: phy1: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


rtl8192cu              66675  0 
rtl_usb                18072  1 rtl8192cu
rtlwifi                52835  2 rtl_usb,rtl8192cu
rtl8192c_common        47340  1 rtl8192cu
mac80211              545990  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              409394  2 mac80211,rtlwifi




module parameters ~~~~~~~~~~~~~~~~~~


cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192cu     (2): debug=0 | swenc=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
====================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID     | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
====================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [dlink5445] | 802.11 WiFi | rtl8192cu | connected   | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>


    *dlink5445:      Infra, <MAC C-01 dlink5445>, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 WPA2


    Address:         192.168.2.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0               | Wired       | tg3       | unavailable | no      |           |              | <MAC eth0>
--------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------




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


dlink5445            : ssid=dlink5445 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search Belkin




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0


--- 192.168.2.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.397/1.397/1.397/0.000 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.037/0.039/0.041/0.002 ms




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


          Current Frequency=2.437 GHz (Channel 6)




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 dlink5445>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"dlink5445"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001c12f94f467
                    Extra: Last beacon: 172ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[rtl8192cu]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8192cufw.bin
srcversion:     7CF9B14C5E7812D872691FA
depends:        rtlwifi,rtl8192c-common,rtl_usb,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           debug:Set debug level (0-5) (default 0) (int)


[rtl_usb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_usb.ko
srcversion:     CE332F200EA30B201483F4F
depends:        rtlwifi,mac80211


[rtlwifi]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211


[rtl8192c_common]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        


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


# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rtl8192cu)
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


BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=607cc82d-62be-4b26-929d-23b231b228dc ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    1.280156] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.280611] audit: initializing netlink socket (disabled)
[    5.943998] tg3 0000:02:00.0 eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   15.616666] intel_rng: don't want to disable this in firmware setup, and if
[   16.154259] rtl8192cu: Chip version 0x10
[   16.247630] rtl8192cu: MAC address: <MAC wlan0>
[   16.247639] rtl8192cu: Board Type 0
[   16.247859] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   16.247906] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   16.536813] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.537489] rtlwifi: wireless switch is on
[   17.653651] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.565737] rtl8192cu: MAC auto ON okay!
[   19.599003] rtl8192cu: Tx queue select: 0x05
[   19.967254] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.969094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.518771] wlan0: authenticate with <MAC C-01 dlink5445>
[   21.530833] wlan0: send auth to <MAC C-01 dlink5445> (try 1/3)
[   21.537516] wlan0: authenticated
[   21.540029] wlan0: associate with <MAC C-01 dlink5445> (try 1/3)
[   21.605894] wlan0: RX AssocResp from <MAC C-01 dlink5445> (capab=0x411 status=0 aid=6)
[   21.605944] wlan0: associated
[   21.606008] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  371.401036] wlan0: deauthenticating from <MAC C-01 dlink5445> by local choice (reason=3)
[  371.401343] rtl_usb: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x50087
[  371.401361] rtl_usb: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x5
[  371.401368] rtl_usb: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x180000
[  371.401376] rtl_usb: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd38000
[  373.742540] rtl8192cu: Chip version 0x10
[  373.824540] rtl8192cu: MAC address: <MAC wlan0>
[  373.824550] rtl8192cu: Board Type 0
[  373.824782] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  373.824837] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[  373.825183] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  373.826037] rtlwifi: wireless switch is on
[  373.882036] rtl8192cu: MAC auto ON okay!
[  373.918175] rtl8192cu: Tx queue select: 0x05
[  374.286263] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  374.287424] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  375.800627] wlan0: authenticate with <MAC C-01 dlink5445>
[  375.826041] wlan0: send auth to <MAC C-01 dlink5445> (try 1/3)
[  375.833127] wlan0: authenticated
[  375.836089] wlan0: associate with <MAC C-01 dlink5445> (try 1/3)
[  375.857748] wlan0: RX AssocResp from <MAC C-01 dlink5445> (capab=0x411 status=0 aid=6)
[  375.857816] wlan0: associated
[  375.857888] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  375.888579] wlan0: deauthenticating from <MAC C-01 dlink5445> by local choice (reason=2)
[  375.904661] wlan0: authenticate with <MAC C-01 dlink5445>
[  375.916793] wlan0: send auth to <MAC C-01 dlink5445> (try 1/3)
[  375.920086] wlan0: authenticated
[  375.924067] wlan0: associate with <MAC C-01 dlink5445> (try 1/3)
[  375.936730] wlan0: RX AssocResp from <MAC C-01 dlink5445> (capab=0x411 status=0 aid=6)
[  375.936802] wlan0: associated


	======== Done ========
```

---

### Post by varunendra on 2014-08-15
The signal strength is indeed a bit weak for a fast connection, you could blame it to the adapter since it is problematic with XP too.

As an attempt to optimize the connection quality, please try a driver parameter -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=1
```
The first command will remove the driver thus disabling it, the second one will reload it with the parameter 'swenc=1', which is supposed to help in case the card's own processor is unable to keep up with the high speed of data traffic.

This will be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent. If it doesn't, please try a patched driver suggested here : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

**PS:**
Since you don't seem to be using IPv6, I suggest setting it to "Ignore" in Network Manager (under IPv6 Settings tab > Method), and see if it helps stability.

---

### Post by sti.que.c.pas.faci on 2014-08-15
> **varunendra said:**
> The signal strength is indeed a bit weak for a fast connection, you could blame it to the adapter since it is problematic with XP too.

As an attempt to optimize the connection quality, please try a driver parameter -
```
sudo modprobe -rv rtl8192cu
sudo modprobe -v rtl8192cu swenc=1
```
The first command will remove the driver thus disabling it, the second one will reload it with the parameter 'swenc=1', which is supposed to help in case the card's own processor is unable to keep up with the high speed of data traffic.

This will be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent. If it doesn't, please try a patched driver suggested here : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

**PS:**
Since you don't seem to be using IPv6, I suggest setting it to "Ignore" in Network Manager (under IPv6 Settings tab > Method), and see if it helps stability.


Ok tried both solution and the first one didn't help me . in fact it was worst.

but 2nd solution (driver fix) did it. 1hour and a half streaming from youtube without any drop..

thanks.. 
I will try on a longer period but I think you can count this as solved.


thank you very much.

---

### Post by varunendra on 2014-08-15
That's an awesome report! :)
> **sti.que.c.pas.faci said:**
> I will try on a longer period but I think you can [COLOR="#0000CD"]count[/COLOR] this as solved.
If it is, I would like to '[COLOR="#0000CD"]see[/COLOR]' it as [SOLVED] :p, which you could do using the "Thread Tools" link above the top post.

---

