---
title: "ralink RT5372 ubuntu 14.10 slow internet"
date: 2014-11-23
forum: Networking &amp; Wireless
---

### Post by LngtOchFintNamn on 2014-11-23
Hello
I've been searching the internet for days trying to find a solution to my problem, tried all solutions to similar issues I could find, no luck. Hoping someone here can solve it for me.
My problem, I can not get decent speed over wireless, can barely load webpages, when I manage to load a speed test site and measure I get around 1Mbit/s (my line is 100), I get 20-30 over wireless using my windows7 laptop, both with the built in card and the ralink USB one. Getting around 100 connected with cable.

The card I'm using (plexgear WU300) seems to have a ralink RT5372 inside. (windows identify it as RT5390)
Ubuntu version 14.10 quite fresh install.

I tried so far: install different drivers, downloaded from manufacturer webpage. This failed during make, they will not build. This seems to be, my google-fu tells me, a known problem that is solved for kernel version 2 with a patch, but not for version 3. And mainly for the problem of the card not working at all, mine is sorta working, just badly.
I have also tried ndiswrapper, but the drivers I dug out from my windows machine will not work, and I have found no other around the internet.
I've tried different settings on my router, running b,g without n, different channels.

I'm quite the novice in using Linux so please bear that in mind when answering.

Any ideas on how to solve this would be very appreciated.


Wireles script output:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

desktop 3.16.0-24-generic x86_64,  Ubuntu 14.10, utopic

CPU    : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
Memory : 3826 MB
Uptime : 20:27:29 up  1:36,  2 users,  load average: 0,45, 0,57, 0,58


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

3f:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755 Gigabit Ethernet PCI Express [14e4:167b] (rev 02)
    Subsystem: Hewlett-Packard Company DC5750 Microtower [103c:280a]
    Kernel driver in use: tg3


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 004: ID 0bda:0111 Realtek Semiconductor Corp. RTS5111 Card Reader Controller
Bus 001 Device 003: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"kramkalas"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 kramkalas>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:41   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800usb              27139  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              93180  1 rt2800usb
rt2x00lib              55170  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              660592  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              510218  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
wmi                    19193  1 hp_wmi


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~


NetworkManager.conf ~~~~~~~~~~~~~~~~



NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

kramkalas            : ssid=kramkalas | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 193.150.193.150
nameserver 83.255.245.11


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.779/5.167/5.556/0.395 ms

--- 193.150.193.150 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 33.515/35.962/38.409/2.447 ms

--- 83.255.245.11 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 49.760/84.904/120.049/35.145 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : sv_SE.UTF-8)
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), NO-IR
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, NO-IR
    (5170 - 5250 @ 40), (3, 20), NO-IR
    (5735 - 5835 @ 40), (3, 20), NO-IR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 kramkalas>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"kramkalas"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000177a9a626
                    Extra: Last beacon: 196ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 ComHem37509>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"ComHem37509"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000db3018e18e
                    Extra: Last beacon: 220ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 ComHem521FC8>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"ComHem521FC8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000185db396b1
                    Extra: Last beacon: 164ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 3Bredband-E5172A-7NHD>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=19/70  Signal level=-91 dBm  
                    Encryption key:on
                    ESSID:"3Bredband-E5172A-7NHD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000df86a8b7b
                    Extra: Last beacon: 4236ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 ASUSBRD>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"ASUSBRD"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000011b95f2a530
                    Extra: Last beacon: 4184ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 WST>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:on
                    ESSID:"WST"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000185d09c45f
                    Extra: Last beacon: 2640ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2800usb]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     0AD26E80763D965C684523C
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     21417B97E30FD4E6E469E1F
depends:        rt2x00lib,mac80211

[rt2800lib]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     8D9F59A658EAF90D8F1EF97
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     02B2F4D2982AACC016889FC
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.16.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     0D5DBE66E4CC44B010DB516
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     DEE8EAA48495E392CD51C2D
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[crc_ccitt]
filename:       /lib/modules/3.16.0-24-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        

[hp_wmi]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/platform/x86/hp-wmi.ko
srcversion:     2BEC5DCE5B3A6695D374C6A
depends:        wmi,sparse-keymap

[wmi]
filename:       /lib/modules/3.16.0-24-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     347CF30B94B5549A75865A8
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:0x167b (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : options iwlwifi 11n_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en
modesetting.conf  : options cirrus modeset=1
                    options mgag200 modeset=1


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/vmlinuz-3.16.0-24-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.018340] Initializing cgroup subsys net_cls
[    0.018358] Initializing cgroup subsys net_prio
[    1.191897] audit: initializing netlink subsys (disabled)
[    1.627799] wmi: Mapper loaded
[    1.723755] tg3 0000:3f:00.0 eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   64.628568] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[   64.663318] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5372 detected
[   65.121248] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   72.752583] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   72.871751] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   73.103867] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.263970] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   83.276161] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   87.452538] wlan0: authenticate with <MAC C-01 kramkalas>
[   87.497807] wlan0: direct probe to <MAC C-01 kramkalas> (try 1/3)
[   87.700025] wlan0: direct probe to <MAC C-01 kramkalas> (try 2/3)
[   87.904030] wlan0: direct probe to <MAC C-01 kramkalas> (try 3/3)
[   88.108024] wlan0: authentication with <MAC C-01 kramkalas> timed out
[   92.528379] wlan0: authenticate with <MAC C-01 kramkalas>
[   92.553846] wlan0: direct probe to <MAC C-01 kramkalas> (try 1/3)
[   92.756024] wlan0: direct probe to <MAC C-01 kramkalas> (try 2/3)
[   92.960025] wlan0: direct probe to <MAC C-01 kramkalas> (try 3/3)
[   93.164024] wlan0: authentication with <MAC C-01 kramkalas> timed out
[  111.188537] wlan0: authenticate with <MAC C-01 kramkalas>
[  111.233844] wlan0: send auth to <MAC C-01 kramkalas> (try 1/3)
[  111.251796] wlan0: authenticated
[  111.251820] rt2800usb 1-5:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  111.251822] rt2800usb 1-5:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  111.252150] wlan0: associate with <MAC C-01 kramkalas> (try 1/3)
[  111.321046] wlan0: RX AssocResp from <MAC C-01 kramkalas> (capab=0x411 status=0 aid=2)
[  111.327667] wlan0: associated
[  111.327692] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  119.217169] wlan0: deauthenticating from <MAC C-01 kramkalas> by local choice (Reason: 3=DEAUTH_LEAVING)
[  119.555825] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  119.975868] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  120.267772] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  122.475818] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  269.295931] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  270.208383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  272.505077] wlan0: authenticate with <MAC C-01 kramkalas>
[  272.535160] wlan0: send auth to <MAC C-01 kramkalas> (try 1/3)
[  272.570192] wlan0: send auth to <MAC C-01 kramkalas> (try 2/3)
[  272.573842] wlan0: authenticated
[  272.573892] rt2800usb 1-5:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  272.573899] rt2800usb 1-5:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  272.576045] wlan0: associate with <MAC C-01 kramkalas> (try 1/3)
[  272.582961] wlan0: RX AssocResp from <MAC C-01 kramkalas> (capab=0x411 status=0 aid=2)
[  272.589685] wlan0: associated
[  272.589750] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  552.562413] wlan0: deauthenticating from <MAC C-01 kramkalas> by local choice (Reason: 3=DEAUTH_LEAVING)
[  552.911984] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5772.464272] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5772.775956] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5773.632036] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5775.844920] wlan0: authenticate with <MAC C-01 kramkalas>
[ 5775.869853] wlan0: send auth to <MAC C-01 kramkalas> (try 1/3)
[ 5775.873779] wlan0: authenticated
[ 5775.873805] rt2800usb 1-5:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 5775.873808] rt2800usb 1-5:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 5775.876033] wlan0: associate with <MAC C-01 kramkalas> (try 1/3)
[ 5775.939943] wlan0: RX AssocResp from <MAC C-01 kramkalas> (capab=0x411 status=0 aid=2)
[ 5775.948817] wlan0: associated
[ 5775.948885] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

    ======== Done ========
```

---

