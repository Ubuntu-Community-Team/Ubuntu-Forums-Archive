---
title: "Incredibly slow download speeds in Ubuntu 14.04."
date: 2014-07-11
forum: Networking &amp; Wireless
---

### Post by carlos53 on 2014-07-11
I recently migrated from Win7 to Ubuntu and I am getting incredibly slow download speeds in both Chromium (sorry if misspeled) and Firefox.
Simply downloading a 50mb file takes about 5 hours, and download speed does not go beyond 100 kb/s. I tried a lot of tweaks (Fixing the daemon bug, Atheros config...) and downloading files remains slow.
Incredibly, loading pages went faster.
Here's the log from Varunenda's Wireless-Info Script:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

carlos-pc 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Pentium(R) CPU B950 @ 2.10GHz
Memory : 5916 MB
Uptime : 15:47:10 up 42 min,  2 users,  load average: 0,48, 0,46, 0,53


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:9181]
    Kernel driver in use: rtl8192ce
08:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: QUANTA Computer Inc Device [152d:0883]
    Kernel driver in use: atl1c


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 003: ID 5986:04ab Acer, Inc 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"SALAZAR NET"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 SALAZAR NET>   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:26043   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

mxm_wmi                13021  0 
rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi
wmi                    19177  1 mxm_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rtl8192ce     (5): debug=0 | fwlps=Y | ips=Y | swenc=N | swlps=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
======================o=============o===========o==============o=========o===========o==============o===========
 Interface & ID       | Type        | Driver    | State        | Default | Speed     | Support      | HW Addr   
======================o=============o===========o==============o=========o===========o==============o===========
 eth0                 | Wired       | atl1c     | unavailable  | no      |           |              | <MAC eth0>
----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------
 wlan0  [SALAZAR NET] | 802.11 WiFi | rtl8192ce | connected    | yes     | 18 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    *SALAZAR NET:    Infra, <MAC C-01 SALAZAR NET>, Freq 2437 MHz, Rate 54 Mb/s, Strength 96 WPA2

    Address:         192.168.1.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------+-------------+-----------+--------------+---------+-----------+--------------+-----------


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

SALAZAR NET          : ssid=SALAZAR NET | mac-address=<MAC wlan0> | mtu=1500 | ipv4=auto | ipv6=ignore 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabela de Roteamento IP do Kernel
Destino         Roteador        MáscaraGen.    Opções Métrica Ref   Uso Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.344/2.403/2.462/0.059 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.022/0.039/0.057/0.018 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "pt_BR.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 SALAZAR NET>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-18 dBm  
                    Encryption key:on
                    ESSID:"SALAZAR NET"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c6a48af4
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Servnet_3_88340413>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"Servnet_3_88340413"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000320018a
                    Extra: Last beacon: 160ms ago
          Cell 03 - Address: <MAC C-03 ReikTech-001>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"ReikTech-001"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000111cf3754d
                    Extra: Last beacon: 248ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Multilaser_0C2DC0>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:on
                    ESSID:"Multilaser_0C2DC0"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a439fe0183
                    Extra: Last beacon: 4192ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Servnet_4_88340413>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"Servnet_4_88340413"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000008502181
                    Extra: Last beacon: 3140ms ago
          Cell 06 - Address: <MAC C-06 Alvaro>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Alvaro"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b3c90181
                    Extra: Last beacon: 508ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 LEONEL.NET_V2>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"LEONEL.NET_V2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000062792272bd
                    Extra: Last beacon: 372ms ago
          Cell 08 - Address: <MAC C-08 CAPITAN2009>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"CAPITAN2009"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000001ed3650ae
                    Extra: Last beacon: 8ms ago
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

[rtl8192ce]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
srcversion:     BF8278DF19B67D7D6C6B8C5
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
parm:           swenc:Set to 1 for software crypto (default 0)
parm:           ips:Set to 0 to not use link power save (default 1)
parm:           swlps:Set to 1 to use SW control power save (default 0)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi

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

# PCI device 0x1969:0x1083 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8176 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
rt2800pci.conf    : options rt2800pci nohwcrypt=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=c6aa92bc-d4d6-43f8-a066-6d0d6da96b0a ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.568219] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.568555] audit: initializing netlink socket (disabled)
[   12.815294] wmi: Mapper loaded
[   13.867776] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   14.053076] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   14.053286] rtlwifi: wireless switch is on
[   24.969332] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   31.672062] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   31.673915] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.918999] wlan0: authenticate with <MAC C-01 SALAZAR NET>
[   33.941688] wlan0: send auth to <MAC C-01 SALAZAR NET> (try 1/3)
[   33.943582] wlan0: authenticated
[   33.943764] rtl8192ce 0000:07:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   33.943768] rtl8192ce 0000:07:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   33.946838] wlan0: associate with <MAC C-01 SALAZAR NET> (try 1/3)
[   33.949225] wlan0: RX AssocResp from <MAC C-01 SALAZAR NET> (capab=0x411 status=0 aid=2)
[   33.949384] wlan0: associated
[   33.949409] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   34.075284] wlan0: deauthenticating from <MAC C-01 SALAZAR NET> by local choice (reason=2)
[   34.099005] wlan0: authenticate with <MAC C-01 SALAZAR NET>
[   34.099101] wlan0: send auth to <MAC C-01 SALAZAR NET> (try 1/3)
[   34.100956] wlan0: authenticated
[   34.101250] rtl8192ce 0000:07:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   34.101253] rtl8192ce 0000:07:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   34.103063] wlan0: associate with <MAC C-01 SALAZAR NET> (try 1/3)
[   34.105432] wlan0: RX AssocResp from <MAC C-01 SALAZAR NET> (capab=0x411 status=0 aid=2)
[   34.105582] wlan0: associated
[ 1417.558555] wlan0: deauthenticated from <MAC C-01 SALAZAR NET> (Reason: 7)
[ 1418.832328] wlan0: authenticate with <MAC C-01 SALAZAR NET>
[ 1418.842225] wlan0: send auth to <MAC C-01 SALAZAR NET> (try 1/3)
[ 1418.845902] wlan0: authenticated
[ 1418.846036] rtl8192ce 0000:07:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1418.846039] rtl8192ce 0000:07:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1418.847859] wlan0: associate with <MAC C-01 SALAZAR NET> (try 1/3)
[ 1418.850235] wlan0: RX AssocResp from <MAC C-01 SALAZAR NET> (capab=0x411 status=0 aid=2)
[ 1418.850357] wlan0: associated

    ======== Done ========
```
Here's the log. Any idea?

---

### Post by TheFu on 2014-07-11
**route** - output from that please. If there are multiple default routes or both the wired and wifi routes collide without a clear metric difference, things can be bad.

Is this the wired or wifi connection?

---

