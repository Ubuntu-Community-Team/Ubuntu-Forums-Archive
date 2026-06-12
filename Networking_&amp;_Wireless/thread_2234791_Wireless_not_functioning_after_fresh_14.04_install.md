---
title: "Wireless not functioning after fresh 14.04 install"
date: 2014-07-17
forum: Networking &amp; Wireless
---

### Post by Heyki on 2014-07-17
Hello

I just installed lubuntu 14.04 on my dell mini 10 (Inspiron 1010) and the Wi-Fi is not fuctioning at all.

I have followed all the steps in the " [SOLVED] How to install a driver for the Broadcom series of PCI wireless cards " thread but yet I have no wireless internet.

My ethernet seems to be working just fine though.

Here is my wireless script report if that helps



    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

jambi-Inspiron-1010 3.13.0-32-generic i686,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Atom(TM) CPU Z520   @ 1.33GHz
Memory : 992 MB
Uptime : 21:38:09 up 9 min,  2 users,  load average: 0.79, 0.63, 0.38


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Dell Device [1028:02c6]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
    Kernel driver in use: b43-pci-bridge


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 0c45:63e3 Microdia 
Bus 001 Device 002: ID 413c:8147 Dell Computer Corp. F3507g Mobile Broadband Module
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: compal-wifi: Wireless LAN        no            no
1: compal-bluetooth: Bluetooth      no            no
2: phy0: Wireless LAN               no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

b43                   356470  0 
bcma                   42043  1 b43
mac80211              546051  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=============o========o==============o=========o===========o==============o===========
 Interface & ID             | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
============================o=============o========o==============o=========o===========o==============o===========
 wlan0                      | 802.11 WiFi | b43    | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    enemeno:         Infra, <MAC C-01 enemeno>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74 WPA WPA2
    hosebee:         Infra, <MAC C-03 hosebee>, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2
    ATT208:          Infra, <MAC C-02 ATT208>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WEP
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 eth0  [Wired connection 1] | Wired       | r8169  | connected    | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.10.110
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4
    DNS:             192.168.10.1
----------------------------+-------------+--------+--------------+---------+-----------+--------------+-----------


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

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.1    0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0

--- 192.168.10.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.411/0.450/0.490/0.044 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.093/0.104/0.115/0.011 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     14 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 enemeno>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=11 dBm  
                    Encryption key:on
                    ESSID:"enemeno"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005baca44ac
                    Extra: Last beacon: 48ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 ATT208>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"ATT208"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000009f4a28930
                    Extra: Last beacon: 48ms ago
          Cell 03 - Address: <MAC C-03 hosebee>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"hosebee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007d16436e15
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/libpisock9.conf]
blacklist visor


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[b43]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     42BAE2DB9BADE3E7ECA2CC0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        

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

[ssb]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
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

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=9ffe6eaf-48fd-4970-b376-6b385e308151 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    1.372767] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.373660] audit: initializing netlink socket (disabled)
[    2.100852] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.140144] ssb: Found chip with id 0x4312, rev 0x01 and package 0x00
[    2.140168] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    2.140184] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    2.140200] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    2.140215] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    2.204365] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[   17.445203] psmouse serio1: elantech: assuming hardware version 2 (with firmware version 0x020801)
[   17.986881] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   18.064139] b43-phy0: Found PHY: Analog 6, Type 5 (LP), Revision 1
[   18.975405] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.312106] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   28.009211] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.010419] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

    ======== Done ========

---

### Post by Hadaka on 2014-07-17
Hi, please do,,
from a wired connection
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43
sudo modprobe b43
```
and since you are loading Lubuntu take a look here to see
if this is also part of your problem
[http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing](http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing)

---

### Post by Heyki on 2014-07-17
Wow! Thank you so much!!!!!

Problem fixed!

---

### Post by Hadaka on 2014-07-17
Glad that worked for you!
Please maek your thread SOLVED
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks

---

