---
title: "Ubuntu/Xubuntu 14.04: Wifi unable to connect to network (Intel 3945)"
date: 2014-09-05
forum: Networking &amp; Wireless
---

### Post by T.Q. on 2014-09-05
Hi,

Can somebody please help me! I'm not computer savvy at all. After spending almost 3 weeks 
with google search, reading through hundreds of posts in the ubuntu forums, and trying out all sorts of  
terminal commands that are being suggested in these forums, I'm at my wits' end.

I've been using Ubuntu 12.04 LTS, and then the upgraded version 14.04, ever since Windows XP expired without any problems. 
However, after a software update roughly 3 weeks ago, my wifi stopped working. Still it is unable to connect to the wireless network due to some kind of authentication problems or so. But the network passwords are correct. Strangely, in cases where a wifi connection is established for whatever reason, I cannot access the internet at all. I can ping the router and the localhost, but no external IP or website.

Ethernet works fine, and my wifi card is an Intel 3945ABG. My laptop is an old HP Pavilion dv5000.

Thus far, I have made several clean installs of Ubuntu 14.04 from a USB stick; I reverted to Ubuntu 12.04 
once; and right now, I have installed Xubuntu 14.04 -- this all in the hope that this wifi problem will resolve itself 
somehow (naive of me, I know), but the same problem pattern still persists. I also have a HP Mini with Ubuntu 14.04 LTS on it and its wifi works perfectly.

Here are some info


```
    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

HP-Pavilion-dv5 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Genuine Intel(R) CPU           T2050  @ 1.60GHz
Memory : 1499 MB
Uptime : 19:43:51 up  8:03,  2 users,  load average: 0.18, 0.10, 0.06


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135b]
    Kernel driver in use: iwl3945
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
mac80211              546051  2 iwl3945,iwlegacy
cfg80211              409394  3 iwl3945,iwlegacy,mac80211
wmi                    18673  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwl3945       (4): antenna=0 | disable_hw_scan=1 | fw_restart=1 | swcrypto=1
iwlegacy      (2): bt_coex_active=Y | led_mode=0
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | e100    | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.16
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | iwl3945 | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    CuVinh:          Infra, <MAC C-01 CuVinh>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA
    D7F393:          Infra, <MAC C-NA D7F393 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    LanVy:           Infra, <MAC C-NA LanVy 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 52 WPA2
    JAZZY1:          Infra, <MAC C-NA JAZZY1 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 44 WEP
    CenturyLink1392: Infra, <MAC C-02 CenturyLink1392>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Anarchy:         Infra, <MAC C-03 Anarchy>, Freq 2422 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

LanVy                : ssid=LanVy | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 20.213/39.626/59.040/19.414 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.058/0.063/0.069/0.009 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     24 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 CuVinh>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"CuVinh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000c8fcf1e81b
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 CenturyLink1392>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink1392"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001d543962363
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Anarchy>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"Anarchy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000386738042a
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[iwl3945]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
version:        in-tree:s
srcversion:     C93C31FCEBBAE1F376E495F
depends:        iwlegacy,cfg80211,mac80211
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
version:        in-tree:
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

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

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1092 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=5727ac1b-4de6-4ac1-a4f0-868ad811e145 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.100341] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.101225] audit: initializing netlink socket (disabled)
[   19.031447] wmi: Mapper loaded
[   19.374466] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   19.374472] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   19.374533] iwl3945 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
[   19.437756] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   19.437765] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   19.437850] iwl3945 0000:06:00.0: irq 45 for MSI/MSI-X
[   19.466540] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   21.844835] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.983557] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
[   23.055934] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.056496] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   51.096508] wlan0: authenticate with <MAC C-NA LanVy 1>
[   51.098240] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[   51.100175] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[   53.236797] wlan0: authenticate with <MAC C-NA LanVy 1>
[   53.241164] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[   53.243241] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[   55.780835] wlan0: authenticate with <MAC C-NA LanVy 1>
[   55.782972] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[   55.784870] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[   58.832787] wlan0: authenticate with <MAC C-NA LanVy 1>
[   58.834826] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[   58.836722] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[   72.904802] wlan0: authenticate with <MAC C-NA LanVy 1>
[   72.906924] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[   72.909849] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[ 4613.612751] wlan0: authenticate with <MAC C-NA LanVy 1>
[ 4613.614689] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[ 4613.617531] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[ 4625.689415] wlan0: authenticate with <MAC C-NA LanVy 1>
[ 4625.691224] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[ 4625.698579] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[ 6781.305108] wlan0: authenticate with <MAC C-NA LanVy 1>
[ 6781.307385] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[ 6781.311960] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[ 6793.345077] wlan0: authenticate with <MAC C-NA LanVy 1>
[ 6793.346861] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[ 6793.351475] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[26755.805624] wlan0: authenticate with <MAC C-NA LanVy 1>
[26755.807908] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[26755.809856] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)
[26767.861210] wlan0: authenticate with <MAC C-NA LanVy 1>
[26767.864714] wlan0: send auth to <MAC C-NA LanVy 1> (try 1/3)
[26767.868808] wlan0: <MAC C-NA LanVy 1> denied authentication (status 1)

    ======== Done ========

```

Any advice is greatly appreciated!

TQ

---

### Post by T.Q. on 2014-09-11
Anybody?

---

### Post by varunendra on 2014-09-11
Welcome to the forums T.Q. !

Did you manually load the iwl3945 driver with "swcrypto=1" parameter before running the script?

Please try this instead -
```
echo "options iwlegacy bt_coex_active=N" | sudo tee /etc/modprobe.d/iwlegacy.conf
```
Reboot and see if the connection is any better. If not, please post back a fresh report with ONLY the suggested change applied.

---

### Post by T.Q. on 2014-09-12
Hi Varun,

Thank you for your welcome and for your reply!

I cannot remember having manually loaded the iwl3945 driver. But it was pretty much right after the clean install of Xubuntu 14.04 that
I went to the forum for help. After that I have for sure messed around with several more commands!

I did what you suggested me to do, but the problem hasn't changed.

I repost the wireless script just to give you an update

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

HP-Pavilion-dv5 3.13.0-35-generic i686,  Ubuntu 14.04.1 LTS, trusty

CPU    : Genuine Intel(R) CPU           T2050  @ 1.60GHz
Memory : 1499 MB
Uptime : 23:29:50 up 10 min,  2 users,  load average: 0.25, 0.29, 0.23


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:135b]
    Kernel driver in use: iwl3945
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:30a5]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

hp_wmi                 13702  0 
sparse_keymap          13708  1 hp_wmi
iwl3945                63619  0 
iwlegacy               88016  1 iwl3945
mac80211              546051  2 iwl3945,iwlegacy
cfg80211              409394  3 iwl3945,iwlegacy,mac80211
wmi                    18673  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwl3945       (4): antenna=0 | disable_hw_scan=1 | fw_restart=1 | swcrypto=1
iwlegacy      (2): bt_coex_active=N | led_mode=0
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o=========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver  | State        | Default | Speed     | Support      | HW Addr   
============================o=============o=========o==============o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired       | e100    | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.27
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             68.105.28.12
    DNS:             68.105.29.12
    DNS:             68.105.28.11
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------
 wlan0                      | 802.11 WiFi | iwl3945 | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    D7F393:          Infra, <MAC C-NA D7F393 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 32 WPA WPA2
    CuVinh:          Infra, <MAC C-01 CuVinh>, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA
    LanVy:           Infra, <MAC C-02 LanVy>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA2
    CenturyLink1392: Infra, <MAC C-03 CenturyLink1392>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Anarchy:         Infra, <MAC C-NA Anarchy 1>, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    JAZZY1:          Infra, <MAC C-NA JAZZY1 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WEP
----------------------------+-------------+---------+--------------+---------+-----------+--------------+-----------


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

LanVy                : ssid=LanVy | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 10.424/41.729/73.034/31.305 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.054/0.065/0.076/0.011 ms


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

wlan0     24 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 52 (5.26 GHz)
          Channel 56 (5.28 GHz)
          Channel 60 (5.3 GHz)
          Channel 64 (5.32 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz) - 11 (2.462 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 CuVinh>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"CuVinh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000144d7ac7e62
                    Extra: Last beacon: 36ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 LanVy>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"LanVy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a1683e52
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 CenturyLink1392>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"CenturyLink1392"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002511eb4a5ca
                    Extra: Last beacon: 36ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[hp_wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     22DCD1B7DA09178B45B1068
depends:        wmi,sparse-keymap

[iwl3945]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
version:        in-tree:s
srcversion:     C93C31FCEBBAE1F376E495F
depends:        iwlegacy,cfg80211,mac80211
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)

[iwlegacy]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
version:        in-tree:
srcversion:     400F302BE5C25B3C98A6CE8
depends:        mac80211,cfg80211
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)

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

[wmi]
filename:       /lib/modules/3.13.0-35-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1092 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlegacy.conf     : options iwlegacy bt_coex_active=N
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=5727ac1b-4de6-4ac1-a4f0-868ad811e145 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.104509] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.105408] audit: initializing netlink socket (disabled)
[   14.678091] wmi: Mapper loaded
[   14.845823] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   14.845830] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   14.845897] iwl3945 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.900093] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.900101] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   14.900184] iwl3945 0000:06:00.0: irq 44 for MSI/MSI-X
[   14.935754] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.645165] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.913937] iwl3945 0000:06:00.0: loaded firmware version 15.32.2.9
[   19.010306] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.010798] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.134921] wlan0: authenticate with <MAC C-02 LanVy>
[   21.137416] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   21.145889] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   23.280822] wlan0: authenticate with <MAC C-02 LanVy>
[   23.282702] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   23.287619] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   25.852750] wlan0: authenticate with <MAC C-02 LanVy>
[   25.854600] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   25.874432] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   28.916727] wlan0: authenticate with <MAC C-02 LanVy>
[   28.918526] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   28.920355] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   43.016681] wlan0: authenticate with <MAC C-02 LanVy>
[   43.018438] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   43.020253] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   49.043840] wlan0: authenticate with <MAC C-02 LanVy>
[   49.043967] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   49.045813] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   61.100726] wlan0: authenticate with <MAC C-02 LanVy>
[   61.102955] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   61.114659] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   77.041378] wlan0: authenticate with <MAC C-02 LanVy>
[   77.041564] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   77.043392] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[   89.085344] wlan0: authenticate with <MAC C-02 LanVy>
[   89.087312] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[   89.089249] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[  105.050867] wlan0: authenticate with <MAC C-02 LanVy>
[  105.050988] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[  105.052808] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[  117.101216] wlan0: authenticate with <MAC C-02 LanVy>
[  117.102779] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[  117.106157] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[  166.141139] wlan0: authenticate with <MAC C-02 LanVy>
[  166.143736] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[  166.146512] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[  178.189346] wlan0: authenticate with <MAC C-02 LanVy>
[  178.191038] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[  178.192986] wlan0: <MAC C-02 LanVy> denied authentication (status 1)
[  333.097487] wlan0: authenticate with <MAC C-02 LanVy>
[  333.099352] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[  333.300094] wlan0: send auth to <MAC C-02 LanVy> (try 2/3)
[  333.504101] wlan0: send auth to <MAC C-02 LanVy> (try 3/3)
[  333.708051] wlan0: authentication with <MAC C-02 LanVy> timed out
[  345.769320] wlan0: authenticate with <MAC C-02 LanVy>
[  345.771265] wlan0: send auth to <MAC C-02 LanVy> (try 1/3)
[  345.773109] wlan0: <MAC C-02 LanVy> denied authentication (status 1)

    ======== Done ========

```

---

### Post by varunendra on 2014-09-12
> **T.Q. said:**
> ```

          Cell 02 - Address: <MAC C-02 LanVy>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                   ** ESSID:"LanVy"**
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a1683e52
                    Extra: Last beacon: 36ms ago
                   ** IE: IEEE 802.11i/WPA2 Version 1**
                        Group Cipher : **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
```

As highlighted above, you are using TKIP with WPA2. The usual combination is TKIP with WPA (1), or AES (CCMP) with WPA2. As such, please try changing the encryption algorithm in your router/access-point to **WPA2-PSK with AES (CCMP)**. Reboot the router after saving the change and retry to connect. Does it succeed now?

---

### Post by T.Q. on 2014-09-12
Hi Varun,

As a third party I do not own the router and I cannot access it. Is there any way around? 

The thing I don't get is that my other laptop, an HP Mini, with Ubuntu 14.04 installed on it is also wirelessly connected to the 'LanVy' network, and its wifi connection is rock solid.

There is a second access point called 'CuVinh' with WPA/TKIP encryption that I can log on as well. But even there I'm facing the same problem: the wifi of the troubled laptop can better connect, but internet doesn't work.

---

### Post by varunendra on 2014-09-12
The suggestion for changing the encryption was just to optimize it. It shouldn't be necessary.

The drivers are supposed to be able to handle minor abnormalities but sometimes they just can't. While the problem may be something else, the card you are using is quite old and sometimes can give a hard time.

For now, I can think of only a few more things to try -

**1)** Set "IPv6" in Network Manager to "Ignore".
**2)** If that doesn't make any difference, delete the currently saved connection profile and let a new one be created automatically with next connection attempt.
**3)** If the above one doesn't help either, try a enabling hardware based encryption on the card (opposite of what we usually try) -
```
sudo modprobe -rv iwl3945
sudo modprobe -v iwl3945 swcrypto=0
```
..and retry to connect.

Some recent cases have made me suspect (..and it may be that I'm just being paranoid) that reloading wifi drivers on a running system like above somehow puts the connection into an infinite connect/disconnect loop. So if it still fails to connect, try the above parameter in permanent mode -
```
echo "options iwl3945 swcrypto=0" | sudo tee /etc/modprobe.d/iwl3945.conf
```
..followed by a reboot.

If none of above works, I guess I would prefer trying a newer, backported driver next instead of trying anything else with the current one.

---

### Post by T.Q. on 2014-09-13
Unfortunately, none of the suggestions work.

It would be great if you can guide me through the installation of the new driver.

Many thanks!

---

