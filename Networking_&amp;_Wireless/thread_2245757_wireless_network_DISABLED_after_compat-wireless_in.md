---
title: "wireless network DISABLED after compat-wireless install"
date: 2014-09-25
forum: Networking &amp; Wireless
---

### Post by Dan_Frecka on 2014-09-25
I just installed an old version of compat-wireless and rebooted on Ubuntu 9.04 in an attempt to curb packet loss (as seen here [https://bugzilla.kernel.org/show_bug.cgi?id=15313](https://bugzilla.kernel.org/show_bug.cgi?id=15313)), but now my wlan0 is not working.

```

lshw -c network
```

shows

```

*-network DISABLED
    description: Wireless interface
    ...
    driver=ath9k driverversion=2.6.28-11-server firmware=N/A ...
```

```

lspci

02:00.0 network controller: Atheros Communications Inc. Device 0030 (rev 01)
```

Any idea?

---

### Post by varunendra on 2014-09-26
Welcome to the forums Dan_Frecka!

Old is old, and Ubuntu 9.04 waaaayyy.... too old! We probably won't be able to help you even if we try with that old kernel.

> Any idea?
I think I have one - why don't you install a supported version of Ubuntu that should be easy to troubleshoot, if needed. Have you tried any? What was the problem?

Please try 14.04.1 or 12.04.5 in Live mode, and if it seems to work, install it. If there are problems, post your problem in a new thread with a descriptive title in a suitable section of the forums.

---

### Post by kc1di on 2014-09-26
Hello Dan_Frecka and Welcome to Ubuntu,

Ubuntu 9.04 reached end of life for support in October of 2010 over 4 years ago. So there will be no way to get support for such an old release. 
you need to updat to  at least 12.04 LTS or 14.04 LTS .  Then everything should start to work. 
If your machine won't run those then you'll have to try a lighter version such as Lubuntu or Xubuntu.  Good luck.

---

### Post by Dan_Frecka on 2014-09-26
Unfortunately, this is a requirement, to use 9.04. Any suggestions?

---

### Post by kc1di on 2014-09-26
why would someone require 9.04 when it's so old?
you may be able to find the archived drivers at[ this page.]("http://old-releases.ubuntu.com/ubuntu/")

---

### Post by Dan_Frecka on 2014-09-26
Too many devices to upgrade I suppose.

---

### Post by varunendra on 2014-09-26
> **Dan_Frecka said:**
> Too many devices to upgrade I suppose.
How about this -

Install on one > install required programs > fully update it (avoid proprietary graphics drivers if different machines need different ones) > clone the partition(s) with clonezilla to an image > restore the image on ALL other machines SIMULTANEOUSLY making the source machine a temporary clonezilla server?

Let us know if you like the idea and need help with that instead. A quick and easy guide is here : [http://clonezilla.org/clonezilla-SE/](http://clonezilla.org/clonezilla-SE/)
The clonezilla server image is about 450 MB in size.

Requiring wireless capability most probably means you need to connect to internet. Multiple machines means it is most probably a network, quite possibly a production environment. Not a good idea to run an unsupported version with unpatched security holes on such a network.

If you still want to stick with 9.04, let us know and we may try to help, if a mod didn't close the thread first. :|

---

### Post by Dan_Frecka on 2014-09-26
It is not possible. I'm going to be sticking with 9.04. However, I already reinstalled, so the problem is gone. However, I'd like to know why I'm getting packet loss, randomly, with the Atheros card? Thanks :p

---

### Post by kc1di on 2014-09-26
run the script that is in the signature of varunendra's post. then post the resulting log page here.

---

### Post by Dan_Frecka on 2014-09-27
```


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

decorator-center 2.6.28-11-server i686,  Ubuntu 9.04, jaunty

CPU    : Intel(R) Pentium(R) CPU G2020 @ 2.90GHz
Memory : 3903 MB
Uptime : 12:01:46 up 20:29,  2 users,  load average: 0.01, 0.00, 0.00


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

00:19.0 Ethernet controller [0200]: Intel Corporation Device [8086:1502] (rev 04
)
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0030
] (rev 01)
    Kernel driver in use: ath9k
    Kernel modules: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 8087:0024  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0461:0010 Primax Electronics, Ltd 
Bus 001 Device 004: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 003: ID 04b3:310c IBM Corp. 
Bus 001 Device 002: ID 8087:0024  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abgn  ESSID:"ea 5GHz"  
          Mode:Managed  Frequency:5.785 GHz  Access Point: <MAC C-15 ea 5GHz>   
          Bit Rate=364.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:169  Invalid misc:12   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

ath9k                 100376  0 
mac80211              324624  1 ath9k
ath9k_common           12032  1 ath9k
ath9k_hw              363424  2 ath9k,ath9k_common
ath                    23936  3 ath9k,ath9k_common,ath9k_hw
cfg80211              181664  3 ath9k,mac80211,ath
compat                 47372  6 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211,rf
kill_backport
led_class              12036  2 ath9k,compat


module parameters ~~~~~~~~~~~~~~~~~~

ath9k         (3): blink=0 | btcoex_enable=0 | nohwcrypt=0
ath9k_hw      (1): force_new_ani=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
compat        (3): compat_base_tree=linux-next.git | compat_base_tree_version=next-20120510 | compat_version=compat-wireless-2012-05-
04
mac80211      (4): ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


================o======o========o========o=========o===========o==============o===========
 Interface & ID | Type | Driver | State  | Default | Speed     | Support      | HW Addr   
================o======o========o========o=========o===========o==============o===========
                |      |        |        |         |           |              |           
----------------+------+--------+--------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~


NetworkManager.conf ~~~~~~~~~~~~~~~~



NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp
wpa-ssid "ea 5GHz"
wpa-psk <WPA key removed>
auto eth0
iface eth0 inet dhcp

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 192.168.2.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 wlan0


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     20 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 11 (2.462 GHz)
          Channel 36 (5.18 GHz)
          Channel 40 (5.2 GHz)
          Channel 44 (5.22 GHz)
          Channel 48 (5.24 GHz)
          Channel 149 (5.745 GHz)
          Channel 153 (5.765 GHz)
          Channel 157 (5.785 GHz)
          Channel 161 (5.805 GHz)
          Channel 165 (5.825 GHz)

          Current Frequency:5.785 GHz (Channel 157)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Gateway Art's>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Gateway Art's"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e37a614900
                    Extra: Last beacon: 4810ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Autry Fiber>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:"Autry Fiber"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e9ab88aeb
                    Extra: Last beacon: 5050ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 FBI_SURV>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"FBI_SURV"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b5720973
                    Extra: Last beacon: 5050ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000b57201a0
                    Extra: Last beacon: 5050ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Jacques AMPED>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Jacques AMPED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002025342c176
                    Extra: Last beacon: 3790ms ago
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 06 - Address: <MAC C-06 1428Guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"1428Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017423f83fa
                    Extra: Last beacon: 3790ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: <MAC C-07 ea>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ea"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000174247550f
                    Extra: Last beacon: 3230ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 ea>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"ea"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001743974160
                    Extra: Last beacon: 3760ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 NETGEAR22>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR22"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002853f59e5ef
                    Extra: Last beacon: 3770ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: <MAC C-10 NETGEAR-Guest>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:off
                    ESSID:"NETGEAR-Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002853f59fabf
                    Extra: Last beacon: 3770ms ago
          Cell 11 - Address: <MAC C-11 sfassnacht>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"sfassnacht"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003e71d378a4
                    Extra: Last beacon: 2730ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 12 - Address: <MAC C-12 ngHub_319437NL03A1E>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"ngHub_319437NL03A1E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000228de574ee
                    Extra: Last beacon: 2720ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 13 - Address: <MAC C-13 Gida>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"Gida"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001357b982d28
                    Extra: Last beacon: 2710ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 14 - Address: <MAC C-14 NETGEAR22-5G>
                    Channel:153
                    Frequency:5.765 GHz (Channel 153)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"NETGEAR22-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002853ddf73f1
                    Extra: Last beacon: 990ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 15 - Address: <MAC C-15 ea 5GHz>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=70/70  Signal level=-27 dBm  
                    Encryption key:on
                    ESSID:"ea 5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001743c1f3d6
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 16 - Address: <MAC C-16 ea 5GHz>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption key:on
                    ESSID:"ea 5GHz"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017434c475c
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 17 - Address: <MAC C-17 1428Guest>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"1428Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=32000017434c4d72
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 18 - Address: <MAC C-18 1415 Race>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"1415 Race"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00001220eef2c80e
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 19 - Address: <MAC C-19 1415 Race Guest>
                    Channel:157
                    Frequency:5.785 GHz (Channel 157)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:"1415 Race Guest"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=32001220eef2cfed
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 20 - Address: <MAC C-20 PrettyFlyforaWiFi>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"PrettyFlyforaWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c1c3b15156
                    Extra: Last beacon: 4060ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 21 - Address: <MAC C-21 fairway bunker>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"fairway bunker"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013118976c3
                    Extra: Last beacon: 2980ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 22 - Address: <MAC C-22 mdu512>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"mdu512"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003561c7d8180
                    Extra: Last beacon: 5340ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 23 - Address: <MAC C-23 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=39/70  Signal level=-71 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e9ab882e4
                    Extra: Last beacon: 5050ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 24 - Address: <MAC C-24 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=40/70  Signal level=-70 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000013118970b9
                    Extra: Last beacon: 2980ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 25 - Address: <MAC C-25 ZyXEL39471>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=53/70  Signal level=-57 dBm  
                    Encryption key:on
                    ESSID:"ZyXEL39471"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000c37278831eb
                    Extra: Last beacon: 5330ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 26 - Address: <MAC C-26 >
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001e37a6135ee
                    Extra: Last beacon: 4810ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 27 - Address: <MAC C-27 1415 Race Guest>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"1415 Race Guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=32001223a1a20a42
                    Extra: Last beacon: 4010ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 28 - Address: <MAC C-28 LoudPenguin>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"LoudPenguin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000285d245c55f
                    Extra: Last beacon: 4270ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 29 - Address: <MAC C-29 HP-Print-4A-Photosmart 7520>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"HP-Print-4A-Photosmart 7520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000020252ca7142
                    Extra: Last beacon: 4050ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 30 - Address: <MAC C-30 senefeld>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"senefeld"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003eb84af147
                    Extra: Last beacon: 2750ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 31 - Address: <MAC C-31 BillWiTheScienceFi>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"BillWiTheScienceFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001f08a290185
                    Extra: Last beacon: 2740ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 32 - Address: <MAC C-32 >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001357b981487
                    Extra: Last beacon: 2720ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist ehci_hcd


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[ath9k]
filename:       /lib/modules/2.6.28-11-server/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     0047960F95FEA87FBABCCC8
depends:        ath9k_hw,mac80211,ath9k_common,led-class,ath,cfg80211,compat
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)

[mac80211]
filename:       /lib/modules/2.6.28-11-server/updates/net/mac80211/mac80211.ko
srcversion:     A4C591DF9FC0111465028A0
depends:        cfg80211,compat
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[ath9k_common]
filename:       /lib/modules/2.6.28-11-server/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     533C795967AD3BDD55340FF
depends:        compat,ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/2.6.28-11-server/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     2AB7D5C0B8E70BCF2A56DFE
depends:        ath,compat
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

[ath]
filename:       /lib/modules/2.6.28-11-server/updates/drivers/net/wireless/ath/ath.ko
srcversion:     4BEA9CAEC4A713B6DA1914A
depends:        cfg80211

[cfg80211]
filename:       /lib/modules/2.6.28-11-server/updates/net/wireless/cfg80211.ko
srcversion:     5CA8FC0CA3479588E499B16
depends:        rfkill_backport,compat
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[compat]
filename:       /lib/modules/2.6.28-11-server/updates/compat/compat.ko
srcversion:     C11A2E5773A16E945645CE0
depends:        pcmcia_core,led-class
parm:           compat_base_tree:The upstream tree used as base for this backport (charp)
parm:           compat_base_tree_version:The git-describe of the upstream base tree (charp)
parm:           compat_version:Version of the kernel compat backport work (charp)

[led_class]
filename:       /lib/modules/2.6.28-11-server/kernel/drivers/leds/led-class.ko
srcversion:     32DAFD0CD9EE07AC4AC07FF
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Not Default
/etc/rc.local       : Not Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modules]
loop

[/etc/rc.local]
REBOOT_REQUIRED=0
if [ -f /lib/modules/384.install ]; then
    echo 'New system modules installed'
    echo 'Updating module registry'
    depmod -a 2.6.28-11-server
    rm -f /lib/modules/384.install
    REBOOT_REQUIRED=1
fi
if [ -f /home/bkrycft/install/v37.scanner.install ]; then
    echo 'Updating Scanner Drivers'
    cd /home/bkrycft/install
    ./v37.scanner
    cd -
    rm -f /home/bkrycft/install/v37.scanner.install
    REBOOT_REQUIRED=1
fi
if [ -f /home/bkrycft/install/cups.printer.install ]; then
    echo 'Installing CUPS (Common Unix Printing System)'
    cd /home/bkrycft/install
    ./cups.printer
    cd -
    rm -f /home/bkrycft/install/cups.printer.install
    REBOOT_REQUIRED=1
fi
if [ 1 = $REBOOT_REQUIRED ]; then
    echo 'Rebooting system'
    reboot
fi
amixer set Master 100%
amixer set Headphone 100%

[/etc/modprobe.d]
params.conf       : options usb_storage delay_use=0

[/etc/pm/config.d/00sleep_module]
# The sleep/wake system to use.  Valid values are:
#   kernel    The built-in kernel suspend/resume support.
#             Use this if nothing else is supported on your system.
#   uswsusp   If your system has support for the userspace
#             suspend programs (s2ram/s2disk/s2both), then use this.
#   tuxonice  If your system has support for tuxonice, use this.
#
# The system defaults to "kernel" if this is commented out.
# SLEEP_MODULE="kernel"

[/etc/pm/sleep.d/action_wpa] [executable]
#!/bin/sh

# Action script to enable/disable wpa-roam interfaces in reaction to
# pm-action or ifplugd events.
#
# Copyright: Copyright (c) 2008, Kel Modderman <kel@otaku42.de>
# License:   GPL-2
#

PATH=/sbin:/usr/sbin:/bin:/usr/bin

if [ ! -x /sbin/wpa_action ]; then
    exit 0
fi

SELF=action_wpa
COMMAND=
IFPLUGD_IFACE=

# pm-action(8) - <action> <suspend method>
#
# On suspend|hibernate, disconnect any wpa-roam managed interfaces,
# reconnect it on resume.

case "${1}" in
        suspend|hibernate)
                COMMAND=disconnect
                ;;
        resume|thaw)
                COMMAND=reconnect
                ;;
esac

if [ -z "$COMMAND" ]; then
    # ifplugd(8) - <iface> <action>
    #
    # If an ifplugd managed interface is brought up, disconnect any
    # wpa-roam managed interfaces so that only one "roaming" interface
    # remains active on the system.

    IFPLUGD_IFACE="${1}"

    case "${2}" in
        up)
            COMMAND=disconnect
            ;;
        down)
            COMMAND=reconnect
            ;;
        *)
            echo "${SELF}: unknown $0 arguments: ${@}" >&2
            exit 1
            ;;
        esac
fi

if [ -z "$COMMAND" ]; then
    echo "${SELF}: unknown arguments: ${@}" >&2
    exit 1
fi

for CTRL in /var/run/wpa_supplicant/*; do
    [ -S "${CTRL}" ] || continue

    IFACE="${CTRL#/var/run/wpa_supplicant/}"

    wpa_action "${IFACE}" check || continue

    if [ "${IFPLUGD_IFACE}" ] && [ "${IFPLUGD_IFACE}" = "${IFACE}" ]; then
        # if ifplugd is managing this interface (not likely but..)
        # do nothing
        continue
    fi

    wpa_cli -i "${IFACE}" "${COMMAND}"
done


Kernel boot line ~~~~~~~~~~~~~~~~~~~

root=/dev/sda1 ro quiet splash vga=788


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.540108] net_namespace: 776 bytes
[    1.139317] audit: initializing netlink socket (disabled)
[   16.900041] acer-wmi: Acer Laptop ACPI-WMI Extras
[   16.900051] acer-wmi: No or unsupported WMI interface, unable to load
[   17.253029] snd_seq_midi: disagrees about version of symbol snd_rawmidi_info_select
[   17.253031] snd_seq_midi: Unknown symbol snd_rawmidi_info_select
[   17.253272] snd_seq_midi: disagrees about version of symbol snd_rawmidi_output_params
[   17.253273] snd_seq_midi: Unknown symbol snd_rawmidi_output_params
[   17.253404] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_read
[   17.253405] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_read
[   17.253494] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_write
[   17.253495] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_write
[   17.253590] snd_seq_midi: disagrees about version of symbol snd_rawmidi_drain_output
[   17.253591] snd_seq_midi: Unknown symbol snd_rawmidi_drain_output
[   17.253763] snd_seq_midi: disagrees about version of symbol snd_rawmidi_input_params
[   17.253764] snd_seq_midi: Unknown symbol snd_rawmidi_input_params
[   17.253862] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_open
[   17.253863] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_open
[   17.253955] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_release
[   17.253956] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_release
[   17.254317] snd_seq_midi: disagrees about version of symbol snd_rawmidi_info_select
[   17.254318] snd_seq_midi: Unknown symbol snd_rawmidi_info_select
[   17.254556] snd_seq_midi: disagrees about version of symbol snd_rawmidi_output_params
[   17.254557] snd_seq_midi: Unknown symbol snd_rawmidi_output_params
[   17.254686] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_read
[   17.254687] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_read
[   17.254776] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_write
[   17.254777] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_write
[   17.254872] snd_seq_midi: disagrees about version of symbol snd_rawmidi_drain_output
[   17.254873] snd_seq_midi: Unknown symbol snd_rawmidi_drain_output
[   17.255046] snd_seq_midi: disagrees about version of symbol snd_rawmidi_input_params
[   17.255047] snd_seq_midi: Unknown symbol snd_rawmidi_input_params
[   17.255145] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_open
[   17.255146] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_open
[   17.255237] snd_seq_midi: disagrees about version of symbol snd_rawmidi_kernel_release
[   17.255238] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_release
[   17.688820] ath9k 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.688831] ath9k 0000:02:00.0: setting latency timer to 64
[   17.768982] ath: EEPROM regdomain: 0x21
[   17.768983] ath: EEPROM indicates we should expect a direct regpair map
[   17.768985] ath: Country alpha2 being used: AU
[   17.768986] ath: Regpair used: 0x21
[   17.842557] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   17.843503] Registered led device: ath9k-phy0
[   21.868190] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1314.453828] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1377.725235] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1454.082539] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1456.766545] wlan0: authenticate with f5d46c28
[ 1456.778594] wlan0: send auth to f5d46c28 (try 1/3)
[ 1456.780585] wlan0: authenticate with f5d46c28
[ 1456.780624] wlan0: send auth to f5d46c28 (try 1/3)
[ 1456.780679] wlan0: authenticated
[ 1456.790106] wlan0: associate with f5d46c28 (try 1/3)
[ 1456.793578] wlan0: RX AssocResp from f5cf907a (capab=0x1431 status=0 aid=2)
[ 1456.793582] wlan0: associated
[ 1456.793836] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1467.150079] wlan0: no IPv6 routers present
[ 1681.124761] wlan0: deauthenticating from df9895dc by local choice (reason=3)
[ 1824.670622] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2569.236817] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2571.859665] wlan0: authenticate with dfdcea28
[ 2571.871587] wlan0: send auth to dfdcea28 (try 1/3)
[ 2571.880130] wlan0: authenticate with dfdcea28
[ 2571.880170] wlan0: send auth to dfdcea28 (try 1/3)
[ 2571.880224] wlan0: authenticated
[ 2571.890025] wlan0: associate with dfdcea28 (try 1/3)
[ 2571.893304] wlan0: RX AssocResp from f5d7707a (capab=0x1511 status=0 aid=4)
[ 2571.893308] wlan0: associated
[ 2571.893559] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2582.600079] wlan0: no IPv6 routers present

    
```

---

### Post by varunendra on 2014-09-28
Well, as per the report above, not only it is 'ENABLED' now, but is also connected to an AP with an awesome speed! Are you still having problems?

If yes, please try these -
```
suod iwconfig wlan0 power off
```
which should turn off the 'Power Management' on the wlan0 interface. Confirm it with the output of -
```
iwconfig
```
Does it help anything? Sometimes the power management may turn back on automatically after initially turning off, the reason and solution for which are slightly different.

Apart from this, you *should* change the encryption type in the router to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP which is inefficient, outdated and less secure.

A driver parameter that you can try additionally -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
..followed by a reboot or a manual reload of the driver -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k
```

Oh, one more very _important thing_ - Your current routing table *seems to be* problematic -
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0**    *[COLOR="#FF0000"]<--- preferred path to reach the gateway[/COLOR]*
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
**0.0.0.0         [B]192.168.2.1**     0.0.0.0         UG    0      0        0 [COLOR="#FF0000"]eth0[/COLOR][/B]    *[COLOR="#FF0000"]<--- preferred gateway[/COLOR]*
0.0.0.0         **192.168.2.1**     0.0.0.0         UG    100    0        0 wlan0
```
Same path and gateway routes exist for both 'eth0' and 'wlan0', so the system would simply take the higher one of the duplicate routes. The problem is, using the same logic, it will prefer the gateway that is on 'eth0' interface. But the preferred path to reach the gateway is the one that is using 'wlan0' interface. So in effect, the route to reach the gateway does not exist (actually it exists, but is not the preferred one).

Practical implication - "wlan0" will connect you to local network, but not internet since it is not the preferred gateway. Preferred gateway (thus the 'gate' to internet) is on "eth0", but no traffic (local or internet) can be sent to it since the preferred route is using "wlan0".

A common routing confusion that is easy to overcome. But to be honest, I'm a bit unsure myself, so not suggesting anything right now as it may be unnecessary. If you can confirm this problem, I'd suggest further as necessary.

---

### Post by Dan_Frecka on 2014-09-29
I am feeling like you are correct with the routing table. What is the next course of action?

---

### Post by varunendra on 2014-09-29
> **Dan_Frecka said:**
> I am feeling like you are correct with the routing table. What is the next course of action?

If you want internet over wifi, then in Network Manager, edit your Ethernet connection setting > "IPv4 Settings" tab > "Routes.." button > put tick marks in the two checkboxes you see (use this connection only for local resources..., and the other, if it is active).

This should get rid of the route that puts gateway on 'eth0'. Either that, or we must manually create a specific route to the gateway using 'wlan0' interface. That will need editing of the wlan0 connection, and slightly different steps.

There is another quirk, but let's first solve the internet issue, and take a look at the changed routing table. Then we'll address the next issue (putting local traffic on 'eth0', since it is faster) as and if required.

---

### Post by Dan_Frecka on 2014-09-29
Sorry, I don't have the ability to use Network Manager

---

### Post by varunendra on 2014-10-01
I am not very expert with the 'interfaces' file method, so I can think of only three ways -

1) Use manual IP configuration instead of DHCP for eth0 interface. Don't assign a Gateway to it. Or..

2) Add a 'up route del default gw' command at the end of the file. It will execute as soon as the 'eth0' interface is brought up, and will remove the default gateway (thus making the wifi one the default). Or..

3) Use a script to reset the routing table once it is created, creating/deleting routes according to your preference. You can also add this script as the command to execute when 'eth0' is brought up. But you may have to experiment with it, as I'm not sure of the sequence the interfaces are brought up (I think it is the order in which they appear in the 'interfaces' file, but not sure).

The ideal routing table in your case should route all internet traffic through wifi, but all local traffic through 'eth0'. Currently it is doing the opposite, and failing at internet.

Manual IP configuration of eth0, if feasible, is the simplest and most promising solution. The script method may take some experiments.


**EDIT:** A good reference on various configuration options of 'interfaces' file : [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

--

---

