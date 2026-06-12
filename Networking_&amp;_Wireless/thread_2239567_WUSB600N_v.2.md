---
title: "WUSB600N v.2"
date: 2014-08-14
forum: Networking &amp; Wireless
---

### Post by dimitarrosenovkolev on 2014-08-14
I am trying to make the wireless addapter WUSB600N to work under Ubuntu 14.04.

I have internet but it will randomly hang and I have to unplug and plug it back in. Has anyone been able to make it work? Can you explain how, please?

---

### Post by varunendra on 2014-08-15
Welcome to the forums dimitarrosenovkolev!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by dimitarrosenovkolev on 2014-08-15
@varunendra thank you for your replay! :)

I am at work at the moment but once I go home I will do as you asked!

---

### Post by varunendra on 2014-08-15
Can't promise a timely reply due to office tasks, but make sure to post the update in a new post, else your post won't get highlighted in search results and I won't know you have posted an update.

If I happen to be unable to reply in time, feel free to invite other potential helpers (via PM) to take a look at your thread. Alternatively, you may (should) bump your thread every 24 hours or more if nobody replies in that time.

---

### Post by dimitarrosenovkolev on 2014-08-15
Thank you for the explanation. I will make sure it is bumped.

Here is the output of the script. This is with the usb-adapter.

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

noname-OptiPlex-990 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i5-2400 CPU @ 3.10GHz
Memory : 3832 MB
Uptime : 22:21:03 up 36 min,  2 users,  load average: 1,43, 1,33, 1,05


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Dell Device [1028:047e]
    Kernel driver in use: e1000e


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 004: ID 04d9:1702 Holtek Semiconductor, Inc. 
Bus 002 Device 003: ID 09da:0080 A4 Tech Co., Ltd 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 1737:0079 Linksys WUSB600N v2 Dual-Band Wireless-N Network Adapter [Ralink RT3572]
Bus 001 Device 004: ID 0480:a007 Toshiba America Info. Systems, Inc. External Disk USB 3.0
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"the home"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC C-01 the home>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:170  Invalid misc:115   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
mac80211              630653  3 rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  2 mac80211,rt2x00lib
crc_ccitt              12707  1 rt2800lib


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rt2800usb     (1): nohwcrypt=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
=====================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID      | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
=====================o=============o===========o=============o=========o===========o==============o===========
 wlan0  [the home 1] | 802.11 WiFi | rt2800usb | connected   | yes     | 54 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    Ziggo81444:      Infra, <MAC C-04 Ziggo81444>, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Ziggo:           Infra, <MAC C-05 Ziggo>, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA2 Enterprise
    Sitecom:         Infra, <MAC C-03 Sitecom>, Freq 2462 MHz, Rate 54 Mb/s, Strength 25 WEP
    *the home:       Infra, <MAC C-01 the home>, Freq 2462 MHz, Rate 54 Mb/s, Strength 73 WPA WPA2
    Sitecom:         Infra, <MAC C-02 Sitecom>, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WEP

    Address:         192.168.1.7
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
---------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 eth0                | Wired       | e1000e    | unavailable | no      |           |              | <MAC eth0>
---------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

Tele2-1              : ssid=Tele2-1 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
the home             : ssid=the home | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
the home 1           : ssid=the home | ipv4=auto | ipv6=auto 
Ziggo39441           : ssid=Ziggo39441 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


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
rtt min/avg/max/mdev = 5.580/5.586/5.592/0.006 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.029/0.030/0.031/0.001 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : nl_NL.UTF-8)
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     27 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 151 (5.755 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 159 (5.795 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency:2.462 GHz (Channel 11)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 the home>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"the home"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000006c5ee511bfd
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Sitecom>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Sitecom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000009307caeb02
                    Extra: Last beacon: 28ms ago
          Cell 03 - Address: <MAC C-03 Sitecom>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Sitecom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000092d8093d94
                    Extra: Last beacon: 28ms ago
          Cell 04 - Address: <MAC C-04 Ziggo81444>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"Ziggo81444"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000034031c0d1e7
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Ziggo>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Ziggo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000034031c0f363
                    Extra: Last beacon: 28ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[rt2800usb]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
firmware:       rt2870.bin
version:        2.3.0
srcversion:     D6F814DAF78F2BEA3DA12CB
depends:        rt2x00lib,rt2800lib,rt2x00usb
parm:           nohwcrypt:Disable hardware encryption. (bool)

[rt2x00usb]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
version:        2.3.0
srcversion:     44768071492503F8EFE1EED
depends:        rt2x00lib,mac80211

[rt2800lib]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
version:        2.3.0
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt

[rt2x00lib]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
version:        2.3.0
srcversion:     CC69EE39E7D673974A21C0A
depends:        mac80211,cfg80211

[mac80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/mac80211/mac80211.ko
srcversion:     8ADA881D348148A3358334C
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
srcversion:     E786D076B61F97809B04B64
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[crc_ccitt]
filename:       /lib/modules/3.13.0-32-generic/kernel/lib/crc-ccitt.ko
srcversion:     2294FCAD06D727386004EEB
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1502 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modules]
rt3572sta

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en
rt3572sta.conf    : install rt3572sta modprobe --ignore-install rt3572sta ; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id
rt3572sta.conf~   : install rt3572sta modprobe --ignore-install rt3572sta ; /bin/echo "1737 0079" > /sys/bus/usb/drivers/rt2870/new_id


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=11000dc4-929f-4242-8f9a-b739b4bbd889 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.413853] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.414130] audit: initializing netlink socket (disabled)
[   18.072565] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  162.998808] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3572, rev 0221 detected
[  163.027112] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0009 detected
[  163.035481] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[  163.058877] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[  163.403693] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  163.404153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  169.515461] wlan0: authenticate with <MAC C-01 the home>
[  169.564430] wlan0: send auth to <MAC C-01 the home> (try 1/3)
[  169.566055] wlan0: authenticated
[  169.566181] rt2800usb 1-1.4:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  169.566185] rt2800usb 1-1.4:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  169.567547] wlan0: associate with <MAC C-01 the home> (try 1/3)
[  169.569847] wlan0: RX AssocResp from <MAC C-01 the home> (capab=0x411 status=0 aid=1)
[  169.576768] wlan0: associated
[  169.576793] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  169.605726] wlan0: deauthenticating from <MAC C-01 the home> by local choice (reason=2)
[  169.635577] wlan0: authenticate with <MAC C-01 the home>
[  169.640268] wlan0: send auth to <MAC C-01 the home> (try 1/3)
[  169.641910] wlan0: authenticated
[  169.642053] rt2800usb 1-1.4:1.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  169.642057] rt2800usb 1-1.4:1.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  169.643516] wlan0: associate with <MAC C-01 the home> (try 1/3)
[  169.645654] wlan0: RX AssocResp from <MAC C-01 the home> (capab=0x411 status=0 aid=1)
[  169.652608] wlan0: associated
[  301.934772] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  301.934790] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  301.934793] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[  301.942390] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  301.942394] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[  301.942401] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[  301.947166] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  301.947182] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  301.947184] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[  301.950547] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[  301.952810] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  302.133609] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  302.133724] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  302.133856] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[  302.133973] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.021201] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1179.021222] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1179.021225] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1179.045571] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1179.045584] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1179.045587] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1179.050068] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1179.050085] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1179.050088] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1179.077190] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.077318] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.083188] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.485599] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1179.485620] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1179.485624] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1179.485660] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 1179.485672] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 1179.485682] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1179.485693] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 1179.485708] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[ 1179.485727] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[ 1179.488981] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1179.489026] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1179.489032] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1179.489069] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[ 1179.489083] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 1179.489094] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1179.489103] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1179.489114] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[ 1179.489123] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[ 1179.509253] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[ 1179.509281] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[ 1179.509284] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[ 1179.589197] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 1179.589216] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 1179.589219] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 1179.589258] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 1179.589270] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 1179.589280] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 1179.589290] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 1179.589305] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 1179.589324] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[ 1179.593693] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[ 1179.593704] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[ 1179.593706] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[ 1179.593715] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 1179.593717] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 7 in queue 2
[ 1179.593719] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 1179.593721] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 1179.593723] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 1179.593725] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[ 1179.613942] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[ 1179.613959] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[ 1179.613963] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[ 1179.673182] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.673307] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.673429] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.691339] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.691455] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.691580] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.691687] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.691812] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.691922] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692078] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692204] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692298] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692422] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692546] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692674] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692798] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.692945] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.693047] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.699975] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.705696] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.706945] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.707046] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.707169] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.707293] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.707418] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.786416] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.786574] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.786652] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.786776] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.786900] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 1179.793778] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[ 1179.793828] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[ 1179.793833] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 0
[ 1179.900008] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 0, dropping
[ 2066.890072] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 2066.890092] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 2066.890095] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 2066.902423] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 2066.902432] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 2066.902435] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 2066.918195] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 2066.918223] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 2066.918225] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 2066.949673] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 2066.949691] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 2066.949694] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 2066.949728] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 2066.966535] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 2066.966558] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 2066.966562] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 2066.966608] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[ 2066.966621] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[ 2066.974419] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 2066.974442] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 2066.974446] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 2067.063887] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.064006] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.064133] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.064256] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.084537] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.084657] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.084768] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.084892] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.099386] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.294085] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 2067.294097] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 2067.294100] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 8 in queue 2
[ 2067.306455] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 2067.306491] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 2067.306494] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 9 in queue 2
[ 2067.309826] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 2067.309833] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 2067.309835] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 10 in queue 2
[ 2067.322205] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[ 2067.322264] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[ 2067.322266] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 11 in queue 2
[ 2067.322312] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 12 in queue 2
[ 2067.322326] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[ 2067.322337] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 14 in queue 2
[ 2067.325611] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 2067.325669] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 2067.325672] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 15 in queue 2
[ 2067.369441] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 2067.369486] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 2067.369489] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 0 in queue 2
[ 2067.369533] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 1 in queue 2
[ 2067.369541] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 2 in queue 2
[ 2067.373962] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 2067.373981] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 2067.373984] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 3 in queue 2
[ 2067.374017] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 4 in queue 2
[ 2067.374025] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 5 in queue 2
[ 2067.374032] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 6 in queue 2
[ 2067.383441] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.383563] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.383683] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.383812] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.383936] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384061] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384187] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384312] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384436] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384561] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384688] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384851] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.384938] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.416471] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping
[ 2067.428202] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping

    ======== Done ========

```

---

### Post by varunendra on 2014-08-15
A few things to try -

[indent]**1)** Please turn "Power Management" off at your wireless interface -
```
sudo iwconfig wlan0 power off
```
This may alone solve the problem, but you may need to run it at every boot. If it seems to be the solution we can make it automatic so you don't have to run it manually at every boot.

**2)** Change the encryption type in your router to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP. Refer to your router's user manual to see how to change that.

**3)** Set "IPv6" to "Ignore" in Network Manager settings for the connection.

**4)** If required, try a driver parameter -
```
sudo modprobe -rv rt2800usb
sudo modprobe -v rt2800usb nohwcrypt=Y
```
The first command will remove the driver disabling wifi. The second will reload it with the 'nohwcrypt=Y' parameter. It'll be a temporary change that will be lost at next boot. If it seems to help, we can make it permanent.[/indent]

Of these, suggestions 2 and 3 can be applied along with suggestion 1, but try 4 only if required (if the first three changes don't seem to help).

After applying suggestion 1, use -
```
iwconfig
```
..command to make sure "Power Management" indeed turned off and remains that way (check again with the above command if the problem occurs again).

Let us know what works, if any of the above.

---

### Post by dimitarrosenovkolev on 2014-08-16
@varunendra I have implemented option #1
```

sudo iwconfig wlan0 power off

```
 from post #6. It has been a few hours with 1+ media streaming platforms open (youtube, twitch) and running. I have had no problems since.

I will wait for 12 hours and if it does not hang I will mark this thread as solved (your signature is very useful).

Thank you for your help.:p

---

### Post by dimitarrosenovkolev on 2014-08-16
It has been 12 hours without it freezing/stopping.

Thank you for your help! That was very quick and simple.:p 

It seems option #1 was enough. I will mark this thread as solved.

---

### Post by varunendra on 2014-08-17
Glad it helped you too. :)

If you need to run the command at every boot, you may try the last two commands suggested in this post : [http://ubuntuforums.org/showthread.php?t=2239432&p=13099321#post13099321](http://ubuntuforums.org/showthread.php?t=2239432&p=13099321#post13099321)
(Ignore the first "sudo make uninstall" command, it is not relevant to your problem. Try only the 2nd one, and if it doesn't work, try the 3rd one).

---

