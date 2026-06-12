---
title: "Slow internet on Ubuntu 14.04"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by andrija2 on 2014-09-16
Well, my internet speed should be around 1.7MB/s, and is currently around 0.4MB/s.
[IMG]http://www.speedtest.net/result/3764167762.png[/IMG]

wireless-info.txt:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

toshiba-Satellite-C660 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz
Memory : 2896 MB
Uptime : 16:25:25 up 20 min,  2 users,  load average: 0,45, 0,48, 0,42


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Toshiba America Info Systems Device [1179:fd3c]
    Kernel driver in use: r8169
14:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8184]
    Kernel driver in use: rtl8192ce


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 0930:a001 Toshiba Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b1d6 Chicony Electronics Co., Ltd CNF9055 Toshiba Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"e5ec70"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 e5ec70>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-68 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6536   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wmi                    18673  1 toshiba_acpi
rtl8192ce              52806  0 
rtl_pci                26314  1 rtl8192ce
rtlwifi                52835  2 rtl_pci,rtl8192ce
rtl8192c_common        47340  1 rtl8192ce
mac80211              546051  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              409394  2 mac80211,rtlwifi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===============================o=============o===========o===========o=========o===========o==============o===========
 Interface & ID                | Type        | Driver    | State     | Default | Speed     | Support      | HW Addr   
===============================o=============o===========o===========o=========o===========o==============o===========
 wlan0  [e5ec70]               | 802.11 WiFi | rtl8192ce | connected | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    HG532e-1F1328:   Infra, <MAC C-02 HG532e-1F1328>, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA WPA2
    HG520c:          Infra, <MAC C-06 HG520c>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA
    Tenda:           Infra, <MAC C-NA Tenda 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Bojan:           Infra, <MAC C-NA Bojan 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    f8d286:          Infra, <MAC C-03 f8d286>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    ChungaLunga:     Infra, <MAC C-05 ChungaLunga>, Freq 2422 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Guest:           Infra, <MAC C-NA Guest 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA
    wirlless:        Infra, <MAC C-04 wirlless>, Freq 2462 MHz, Rate 11 Mb/s, Strength 24 WPA WPA2
    *e5ec70:         Infra, <MAC C-01 e5ec70>, Freq 2462 MHz, Rate 54 Mb/s, Strength 48 WPA WPA2
    HG532e-1EFF19:   Infra, <MAC C-NA HG532e-1EFF19 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    TP-LINK_8F62F4:  Infra, <MAC C-NA TP-LINK_8F62F4 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2

    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             89.216.1.30
    DNS:             89.216.1.50
-------------------------------+-------------+-----------+-----------+---------+-----------+--------------+-----------
 eth0  [Ethernet connection 1] | Wired       | r8169     | connected | no      | 100 Mb/s  |              | <MAC eth0>

    Address:         10.42.0.1
    Prefix:          24 (255.255.255.0)
    Gateway:         0.0.0.0
-------------------------------+-------------+-----------+-----------+---------+-----------+--------------+-----------


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

no-auto-default=<MAC eth0>,

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

e5ec70               : ssid=e5ec70 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
10.42.0.0       0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 1.922/2.062/2.203/0.147 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.055/0.060/0.065/0.005 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : sr_RS)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency=2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 e5ec70>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"e5ec70"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002157edf4e7
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 HG532e-1F1328>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"HG532e-1F1328"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001b7baf17fb8
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 f8d286>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"f8d286"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000020e449c194
                    Extra: Last beacon: 124ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 wirlless>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"wirlless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000011daf154181
                    Extra: Last beacon: 376ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 ChungaLunga>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"ChungaLunga"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000497fd201ef
                    Extra: Last beacon: 3464ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 HG520c>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"HG520c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ff30c0847
                    Extra: Last beacon: 12ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[rtl8192ce]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     EF063698748457BBEDB4633
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi

[rtlwifi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211

[rtl8192c_common]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
srcversion:     32F826C623BC49F764F7974
depends:        

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

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
rtl8192ce

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=e1101e7b-be18-41a7-8875-5e590a815f09 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.719234] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.719534] audit: initializing netlink socket (disabled)
[    1.213404] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   16.413686] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   16.461587] wmi: Mapper loaded
[   16.653742] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   16.654044] rtlwifi: wireless switch is on
[   20.849066] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.735939] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.736298] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.860632] wlan0: authenticate with <MAC C-01 e5ec70>
[   25.882180] wlan0: send auth to <MAC C-01 e5ec70> (try 1/3)
[   25.886923] wlan0: authenticated
[   25.887275] rtl8192ce 0000:14:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   25.887279] rtl8192ce 0000:14:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   25.888151] wlan0: associate with <MAC C-01 e5ec70> (try 1/3)
[   25.890281] wlan0: RX AssocResp from <MAC C-01 e5ec70> (capab=0x411 status=0 aid=1)
[   25.890414] wlan0: associated
[   25.890452] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.964850] wlan0: deauthenticating from <MAC C-01 e5ec70> by local choice (reason=2)
[   25.975327] wlan0: authenticate with <MAC C-01 e5ec70>
[   26.318479] wlan0: send auth to <MAC C-01 e5ec70> (try 1/3)
[   27.820069] wlan0: send auth to <MAC C-01 e5ec70> (try 2/3)
[   27.821979] wlan0: authenticated
[   27.822186] rtl8192ce 0000:14:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   27.822191] rtl8192ce 0000:14:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   27.824049] wlan0: associate with <MAC C-01 e5ec70> (try 1/3)
[   27.826384] wlan0: RX AssocResp from <MAC C-01 e5ec70> (capab=0x411 status=0 aid=1)
[   27.826513] wlan0: associated
[   58.824114] wlan0: Connection to AP <MAC C-01 e5ec70> lost
[   59.860547] wlan0: authenticate with <MAC C-01 e5ec70>
[   59.880353] wlan0: send auth to <MAC C-01 e5ec70> (try 1/3)
[   59.882367] wlan0: authenticated
[   59.882544] rtl8192ce 0000:14:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   59.882548] rtl8192ce 0000:14:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   59.884058] wlan0: associate with <MAC C-01 e5ec70> (try 1/3)
[   59.886458] wlan0: RX AssocResp from <MAC C-01 e5ec70> (capab=0x411 status=0 aid=1)
[   59.886576] wlan0: associated

    ======== Done ========
```

---

### Post by praseodym on 2014-09-16
Hi,

try pure WPA2-AES (CCMP) encryption -check the router manual- and/or these module parameters:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

---

