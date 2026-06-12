---
title: "VERY slow internet after installing Ubuntu 14.04"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by S2005x on 2014-09-10
So, the wife and I decided to give Ubuntu a shot. Never used linux before. Formatted her computer, and installed Ubuntu. The wireless USB dongle we had, was incompatable. I purchased one on Amazon, a Panda PAU03. I plugged it into the USB port, booted the computer, and it allows me to connect to our WiFi, but it is EXTREMELY slow. I finally got Chrome installed, and ran a speed test at Ookla.com, and I was getting less than 1Mb/s.

[[IMG]http://www.speedtest.net/result/3751663804.png[/IMG]](http://www.speedtest.net/my-result/3751663804)

---

### Post by varunendra on 2014-09-10
Welcome to the forums steven47!

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by S2005x on 2014-09-10
Thanks so much for the reply!!! 

I have it re-installing Ubuntu right now : \ Thought maybe that would help. As soon as it is done, I'll do what you recommended and post the results :D

I had an extra GPU laying around that was better than the one in the case, and a better HDD too, so I made those changes, and am re-installing now.

**EDIT**

Thank you for the welcome! Minor question, is there a way to change my username? Steven47 isn't exactly what I'd like to use... : \

---

### Post by varunendra on 2014-09-11
> **steven47 said:**
> ..is there a way to change my username?..

Yes, there is a system for that. Please post your request as a new thread in the "**[Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123")**" section of the forum, and wait for an admin to have a look at it. They monitor and serve the requests on a regular basis.

---

### Post by S2005x on 2014-09-11
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

jenny-H61MU3 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz
Memory : 7968 MB
Uptime : 23:32:52 up 5 min,  2 users,  load average: 0.30, 0.53, 0.31


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Biostar Microtech Int'l Corp Device [1565:230a]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 003: ID 04f2:0833 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"A Series of Tubes"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 A Series of Tubes>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1431  Invalid misc:5031   Missed beacon:0



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
============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
============================o=============o===========o=============o=========o===========o==============o===========
 eth0                       | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [A Series of Tubes] | 802.11 WiFi | rt2800usb | connected   | yes     | 28 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    A Series of Tubes: Infra, <MAC C-02 A Series of Tubes>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA WPA2
    A Series of Tubes: Infra, <MAC C-03 A Series of Tubes>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *A Series of Tubes: Infra, <MAC C-01 A Series of Tubes>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA2

    Address:         192.168.1.246
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1

    Address:         2602:306:cf2e:14a0::21
    Prefix:          128
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         2602:306:cf2e:14a0:fcb2:1e67:2ff8:4a75
    Prefix:          64
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         2602:306:cf2e:14a0:7edd:90ff:fe6a:653d
    Prefix:          64
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         fe80::7edd:90ff:fe6a:653d
    Prefix:          64
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         2602:306:cf2e:14a0::21
    Prefix:          128
    Gateway:         ::
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

A Series of Tubes    : ssid=A Series of Tubes | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search attlocal.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.079/4.334/4.589/0.255 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.027/0.027/0.028/0.005 ms


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

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 A Series of Tubes>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"A Series of Tubes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d2ace7cc07
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 A Series of Tubes>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"A Series of Tubes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000019372c3cb70
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 A Series of Tubes>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"A Series of Tubes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007fa53d4d78
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


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

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=fef9f798-207b-4c8b-83d7-83be3cc717d2 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.588297] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.588512] audit: initializing netlink socket (disabled)
[    5.974749] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   12.778010] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   12.806253] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   16.609864] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.852875] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   19.902501] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   20.133057] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.133321] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.814220] wlan0: authenticate with <MAC C-03 A Series of Tubes>
[   21.838016] wlan0: send auth to <MAC C-03 A Series of Tubes> (try 1/3)
[   21.839611] wlan0: authenticated
[   21.843180] wlan0: associate with <MAC C-03 A Series of Tubes> (try 1/3)
[   21.846473] wlan0: RX AssocResp from <MAC C-03 A Series of Tubes> (capab=0x411 status=0 aid=2)
[   21.853249] wlan0: associated
[   21.853270] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.044877] wlan0: authenticate with <MAC C-01 A Series of Tubes>
[   48.064058] wlan0: send auth to <MAC C-01 A Series of Tubes> (try 1/3)
[   48.065635] wlan0: authenticated
[   48.067263] wlan0: associate with <MAC C-01 A Series of Tubes> (try 1/3)
[   48.072507] wlan0: RX AssocResp from <MAC C-01 A Series of Tubes> (capab=0x411 status=0 aid=4)
[   48.079116] wlan0: associated

    ======== Done ========
```

---

### Post by varunendra on 2014-09-11
Please try -
```
sudo iwconfig wlan0 power off
```
Does it help? If not, please check -
```
iwconfig
```
..and make sure "Power Management" appears to be "off". If not, report back and we'll try to force it off.

If it does turn the power management off, but it doesn't help speeds, please try -
```
echo "options rt2800usb nohwcrypt=Y" | sudo tee /etc/modprobe.d/rt2800usb.conf
```
..followed by a reboot (required in some cases), or a manual reload of the driver by -
```
sudo modprobe -rv rt2800usb
sudo modprobe -v rt2800usb
```
Any better now?

**PS:**
One of your three access-points is using WPA/WPA2 mixed mode with TKIP. It is highly recommended to change the encryption to pure WPA2-PSK with AES (CCMP), like the two others have.

---

### Post by S2005x on 2014-09-11
Tried the first code. Didn't help. 

I typed iwconfig, and the Power Management was off.

Still slow WiFi. 

I tried the echo code, followed by a reboot, and it was still slow. 

I tried the modprobe codes (One line at a time, right?) and now it won't connect at all.

(Had to post this from a different computer)


***EDIT*** 

Rebooted, and now I'm connected to the internet again, but it's still horribly slow.

I think I fixed the access point that was mixed, and have them all set the same now... I went ahead and ran your script thing again:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

jenny-H61MU3 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz
Memory : 7968 MB
Uptime : 01:04:39 up 9 min,  2 users,  load average: 0.36, 0.42, 0.26


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Biostar Microtech Int'l Corp Device [1565:230a]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 003: ID 04f2:0833 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"A Series of Tubes"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC C-01 A Series of Tubes>   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3889  Invalid misc:11021   Missed beacon:0



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
rt2800usb     (1): nohwcrypt=Y


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o===========o=============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver    | State       | Default | Speed     | Support      | HW Addr   
============================o=============o===========o=============o=========o===========o==============o===========
 eth0                       | Wired       | r8169     | unavailable | no      |           |              | <MAC eth0>
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------
 wlan0  [A Series of Tubes] | 802.11 WiFi | rt2800usb | connected   | yes     | 52 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    A Series of Tubes: Infra, <MAC C-03 A Series of Tubes>, Freq 2462 MHz, Rate 54 Mb/s, Strength 92 WPA2
    A Series of Tubes: Infra, <MAC C-02 A Series of Tubes>, Freq 2437 MHz, Rate 54 Mb/s, Strength 72 WPA2
    *A Series of Tubes: Infra, <MAC C-01 A Series of Tubes>, Freq 2437 MHz, Rate 54 Mb/s, Strength 81 WPA2

    Address:         192.168.1.246
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1

    Address:         2602:306:cf2e:14a0::21
    Prefix:          128
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         2602:306:cf2e:14a0:c828:564f:88e0:8c08
    Prefix:          64
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         2602:306:cf2e:14a0:7edd:90ff:fe6a:653d
    Prefix:          64
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         fe80::7edd:90ff:fe6a:653d
    Prefix:          64
    Gateway:         fe80::6655:b1ff:fe74:7530

    Address:         2602:306:cf2e:14a0::21
    Prefix:          128
    Gateway:         ::
----------------------------+-------------+-----------+-------------+---------+-----------+--------------+-----------


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

A Series of Tubes    : ssid=A Series of Tubes | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search attlocal.net


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.127/1.465/1.803/0.338 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.025/0.027/0.030/0.005 ms


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

          Current Frequency:2.437 GHz (Channel 6)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 A Series of Tubes>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:on
                    ESSID:"A Series of Tubes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d3f4ec04eb
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 A Series of Tubes>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"A Series of Tubes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000005be665f6
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 A Series of Tubes>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"A Series of Tubes"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000080ed3be035
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


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

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
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
rt2800usb.conf    : options rt2800usb nohwcrypt=Y


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=fef9f798-207b-4c8b-83d7-83be3cc717d2 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.587145] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.587359] audit: initializing netlink socket (disabled)
[    5.974500] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   14.992971] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 0502 detected
[   15.021099] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5370 detected
[   16.821434] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.338708] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   18.364525] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   18.600023] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.600269] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.974426] wlan0: authenticate with <MAC C-01 A Series of Tubes>
[   19.996963] wlan0: send auth to <MAC C-01 A Series of Tubes> (try 1/3)
[   19.998444] wlan0: authenticated
[   20.002213] wlan0: associate with <MAC C-01 A Series of Tubes> (try 1/3)
[   20.005316] wlan0: RX AssocResp from <MAC C-01 A Series of Tubes> (capab=0x411 status=0 aid=2)
[   20.012060] wlan0: associated
[   20.012085] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  381.396828] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  381.396850] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  381.396853] ieee80211 phy0: rt2800usb_entry_txstatus_timeout: Warning - TX status timeout for entry 13 in queue 2
[  381.407710] ieee80211 phy0: rt2800usb_txdone: Warning - Got TX status for an empty queue 2, dropping

    ======== Done ========
```

[[URL=http://www.speedtest.net/my-result/3751777124][IMG]http://www.speedtest.net/result/3751777124.png[/IMG]]("http://www.speedtest.net/my-result/3751777124")[/URL]

---

### Post by S2005x on 2014-09-11
It's also worth mentioning that I do have 2 other WiFi USB dongels that I could try...

I have:
Netgear WG111v2
Linksys AE2500 (This is the one we were using with Windows, and worked, but after Ubuntu, it won't even recognize it)


**EDIT**

Unplugged the Panda Wireless one, and hooked up the WG111v2, and I'm getting better, but still awful speed. I'm going to try a reboot.
[[IMG]http://www.speedtest.net/result/3751850576.png[/IMG]]("http://www.speedtest.net/my-result/3751850576")


***EDIT 2***

Ok, so after a reboot, using the WG111v2 (Also it's in a different USB port, if that matters)

[[IMG]http://www.speedtest.net/result/3751856103.png[/IMG]](http://www.speedtest.net/my-result/3751856103)

---

### Post by varunendra on 2014-09-11
For a test, please set "IPv6" to "Ignore" in Network Manager. Reboot if it doesn't make a difference. If still the same results, try disabling it permanently (can be easily reverted if needed later) following this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)

---

### Post by S2005x on 2014-09-11
That didn't really help much either. I think its this wirless adapter. The Panda PAU03 I got on Amazon. I'm going to get a refund.

The Netgear WG111v2 seems to work significantly better, but I'm going to find a PCIe wireless card to go internal :D

Do you recommend one that's better than the others, and works with Ubuntu?

---

### Post by varunendra on 2014-09-11
All my experience with wifi cards is limited to what I learnt here, and here only those come who have problems. So this way, I know of no cards which can be guaranteed to work fantastically. I personally like my atheros AR9285, but I also know the same card needs a driver tweak in current kernel versions to work nicely.

Some folks here like Intels, but I don't know which ones are the best (I do know that the one "I" once considered the best - AC7260, has the most firmware confusion currently).

As such, I think you should browse this section of the forums and find out yourself which ones needed least amount of tweaking to work nicely.

Either that, or you may consider trying "thinkpenguin.com" - I've read here that they are good at customer service and replacements, if required.

---

### Post by S2005x on 2014-09-11
Looking at 3 cards on Newegg right now, I'm not sure if they use Atheros AR9285 or even how to find that out...
All 3 say "[COLOR=#4D4D4D][FONT=helvetica]Linux Kernel 2.6"[/FONT][/COLOR]
[ASUS PCE-N15]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320074&Tpk=33-320-074&cm_sp=WirelessNetworking-_-VisNav-_-WirelessAdapters") $28.99
[ASUS PCE-N10]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320071") $11.99 After MiR
[ASUS PCE-N53]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320113") $29.99 After MiR

---

### Post by varunendra on 2014-09-11
> **S2005x said:**
> Looking at 3 cards on Newegg right now, I'm not sure if they use Atheros AR9285 or even how to find that out...
All 3 say "[COLOR=#4D4D4D][FONT=helvetica]Linux Kernel 2.6"[/FONT][/COLOR]
[ASUS PCE-N15]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320074&Tpk=33-320-074&cm_sp=WirelessNetworking-_-VisNav-_-WirelessAdapters") $28.99
[ASUS PCE-N10]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320071") $11.99 After MiR
[ASUS PCE-N53]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833320113") $29.99 After MiR

Two of them, it seems, use 'rtl8192ce' driver, and one doesn't have a linux driver at all! (If I remember correctly, Asus supplies a driver for N53, but my "if-i-remember-correctly" isn't very reliable)

You can find driver details of most of the cards on wikidevi.com. The ones you listed above are here :

[https://wikidevi.com/wiki/Asus_PCE-N15](https://wikidevi.com/wiki/Asus_PCE-N15)
[https://wikidevi.com/wiki/Asus_PCE-N10](https://wikidevi.com/wiki/Asus_PCE-N10)
[https://wikidevi.com/wiki/ASUS_PCE-N53](https://wikidevi.com/wiki/ASUS_PCE-N53)

rtl8192ce works, but is a bit (sometimes 'quite') shaky at the moment and sometimes an entirely uncontrollable beast. Means, when it decides not to work nicely, it can give us a really hard time.

I would personally go with anything that uses an ath9k (atheros), iwlwifi (Intel), b43 (broadcom) or even rt2800pci (ralink) driver. Well, I would consider ralink the last choice, since although the most common of its chips are currently working okay, most of the linux-drivers on its official site are way too outdated and the native one (rt2800pci) in earlier kernel versions didn't work very nicely. Currently it does, but I can't call this niceness 'consistent' yet.

As you can see, realtek is out of my list of choice. Doesn't necessarily mean they are bad, but like I said, it is currently proving to be 'uncontrollable'.

---

### Post by sheldon-corey on 2014-09-12
I may be wrong on the model but most any intel or realtek express34 adapter (if express34 is available on machine) can be internalized

---

### Post by S2005x on 2014-09-12
Cool, thanks for the info guys. 

Do you recommend any specific cards? That are at or under $20?

---

### Post by S2005x on 2014-09-12
Ok, tried another method. I used a spare wireless router to set up DDWRT on, and it worked great on my Win7 PC. 

I moved it over to the Ubuntu box, and I'm getting awful speeds (The W7 box got around 16Mb/s)

[[IMG]http://www.speedtest.net/result/3756391417.png[/IMG]](http://www.speedtest.net/my-result/3756391417)

---

### Post by S2005x on 2014-09-12
I went ahead and ran that script again too incase any of that info is helpful :D

```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


jenny-H61MU3 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty


CPU    : Intel(R) Core(TM) i3-2120 CPU @ 3.30GHz
Memory : 7968 MB
Uptime : 21:27:58 up 9 min,  2 users,  load average: 0.25, 0.41, 0.27




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Biostar Microtech Int'l Corp Device [1565:230a]
	Kernel driver in use: r8169




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 003: ID 04f2:0833 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~






iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~








module parameters ~~~~~~~~~~~~~~~~~~




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: connected (global)
============================o=======o========o===========o=========o===========o==============o===========
 Interface & ID             | Type  | Driver | State     | Default | Speed     | Support      | HW Addr   
============================o=======o========o===========o=========o===========o==============o===========
 eth0  [Wired connection 1] | Wired | r8169  | connected | yes     | 100 Mb/s  |              | <MAC eth0>


    Address:         192.168.1.195
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1
    DNS:             192.168.1.1
----------------------------+-------+--------+-----------+---------+-----------+--------------+-----------




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


A Series of Tubes    : ssid=A Series of Tubes | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
A Series of Tubes 1  : ssid=A Series of Tubes | mac-address=<MAC wlan1> | ipv4=auto | ipv6=ignore 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~


nameserver 127.0.1.1
search attlocal.net




Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


--- 192.168.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 7.277/8.716/10.156/1.442 ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.024/0.027/0.030/0.003 ms




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






blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# USB device 0x:0x (rtl8187)
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
rt2800usb.conf    : options rt2800usb nohwcrypt=Y




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=fef9f798-207b-4c8b-83d7-83be3cc717d2 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    3.588238] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.588448] audit: initializing netlink socket (disabled)
[    5.979918] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   16.217164] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


	======== Done ========
```

---

### Post by S2005x on 2014-09-12
Ok... no idea what is going on here... 

Didn't change ANYTHING. For some reason, my AT&T Gateway lost connection and reset.

Now I'm getting this:

[[IMG]http://www.speedtest.net/result/3756420710.png[/IMG]](http://www.speedtest.net/my-result/3756420710)

---

### Post by varunendra on 2014-09-12
..and the wireless-info report you posted was from when the device wasn't plugged in it seems. Or was it just lost from the sight of the OS magically?

I'm just as lost as you are. :p

---

### Post by S2005x on 2014-09-12
Lol CONFUSED... but hey, if it works, I'm happy :D 

Now I'm having issues with PlayOnLinux... and Ubuntu Updates...

I can surf, and do speedtests, but when I try to download something through the repository, or PlayOnLinux is trying to install Wine, or Ubuntu Updates, none of them download. The downloading bar pops up, and no progress ever happens :(

---

