---
title: "No connection/ reconnect problem in ubuntu 14.04"
date: 2014-05-22
forum: Networking &amp; Wireless
---

### Post by rschanzenbacher on 2014-05-22
Whenever i try to connect to my WiFi network after about 3 minutes it asks for the password again in an infinite process. Is there any way i can fix this? I'm using a fresh install of Ubuntu 14.04LTS i686. I cant plugin an Ethernet cable to my computer because i have no wires for it and i don't wanna move my computer. i can download files from my windows installation. ;) Any help would be appreciated. (NOTE: Sometimes it connects for some reason but after reboot it doesn't again. I feel somethings up with the 4-way handshake process. I have WPA2 auth.)

---

### Post by varunendra on 2014-05-27
Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by rschanzenbacher on 2014-06-17
Sorry it took so long it woldnt connect but i got it. here's the output code:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ryan-ubuntu-gaming 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
Memory : 3007 MB
Uptime : 18:49:03 up 14 min,  2 users,  load average: 0.57, 0.26, 0.23


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express [14e4:169b] (rev 02)
    Subsystem: Dell Device [1028:0220]
    Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 005: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 004: ID 045e:076f Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              626489  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192cu     (2): debug=0 | swenc=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
================o=============o===========o==============o=========o===========o==============o===========
 wlan0          | 802.11 WiFi | rtl8192cu | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Home:            Infra, <MAC C-01 Home>, Freq 2432 MHz, Rate 54 Mb/s, Strength 70 WPA WPA2
----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0           | Wired       | tg3       | unavailable  | no      |           |              | <MAC eth0>
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

Home                 : ssid=Home | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


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

wlan0     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Home>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"Home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000033609894d
                    Extra: Last beacon: 36ms ago
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

# PCI device 0x14e4:0x169b (tg3)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=dfe97c94-ed5a-4cd8-a6d6-77a2fe088511 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.852436] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.852822] audit: initializing netlink socket (disabled)
[    1.107904] tg3 0000:02:00.0 eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    6.200374] intel_rng: don't want to disable this in firmware setup, and if
[    6.794414] wmi: Mapper loaded
[    7.816933] rtl8192cu: Chip version 0x10
[    7.919552] rtl8192cu: MAC address: <MAC wlan0>
[    7.919557] rtl8192cu: Board Type 0
[    7.919798] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    7.919839] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[    8.145360] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    8.146552] rtlwifi: wireless switch is on
[    8.227916] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.453805] rtl8192cu: MAC auto ON okay!
[   12.486560] rtl8192cu: Tx queue select: 0x05
[   12.849504] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.849984] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.615335] wlan0: authenticate with <MAC C-01 Home>
[   14.627991] wlan0: direct probe to <MAC C-01 Home> (try 1/3)
[   14.832027] wlan0: send auth to <MAC C-01 Home> (try 2/3)
[   14.834089] wlan0: authenticated
[   14.836050] wlan0: associate with <MAC C-01 Home> (try 1/3)
[   14.884095] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[   14.884138] wlan0: associated
[   14.884520] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   15.102871] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[   18.926088] wlan0: deauthenticated from <MAC C-01 Home> (Reason: 2)
[   19.756590] wlan0: authenticate with <MAC C-01 Home>
[   19.780394] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[   19.884040] wlan0: send auth to <MAC C-01 Home> (try 2/3)
[   19.937071] wlan0: authenticated
[   19.940059] wlan0: associate with <MAC C-01 Home> (try 1/3)
[   20.040092] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[   20.040140] wlan0: associated
[   20.325242] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[   61.202843] wlan0: deauthenticating from <MAC C-01 Home> by local choice (reason=3)
[   98.552465] wlan0: authenticate with <MAC C-01 Home>
[   98.576321] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[   98.616741] wlan0: authenticated
[   98.620031] wlan0: associate with <MAC C-01 Home> (try 1/3)
[   98.683504] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[   98.683551] wlan0: associated
[   98.865666] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[  101.685900] wlan0: deauthenticated from <MAC C-01 Home> (Reason: 2)
[  105.612462] wlan0: authenticate with <MAC C-01 Home>
[  105.636575] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[  105.740081] wlan0: send auth to <MAC C-01 Home> (try 2/3)
[  105.744035] wlan0: authenticated
[  105.748098] wlan0: associate with <MAC C-01 Home> (try 1/3)
[  105.786878] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[  105.786916] wlan0: associated
[  106.136057] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[  153.206067] wlan0: deauthenticating from <MAC C-01 Home> by local choice (reason=3)
[  385.308480] wlan0: authenticate with <MAC C-01 Home>
[  385.332376] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[  385.436024] wlan0: send auth to <MAC C-01 Home> (try 2/3)
[  385.527816] wlan0: authenticated
[  385.532023] wlan0: associate with <MAC C-01 Home> (try 1/3)
[  385.636016] wlan0: associate with <MAC C-01 Home> (try 2/3)
[  385.739565] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[  385.739610] wlan0: associated
[  385.788956] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[  405.634321] wlan0: deauthenticated from <MAC C-01 Home> (Reason: 2)
[  406.468494] wlan0: authenticate with <MAC C-01 Home>
[  406.492632] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[  406.495814] wlan0: authenticated
[  406.496046] wlan0: associate with <MAC C-01 Home> (try 1/3)
[  406.500683] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[  406.500717] wlan0: associated
[  406.576104] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[  409.503080] wlan0: deauthenticated from <MAC C-01 Home> (Reason: 2)
[  421.360480] wlan0: authenticate with <MAC C-01 Home>
[  421.384388] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[  421.447586] wlan0: authenticated
[  421.448023] wlan0: associate with <MAC C-01 Home> (try 1/3)
[  421.552015] wlan0: associate with <MAC C-01 Home> (try 2/3)
[  421.559458] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[  421.559504] wlan0: associated
[  421.731229] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[  423.560963] wlan0: deauthenticated from <MAC C-01 Home> (Reason: 2)
[  425.763513] wlan0: authenticate with <MAC C-01 Home>
[  425.776021] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[  425.791702] wlan0: authenticated
[  425.796055] wlan0: associate with <MAC C-01 Home> (try 1/3)
[  425.840600] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[  425.840649] wlan0: associated
[  426.134366] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[  428.836086] wlan0: deauthenticated from <MAC C-01 Home> (Reason: 2)
[  431.408508] wlan0: authenticate with <MAC C-01 Home>
[  431.432523] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[  431.536024] wlan0: send auth to <MAC C-01 Home> (try 2/3)
[  431.640017] wlan0: send auth to <MAC C-01 Home> (try 3/3)
[  431.744020] wlan0: authentication with <MAC C-01 Home> timed out
[  442.464485] wlan0: authenticate with <MAC C-01 Home>
[  442.488288] wlan0: send auth to <MAC C-01 Home> (try 1/3)
[  442.592028] wlan0: send auth to <MAC C-01 Home> (try 2/3)
[  442.639705] wlan0: authenticated
[  442.640018] wlan0: associate with <MAC C-01 Home> (try 1/3)
[  442.744021] wlan0: associate with <MAC C-01 Home> (try 2/3)
[  442.795605] wlan0: RX AssocResp from <MAC C-01 Home> (capab=0x431 status=0 aid=1)
[  442.795652] wlan0: associated
[  443.030371] wlan0: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-01 Home>
[  444.794630] wlan0: deauthenticated from <MAC C-01 Home> (Reason: 2)
[  446.808681] wlan0: authenticate with <MAC C-01 Home>

    ======== Done ========
```

Also now it connects just it takes quite a few tries and gets annoying... HELP!!! PLEASE!

Any recommended drivers to use?

---

### Post by varunendra on 2014-06-18
Try a patched driver suggested here : [http://ubuntuforums.org/showpost.php?p=13026049](http://ubuntuforums.org/showpost.php?p=13026049)

Additionally, change the encryption type in the router/access-point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode which is not recommended. Also try channels 1 or 11 instead of 'Auto' or 5 which is currently in use. Reboot the router after saving the changes.

If these don't help, please post back a fresh report of the wireless_script with the above changes applied.

---

### Post by rschanzenbacher on 2014-06-18
That made it worse (the settings) would connect then disconnect after 30 seconds or so...

Is there a way I can get the driver on my windows install then compile on ubuntu?

Code:
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ryan-ubuntu-gaming 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
Memory : 3007 MB
Uptime : 15:58:16 up 13 min,  1 user,  load average: 1.22, 0.55, 0.29


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express [14e4:169b] (rev 02)
    Subsystem: Dell Device [1028:0220]
    Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 005: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 004: ID 045e:076f Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rtl8192cu              67723  0 
rtl_usb                18448  1 rtl8192cu
rtlwifi                63475  2 rtl_usb,rtl8192cu
rtl8192c_common        53172  1 rtl8192cu
mac80211              626489  3 rtl_usb,rtlwifi,rtl8192cu
cfg80211              484040  2 mac80211,rtlwifi
mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192cu     (2): debug=0 | swenc=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connecting
=================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID  | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
=================o=============o===========o==============o=========o===========o==============o===========
 wlan1  [Home 1] | 802.11 WiFi | rtl8192cu | connecting (getting IP configuration)| no      |           | WEP/WPA/WPA2 | <MAC wlan1>

    Home:            Infra, <MAC C-NA Home 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 77 WPA2
-----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 eth0            | Wired       | tg3       | unavailable  | no      |           |              | <MAC eth0>
-----------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

wlan1     11 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


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

# PCI device 0x14e4:0x169b (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=dfe97c94-ed5a-4cd8-a6d6-77a2fe088511 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.848481] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.848867] audit: initializing netlink socket (disabled)
[    1.094182] tg3 0000:02:00.0 eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   10.687389] intel_rng: don't want to disable this in firmware setup, and if
[   10.695619] wmi: Mapper loaded
[   11.189609] rtl8192cu: Chip version 0x10
[   11.601154] rtl8192cu: MAC address: <MAC wlan1>
[   11.601159] rtl8192cu: Board Type 0
[   11.601399] rtl_usb: rx_max_size 15360, rx_urb_num 8, in_ep 1
[   11.601439] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw_TMSC.bin
[   11.776348] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.778280] rtlwifi: wireless switch is on
[   11.828330] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.024138] systemd-udevd[322]: renamed network interface wlan0 to wlan1
[   13.031155] rtl8192cu: MAC auto ON okay!
[   13.063794] rtl8192cu: Tx queue select: 0x05
[   13.425846] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   13.426302] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   90.024461] wlan1: authenticate with <MAC C-NA Home 1>
[   90.053780] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[   90.059349] wlan1: authenticated
[   90.059560] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[   90.060025] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[   90.076352] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[   90.076399] wlan1: associated
[   90.076448] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   90.158999] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[   91.710452] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  116.292843] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  152.464604] wlan1: authenticate with <MAC C-NA Home 1>
[  152.477079] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  152.542628] wlan1: authenticated
[  152.542842] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  152.544026] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  152.562511] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  152.562554] wlan1: associated
[  152.562600] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  152.622656] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  171.685329] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  187.251299] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  243.102044] rtl8192cu: MAC auto ON okay!
[  243.134681] rtl8192cu: Tx queue select: 0x05
[  243.496650] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  244.964455] wlan1: authenticate with <MAC C-NA Home 1>
[  244.977751] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  244.982188] wlan1: authenticated
[  244.982344] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  244.984068] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  244.991569] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  244.991624] wlan1: associated
[  244.991637] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  245.018377] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=2)
[  245.030550] wlan1: authenticate with <MAC C-NA Home 1>
[  245.042627] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  245.068209] wlan1: authenticated
[  245.068507] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  245.072041] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  245.084320] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  245.084364] wlan1: associated
[  245.089339] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  251.656369] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  267.238428] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  429.029466] rtl8192cu: MAC auto ON okay!
[  429.062073] rtl8192cu: Tx queue select: 0x05
[  429.423531] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  430.880577] wlan1: authenticate with <MAC C-NA Home 1>
[  430.894387] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  430.914077] wlan1: authenticated
[  430.914270] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  430.916023] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  430.928065] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  430.928105] wlan1: associated
[  430.928148] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  430.945720] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  430.961682] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=2)
[  430.974660] wlan1: authenticate with <MAC C-NA Home 1>
[  430.986888] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  430.994339] wlan1: authenticated
[  430.994612] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  430.996061] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  431.007089] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  431.007127] wlan1: associated
[  431.048091] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  431.781255] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  476.206409] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  492.516499] wlan1: authenticate with <MAC C-NA Home 1>
[  492.529053] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  492.544494] wlan1: authenticated
[  492.544705] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  492.548057] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  492.553228] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  492.553268] wlan1: associated
[  492.553313] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  492.590144] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  511.756462] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  527.244328] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  538.258835] rtl8192cu: MAC auto ON okay!
[  538.291478] rtl8192cu: Tx queue select: 0x05
[  538.657277] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  540.108477] wlan1: authenticate with <MAC C-NA Home 1>
[  540.121546] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  540.127104] wlan1: authenticated
[  540.127299] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  540.128135] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  540.152001] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  540.152142] wlan1: associated
[  540.152157] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  540.179674] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=2)
[  540.191798] wlan1: authenticate with <MAC C-NA Home 1>
[  540.203919] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  540.239744] wlan1: authenticated
[  540.239986] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  540.240094] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  540.260749] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  540.260798] wlan1: associated
[  540.310801] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  543.774480] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  544.600669] wlan1: authenticate with <MAC C-NA Home 1>
[  544.613163] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  544.628483] wlan1: authenticated
[  544.628683] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  544.632025] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  544.655356] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  544.655397] wlan1: associated
[  544.656369] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  545.492489] wlan1: authenticate with <MAC C-NA Home 1>
[  545.505294] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  545.528102] wlan1: authenticated
[  545.528292] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  545.532019] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  545.548854] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  545.548904] wlan1: associated
[  545.550611] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  546.384510] wlan1: authenticate with <MAC C-NA Home 1>
[  546.397169] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  546.406224] wlan1: authenticated
[  546.406374] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  546.408026] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  546.416101] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  546.416136] wlan1: associated
[  546.417284] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  558.680464] wlan1: authenticate with <MAC C-NA Home 1>
[  558.693450] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  558.708892] wlan1: authenticated
[  558.709067] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  558.712072] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  558.723888] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  558.723941] wlan1: associated
[  558.724887] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  562.035071] wlan1: authenticate with <MAC C-NA Home 1>
[  562.047454] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  562.050905] wlan1: authenticated
[  562.051060] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  562.052029] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  562.055277] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  562.055313] wlan1: associated
[  562.060110] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  574.308501] wlan1: authenticate with <MAC C-NA Home 1>
[  574.321334] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  574.361648] wlan1: authenticated
[  574.361855] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  574.364021] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  574.386161] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  574.386204] wlan1: associated
[  574.387319] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  583.880750] wlan1: authenticate with <MAC C-NA Home 1>
[  583.898334] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  583.901422] wlan1: authenticated
[  583.901589] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  583.904150] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  583.914675] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  583.914715] wlan1: associated
[  583.919238] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  589.895766] rtl8192cu: MAC auto ON okay!
[  589.933533] rtl8192cu: Tx queue select: 0x05
[  590.300376] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  591.752464] wlan1: authenticate with <MAC C-NA Home 1>
[  591.766859] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  591.768912] wlan1: authenticated
[  591.769072] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  591.772026] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  591.775280] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  591.775317] wlan1: associated
[  591.775358] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  591.776568] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  591.805190] wlan1: authenticate with <MAC C-NA Home 1>
[  591.817229] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  591.841051] wlan1: authenticated
[  591.841442] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  591.844025] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  591.847294] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  591.847335] wlan1: associated
[  591.848409] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  592.672463] wlan1: authenticate with <MAC C-NA Home 1>
[  592.685104] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  592.687168] wlan1: authenticated
[  592.687516] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  592.688569] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  592.691782] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  592.691818] wlan1: associated
[  592.692909] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  593.520450] wlan1: authenticate with <MAC C-NA Home 1>
[  593.533216] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  593.535290] wlan1: authenticated
[  593.535447] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  593.536063] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  593.584793] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  593.584839] wlan1: associated
[  593.586009] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  605.832534] wlan1: authenticate with <MAC C-NA Home 1>
[  605.845355] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  605.873177] wlan1: authenticated
[  605.873378] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  605.876034] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  605.879294] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  605.879333] wlan1: associated
[  605.952325] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  606.105986] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  622.524641] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  644.086301] rtl8192cu: MAC auto ON okay!
[  644.118937] rtl8192cu: Tx queue select: 0x05
[  644.484169] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  645.956463] wlan1: authenticate with <MAC C-NA Home 1>
[  645.969637] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  645.997197] wlan1: authenticated
[  645.997392] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  646.000027] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  646.004191] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  646.004232] wlan1: associated
[  646.004274] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  646.093983] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  646.097175] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=2)
[  646.109356] wlan1: authenticate with <MAC C-NA Home 1>
[  646.121382] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  646.123449] wlan1: authenticated
[  646.123589] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  646.124022] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  646.128095] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  646.128137] wlan1: associated
[  646.289924] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  691.205968] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  705.808461] rtl8192cu: MAC auto ON okay!
[  705.842109] rtl8192cu: Tx queue select: 0x05
[  706.206569] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  707.660455] wlan1: authenticate with <MAC C-NA Home 1>
[  707.674155] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  707.694623] wlan1: authenticated
[  707.694837] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  707.696066] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  707.706605] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  707.706659] wlan1: associated
[  707.706672] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  707.735598] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=2)
[  707.753221] wlan1: authenticate with <MAC C-NA Home 1>
[  707.765537] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  707.767910] wlan1: authenticated
[  707.768049] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  707.772024] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  707.787746] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=2)
[  707.787785] wlan1: associated
[  707.839136] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  711.208608] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  711.228109] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)
[  753.203464] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  771.944450] wlan1: authenticate with <MAC C-NA Home 1>
[  771.957347] wlan1: send auth to <MAC C-NA Home 1> (try 1/3)
[  771.986261] wlan1: authenticated
[  771.986411] rtl8192cu 1-7:1.0 wlan1: disabling HT/VHT due to WEP/TKIP use
[  771.988024] wlan1: associate with <MAC C-NA Home 1> (try 1/3)
[  772.002895] wlan1: RX AssocResp from <MAC C-NA Home 1> (capab=0x431 status=0 aid=1)
[  772.002948] wlan1: associated
[  772.002960] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  772.043679] wlan1: Limiting TX power to 27 (27 - 0) dBm as advertised by <MAC C-NA Home 1>
[  772.147145] wlan1: deauthenticated from <MAC C-NA Home 1> (Reason: 14)
[  772.160113] wlan1: deauthenticating from <MAC C-NA Home 1> by local choice (reason=14)

    ======== Done ========


```

---

### Post by varunendra on 2014-06-19
> **rschanzenbacher said:**
> Is there a way I can get the driver on my windows install then compile on ubuntu?

Yup, download the driver as a zip package, which is provided on its github page : [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes)
Direct download link for the zip package, in case you can't locate it on the page : [https://github.com/pvaret/rtl8192cu-fixes/archive/master.zip](https://github.com/pvaret/rtl8192cu-fixes/archive/master.zip)

Extract the contents in your home directory and proceed with the "sudo dkms add.." command in the guide post I linked to (assuming the name of the extracted directory would be "rtl8192cu-fixes").

---

### Post by rschanzenbacher on 2014-06-19
Hey again! I got a wired connect to ubuntu for now... :D but anyway i installed the driver and now it will not even detect the wifi. Any more suggestions?
Wireless script:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ryan-ubuntu-gaming 3.13.0-29-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
Memory : 3007 MB
Uptime : 16:02:09 up 3 min,  1 user,  load average: 0.30, 0.26, 0.11


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787 Gigabit Ethernet PCI Express [14e4:169b] (rev 02)
    Subsystem: Dell Device [1028:0220]
    Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 006: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 001 Device 004: ID 045e:076f Microsoft Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mxm_wmi                13021  1 nouveau
wmi                    19177  2 mxm_wmi,nouveau


module parameters ~~~~~~~~~~~~~~~~~~

wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o========o==============o=========o===========o==============o===========
 Interface & ID | Type  | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=======o========o==============o=========o===========o==============o===========
 eth0           | Wired | tg3    | unavailable  | no      |           |              | <MAC eth0>
----------------+-------+--------+--------------+---------+-----------+--------------+-----------


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
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

No way to aquire root rights found.


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-native-rtl8192.conf]
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x169b (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-29-generic root=UUID=dfe97c94-ed5a-4cd8-a6d6-77a2fe088511 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.858930] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.859308] audit: initializing netlink socket (disabled)
[    1.106431] tg3 0000:02:00.0 eth0: attached PHY is 5787 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   11.354374] intel_rng: don't want to disable this in firmware setup, and if
[   12.372788] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.467922] wmi: Mapper loaded

    ======== Done ========
```

Yeah... Not much

Image:

[http://postimg.org/image/hun4h5z3h/](http://postimg.org/image/hun4h5z3h/)

At least I can play my technic pack for now! :KS

---

### Post by varunendra on 2014-06-20
Was the installation successful? Any error messages? And did you reboot after installation?

What is the output of -
```
modinfo 8192cu
```??

From the above report, it looks like the installed driver didn't load (not installed properly, or some other issue), and the native one didn't load because it is blacklisted. So currently there are no drivers to drive the card.

---

### Post by rschanzenbacher on 2014-06-20
Good News! I intalled the driver again and now it works! Thank you so much!

---

