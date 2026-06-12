---
title: "Wireless USB adapter woes, Realtek RTL8188SU"
date: 2014-06-11
forum: Networking &amp; Wireless
---

### Post by Waco_Tohausen on 2014-06-11
I have an IBM ThinkPad T30 with a 2 gHz processor, 1 GB of RAM, and a 40 GB HD. I just did a clean install of Lubuntu 14.04. So far, so good.

I have a Belkin N150 wireless USB adapter, plugged into the ThinkPad's USB 1.0 port (I have two but the body of the adapter covers the other port when it's plugged in).

I can get it to connect to the wireless at the public library and at my apartment... however:

1) I cannot get the network manager indicator to stay in my tray (I've tried all the tricks here, but if I close the terminal, it vanishes).

2) Once the wireless starts being used, it quickly loses connection (without indicating it has done so) and I have to try to figure out either how to reset it or unplug and re-plug the actual dongle. It does this every single time I try to use the internet, and I'm not familiar enough with Linux yet to understand what's going on.

When this computer had WinXP on it, the wireless never did this - it stayed connected continually.

Results of the Wireless Script:

```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Newton 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz
Memory : 1001 MB
Uptime : 12:03:35 up  1:44,  4 users,  load average: 0.36, 0.62, 0.64


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
    Subsystem: IBM ThinkPad A/T/X Series [1014:0209]
    Kernel driver in use: e100


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 017: ID 050d:945a Belkin Components F7D1101 v1 Basic Wireless Adapter [Realtek RTL8188SU]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"plchwifi"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-04 plchwifi>   
          Bit Rate:150 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

r8712u                158706  0 


module parameters ~~~~~~~~~~~~~~~~~~

r8712u       (21): ampdu_enable=1 | busy_thresh=40 | cbw40_enable=1 | channel=1 | chip_version=2 | hci=1 | ht_enable=1 | ifname=wlan0 | initmac=(null) | lbkmode=0 | low_power=0 | mp_mode=0 | network_mode=0 | power_mgnt=0 | rf_config=1 | rfintfs=2 | vcs_type=1 | video_mode=1 | vrtl_carrier_sense=2 | wifi_test=0 | wmm_enable=0


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o========o==============o=========o===========o==============o===========
 Interface & ID    | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
===================o=============o========o==============o=========o===========o==============o===========
 wlan0  [plchwifi] | 802.11 WiFi | r8712u | connected    | yes     | 150 Mb/s  | WEP/WPA/WPA2 | <MAC wlan0>

    plchwifi:        Infra, <MAC C-08 plchwifi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 58
    plchwifi:        Infra, <MAC C-36 plchwifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
    plchwifi:        Infra, <MAC C-28 plchwifi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 44
    plchwifi:        Infra, <MAC C-06 plchwifi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    HP0236B6:        Ad-Hoc, <MAC C-NA HP0236B6 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42
    plchwifi:        Infra, <MAC C-NA plchwifi 4>, Freq 2412 MHz, Rate 54 Mb/s, Strength 26
    *plchwifi:       Infra, <MAC C-04 plchwifi>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    plchwifi:        Infra, <MAC C-43 plchwifi>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42

    Address:         10.202.235.10
    Prefix:          16 (255.255.0.0)
    Gateway:         10.202.0.1
    DNS:             10.110.10.12
    DNS:             10.110.10.13
    DNS:             10.110.10.151
-------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0              | Wired       | e100   | unavailable  | no      |           |              | <MAC eth0>
-------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

plchwifi             : ssid=plchwifi | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search cincinnatilibrary.org


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.202.0.1      0.0.0.0         UG    0      0        0 wlan0
10.202.0.0      0.0.0.0         255.255.0.0     U     9      0        0 wlan0

--- 10.202.0.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms


--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.056/0.062/0.069/0.010 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)

          Current Frequency=2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=70/100  
          Cell 02 - Address: <MAC C-02 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 03 - Address: <MAC C-03 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=45/100  
          Cell 04 - Address: <MAC C-04 plchwifi>
                    ESSID:"plchwifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=100/100  
          Cell 05 - Address: <MAC C-05 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 06 - Address: <MAC C-06 plchwifi>
                    ESSID:"plchwifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=47/100  
          Cell 07 - Address: <MAC C-07 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=60/100  
          Cell 08 - Address: <MAC C-08 plchwifi>
                    ESSID:"plchwifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=62/100  
          Cell 09 - Address: <MAC C-09 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 10 - Address: <MAC C-10 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=72/100  
          Cell 11 - Address: <MAC C-11 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 12 - Address: <MAC C-12 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 13 - Address: <MAC C-13 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=62/100  
          Cell 14 - Address: <MAC C-14 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac012800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=58/100  
          Cell 15 - Address: <MAC C-15 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 16 - Address: <MAC C-16 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac012800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=100/100  
          Cell 17 - Address: <MAC C-17 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac012800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=72/100  
          Cell 18 - Address: <MAC C-18 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 19 - Address: <MAC C-19 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=58/100  
          Cell 20 - Address: <MAC C-20 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=26/100  
          Cell 21 - Address: <MAC C-21 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=60/100  
          Cell 22 - Address: <MAC C-22 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=100/100  
          Cell 23 - Address: <MAC C-23 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=46/100  
          Cell 24 - Address: <MAC C-24 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=70/100  
          Cell 25 - Address: <MAC C-25 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=46/100  
          Cell 26 - Address: <MAC C-26 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=46/100  
          Cell 27 - Address: <MAC C-27 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 28 - Address: <MAC C-28 plchwifi>
                    ESSID:"plchwifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=46/100  
          Cell 29 - Address: <MAC C-29 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac012800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=44/100  
          Cell 30 - Address: <MAC C-30 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 31 - Address: <MAC C-31 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 32 - Address: <MAC C-32 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=46/100  
          Cell 33 - Address: <MAC C-33 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac012800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Signal level=44/100  
          Cell 34 - Address: <MAC C-34 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=10/100  
          Cell 35 - Address: <MAC C-35 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 36 - Address: <MAC C-36 plchwifi>
                    ESSID:"plchwifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=42/100  
          Cell 37 - Address: <MAC C-37 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=46/100  
          Cell 38 - Address: <MAC C-38 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 39 - Address: <MAC C-39 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 40 - Address: <MAC C-40 HPEF0C3A>
                    ESSID:"HPEF0C3A"
                    Protocol:IEEE 802.11b
                    Mode:Ad-Hoc
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Signal level=42/100  
          Cell 41 - Address: <MAC C-41 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  
          Cell 42 - Address: <MAC C-42 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=43/100  
          Cell 43 - Address: <MAC C-43 plchwifi>
                    ESSID:"plchwifi"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Signal level=26/100  
          Cell 44 - Address: <MAC C-44 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=26/100  
          Cell 45 - Address: <MAC C-45 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=44/100  
          Cell 46 - Address: <MAC C-46 <hidden>>
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:rsn_ie=30140100000fac040100000fac040100000fac022800
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Signal level=42/100  


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[r8712u]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/staging/rtl8712/r8712u.ko
firmware:       rtlwifi/rtl8712u.bin
srcversion:     607999565FE22A6079602D8
depends:        
parm:           wifi_test:int
parm:           video_mode:int
parm:           chip_version:int
parm:           rfintfs:int
parm:           lbkmode:int
parm:           hci:int
parm:           network_mode:int
parm:           channel:int
parm:           mp_mode:int
parm:           wmm_enable:int
parm:           vrtl_carrier_sense:int
parm:           vcs_type:int
parm:           busy_thresh:int
parm:           ht_enable:int
parm:           cbw40_enable:int
parm:           ampdu_enable:int
parm:           rf_config:int
parm:           power_mgnt:int
parm:           low_power:int
parm:           ifname: Net interface name, wlan%d=default (string)
parm:           initmac:MAC-Address, default: use FUSE (charp)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x8086:0x1031 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (r8712u)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=ef182d00-03b6-4bf4-ab64-d409eee150d0 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.180753] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.181319] audit: initializing netlink socket (disabled)
[   18.835391] thinkpad_acpi: http://ibm-acpi.sf.net/
[   19.163331] r8712u: module is from the staging directory, the quality is unknown, you have been warned.
[   19.265058] r8712u: Staging version
[   19.265113] r8712u: register rtl8712_netdev_ops to netdev_ops
[   19.265124] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[   19.282928] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[   21.010086] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.184732] usb 2-1: r8712u: CustomerID = 0x0000
[   23.184743] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[   23.184748] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[   23.946019] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   29.950444] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[   29.953442] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[   30.088468] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.089325] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.397414] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  240.112546] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  244.077748] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 47280, tid = 0
[  948.982148] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  971.048797] r8712u: Staging version
[  971.048855] r8712u: register rtl8712_netdev_ops to netdev_ops
[  971.048869] usb 2-2: r8712u: USB_SPEED_LOW with 4 endpoints
[  971.052466] usb 2-2: r8712u: Boot from EFUSE: Autoload OK
[  973.889608] usb 2-2: r8712u: CustomerID = 0x0000
[  973.889622] usb 2-2: r8712u: MAC Address from efuse = <MAC wlan0>
[  973.889630] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[  974.866450] r8712u 2-2:1.0 wlan0: 1 RCR=0x153f00e
[  974.869456] r8712u 2-2:1.0 wlan0: 2 RCR=0x553f00e
[  974.992515] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  974.996908] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  975.305473] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  995.852148] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  996.793805] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 55040, tid = 0
[ 1326.789751] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1372.626232] r8712u: Staging version
[ 1372.626289] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 1372.626304] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 1372.629081] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 1375.473603] usb 2-1: r8712u: CustomerID = 0x0000
[ 1375.473618] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 1375.473627] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 1376.422448] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 1376.425443] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 1376.548509] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1376.551151] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1376.861565] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1397.341164] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1397.863940] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 65472, tid = 0
[ 2065.361316] r8712u: Staging version
[ 2065.361376] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 2065.361390] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 2065.364146] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 2068.204687] usb 2-1: r8712u: CustomerID = 0x0000
[ 2068.204702] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 2068.204710] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 2069.166553] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 2069.169523] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 2069.292593] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2069.294360] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2069.600544] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2090.142255] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2090.990890] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-08 plchwifi>, seq = 48256, tid = 0
[ 2374.289657] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 3552, tid = 0
[ 2461.681074] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 14976, tid = 0
[ 2834.890218] r8712u: Staging version
[ 2834.890276] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 2834.890290] usb 2-2: r8712u: USB_SPEED_LOW with 4 endpoints
[ 2834.893072] usb 2-2: r8712u: Boot from EFUSE: Autoload OK
[ 2837.729603] usb 2-2: r8712u: CustomerID = 0x0000
[ 2837.729617] usb 2-2: r8712u: MAC Address from efuse = <MAC wlan0>
[ 2837.729625] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 2838.690442] r8712u 2-2:1.0 wlan0: 1 RCR=0x153f00e
[ 2838.693443] r8712u 2-2:1.0 wlan0: 2 RCR=0x553f00e
[ 2838.816509] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2838.818536] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2839.125572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2872.542042] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2872.677793] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-08 plchwifi>, seq = 7344, tid = 0
[ 4025.373664] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-08 plchwifi>, seq = 42128, tid = 0
[ 4054.679818] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-08 plchwifi>, seq = 46640, tid = 0
[ 4094.135846] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 3440, tid = 0
[ 4345.564636] r8712u: Staging version
[ 4345.564697] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 4345.564711] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 4345.567149] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 4348.417689] usb 2-1: r8712u: CustomerID = 0x0000
[ 4348.417704] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 4348.417713] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 4349.374536] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 4349.377526] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 4349.500704] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4349.503064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4349.812638] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4371.132141] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4371.262886] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 6320, tid = 0
[ 4464.406311] r8712u: Staging version
[ 4464.406371] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 4464.406384] usb 2-2: r8712u: USB_SPEED_LOW with 4 endpoints
[ 4464.409160] usb 2-2: r8712u: Boot from EFUSE: Autoload OK
[ 4467.269681] usb 2-2: r8712u: CustomerID = 0x0000
[ 4467.269696] usb 2-2: r8712u: MAC Address from efuse = <MAC wlan0>
[ 4467.269704] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 4468.226528] r8712u 2-2:1.0 wlan0: 1 RCR=0x153f00e
[ 4468.229536] r8712u 2-2:1.0 wlan0: 2 RCR=0x553f00e
[ 4468.352595] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4468.354381] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4468.660669] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4479.641820] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4479.753630] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-28 plchwifi>, seq = 56688, tid = 0
[ 4669.463865] r8712u: Staging version
[ 4669.463921] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 4669.463935] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 4669.467505] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 4672.332047] usb 2-1: r8712u: CustomerID = 0x0000
[ 4672.332062] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 4672.332070] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 4673.282886] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 4673.285873] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 4673.409069] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4673.410939] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4673.717007] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4694.277604] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4695.114259] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 28544, tid = 0
[ 4888.152885] r8712u: Staging version
[ 4888.152943] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 4888.152957] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 4888.156458] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 4890.128813] usb 2-1: r8712u: CustomerID = 0x0000
[ 4890.128828] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 4890.128837] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 4890.344201] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4890.538867] r8712u: Staging version
[ 4890.538922] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 4890.538932] usb 2-2: r8712u: USB_SPEED_LOW with 4 endpoints
[ 4890.540746] usb 2-2: r8712u: Boot from EFUSE: Autoload OK
[ 4893.430250] usb 2-2: r8712u: CustomerID = 0x0000
[ 4893.430265] usb 2-2: r8712u: MAC Address from efuse = <MAC wlan0>
[ 4893.430273] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 4893.465777] net wlan0: r8172u: Badfw->size of -240153984
[ 4893.496671] systemd-udevd[5678]: renamed network interface wlan1 to wlan0
[ 4894.423102] r8712u 2-2:1.0 wlan0: 1 RCR=0x153f00e
[ 4894.426088] r8712u 2-2:1.0 wlan0: 2 RCR=0x553f00e
[ 4894.549140] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5001.679255] r8712u: Staging version
[ 5001.679317] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 5001.679331] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 5001.682082] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 5004.522627] usb 2-1: r8712u: CustomerID = 0x0000
[ 5004.522642] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 5004.522650] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 5005.402467] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 5005.405475] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 5005.528535] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5005.534153] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5016.480864] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5016.952546] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 42672, tid = 0
[ 5142.873311] r8712u: Staging version
[ 5142.873372] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 5142.873384] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 5142.876471] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 5145.745686] usb 2-1: r8712u: CustomerID = 0x0000
[ 5145.745701] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 5145.745709] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 5146.702522] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 5146.705519] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 5146.828584] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5146.830413] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5147.137668] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5167.641266] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5168.607901] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 51456, tid = 0
[ 5232.334245] r8712u: Staging version
[ 5232.334307] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 5232.334320] usb 2-2: r8712u: USB_SPEED_LOW with 4 endpoints
[ 5232.337079] usb 2-2: r8712u: Boot from EFUSE: Autoload OK
[ 5235.197590] usb 2-2: r8712u: CustomerID = 0x0000
[ 5235.197605] usb 2-2: r8712u: MAC Address from efuse = <MAC wlan0>
[ 5235.197613] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 5236.170477] r8712u 2-2:1.0 wlan0: 1 RCR=0x153f00e
[ 5236.173445] r8712u 2-2:1.0 wlan0: 2 RCR=0x553f00e
[ 5236.296513] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5236.301500] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5236.613768] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5257.136201] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5257.825849] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-08 plchwifi>, seq = 54480, tid = 0
[ 5620.633946] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-06 plchwifi>, seq = 23360, tid = 0
[ 5749.072417] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 34160, tid = 0
[ 5832.588818] r8712u: Staging version
[ 5832.588877] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 5832.588890] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 5832.592465] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 5835.438712] usb 2-1: r8712u: CustomerID = 0x0000
[ 5835.438729] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 5835.438737] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 5836.506506] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 5836.509505] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 5836.632572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5836.634649] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5836.940525] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5857.504235] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5858.017922] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 38992, tid = 0
[ 5870.906827] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 39200, tid = 0
[ 6007.828846] r8712u: Staging version
[ 6007.828905] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 6007.828920] usb 2-1: r8712u: USB_SPEED_LOW with 4 endpoints
[ 6007.832457] usb 2-1: r8712u: Boot from EFUSE: Autoload OK
[ 6010.672682] usb 2-1: r8712u: CustomerID = 0x0000
[ 6010.672696] usb 2-1: r8712u: MAC Address from efuse = <MAC wlan0>
[ 6010.672704] usb 2-1: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 6011.650554] r8712u 2-1:1.0 wlan0: 1 RCR=0x153f00e
[ 6011.653526] r8712u 2-1:1.0 wlan0: 2 RCR=0x553f00e
[ 6011.780585] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6011.783094] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6012.092655] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6032.722245] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6033.206944] r8712u 2-1:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 43616, tid = 0
[ 6108.092838] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6218.063637] r8712u: Staging version
[ 6218.063698] r8712u: register rtl8712_netdev_ops to netdev_ops
[ 6218.063714] usb 2-2: r8712u: USB_SPEED_LOW with 4 endpoints
[ 6218.066461] usb 2-2: r8712u: Boot from EFUSE: Autoload OK
[ 6220.921990] usb 2-2: r8712u: CustomerID = 0x0000
[ 6220.922005] usb 2-2: r8712u: MAC Address from efuse = <MAC wlan0>
[ 6220.922013] usb 2-2: r8712u: Loading firmware from "rtlwifi/rtl8712u.bin"
[ 6221.894821] r8712u 2-2:1.0 wlan0: 1 RCR=0x153f00e
[ 6221.897832] r8712u 2-2:1.0 wlan0: 2 RCR=0x553f00e
[ 6222.020903] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6222.022707] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6222.328849] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6256.399210] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6256.493077] r8712u 2-2:1.0 wlan0: r8712_got_addbareq_event_callback: mac = <MAC C-04 plchwifi>, seq = 50224, tid = 0

    ======== Done ========


```

With the dongle inserted, here are the results for wlan0 for:
iwconfig:
```

unassociated
Nickname:"rtl_wifi"
Mode:Auto
Access Point: Not-Associated
Sensitivity:0/0
Retry:off
RTS thr:off
Fragment thr:off
Power Management:off
Link Quality (and all fields after this):0

```
For ifconfig:
```

Link encap:Ethernet
HWaddr: ec:la:59:30:22:57
inet addr:10.202.235.10
Bcast:10.202.255.255
Mask:255.255.0.0
inet6 addr: fe80::ee1a::59ff::fe30::2257/64
Scope:link
UP BROADCAST RUNNING MULTICAST
MTU:1500
Metric:1
RX packets:129 errors:0 dropped:103: overruns:0 frame:0
TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:13271 (13.2 KB) TX bytes:393510 (393.5 KB)
```

---

### Post by Mar Komus on 2014-06-11
Looks like we have two problems in one--and maybe solving one will help us better understand the other.

Since I'm running Lubuntu as well we should be able to compare notes relatively easily.

Let's first look at the "network manager indicator." I might be lost at this point, so let me see if I can get myself on the same page. Do you mean the icon that appears in the Panel that when you hover over it it says, "Network Connection: {*dev*}?" It looks like an inverted cone and is there to keep you updated on the status of your network connection, right? If so, then the second point where I'm lost is when you said, "I've tried all the tricks here, but if I close the terminal, it vanishes." I don't know what tricks you tried :) so I'm going to presume that the following will work for you as it did for me. Let me know if it fails. If you've already tried it, will you humor me anyway?

1. Right-click on the Panel in which you want the Network Connection indicator to appear.
2. Click on, "Add/Remove Panel Items"
3. Click on, "Indicator applets" to highlight (Don't double-click)
4. Click on, "+ Add"
5. A new dialog box will appear. Click on, "Network Status Monitor"
6. Click on, "+ Add"
7. The Network Status Monitor will be added and the dialog box will close
8. You may close the Panel Preferences dialog box

That's what I have for your first problem--provided I understood correctly. The second one I'll have to think through or someone else should get back to you. But let us know how that works out for #1

---

### Post by Waco_Tohausen on 2014-06-12
Thank you Mar Komus for offering to assist. I used Linux boxes years ago (mid-90s, military), but they were a far cry from what I'm seeing now. (Clarification: I LIKE what I see now)

What I was referring to was the nm-applet - the typical 'strength bar' that pops up on cell phones, etc. I did the process above, and somehow have two inverted cones - one that stays up and one that keeps changing based on my adapter activity.

For what it's worth, I DID get the nm-applet to stay up after closing the terminal window, but it doesn't come back during my next session - have to sudo it again, each time I log on.

The doubled cones come up though (visions of Madonna swim in my head)... but it's the bars that gives me the network connection menus. Last night, I spent about an hour solid on-line, though my connection speeds were pretty shoddy - that can be chalked up to the building's router being a floor below my apartment. Then, just as I was getting comfortable, it quit again. If I click on the connection - which shows as if it is connected - it disconnects and starts doing the swirling lights dance on the icon, but won't come back up unless I physically detach and reattach the Belkin. Sometimes that hard reset works fine; other times, the Belkin processes about 300 kb and quits again right away.

By 'quit' I should clarify: according to the device monitor, it's sending out packets steadily. But it stops receiving packets. This happens both at the apartment building and at the public library, who are presumably using different sytems, so I am reluctant to fault the actual base stations involved. I am personally leaning toward the fact it's an old computer with USB-1.0 connectors... maybe the Belkin has some internal buffer that's getting jammed up, because it's funnelling data through an old USB connection? Is there a way to access the Belkin's on-board files and figure out what's going on?

In spite of losing the ability to play Civ III - and access to my fav audio player, AIMP - I still think switching to Lubuntu has been awesome.

---

### Post by Mar Komus on 2014-06-12
Ah...so you're an old "neck beard" from the 90s, but a shaven neck beard (military style). Ha! Well yours truly is a coming-of-ager from the 90s, but I went to Bible college (different kind of soldier, different kind of war). Glad to see you appreciate the changes. I remember thinking, "Linux? Uh. No thanks." But the current versions--especially of the Lubuntu and Ubuntu stripe--fit this current generation of coming-of-agers. I'd say the Ubuntu/Lubuntu projects themselves are just about at the end of those years and are poised to be good, genuine competition for the big guys. But that's off topic. :)

I'll have to look into the nm-applet, but I'm away from my business machine for the day.

Madonna. Ha! You are a man of the 90s!

I'd have to concur with the idea of the old USB 1.0 presenting problems. Maybe there's something Linux does differently than Windows in handling USB 1.0 traffick?

Incidentally, what's the story on this one's wireless solution? I see on the Lenovo site that "s[FONT=Arial]elected models will have Intel Wireless and modem Mini PCI combo cards." Did this one have nothing and that's the reason for the dongle? That's totally cool, of course, but I'm just curious. :)

My next recommendation, though, would be to plug the dongle into a few other machines--hopefully one with Lubuntu and at least USB 2.0--and see what results you can reproduce. Maybe have a friend bring a laptop over to see what might be the case.
[/FONT]

---

### Post by coffeecat on 2014-06-12
> **Waco_Tohausen said:**
> 1) I cannot get the network manager indicator to stay in my tray (I've tried all the tricks here, but if I close the terminal, it vanishes).


There's a bug that means the network manager icon is missing from the panel in some Lubuntu 14.04 installations. A couple of fixes here:

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

The first worked for me when I installed Lubuntu to a netbook and the nm-applet icon was missing.

---

### Post by Waco_Tohausen on 2014-06-13
The story with this unit is: I got it as-is for $40 on eBay - just needed a quick machine - and the wireless card has been physically removed from the system. Not too sure why, but there it is - two bare connector leads are all that's left of the original card.

So anyway, coffeecat (LOVE that nick, by the way), I'll look into those. (Not at my box atm) Oddly enough, last night it connected for a good four hours straight (on the dock's single USB port), then quit during WINE download - but once I removed and replaced it, it worked again until I shut down for the night.

I'm almost ready to blame the weather, solar flare activity, or Prince's sexual orientation of the moment on my wireless troubles...

Since I'm a newbie (returning, true), anyone have any pointers about using AIMP in Lubuntu? I installed Wine last night, ready to try her out, just wanted to know what to expect.

Thanks, guys - Windows has left me soft and lazy...

---

### Post by kurt18947 on 2014-06-13
I don't have this adapter - I have Realtek RTL8192CU and an RTL8188CUs and both behave somewhat like you're describing, except mine won't stay connected for more than a few minutes.  I can disable/enable WiFi via the NM-Applet, I don't have to unplug/replug but then my NM-Applet icon hasn't chosen to play hide-and-seek:smile:.  They will reconnect for a few minutes and stall.  There is a patched driver on GitHub for my devices.  Unfortunately, it appears the 8188SU uses a different driver and the last kernel it claims to support is 3.0.2.  Here's the download page:

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

Unless you or someone you know has the skill to patch that driver, I doubt it'll be of much help.   Have you searched the networking & Wireless forum here using some search criteria like "RTL8188SU"?  You might find something, or at least find out what hasn't worked.

The wireless adapters I've used without having to jump through hoops are TrendNet TEW-649UB(RTL8192SU), Tenda W311MI (RT5370 chip set) or Netgear WNA1100 (Atheros 9172(?)chip set).  Another consideration would be to replace the internal WiFi card.  I have a Thinkpad X61 with an Intel 4965AGN card that has worked with every linux distro I've tried on that machine.  Thinkpads require a little caution though; the BIOS whitelists WiFi cards that work with that machine.  A 'non-approved' WiFi card would require a 3rd party BIOS.  That's why so far, I've used USB adapters rather than replacing internal cards.  If you want to explore replacing the card, Thinkpad manuals are available on Lenovo's site and list the approved cards.  Good luck, Wireless networking may be the biggest hardware challenge in Linux land.

---

### Post by Waco_Tohausen on 2014-06-13
Well, for all I've been pulling my hair out, NOW the thing seems to be working OK. For some reason, it works several times better when the pad is docked - I'm wondering if it's getting a better power supply through the dock, or if the connection is just more robust. 

Whatever the deal, this tempermental old beast is settling down, so it can stay.

Kurt, thanks for the offered assist. I'm not too eager to try to replace the internal card - looks like it might take specific soldering tools to reconnect the leads (not just a plug-in-and-go), so I'll stick to the USB for now. Locally, it seems like Belkin bought out the market for USB adapters - I'll have to see if I can get one online somewhere.

CoffeeCat, the LXESession addition seems to have done the trick. Good looking out!

I gotta say, guys - the support here beats the HECK out of MS's...

UPDATE: If I'm reading this correctly, my adapter is running solely on firmware drivers. There's not a single solitary driver module running for my adapter. I'm currently following the installation procedures found at [http://ubuntuforums.org/showthread.php?t=1382798](http://ubuntuforums.org/showthread.php?t=1382798) to see what, if anything, this will do. 

The drops are very sporadic. System stayed on-line this morning for hours, then a little bit ago would not stay connected for more than five minutes, now it's back again. Rrrrrr

---

