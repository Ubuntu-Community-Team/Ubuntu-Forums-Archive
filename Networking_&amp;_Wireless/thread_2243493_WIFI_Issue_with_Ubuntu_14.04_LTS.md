---
title: "WIFI Issue with Ubuntu 14.04 LTS"
date: 2014-09-09
forum: Networking &amp; Wireless
---

### Post by Anidro on 2014-09-09
My wifi connection is really slow and unstable. With cable ethernet connection I do not have problems. I have read other similar post on this forum but I am not able to find the solution to my problem. I try the following solutions: 

[TABLE="class: outer_border, width: 500"]
[TR]
[TD]sudo rmmod iwlwif
sudo modprobe iwlwifi 11n_disable=1
[/TD]
[/TR]
[/TABLE]
and
[TABLE="class: outer_border, width: 500"]
[TR]
[TD]sudo gedit /etc/nsswitch.conf

In here, look for the following line:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

If you find this file, replace it with the following line:

hosts:          files dns

Save  it, close it, restart your computer. 
[/TD]
[/TR]
[/TABLE]
Somebody can help me to found solution to my problem?

---

### Post by varunendra on 2014-09-11
Welcome to the forums Anidro!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by Anidro on 2014-09-12
Really sorry for the errors in the creation of my post.

The output of wireless_script is:

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

luigi-Lenovo-IdeaPad-Y510P 3.13.0-36-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
Memory : 15961 MB
Uptime : 17:56:57 up 49 min,  2 users,  load average: 0,16, 0,28, 0,30


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: Lenovo Device [17aa:3800]
    Kernel driver in use: alx
08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:07da Intel Corp. 
Bus 003 Device 003: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"LUIGI-HP_Network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 LUIGI-HP_Network>   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=28/70  Signal level=-82 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:12  Invalid misc:1   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      yes           no
2: hci0: Bluetooth                   no            no
3: phy0: Wireless LAN                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=0 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===========================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID            | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
===========================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [LUIGI-HP_Network] | 802.11 WiFi | iwlwifi | connected   | yes     | 5 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    Alice-35868379:  Infra, <MAC C-04 Alice-35868379>, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Alice-73522017:  Infra, <MAC C-02 Alice-73522017>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    D-Link_deri:     Infra, <MAC C-05 D-Link_deri>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA WPA2
    Alice-73522017:  Infra, <MAC C-07 Alice-73522017>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    *LUIGI-HP_Network: Infra, <MAC C-01 LUIGI-HP_Network>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    D-Link_deri:     Infra, <MAC C-06 D-Link_deri>, Freq 2462 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    vgn:             Infra, <MAC C-03 vgn>, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2

    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
---------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                      | Wired       | alx     | unavailable | no      |           |              | <MAC eth0>
---------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

Alfa-Omega           : ssid=Alfa-Omega | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
LUIGI-HP_Network     : ssid=LUIGI-HP_Network | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.813/2.189/2.566/0.379 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.015/0.019/0.024/0.006 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "it_IT.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 LUIGI-HP_Network>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"LUIGI-HP_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001502cfa57b
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Alice-73522017>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"Alice-73522017"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001500c40549
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 vgn>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"vgn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015020c5944
                    Extra: Last beacon: 1092ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Alice-35868379>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"Alice-35868379"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001aec110b
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 D-Link_deri>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"D-Link_deri"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000015021eb91f
                    Extra: Last beacon: 25400ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 D-Link_deri>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"D-Link_deri"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a48e22d0
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 Alice-73522017>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Alice-73522017"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000013f3e74ea
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwldvm]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x0888 (iwlwifi)
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
iwlwifi.conf~     : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-36-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.102492] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.102732] audit: initializing netlink socket (disabled)
[    1.465772] alx 0000:07:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    2.104770] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f01)
[    3.688478] wmi: Mapper loaded
[    3.772039] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.772093] iwlwifi 0000:08:00.0: irq 47 for MSI/MSI-X
[    3.789937] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    3.804096] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.804099] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.804100] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.804103] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    3.804156] iwlwifi 0000:08:00.0: L1 Disabled; Enabling L0S
[    3.832600] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.026164] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.142824] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.039986] iwlwifi 0000:08:00.0: L1 Disabled; Enabling L0S
[   27.047449] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   27.288828] iwlwifi 0000:08:00.0: L1 Disabled; Enabling L0S
[   27.296233] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[   27.363850] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.879906] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[   27.891159] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[   27.893824] wlan0: authenticated
[   27.893914] wlan0: waiting for beacon from <MAC C-01 LUIGI-HP_Network>
[   28.580770] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[   28.584887] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[   28.587757] wlan0: authenticated
[   28.590845] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[   28.594746] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=4)
[   28.614827] wlan0: associated
[   28.614854] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  133.007634] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  133.007645] iwlwifi 0000:08:00.0: Current SW read_ptr 10 write_ptr 14
[  133.007678] iwl data: 00000000: 00 3c 00 00 00 00 00 00 00 00 00 00 00 00 00 00  .<..............
[  133.007697] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  133.007716] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010200d
[  133.007733] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  133.007750] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030000a
[  133.007766] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  133.007783] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  133.007799] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  133.007816] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090cc
[  133.007879] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [11,11]
[  133.007940] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  133.008000] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [10,14]
[  133.008061] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008122] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008182] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  133.008243] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  133.008303] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  133.008364] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  133.008425] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [205,205]
[  133.008486] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  133.008547] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008608] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008668] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008729] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008790] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008851] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008912] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.008973] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  133.009034] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.555668] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  160.555679] iwlwifi 0000:08:00.0: Current SW read_ptr 198 write_ptr 216
[  160.555709] iwl data: 00000000: c0 ff 3f 00 00 00 00 00 00 00 00 00 00 00 00 00  ..?.............
[  160.555727] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  160.555744] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020d5
[  160.555761] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  160.555778] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030000b
[  160.555795] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  160.555811] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  160.555827] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  160.555844] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090fe
[  160.555907] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [12,12]
[  160.555968] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  160.556029] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [198,216]
[  160.556090] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556151] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556212] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  160.556273] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  160.556334] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  160.556395] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  160.556456] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [255,255]
[  160.556517] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  160.556578] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556639] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556700] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556761] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556822] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556883] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.556943] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.557004] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  160.557065] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.259739] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  243.259751] iwlwifi 0000:08:00.0: Current SW read_ptr 93 write_ptr 142
[  243.259782] iwl data: 00000000: 00 00 00 e0 00 00 00 00 ff 1f 00 00 00 00 00 00  ................
[  243.259801] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  243.259818] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010206c
[  243.259835] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  243.259851] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300011
[  243.259868] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  243.259884] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  243.259901] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  243.259918] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070909c
[  243.259981] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [18,18]
[  243.260042] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  243.260103] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [93,142]
[  243.260164] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.260225] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.260286] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  243.260347] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  243.260408] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  243.260469] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  243.260530] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [157,157]
[  243.260591] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  243.260652] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.260713] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.260774] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.260835] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.260896] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.260956] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.261017] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.261078] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  243.261139] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.200091] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  277.200102] iwlwifi 0000:08:00.0: Current SW read_ptr 65 write_ptr 102
[  277.200134] iwl data: 00000000: fe ff 01 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  277.200152] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  277.200169] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102050
[  277.200186] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  277.200202] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300015
[  277.200219] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  277.200235] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  277.200251] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  277.200268] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090f4
[  277.200330] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [22,22]
[  277.200391] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  277.200452] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [65,102]
[  277.200513] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.200574] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.200635] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  277.200696] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  277.200760] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  277.200825] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  277.200895] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [245,245]
[  277.200961] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  277.201027] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201094] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201159] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201220] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201281] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201342] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201403] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201464] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  277.201525] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.771004] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  346.771015] iwlwifi 0000:08:00.0: Current SW read_ptr 199 write_ptr 206
[  346.771046] iwl data: 00000000: 80 3f 00 00 00 00 00 00 00 00 00 00 00 00 00 00  .?..............
[  346.771064] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  346.771081] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020cd
[  346.771098] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  346.771114] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300019
[  346.771131] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  346.771147] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  346.771164] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  346.771181] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709097
[  346.771243] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [26,26]
[  346.771305] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  346.771366] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [199,206]
[  346.771427] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.771488] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.771549] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  346.771610] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  346.771670] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  346.771731] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  346.771792] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [152,152]
[  346.771853] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  346.771914] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.771975] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.772036] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.772097] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.772157] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.772218] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.772278] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.772339] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  346.772399] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.671599] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  466.671605] iwlwifi 0000:08:00.0: Current SW read_ptr 53 write_ptr 140
[  466.671632] iwl data: 00000000: 1f 00 00 00 00 00 00 00 00 00 e0 ff 00 00 00 00  ................
[  466.671647] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  466.671662] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102044
[  466.671676] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  466.671691] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300027
[  466.671705] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  466.671720] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  466.671734] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  466.671749] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070908d
[  466.671807] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [40,40]
[  466.671865] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  466.671922] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [53,140]
[  466.671980] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672037] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672094] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  466.672151] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  466.672209] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  466.672266] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  466.672324] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [142,142]
[  466.672381] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  466.672438] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672496] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672553] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672610] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672667] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672724] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672781] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672839] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  466.672896] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.401703] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  477.401714] iwlwifi 0000:08:00.0: Current SW read_ptr 117 write_ptr 238
[  477.401745] iwl data: 00000000: 1f 00 00 00 00 00 00 00 00 00 e0 ff 00 00 00 00  ................
[  477.401763] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  477.401780] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102084
[  477.401796] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  477.401813] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300028
[  477.401829] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  477.401846] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  477.401863] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  477.401880] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090a0
[  477.401943] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [41,41]
[  477.402004] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  477.402065] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [117,238]
[  477.402126] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402187] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402248] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  477.402309] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  477.402370] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  477.402431] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  477.402493] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [161,161]
[  477.402554] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  477.402615] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402676] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402737] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402798] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402859] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402920] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.402981] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.403042] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  477.403103] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.680501] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  586.680512] iwlwifi 0000:08:00.0: Current SW read_ptr 245 write_ptr 70
[  586.680543] iwl data: 00000000: 1f 00 00 00 00 00 00 00 00 00 e0 ff 00 00 00 00  ................
[  586.680561] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  586.680578] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102004
[  586.680595] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  586.680611] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300064
[  586.680628] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  586.680644] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  586.680661] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  586.680677] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090c2
[  586.680740] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [101,101]
[  586.680801] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  586.680862] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [245,70]
[  586.680923] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.680984] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681045] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  586.681106] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  586.681166] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  586.681227] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  586.681288] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [195,195]
[  586.681349] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  586.681410] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681471] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681532] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681592] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681653] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681713] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681773] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681833] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  586.681893] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.700987] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  669.700998] iwlwifi 0000:08:00.0: Current SW read_ptr 86 write_ptr 98
[  669.701029] iwl data: 00000000: 00 00 c0 ff 00 00 00 00 03 00 00 00 00 00 00 00  ................
[  669.701047] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  669.701064] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102061
[  669.701081] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  669.701098] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030006b
[  669.701114] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  669.701131] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  669.701147] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  669.701164] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070903f
[  669.701227] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [108,108]
[  669.701288] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  669.701349] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [86,98]
[  669.701411] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.701471] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.701532] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  669.701593] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  669.701654] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  669.701715] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  669.701776] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [64,64]
[  669.701837] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  669.701898] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.701959] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.702020] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.702081] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.702142] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.702203] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.702263] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.702324] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  669.702385] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.822806] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  707.822818] iwlwifi 0000:08:00.0: Current SW read_ptr 78 write_ptr 165
[  707.822848] iwl data: 00000000: 00 c0 ff 3f 00 00 00 00 00 00 00 00 00 00 00 00  ...?............
[  707.822866] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  707.822884] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010205d
[  707.822900] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  707.822917] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030006e
[  707.822934] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  707.822950] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  707.822966] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  707.822983] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070909c
[  707.823045] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [111,111]
[  707.823106] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  707.823167] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [78,165]
[  707.823227] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.823288] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.823349] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  707.823410] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  707.823471] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  707.823532] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  707.823593] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [157,157]
[  707.823654] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  707.823715] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.823777] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.823850] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.823911] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.823972] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.824032] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.824093] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.824154] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  707.824215] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.754517] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  713.754527] iwlwifi 0000:08:00.0: Current SW read_ptr 118 write_ptr 198
[  713.754558] iwl data: 00000000: 3f 00 00 00 00 00 00 00 00 00 c0 ff 00 00 00 00  ?...............
[  713.754576] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  713.754593] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102085
[  713.754610] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  713.754626] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300070
[  713.754643] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  713.754659] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  713.754676] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  713.754693] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090ac
[  713.754755] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [113,113]
[  713.754817] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  713.754878] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [118,198]
[  713.754939] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755000] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755061] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  713.755122] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  713.755182] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  713.755243] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  713.755305] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [173,173]
[  713.755366] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  713.755427] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755488] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755548] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755609] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755670] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755730] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755791] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755852] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  713.755914] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.797573] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  752.797584] iwlwifi 0000:08:00.0: Current SW read_ptr 150 write_ptr 210
[  752.797616] iwl data: 00000000: 00 00 c0 ff 00 00 00 00 3f 00 00 00 00 00 00 00  ........?.......
[  752.797635] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  752.797654] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020a5
[  752.797671] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  752.797688] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300081
[  752.797705] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  752.797721] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  752.797737] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  752.797754] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709008
[  752.797817] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [130,130]
[  752.797878] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  752.797939] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [150,210]
[  752.798000] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798061] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798122] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  752.798183] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  752.798244] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  752.798305] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  752.798366] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [9,9]
[  752.798427] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  752.798488] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798549] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798610] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798671] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798731] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798792] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798853] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798914] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  752.798975] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.903557] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  833.903568] iwlwifi 0000:08:00.0: Current SW read_ptr 141 write_ptr 204
[  833.903600] iwl data: 00000000: 00 e0 ff 1f 00 00 00 00 00 00 00 00 00 00 00 00  ................
[  833.903617] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  833.903635] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010209c
[  833.903651] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  833.903668] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300094
[  833.903685] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  833.903701] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  833.903718] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  833.903734] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090d8
[  833.903796] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [149,149]
[  833.903857] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  833.903918] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [141,204]
[  833.903979] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904040] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904100] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  833.904161] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  833.904222] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  833.904283] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  833.904344] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [217,217]
[  833.904405] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  833.904466] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904527] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904588] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904649] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904710] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904770] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904831] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904892] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  833.904966] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.914169] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[  835.914180] iwlwifi 0000:08:00.0: Current SW read_ptr 148 write_ptr 21
[  835.914211] iwl data: 00000000: 00 00 f0 ff 00 00 00 00 0f 00 00 00 00 00 00 00  ................
[  835.914229] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[  835.914246] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020a3
[  835.914263] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[  835.914279] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300095
[  835.914296] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[  835.914312] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[  835.914329] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[  835.914345] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090da
[  835.914408] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [150,150]
[  835.914469] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  835.914530] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [148,21]
[  835.914591] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.914652] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.914713] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  835.914774] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[  835.914835] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  835.914896] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[  835.914956] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [219,219]
[  835.915017] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[  835.915078] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915139] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915199] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915260] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915321] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915382] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915442] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915503] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  835.915564] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[  836.469661] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  836.474054] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  836.476854] wlan0: authenticated
[  836.478873] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  836.514370] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 2/3)
[  836.518335] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=4)
[  836.538859] wlan0: associated
[  838.473166] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  838.476956] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  838.500206] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 2/3)
[  838.502938] wlan0: authenticated
[  838.505483] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  838.545577] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 2/3)
[  838.549398] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=4)
[  838.568920] wlan0: associated
[  840.512503] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  840.515714] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  840.540855] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 2/3)
[  840.543653] wlan0: authenticated
[  840.544160] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  840.590657] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 2/3)
[  840.623293] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 3/3)
[  840.656101] wlan0: association with <MAC C-01 LUIGI-HP_Network> timed out
[  851.355907] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  854.170368] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  854.174493] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  854.177183] wlan0: authenticated
[  854.177263] wlan0: waiting for beacon from <MAC C-01 LUIGI-HP_Network>
[  864.761015] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  864.764613] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  864.783352] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 2/3)
[  864.788343] wlan0: authenticated
[  864.788514] wlan0: waiting for beacon from <MAC C-01 LUIGI-HP_Network>
[  879.213405] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  879.217442] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  879.220111] wlan0: authenticated
[  879.220189] wlan0: waiting for beacon from <MAC C-01 LUIGI-HP_Network>
[  879.326822] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  879.330674] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=4)
[  879.350127] wlan0: associated
[  879.350155] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  958.953548] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  958.958435] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  958.961287] wlan0: authenticated
[  958.968663] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  958.972476] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=4)
[  958.991967] wlan0: associated
[  963.176736] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  963.180903] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  963.183739] wlan0: authenticated
[  963.189964] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  963.193842] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=4)
[  963.213661] wlan0: associated
[  978.629947] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[  978.635735] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  978.638522] wlan0: authenticated
[  978.642760] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[  978.648060] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=4)
[  978.667827] wlan0: associated
[ 1092.237440] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1092.237447] iwlwifi 0000:08:00.0: Current SW read_ptr 210 write_ptr 60
[ 1092.237475] iwl data: 00000000: 00 00 fc ff 00 00 00 00 03 00 00 00 00 00 00 00  ................
[ 1092.237491] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1092.237506] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020e1
[ 1092.237521] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1092.237536] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000d0
[ 1092.237551] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1092.237566] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1092.237581] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1092.237596] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709080
[ 1092.237655] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [209,209]
[ 1092.237714] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1092.237772] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [210,60]
[ 1092.237830] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.237888] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.237945] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1092.238003] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1092.238061] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1092.238121] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1092.238183] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [129,129]
[ 1092.238245] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1092.238308] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238369] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238432] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238494] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238556] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238619] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238681] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238743] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1092.238804] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.047978] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1120.047986] iwlwifi 0000:08:00.0: Current SW read_ptr 238 write_ptr 64
[ 1120.048014] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 c0 ff 3f 00 00 00 00  ...........?....
[ 1120.048030] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1120.048045] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020fd
[ 1120.048060] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1120.048075] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000d7
[ 1120.048090] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1120.048104] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1120.048119] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1120.048134] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090d4
[ 1120.048192] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [216,216]
[ 1120.048251] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1120.048309] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [238,64]
[ 1120.048366] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.048424] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.048482] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1120.048540] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1120.048598] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1120.048655] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1120.048713] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [213,213]
[ 1120.048772] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1120.048830] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.048888] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.048946] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.049004] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.049062] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.049120] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.049178] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.049236] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1120.049294] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.549764] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1315.549777] iwlwifi 0000:08:00.0: Current SW read_ptr 121 write_ptr 148
[ 1315.549809] iwl data: 00000000: ff 01 00 00 00 00 00 00 00 00 00 fe 00 00 00 00  ................
[ 1315.549827] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1315.549844] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102088
[ 1315.549860] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1315.549877] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000e1
[ 1315.549893] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1315.549909] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1315.549926] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1315.549942] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709013
[ 1315.550005] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [226,226]
[ 1315.550081] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1315.550142] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [121,148]
[ 1315.550203] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.550264] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.550324] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1315.550385] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1315.550446] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1315.550507] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1315.550568] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [20,20]
[ 1315.550629] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1315.550691] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.550752] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.550813] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.550879] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.550947] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.551017] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.551082] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.551148] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1315.551214] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.297851] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1360.297860] iwlwifi 0000:08:00.0: Current SW read_ptr 41 write_ptr 166
[ 1360.297890] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 fe ff 01 00 00 00 00  ................
[ 1360.297908] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1360.297924] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102038
[ 1360.297940] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1360.297956] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000e5
[ 1360.297972] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1360.297988] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1360.298004] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1360.298021] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070906b
[ 1360.298082] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [230,230]
[ 1360.298143] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1360.298202] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [41,166]
[ 1360.298263] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.298323] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.298383] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1360.298443] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1360.298503] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1360.298563] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1360.298623] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [108,108]
[ 1360.298684] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1360.298744] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.298804] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.298864] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.298926] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.298989] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.299049] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.299109] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.299170] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1360.299230] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.299636] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1392.299639] iwlwifi 0000:08:00.0: Current SW read_ptr 37 write_ptr 74
[ 1392.299664] iwl data: 00000000: 00 00 00 00 00 00 00 00 e0 ff 1f 00 00 00 00 00  ................
[ 1392.299677] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1392.299691] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102034
[ 1392.299703] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1392.299717] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000ea
[ 1392.299730] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1392.299743] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1392.299756] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1392.299769] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090db
[ 1392.299825] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [235,235]
[ 1392.299880] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1392.299936] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [37,74]
[ 1392.299991] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300046] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300101] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1392.300156] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1392.300211] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1392.300266] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1392.300321] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [220,220]
[ 1392.300376] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1392.300431] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300486] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300541] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300596] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300651] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300706] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300761] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300816] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1392.300871] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.274163] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1405.274173] iwlwifi 0000:08:00.0: Current SW read_ptr 129 write_ptr 139
[ 1405.274203] iwl data: 00000000: fe 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 1405.274221] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1405.274238] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010208a
[ 1405.274255] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1405.274271] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000ee
[ 1405.274288] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1405.274305] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1405.274322] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1405.274339] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090f2
[ 1405.274400] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [239,239]
[ 1405.274462] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1405.274523] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [129,139]
[ 1405.274584] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.274644] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.274705] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1405.274766] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1405.274826] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1405.274886] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1405.274947] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [243,243]
[ 1405.275008] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1405.275069] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275130] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275191] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275252] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275312] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275373] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275434] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275495] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1405.275557] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.354102] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1499.354114] iwlwifi 0000:08:00.0: Current SW read_ptr 179 write_ptr 222
[ 1499.354145] iwl data: 00000000: 07 00 00 00 00 00 00 00 00 00 f8 ff 00 00 00 00  ................
[ 1499.354163] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1499.354180] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020c2
[ 1499.354196] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1499.354213] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000f6
[ 1499.354230] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1499.354246] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1499.354262] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1499.354279] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090af
[ 1499.354341] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [247,247]
[ 1499.354402] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1499.354463] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [179,222]
[ 1499.354525] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.354585] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.354646] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1499.354707] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1499.354768] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1499.354829] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1499.354981] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [176,176]
[ 1499.355043] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1499.355104] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355165] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355226] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355287] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355348] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355409] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355470] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355531] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1499.355592] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.771687] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1555.771697] iwlwifi 0000:08:00.0: Current SW read_ptr 144 write_ptr 255
[ 1555.771728] iwl data: 00000000: 00 00 ff ff 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 1555.771746] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1555.771763] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010209f
[ 1555.771780] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1555.771796] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300006
[ 1555.771813] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1555.771830] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1555.771846] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1555.771863] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709064
[ 1555.771925] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [7,7]
[ 1555.771987] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1555.772048] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [144,255]
[ 1555.772109] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772170] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772231] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1555.772292] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1555.772353] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1555.772414] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1555.772475] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [101,101]
[ 1555.772536] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1555.772597] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772658] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772719] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772780] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772840] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772901] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.772963] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.773023] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1555.773085] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.680474] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1675.680485] iwlwifi 0000:08:00.0: Current SW read_ptr 41 write_ptr 64
[ 1675.680516] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 fe ff 01 00 00 00 00  ................
[ 1675.680534] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1675.680551] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102038
[ 1675.680568] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1675.680585] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030001d
[ 1675.680601] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1675.680618] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1675.680635] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1675.680652] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709085
[ 1675.680714] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [30,30]
[ 1675.680776] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1675.680837] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [41,64]
[ 1675.680898] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.680959] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681021] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1675.681082] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1675.681143] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1675.681204] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1675.681265] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [134,134]
[ 1675.681327] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1675.681387] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681449] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681510] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681571] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681632] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681693] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681754] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681815] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1675.681876] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.535589] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1689.535602] iwlwifi 0000:08:00.0: Current SW read_ptr 153 write_ptr 169
[ 1689.535633] iwl data: 00000000: 00 00 00 fe 00 00 00 00 ff 01 00 00 00 00 00 00  ................
[ 1689.535652] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1689.535668] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020a8
[ 1689.535685] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1689.535701] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030001f
[ 1689.535718] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1689.535734] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1689.535751] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1689.535768] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090ae
[ 1689.535830] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [32,32]
[ 1689.535891] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1689.535952] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [153,169]
[ 1689.536013] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536074] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536135] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1689.536196] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1689.536257] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1689.536317] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1689.536379] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [175,175]
[ 1689.536440] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1689.536500] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536561] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536621] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536682] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536743] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536804] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536864] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536925] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1689.536986] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.514092] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1697.514103] iwlwifi 0000:08:00.0: Current SW read_ptr 219 write_ptr 251
[ 1697.514135] iwl data: 00000000: 00 00 00 f8 00 00 00 00 ff 07 00 00 00 00 00 00  ................
[ 1697.514153] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1697.514170] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020ea
[ 1697.514186] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1697.514203] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300020
[ 1697.514219] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1697.514236] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1697.514253] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1697.514269] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090cc
[ 1697.514332] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [33,33]
[ 1697.514393] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1697.514454] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [219,251]
[ 1697.514515] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.514575] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.514636] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1697.514697] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1697.514758] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1697.514819] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1697.514880] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [205,205]
[ 1697.514941] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1697.515002] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515063] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515124] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515184] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515245] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515306] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515367] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515427] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1697.515488] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.576542] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1705.576553] iwlwifi 0000:08:00.0: Current SW read_ptr 17 write_ptr 92
[ 1705.576584] iwl data: 00000000: 00 00 fe ff 00 00 00 00 01 00 00 00 00 00 00 00  ................
[ 1705.576602] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1705.576619] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102020
[ 1705.576636] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1705.576653] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300021
[ 1705.576669] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1705.576686] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1705.576702] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1705.576719] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090e9
[ 1705.576782] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [34,34]
[ 1705.576844] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1705.576905] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [17,92]
[ 1705.576966] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577026] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577087] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1705.577148] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1705.577209] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1705.577271] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1705.577332] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [234,234]
[ 1705.577393] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1705.577454] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577515] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577576] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577637] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577698] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577759] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577820] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577881] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1705.577943] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.559817] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1709.559829] iwlwifi 0000:08:00.0: Current SW read_ptr 55 write_ptr 136
[ 1709.559860] iwl data: 00000000: 7f 00 00 00 00 00 00 00 00 00 80 ff 00 00 00 00  ................
[ 1709.559878] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1709.559895] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102046
[ 1709.559912] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1709.559928] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300022
[ 1709.559945] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1709.559962] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1709.559979] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1709.559995] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090f6
[ 1709.560058] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [35,35]
[ 1709.560119] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1709.560180] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [55,136]
[ 1709.560241] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.560303] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.560363] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1709.560425] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1709.560486] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1709.560547] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1709.560607] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [247,247]
[ 1709.560669] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1709.560729] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.560790] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.560851] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.560912] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.560972] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.561033] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.561094] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.561155] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1709.561216] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.587048] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1713.587056] iwlwifi 0000:08:00.0: Current SW read_ptr 72 write_ptr 176
[ 1713.587085] iwl data: 00000000: 00 ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 1713.587101] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1713.587117] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102057
[ 1713.587132] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1713.587147] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300023
[ 1713.587162] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1713.587177] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1713.587192] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1713.587207] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709000
[ 1713.587266] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [36,36]
[ 1713.587324] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1713.587383] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [72,176]
[ 1713.587441] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.587499] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.587557] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1713.587615] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1713.587673] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1713.587731] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1713.587789] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [1,1]
[ 1713.587847] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1713.587905] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.587963] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.588021] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.588079] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.588137] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.588195] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.588253] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.588311] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1713.588370] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.540622] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1720.540633] iwlwifi 0000:08:00.0: Current SW read_ptr 123 write_ptr 220
[ 1720.540664] iwl data: 00000000: ff 07 00 00 00 00 00 00 00 00 00 f8 00 00 00 00  ................
[ 1720.540682] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1720.540699] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010208a
[ 1720.540716] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1720.540732] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300024
[ 1720.540749] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1720.540766] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1720.540783] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1720.540800] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709018
[ 1720.540863] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [37,37]
[ 1720.540924] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1720.540985] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [123,220]
[ 1720.541047] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541108] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541169] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1720.541230] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1720.541291] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1720.541351] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1720.541412] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [25,25]
[ 1720.541473] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1720.541534] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541595] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541655] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541716] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541777] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541838] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541899] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.541960] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1720.542022] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.595868] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1724.595879] iwlwifi 0000:08:00.0: Current SW read_ptr 155 write_ptr 255
[ 1724.595910] iwl data: 00000000: 00 00 00 f8 00 00 00 00 ff 07 00 00 00 00 00 00  ................
[ 1724.595928] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1724.595945] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020aa
[ 1724.595962] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1724.595979] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300025
[ 1724.595995] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1724.596011] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1724.596028] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1724.596045] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709027
[ 1724.596107] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [38,38]
[ 1724.596169] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1724.596230] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [155,255]
[ 1724.596290] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.596351] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.596412] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1724.596473] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1724.596534] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1724.596596] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1724.596659] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [40,40]
[ 1724.596723] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1724.596789] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.596856] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.596920] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.596985] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.597050] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.597117] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.597182] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.597248] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1724.597311] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.539103] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1733.539114] iwlwifi 0000:08:00.0: Current SW read_ptr 234 write_ptr 64
[ 1733.539145] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 fc ff 03 00 00 00 00  ................
[ 1733.539163] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1733.539180] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020f9
[ 1733.539197] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1733.539213] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300026
[ 1733.539230] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1733.539247] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1733.539263] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1733.539280] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709050
[ 1733.539342] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [39,39]
[ 1733.539403] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1733.539464] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [234,64]
[ 1733.539525] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.539586] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.539646] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1733.539707] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1733.539768] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1733.539830] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1733.539891] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [81,81]
[ 1733.539952] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1733.540013] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540074] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540135] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540196] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540257] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540317] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540378] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540439] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1733.540500] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.592938] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 1750.592949] iwlwifi 0000:08:00.0: Current SW read_ptr 123 write_ptr 165
[ 1750.592981] iwl data: 00000000: ff 07 00 00 00 00 00 00 00 00 00 f8 00 00 00 00  ................
[ 1750.592998] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 1750.593015] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010208a
[ 1750.593032] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 1750.593049] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030002d
[ 1750.593065] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 1750.593082] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 1750.593098] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 1750.593115] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709077
[ 1750.593177] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [46,46]
[ 1750.593239] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1750.593300] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [123,165]
[ 1750.593361] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.593422] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.593483] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1750.593544] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 1750.593605] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1750.593665] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 1750.593726] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [120,120]
[ 1750.593788] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 1750.593849] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.593909] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.593970] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.594031] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.594092] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.594153] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.594213] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.594274] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 1750.594335] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.423647] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2036.423658] iwlwifi 0000:08:00.0: Current SW read_ptr 153 write_ptr 200
[ 2036.423689] iwl data: 00000000: 00 00 00 fe 00 00 00 00 ff 01 00 00 00 00 00 00  ................
[ 2036.423707] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2036.423724] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020a8
[ 2036.423741] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2036.423758] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300035
[ 2036.423774] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2036.423791] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2036.423808] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2036.423825] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070900d
[ 2036.423888] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [54,54]
[ 2036.423949] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2036.424010] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [153,200]
[ 2036.424071] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424133] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424194] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2036.424255] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2036.424315] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2036.424376] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2036.424437] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [14,14]
[ 2036.424498] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2036.424560] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424620] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424681] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424742] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424803] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424864] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424925] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.424986] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2036.425047] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.441332] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2276.441336] iwlwifi 0000:08:00.0: Current SW read_ptr 110 write_ptr 183
[ 2276.441361] iwl data: 00000000: 00 00 00 00 00 00 00 00 00 c0 ff 3f 00 00 00 00  ...........?....
[ 2276.441375] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2276.441389] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010207d
[ 2276.441403] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2276.441416] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030003a
[ 2276.441430] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2276.441443] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2276.441457] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2276.441470] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709068
[ 2276.441527] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [59,59]
[ 2276.441583] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2276.441638] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [110,183]
[ 2276.441694] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.441750] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.441806] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2276.441861] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2276.441917] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2276.441972] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2276.442028] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [105,105]
[ 2276.442084] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2276.442139] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442195] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442251] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442307] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442362] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442418] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442474] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442530] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2276.442586] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.028532] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2325.028544] iwlwifi 0000:08:00.0: Current SW read_ptr 64 write_ptr 103
[ 2325.028575] iwl data: 00000000: ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 2325.028593] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2325.028611] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x8010204f
[ 2325.028628] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2325.028644] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300040
[ 2325.028661] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2325.028678] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2325.028694] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2325.028711] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090bc
[ 2325.028773] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [65,65]
[ 2325.028834] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2325.028895] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [64,103]
[ 2325.028957] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029017] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029082] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2325.029150] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2325.029217] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2325.029281] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2325.029342] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [189,189]
[ 2325.029404] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2325.029465] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029526] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029587] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029647] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029708] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029774] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029837] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029898] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2325.029959] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.078949] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2328.078953] iwlwifi 0000:08:00.0: Current SW read_ptr 89 write_ptr 113
[ 2328.078979] iwl data: 00000000: 00 00 00 fe 00 00 00 00 ff 01 00 00 00 00 00 00  ................
[ 2328.078993] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2328.079007] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102068
[ 2328.079020] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2328.079034] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300041
[ 2328.079047] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2328.079061] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2328.079074] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2328.079088] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090c3
[ 2328.079144] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [66,66]
[ 2328.079200] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2328.079256] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [89,113]
[ 2328.079312] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.079368] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.079424] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2328.079480] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2328.079536] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2328.079591] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2328.079648] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [196,196]
[ 2328.079704] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2328.079759] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.079815] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.079871] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.079927] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.079983] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.080039] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.080095] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.080151] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2328.080207] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.062268] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2332.062280] iwlwifi 0000:08:00.0: Current SW read_ptr 122 write_ptr 133
[ 2332.062311] iwl data: 00000000: 1f 00 00 00 00 00 00 00 00 00 00 fc 00 00 00 00  ................
[ 2332.062330] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2332.062347] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x80102084
[ 2332.062364] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2332.062380] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300042
[ 2332.062396] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2332.062413] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2332.062429] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2332.062446] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x007090ce
[ 2332.062509] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [67,67]
[ 2332.062571] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2332.062632] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [122,133]
[ 2332.062693] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.062754] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.062815] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2332.062876] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2332.062937] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2332.062998] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2332.063059] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [207,207]
[ 2332.063120] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2332.063181] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063242] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063303] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063364] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063426] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063487] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063548] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063609] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2332.063670] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.246021] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2396.246032] iwlwifi 0000:08:00.0: Current SW read_ptr 204 write_ptr 8
[ 2396.246064] iwl data: 00000000: 00 f0 ff 0f 00 00 00 00 00 00 00 00 00 00 00 00  ................
[ 2396.246082] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2396.246098] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020db
[ 2396.246115] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2396.246132] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030004f
[ 2396.246148] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2396.246164] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2396.246181] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2396.246197] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709023
[ 2396.246260] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [80,80]
[ 2396.246321] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2396.246382] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [204,8]
[ 2396.246443] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.246504] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.246565] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2396.246626] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2396.246687] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2396.246747] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2396.246807] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [36,36]
[ 2396.246868] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2396.246929] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.246990] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.247050] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.247111] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.247171] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.247232] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.247293] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.247354] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2396.247415] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.576915] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2756.576926] iwlwifi 0000:08:00.0: Current SW read_ptr 189 write_ptr 103
[ 2756.576958] iwl data: 00000000: ff 1f 00 00 00 00 00 00 00 00 00 e0 00 00 00 00  ................
[ 2756.576976] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2756.576993] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020cc
[ 2756.577009] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2756.577026] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x80300093
[ 2756.577043] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2756.577059] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2756.577075] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2756.577092] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x0070906b
[ 2756.577153] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [148,148]
[ 2756.577215] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2756.577275] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [189,103]
[ 2756.577336] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.577397] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.577458] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2756.577519] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2756.577580] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2756.577640] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2756.577701] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [108,108]
[ 2756.577762] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2756.577824] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.577885] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.577945] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.578006] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.578067] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.578128] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.578189] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.578250] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2756.578311] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.424307] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 2
[ 2800.424318] iwlwifi 0000:08:00.0: Current SW read_ptr 219 write_ptr 108
[ 2800.424349] iwl data: 00000000: 00 00 00 f8 00 00 00 00 ff 07 00 00 00 00 00 00  ................
[ 2800.424367] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x00000000
[ 2800.424384] iwlwifi 0000:08:00.0: FH TRBs(1) = 0x801020ea
[ 2800.424401] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2800.424418] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x803000a4
[ 2800.424434] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2800.424451] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2800.424467] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2800.424484] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709097
[ 2800.424547] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [165,165]
[ 2800.424608] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2800.424670] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [219,108]
[ 2800.424731] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.424792] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.424853] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2800.424914] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2800.424974] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2800.425035] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2800.425096] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [152,152]
[ 2800.425158] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2800.425219] iwlwifi 0000:08:00.0: Q 11 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425280] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425341] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425401] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425462] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425523] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425584] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425645] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2800.425705] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2944.213615] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[ 2944.220960] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[ 2944.223817] wlan0: authenticated
[ 2944.224297] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[ 2944.228285] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=1)
[ 2944.248683] wlan0: associated

    ======== Done ========

```

---

### Post by varunendra on 2014-09-12
In Ubuntu, please set "IPv6" to "Ignore" in Network Manager, and try a driver parameter -
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
..and explicitly set your country's RegDomain code -
```
sudo sed -i 's/^REG.*=$/&IT/' /etc/default/crda
sudo iw reg set IT
```
Assuming (from you language setting) you are in ITaly, for which the regdomain code is "IT". If you are in some other country, please refer to this table to find the respective country code and replace "IT" with that in above commands : [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2#Decoding_table)

Reboot the computer after above two changes, and reconnect to see if things improved.

Whether they improved or not, it is highly recommended that you also change the encryption in your router/Access-Point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP. Reboot the router also after saving the change. Sometimes some routers may take two consecutive reboots (after a gap of a minute or two) after such a change.

If these changes don't seem to help, please post a fresh report showing the status after the change.

**PS:**
I think you should delete the backup file of /etc/modprobe.d/iwlwifi.conf that is automatically created when you edit it using your GUI text editor. May not be necessary, but won't hurt either -
```
sudo rm /etc/modprobe.d/**iwlwifi.conf~**
```
Note the "~" in the filename - very important, else you will delete the main file instead. :)

---

### Post by Anidro on 2014-09-13
Using the code suggested I improve my wifi behaviour. Now the connection is stable but not always fast. Sometime I have to reboot firefox because I can not load google pages. Furthermore, I think could be problem with signal signal level (the wifi is faster near router). 

I post wireless_script fresh report: 

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

luigi-Lenovo-IdeaPad-Y510P 3.13.0-36-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i7-4700MQ CPU @ 2.40GHz
Memory : 15961 MB
Uptime : 17:19:01 up 54 min,  2 users,  load average: 0,12, 0,20, 0,27


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

07:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8171 Gigabit Ethernet [1969:10a1] (rev 10)
    Subsystem: Lenovo Device [17aa:3800]
    Kernel driver in use: alx
08:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0888] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4262]
    Kernel driver in use: iwlwifi


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 8087:07da Intel Corp. 
Bus 003 Device 005: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 003 Device 002: ID 174f:1474 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"LUIGI-HP_Network"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC C-01 LUIGI-HP_Network>   
          Bit Rate=45 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=22/70  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:155  Invalid misc:522   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                  Soft blocked  Hard blocked
0: ideapad_wlan: Wireless LAN        no            no
1: ideapad_bluetooth: Bluetooth      yes           no
2: hci0: Bluetooth                   no            no
3: phy0: Wireless LAN                no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

iwldvm                232285  0 
mac80211              630653  1 iwldvm
iwlwifi               169932  1 iwldvm
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
wmi                    19177  0 


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
iwlwifi      (11): 11n_disable=8 | amsdu_size_8K=0 | antenna_coupling=0 | bt_coex_active=Y | fw_restart=Y | led_mode=0 | nvm_file=(null) | power_level=0 | power_save=N | swcrypto=0 | wd_disable=1
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===========================o=============o=========o=============o=========o===========o==============o===========
 Interface & ID            | Type        | Driver  | State       | Default | Speed     | Support      | HW Addr   
===========================o=============o=========o=============o=========o===========o==============o===========
 wlan0  [LUIGI-HP_Network] | 802.11 WiFi | iwlwifi | connected   | yes     | 30 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    Alice-73522017:  Infra, <MAC C-02 Alice-73522017>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44 WPA WPA2
    D-Link_deri:     Infra, <MAC C-07 D-Link_deri>, Freq 2462 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Alice-35868379:  Infra, <MAC C-05 Alice-35868379>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    vgn:             Infra, <MAC C-04 vgn>, Freq 2417 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Alice-73522017:  Infra, <MAC C-03 Alice-73522017>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    Alice-18152354:  Infra, <MAC C-06 Alice-18152354>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    D-Link_deri:     Infra, <MAC C-08 D-Link_deri>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    *LUIGI-HP_Network: Infra, <MAC C-01 LUIGI-HP_Network>, Freq 2427 MHz, Rate 54 Mb/s, Strength 43 WPA2

    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.168.0.1
    DNS:             8.8.8.8
---------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------
 eth0                      | Wired       | alx     | unavailable | no      |           |              | <MAC eth0>
---------------------------+-------------+---------+-------------+---------+-----------+--------------+-----------


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

Alfa-Omega           : ssid=Alfa-Omega | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
LUIGI-HP_Network     : ssid=LUIGI-HP_Network | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 2.012/2.591/3.171/0.581 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.039/0.042/0.046/0.007 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "it_IT.UTF-8")
country IT:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.427 GHz (Channel 4)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 LUIGI-HP_Network>
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"LUIGI-HP_Network"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000045e086e07
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Alice-73522017>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Alice-73522017"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000002896e3de8a
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Alice-73522017>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"Alice-73522017"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000004a3f70
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 vgn>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"vgn"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000028999eeb61
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Alice-35868379>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Alice-35868379"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000013b1044824
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 Alice-18152354>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Alice-18152354"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000001b9cc842d0
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 D-Link_deri>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"D-Link_deri"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000025d5ffac
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 D-Link_deri>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"D-Link_deri"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[iwldvm]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/dvm/iwldvm.ko
version:        in-tree:
srcversion:     CC4D1BA11C1EF73A6ABDE53
depends:        iwlwifi,mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/mac80211/mac80211.ko
srcversion:     B822641624778B987844F6F
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
version:        in-tree:
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-7265-7.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
srcversion:     C2D0F3DFCA289585C100E36
depends:        cfg80211
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           nvm_file:NVM file name (charp)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)

[cfg80211]
filename:       /lib/modules/3.13.0-36-generic/kernel/net/wireless/cfg80211.ko
srcversion:     C2478077E22138832B71659
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[wmi]
filename:       /lib/modules/3.13.0-36-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x1969:0x10a1 (alx)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x0888 (iwlwifi)
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
                    options iwlwifi 11n_disable=8
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.13.0-36-generic.efi.signed root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.103696] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.103938] audit: initializing netlink socket (disabled)
[    1.465529] alx 0000:07:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [<MAC eth0>]
[    2.119518] psmouse serio1: elantech: assuming hardware version 4 (with firmware version 0x461f01)
[    3.711866] wmi: Mapper loaded
[    3.799619] iwlwifi 0000:08:00.0: can't disable ASPM; OS doesn't have ASPM control
[    3.799667] iwlwifi 0000:08:00.0: irq 47 for MSI/MSI-X
[    3.813506] iwlwifi 0000:08:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[    3.829324] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    3.829327] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    3.829328] iwlwifi 0000:08:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    3.829330] iwlwifi 0000:08:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[    3.829378] iwlwifi 0000:08:00.0: L1 Disabled; Enabling L0S
[    3.862315] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    4.028184] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.165723] iwlwifi 0000:08:00.0: L1 Disabled; Enabling L0S
[    4.173204] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[    4.415762] iwlwifi 0000:08:00.0: L1 Disabled; Enabling L0S
[    4.424069] iwlwifi 0000:08:00.0: Radio type=0x2-0x0-0x0
[    4.484593] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.484789] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    4.997653] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[    5.004646] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[    5.007346] wlan0: authenticated
[    5.007427] wlan0: waiting for beacon from <MAC C-01 LUIGI-HP_Network>
[    5.105022] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[    5.108928] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=3)
[    5.131377] wlan0: associated
[    5.131405] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2028.715361] wlan0: deauthenticating from <MAC C-01 LUIGI-HP_Network> by local choice (reason=3)
[ 2029.293192] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[ 2029.302247] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[ 2029.305360] wlan0: authenticated
[ 2029.306130] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[ 2029.310030] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=3)
[ 2029.332378] wlan0: associated
[ 2342.819406] wlan0: deauthenticating from <MAC C-01 LUIGI-HP_Network> by local choice (reason=3)
[ 2343.314567] wlan0: authenticate with <MAC C-01 LUIGI-HP_Network>
[ 2343.323252] wlan0: send auth to <MAC C-01 LUIGI-HP_Network> (try 1/3)
[ 2343.326026] wlan0: authenticated
[ 2343.328463] wlan0: associate with <MAC C-01 LUIGI-HP_Network> (try 1/3)
[ 2343.332291] wlan0: RX AssocResp from <MAC C-01 LUIGI-HP_Network> (capab=0x411 status=0 aid=3)
[ 2343.353499] wlan0: associated
[ 2652.570933] iwlwifi 0000:08:00.0: fail to flush all tx fifo queues Q 11
[ 2652.570943] iwlwifi 0000:08:00.0: Current SW read_ptr 238 write_ptr 60
[ 2652.570974] iwl data: 00000000: ff 01 00 00 0f 00 00 00 00 c0 ff ff 00 00 00 fe  ................
[ 2652.570992] iwlwifi 0000:08:00.0: FH TRBs(0) = 0x80003005
[ 2652.571009] iwlwifi 0000:08:00.0: FH TRBs(1) = 0xc010b008
[ 2652.571026] iwlwifi 0000:08:00.0: FH TRBs(2) = 0x00000000
[ 2652.571043] iwlwifi 0000:08:00.0: FH TRBs(3) = 0x8030008d
[ 2652.571059] iwlwifi 0000:08:00.0: FH TRBs(4) = 0x00000000
[ 2652.571076] iwlwifi 0000:08:00.0: FH TRBs(5) = 0x00000000
[ 2652.571092] iwlwifi 0000:08:00.0: FH TRBs(6) = 0x00000000
[ 2652.571108] iwlwifi 0000:08:00.0: FH TRBs(7) = 0x00709094
[ 2652.571171] iwlwifi 0000:08:00.0: Q 0 is active and mapped to fifo 3 ra_tid 0x0000 [142,142]
[ 2652.571232] iwlwifi 0000:08:00.0: Q 1 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2652.571294] iwlwifi 0000:08:00.0: Q 2 is active and mapped to fifo 1 ra_tid 0x0000 [56,56]
[ 2652.571354] iwlwifi 0000:08:00.0: Q 3 is active and mapped to fifo 0 ra_tid 0x0000 [6,6]
[ 2652.571414] iwlwifi 0000:08:00.0: Q 4 is active and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2652.571475] iwlwifi 0000:08:00.0: Q 5 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2652.571535] iwlwifi 0000:08:00.0: Q 6 is active and mapped to fifo 2 ra_tid 0x0000 [0,0]
[ 2652.571596] iwlwifi 0000:08:00.0: Q 7 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2652.571657] iwlwifi 0000:08:00.0: Q 8 is active and mapped to fifo 4 ra_tid 0x0000 [0,0]
[ 2652.571717] iwlwifi 0000:08:00.0: Q 9 is active and mapped to fifo 7 ra_tid 0x0000 [149,149]
[ 2652.571778] iwlwifi 0000:08:00.0: Q 10 is active and mapped to fifo 5 ra_tid 0x0000 [0,0]
[ 2652.571839] iwlwifi 0000:08:00.0: Q 11 is active and mapped to fifo 1 ra_tid 0x0000 [238,60]
[ 2652.571900] iwlwifi 0000:08:00.0: Q 12 is inactive and mapped to fifo 3 ra_tid 0x0006 [48,48]
[ 2652.571962] iwlwifi 0000:08:00.0: Q 13 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2652.572023] iwlwifi 0000:08:00.0: Q 14 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2652.572084] iwlwifi 0000:08:00.0: Q 15 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2652.572144] iwlwifi 0000:08:00.0: Q 16 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2652.572205] iwlwifi 0000:08:00.0: Q 17 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2652.572266] iwlwifi 0000:08:00.0: Q 18 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]
[ 2652.572327] iwlwifi 0000:08:00.0: Q 19 is inactive and mapped to fifo 0 ra_tid 0x0000 [0,0]

    ======== Done ========

```

Other suggest to further improve my wifi connection??

---

### Post by varunendra on 2014-09-13
> **Anidro said:**
> ```
iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"LUIGI-HP_Network"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC C-01 LUIGI-HP_Network>   
          Bit Rate=45 Mb/s   **Tx-Power=16 dBm**   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
         ** Link Quality=[COLOR="#FF0000"]22/70[/COLOR]**  Signal level=-88 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:155  Invalid misc:522   Missed beacon:0
```

Sorry, with the above level of signal, I don't think we can do much.

The only thing we can do about signal strength at software end is to *try* increasing the transmission signal strength, and even that is not guaranteed to work as only some cards support that. We can't increase the 'Received' signal strength from the OS at all (obviously).

There are a couple of other driver parameters as well that can be tried, but if the speed is good when you are closer to the access-point, I don't think they can make up for the signal loss due to longer distance.

For now, the easiest thing you can try is to set "IPv6" to "Ignore" in Network Manager.

How far are you from the Access-Point when the signal strength shows 22/70 like above? Walls/roofs/floors in-between?

---

### Post by Anidro on 2014-09-15
I have a Netgear N300 Wireless DSL Modem Router DGN2200. The router is 7-8 meters away from the computer but there are 2 walls, a library and a wardrobe between the computer and the router. But with my old laptop windows (Hp Pavilion dv3105) I do not have signal problem. This problem is related to the wifi card of new laptop or to linux driver? I will try to disable IPv6 in Network Manager.

---

### Post by varunendra on 2014-09-16
It could be the card, but for what it is worth, we had a similar situation in my previous work place - a Netgear Router/AP (150 Mbps), a distance of about 6-7 meters, two 13" brick walls in-between. The old laptop (running windows XP or 7, don't remember) was barely able to connect to it with frequent disconnections, signal being lost frequently.

Tried a new Asus router/AP (150 Mbps), and the signal jumped to almost maximum, with a rock-solid connection. Same laptop, same OS, same distance and placement. Since then, I don't trust Netgears much. Oh, and the Asus wasn't any costlier either.

I don't remember the driver iwlwifi being reported for weaker signal reception compared to any other drivers, windows or linux ones. Maybe check the card's antenna connections as well. It is not uncommon for them to get loose over time, and causing problems like this.

---

### Post by Anidro on 2014-09-16
I have set "IPv6" to "Ignore" in Network Manager and my connection has further improved.
I think that the last problem is related only to signal level.
Thank you very much for help!!

Last question: what sets the following code?

```
 
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf

```

---

### Post by varunendra on 2014-09-17
> **Anidro said:**
> Last question: what sets the following code?

```
 
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf

```

The description of the parameter in "modinfo iwlwifi" says -
```
parm:           **11n_disable:**disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, **8 enable agg TX** (uint)
```

So, as per my own understanding, it enables aggregation of TX (Transmission) frames/packets. Some further searching tells me it is aggregation of 'AMPDU'. A good description/comparison here : [http://ergodicthoughts.blogspot.in/2012/02/difference-between-mpdu-msdu-ampdu-and.html](http://ergodicthoughts.blogspot.in/2012/02/difference-between-mpdu-msdu-ampdu-and.html)
> AMPDU: These are are the aggregated MPDU units which are pushed into a single PPDU (physical protocol data unit).  All frames will have a single PLCP header and preamble.

So basically, it just enables pushing larger chunk of data with every transmitted packet, thus attempting to push more data per second.

---

