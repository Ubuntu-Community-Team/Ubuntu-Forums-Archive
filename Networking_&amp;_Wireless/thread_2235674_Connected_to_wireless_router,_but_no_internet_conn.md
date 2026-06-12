---
title: "Connected to wireless router, but no internet connection"
date: 2014-07-22
forum: Networking &amp; Wireless
---

### Post by markkasville on 2014-07-22
I have this common problem: I can connect to wifi but still have no internet connection. This problem occurs only with my router. I can connect my laptop to other wifi networks eg. one provided by my cellphone or at university and so on. However, other devices suchs as cellphone and my friends' laptops running windows as operating system can use my wifi with no problems at all. I'm running ubuntu 14.04 LTS. 

Heeelp!

---

### Post by markkasville on 2014-07-22
Okay, I've been trying to look for an answer for three months before posting this thread and now after posting it I found a solution:
[http://ubuntuforums.org/showthread.php?t=1962635](http://ubuntuforums.org/showthread.php?t=1962635)

So thanks anyway :D

---

### Post by kc1di on 2014-07-22
Congratulations on your perseverance :)

---

### Post by markkasville on 2014-07-24
ARGHHHH. It only worked for one day... It seems to me that I need some help anyway. Any suggestions?

---

### Post by westie457 on 2014-07-24
From the old thread you linked are you still using these to install your wireless drivers? ```
sudo apt-get install [COLOR=#000000][FONT=Ubuntu Mono]b43-fwcutter firmware-b43-lpphy-installer[/FONT][/COLOR]
```

---

### Post by markkasville on 2014-07-24
No, I didn't need to do that. Actually all I did was to disable encryption from my connection.. When it didn't work I put it back on and there! That joy did not last long...

---

### Post by westie457 on 2014-07-24
Those drivers mentioned have now been deprecated, there is a different one in use now.
Are you using the one bundled in 'linux-firmware-nonfree' or something completely different?

---

### Post by markkasville on 2014-07-24
I have no idea

---

### Post by westie457 on 2014-07-24
Okay, with you not being sure of which driver you have go to [http://ubuntuforums.org/showthread.php?p=13024222#post13024222](http://ubuntuforums.org/showthread.php?p=13024222#post13024222) 
Follow the instructions there. We should get enough info to work on a fix.

Thank you

---

### Post by markkasville on 2014-07-24
Okay this is what I got:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Markkasville 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Athlon(tm) X2 Dual-Core QL-64
Memory : 3700 MB
Uptime : 11:41:44 up 58 min,  2 users,  load average: 0,34, 0,17, 0,10


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0207]
    Kernel driver in use: tg3
06:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Sukkalaatikko"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: <MAC C-01 Sukkalaatikko>   
          Bit Rate=52 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:219   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: acer-wireless: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  1 acer_wmi
video                  19476  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=0 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
==========================o=============o========o  ===========o=========o===========o==============o=  ==========
 Interface & ID           | Type        | Driver | State     | Default | Speed     | Support      | HW Addr   
==========================o=============o========o  ===========o=========o===========o==============o=  ==========
 wlan0  [Sukkalaatikko]   | 802.11 WiFi | ath9k  | connected | no      | 52 Mb/s   | WEP/WPA/WPA2 | <MAC wlan0>

    Angi & Co:       Infra, <MAC C-02 Angi <MAC C-NA Angi <MAC ID removed> Co 1> Co>, Freq 2412 MHz, Rate 54 Mb/s, Strength 60 WPA
    Hindut haisee:   Infra, <MAC C-07 Hindut haisee>, Freq 2447 MHz, Rate 54 Mb/s, Strength 72 WPA2
    Muikkuverkko:    Infra, <MAC C-06 Muikkuverkko>, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 WEP
    Kirahvinet:      Infra, <MAC C-05 Kirahvinet>, Freq 2437 MHz, Rate 22 Mb/s, Strength 24 WEP
    dlink:           Infra, <MAC C-09 dlink>, Freq 2432 MHz, Rate 54 Mb/s, Strength 35
    uusi:            Infra, <MAC C-04 uusi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA
    HATeittinen:     Infra, <MAC C-03 HATeittinen>, Freq 2472 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    *Sukkalaatikko:  Infra, <MAC C-01 Sukkalaatikko>, Freq 2472 MHz, Rate 54 Mb/s, Strength 93 WPA WPA2
    Andrea's:        Infra, <MAC C-NA Andrea's 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    DanMacBook :     Infra, <MAC C-08 DanMacBook >, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2

    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.89.123.29
    DNS:             193.210.19.19
--------------------------+-------------+--------+-----------+---------+-----------+--------------+-----------
 eth0  [Kiinteä yhteys 1]| Wired       | tg3    | connected | yes     | 100 Mb/s  |              | <MAC eth0>

    Address:         192.168.0.103
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1
    DNS:             192.89.123.29
    DNS:             193.210.19.19
--------------------------+-------------+--------+-----------+---------+-----------+--------------+-----------


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

NOKIA Lumia 800_1657 : ssid=NOKIA Lumia 800_1657 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Saavi                : ssid=Saavi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Saavi 1              : ssid=Saavi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Sukkalaatikko        : ssid=Sukkalaatikko | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Univ Helsinki HUPnet : ssid=Univ Helsinki HUPnet | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
VR-junaverkko        : ssid=VR-junaverkko | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Xperia Z             : ssid=Xperia Z | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ZyXEL_3D24           : ssid=ZyXEL_3D24 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1
search dhcp.inet.fi


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.0.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.369/0.406/0.444/0.042 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.067/0.090/0.114/0.025 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "fi_FI.UTF-8")
country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.472 GHz (Channel 13)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Sukkalaatikko>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"Sukkalaatikko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000cc763c85
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Angi <MAC C-NA Angi <MAC ID removed> Co 1> Co>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Angi & Co"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004faf2e3e33
                    Extra: Last beacon: 8ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 HATeittinen>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"HATeittinen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d46aa8173
                    Extra: Last beacon: 80ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 uusi>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"uusi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000008945a6815b
                    Extra: Last beacon: 1576ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 Kirahvinet>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"Kirahvinet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Mode:Master
                    Extra:tsf=0000004d842a0017
                    Extra: Last beacon: 8ms ago
          Cell 06 - Address: <MAC C-06 Muikkuverkko>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Muikkuverkko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000004fa7da0994
                    Extra: Last beacon: 8ms ago
          Cell 07 - Address: <MAC C-07 Hindut haisee>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=51/70  Signal level=-59 dBm  
                    Encryption key:on
                    ESSID:"Hindut haisee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000b689f2ceea
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 DanMacBook >
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"DanMacBook "
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 8ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 dlink>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000000eadc42d
                    Extra: Last beacon: 8ms ago


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

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

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:04.0/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:05.0/0000:06:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Not Default

[/etc/modprobe.d]
iwlagn.conf       : options iwlwifi 11n_disable=1
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
                    options iwlwifi 11n_disable=1
iwlwifi.conf~     : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
iwlwifi.conf.dpkg-old: options iwlwifi lln_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en

[/etc/pm/power.d/wireless]
#!/bin/sh/sbin/iwconfig wlan0 power off


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=70b3fcc9-8c73-4645-9ee5-b33006e0de86 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.660504] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.660989] audit: initializing netlink socket (disabled)
[    1.528508] tg3 0000:03:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   14.021995] wmi: Mapper loaded
[   15.905390] ath: EEPROM regdomain: 0x65
[   15.905397] ath: EEPROM indicates we should expect a direct regpair map
[   15.905401] ath: Country alpha2 being used: 00
[   15.905403] ath: Regpair used: 0x65
[   16.795931] acer_wmi: Acer Laptop ACPI-WMI Extras
[   16.799771] acer_wmi: Function bitmap for Communication Device: 0x3
[   16.800320] acer_wmi: Brightness must be controlled by acpi video driver
[   17.869332] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.825028] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.825569] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.218588] wlan0: authenticate with <MAC ID removed>
[   30.240120] wlan0: send auth to <MAC ID removed> (try 1/3)
[   30.242959] wlan0: authenticated
[   30.244090] wlan0: associate with <MAC ID removed> (try 1/3)
[   30.253877] wlan0: RX AssocResp from <MAC ID removed> (capab=0x431 status=0 aid=4)
[   30.253947] wlan0: associated
[   30.253995] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.452180] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=2)
[   30.461461] wlan0: authenticate with <MAC ID removed>
[   30.478995] wlan0: send auth to <MAC ID removed> (try 1/3)
[   30.483426] wlan0: authenticated
[   30.488405] wlan0: associate with <MAC ID removed> (try 1/3)
[   30.498431] wlan0: RX AssocResp from <MAC ID removed> (capab=0x431 status=0 aid=5)
[   30.498493] wlan0: associated
[  240.976766] wlan0: deauthenticating from <MAC ID removed> by local choice (reason=3)
[  254.505691] wlan0: authenticate with <MAC C-01 Sukkalaatikko>
[  254.527884] wlan0: send auth to <MAC C-01 Sukkalaatikko> (try 1/3)
[  254.530160] wlan0: authenticated
[  254.536504] wlan0: associate with <MAC C-01 Sukkalaatikko> (try 1/3)
[  254.540881] wlan0: RX AssocResp from <MAC C-01 Sukkalaatikko> (capab=0xc11 status=0 aid=2)
[  254.540948] wlan0: associated
[  254.550633] ath: EEPROM regdomain: 0x833a
[  254.550641] ath: EEPROM indicates we should expect a country code
[  254.550643] ath: doing EEPROM country->regdmn map search
[  254.550645] ath: country maps to regdmn code: 0x37
[  254.550647] ath: Country alpha2 being used: GB
[  254.550649] ath: Regpair used: 0x37
[  254.550651] ath: regdomain 0x833a dynamically updated by country IE

    ======== Done ========
```

---

### Post by markkasville on 2014-07-25
Anyone? I have absolutely no idea what to do.

---

### Post by varunendra on 2014-07-25
Why did you need to create that "/etc/pm/power.d/wireless" script? Was "Power Management" on your wifi interface automatically turning on?

The script is wrong by the way, and I suspect needless too, so please remove it, along with two other needless files -
```
sudo rm /etc/pm/power.d/wireless
sudo rm /etc/modprobe.d/{iwlagn,iwlwifi}.conf
```

Then moving towards a real fix, please change the encryption in your router/access-point to pure WPA2-PSK with AES (CCMP). Currently it is using WPA/WPA2 mixed mode with TKIP which should be avoided. Also try changing the channel to 1 or 11. Reboot the router after saving the changes.

In Ubuntu, if required after the above, try this -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot and let us know the status.

---

### Post by markkasville on 2014-07-25
I was desperate and tried everything I found from other threads so that is why those needless files exist. Anyway, I've done everything you suggested above and there no improvement.. :confused:

---

### Post by steeldriver on 2014-07-25
What **exactly **are your symptoms? can you ping an external host by IP? by name? not at all? When you try to open a page in your browser, what errors do you get?

---

### Post by markkasville on 2014-07-25
Symptoms: I am connected to my wireless network, but when I open the browser it just keeps connecting... and nothing happens. There is no error messages it just says "connecting..."
When I try to ping, I'll get this:
```
markkasville@Markkasville:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=8 ttl=48 time=18.6 ms

```
It answers only once and then silence continues

Oh and when I tried to ping [www.google.com](www.google.com), Igot "unknown host"
And when I tried to ping my router 192.168.0.1 I got the same result with 8.8.8.8

---

### Post by yash_pal2 on 2014-07-25
I do not know if my experience will be of any help.
I had the same problem when I installed Ubuntu 14.04 jus tt after release; I called up the ISP, got the modem checked etc. Then one person from the ISP told me that it was a driver problem.
I searched on the net and 'ask Ubuntu' etc; what I could make out was that I purge the proprietary driver and install another driver through the command line (I have forgotten which driver). I did it and got the WiFi back. I do not however, edit any system files.Do not know how to do it.

---

### Post by steeldriver on 2014-07-25
How are you setting your IP addresses? is the 192.168.1.102 obtained via DHCP or set manually (statically)? Is it possible that another device on the LAN segment is using the same IP?

---

### Post by markkasville on 2014-07-25
Via DHCP. And for the other question, I dont know?

---

### Post by varunendra on 2014-07-26
After running a ping -
```
ping -c4 8.8.8.8
```
..and letting it finish, please run these -
```
ifconfig -a
dmesg | tail -20
route -n
nm-tool
```
..and post back their results.

And have you also tried manually assigning a different IP yet? Like 192.168.1.250, or any other one on the same subnet, one that you are sure is 'Outside' the DHCP pool (check in the router) and is not already being used by some other device on the network?

---

### Post by jeremy31 on 2014-07-26
So are you in Finland or Great Britain?  The results from ```
iw reg get
``` in the wireless script says GB.  What is the manufacturer and model number of your router?

---

### Post by mode7 on 2014-07-26
Seeing as we are using two completely different network devices, I highly doubt my issue ([http://ubuntuforums.org/showthread.php?t=2236092](http://ubuntuforums.org/showthread.php?t=2236092)) is related, but I am having somewhat similar issues.

Does your network indicator always say that you are connected, even when you obviously can't connect to the internet?
My connection seems to vary between working and not (Usually not), and when it isn't working, I can't even ping my gateway.

I've found that both Ubuntu 14.04 and Fedora 20 suffer the same issue, although Mac OSX and Ubuntu 12.04 do not have the issue. Not to mention the modern distros worked fine until a ~week ago!

So just curious, if you have any older copies of Ubuntu or maybe another distro to burn to a USB key, just to use the internet for a bit and see if it works. No clue if the atheros drivers automatically start in a live environment, unlike mine.
Would nail it down a bit further (Hardware/software/router, etc..) Good luck, will keep an eye on this.

---

### Post by markkasville on 2014-07-27
Here are the results:
```
markkasville@Markkasville:~$ ping -c4 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=2 ttl=48 time=20.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=48 time=19.7 ms

--- 8.8.8.8 ping statistics ---
4 packets transmitted, 2 received, 50% packet loss, time 3012ms
rtt min/avg/max/mdev = 19.759/20.271/20.784/0.531 ms
markkasville@Markkasville:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:16:99:01:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:19062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2844739 (2.8 MB)  TX bytes:2844739 (2.8 MB)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:7d:0b:a2  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:c4ff:fe7d:ba2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17643 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19847 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9702385 (9.7 MB)  TX bytes:4826190 (4.8 MB)

markkasville@Markkasville:~$ dmesg | tail -20
[21855.132530] wlan0: send auth to 78:54:2e:52:3b:c4 (try 1/3)
[21855.136098] wlan0: authenticated
[21855.140098] wlan0: associate with 78:54:2e:52:3b:c4 (try 1/3)
[21855.147234] wlan0: RX AssocResp from 78:54:2e:52:3b:c4 (capab=0xc11 status=0 aid=2)
[21855.147297] wlan0: associated
[21855.147381] cfg80211: Calling CRDA for country: GB
[21855.153340] ath: EEPROM regdomain: 0x833a
[21855.153347] ath: EEPROM indicates we should expect a country code
[21855.153350] ath: doing EEPROM country->regdmn map search
[21855.153352] ath: country maps to regdmn code: 0x37
[21855.153354] ath: Country alpha2 being used: GB
[21855.153356] ath: Regpair used: 0x37
[21855.153358] ath: regdomain 0x833a dynamically updated by country IE
[21855.153385] cfg80211: Regulatory domain changed to country: GB
[21855.153387] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[21855.153389] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[21855.153392] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[21855.153394] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[21855.153396] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[21855.153398] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
markkasville@Markkasville:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0
markkasville@Markkasville:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Sukkalaatikko] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             connected
  Default:           yes
  HW Address:        00:17:C4:7D:0B:A2

  Capabilities:
    Speed:           52 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Angi & Co:       Infra, 10:0D:7F:AC:13:9C, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA
    Hindut haisee:   Infra, 00:1E:AB:03:78:D4, Freq 2447 MHz, Rate 54 Mb/s, Strength 87 WPA2
    uusi:            Infra, C8:3A:35:5B:34:98, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA
    Andrea's:        Infra, 12:7B:EF:5C:5F:10, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    enuma elish:     Infra, C8:BE:19:B3:10:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    ZyXEL_5286:      Infra, B0:B2:DC:CB:C2:85, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Koti_C2FC:       Infra, 2A:28:5D:40:C2:FC, Freq 2467 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    SoneraGateway08-76-FF-95-1E-77: Infra, 08:76:FF:95:1E:77, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    VDSL-AP:         Infra, 00:1E:AB:05:61:2C, Freq 2422 MHz, Rate 54 Mb/s, Strength 14 WPA
    Kirahvinet:      Infra, 00:80:C8:23:9E:05, Freq 2437 MHz, Rate 22 Mb/s, Strength 30 WEP
    dlink:           Infra, C8:D3:A3:07:7D:BA, Freq 2427 MHz, Rate 54 Mb/s, Strength 42
    Muikkuverkko:    Infra, 34:08:04:25:4D:1E, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WEP
    Langatonkoti2:   Infra, BC:EE:7B:71:29:81, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA2
    4318d6:          Infra, 4C:72:B9:0B:EB:FB, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    ZTE_087c:        Infra, 00:26:ED:60:08:7D, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA
    ZyXEL_2728:      Infra, CC:5D:4E:7A:EB:CB, Freq 2412 MHz, Rate 54 Mb/s, Strength 15 WPA2
    dd-wrt:          Infra, 00:18:39:C0:12:CD, Freq 2437 MHz, Rate 54 Mb/s, Strength 17
    Xperia Z:        Infra, A0:E4:53:CA:1E:1A, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2
    Jotainmuuta:     Infra, 84:DB:2F:44:9C:A9, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    ZyXEL_5745:      Infra, B0:B2:DC:ED:6B:1F, Freq 2437 MHz, Rate 54 Mb/s, Strength 17 WPA2
    *Sukkalaatikko:  Infra, 78:54:2E:52:3B:C4, Freq 2412 MHz, Rate 54 Mb/s, Strength 69 WPA2
    NETGEAR63:       Infra, 74:44:01:9E:7C:C8, Freq 2417 MHz, Rate 54 Mb/s, Strength 19 WPA2
    NETGEAR31:       Infra, 10:0D:7F:AA:05:A6, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.89.123.29
    DNS:             193.210.19.19


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        00:1F:16:99:01:B3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

```

And no I haven't tried assigning a different IP manually, but will do that soon.. 

For jeremy31, I am in Finland. 

I had this same issue also with 12.04.

---

### Post by markkasville on 2014-07-27
I have tested now with static IP, and no improvement... :confused:

---

### Post by jeremy31 on 2014-07-27
If you are in Finland you will want this set```
sudo iw reg set FI
```
and ```
sudo gedit /etc/default/crda
``` and change the last line so that it is ```
REGDOMAIN=FI
```
Save and exit program, reboot

---

### Post by markkasville on 2014-07-27
Done. Oh, and the router that I'm using is dlink GO-RT-N150.

---

### Post by varunendra on 2014-07-27
So was there any improvement with that modification? To confirm the change took effect, check the output of -
```
iw reg get
```
It should now show "FI" and settings pertaining to it.

Since you don't seem to be using IPv6, I suggest completely disabling it following instructions in this post : [http://ubuntuforums.org/showpost.php?p=12640479](http://ubuntuforums.org/showpost.php?p=12640479)
If the problem is due to some IPv6 confusion between the system and the router, this should fix it.

---

### Post by jeremy31 on 2014-07-27
> **markkasville said:**
> Done. Oh, and the router that I'm using is dlink GO-RT-N150.

Did you make any modifications to the stock settings, maybe MAC address filtering or disable some wireless options

---

### Post by markkasville on 2014-07-27
No there was no improvement.. iw reg get says now FI, so that is ok. 
And nope, I haven't made any modifications to the settings.

---

### Post by markkasville on 2014-07-27
I have also now disabled IPv6, no improvement.

---

### Post by varunendra on 2014-07-29
May we see a fresh wireless_script report then?

---

### Post by UltimateCat on 2014-07-30
Hi:

Looking at the output of your Ethernet card: BCM5784m-

Installing the the broadcom driver for you network interface card might solve the issue.
 
[http://drivers.softpedia.com/downloadTag/Broadcom+BCM5784M+LAN+driver](http://drivers.softpedia.com/downloadTag/Broadcom+BCM5784M+LAN+driver)
[http://www.broadcom.com/support/ethernet_nic/netlink.php](http://www.broadcom.com/support/ethernet_nic/netlink.php)

But your wireless card is a Atheros AR928x-
I would think the the kernel would be providing support, the module/driver for your wireless card.
Maybe look for a driver for the Atheros card?

If that doesn't help try installing the driver for your chipset on your mobo-

Aside from that I wonder if the 2 cards are generating conflict? (anything is possible)

Look in your network interface file and make sure that the wireless option isn't blocked out by the (#) pound sign.

Mine was and Wired was uncommented.  As soon as I commented out 'Wired' and made sure 'Wireless' was uncommented my wireless worked.
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

Hope that helps-

---

### Post by markkasville on 2014-08-01
Here is the wireless script:
```

    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

Markkasville 3.13.0-32-generic x86_64,  Ubuntu 14.04.1 LTS, trusty

CPU    : AMD Athlon(tm) X2 Dual-Core QL-64
Memory : 3700 MB
Uptime : 11:00:14 up  1:52,  2 users,  load average: 0,28, 0,19, 0,10


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:0207]
    Kernel driver in use: tg3
06:00.0 Network controller [0280]: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 003: ID 04f2:b044 Chicony Electronics Co., Ltd Acer CrystalEye Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 13ee:0001 MosArt 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:"Xperia Z"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC C-01 Xperia Z>   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface                 Soft blocked  Hard blocked
0: phy0: Wireless LAN               no            no
1: acer-wireless: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

acer_wmi               32522  0 
sparse_keymap          13948  1 acer_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
video                  19476  1 acer_wmi
wmi                    19177  1 acer_wmi


module parameters ~~~~~~~~~~~~~~~~~~

acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
ath9k         (5): blink=0 | bt_ant_diversity=0 | btcoex_enable=0 | nohwcrypt=1 | ps_enable=0
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
===================o=============o========o=======  ======o=========o===========o==============o======  =====
 Interface & ID    | Type        | Driver | State       | Default | Speed     | Support      | HW Addr   
===================o=============o========o=======  ======o=========o===========o==============o======  =====
 wlan0  [Xperia Z] | 802.11 WiFi | ath9k  | connected   | yes     | 1 Mb/s    | WEP/WPA/WPA2 | <MAC wlan0>

    Hindut haisee:   Infra, <MAC C-04 Hindut haisee>, Freq 2447 MHz, Rate 54 Mb/s, Strength 99 WPA2
    Angi & Co:       Infra, <MAC C-03 Angi <MAC C-NA Angi <MAC ID removed> Co 1> Co>, Freq 2412 MHz, Rate 54 Mb/s, Strength 52 WPA
    uusi:            Infra, <MAC C-09 uusi>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA
    dlink:           Infra, <MAC C-05 dlink>, Freq 2442 MHz, Rate 54 Mb/s, Strength 35
    Andrea's:        Infra, <MAC C-08 Andrea's>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    Hamsterbackenkönigin: Infra, <MAC C-07 Hamsterbackenkönigin>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    ZyXEL_5286:      Infra, <MAC C-NA ZyXEL_5286 1>, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WPA2
    360WiFi-1329:    Infra, <MAC C-NA 360WiFi-1329 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    Sukkalaatikko:   Infra, <MAC C-02 Sukkalaatikko>, Freq 2412 MHz, Rate 54 Mb/s, Strength 68 WPA2
    Muikkuverkko:    Infra, <MAC C-NA Muikkuverkko 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP
    *Xperia Z:       Infra, <MAC C-01 Xperia Z>, Freq 2412 MHz, Rate 54 Mb/s, Strength 80 WPA2
    dd-wrt:          Infra, <MAC C-06 dd-wrt>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19

    Address:         192.168.43.145
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.43.1
    DNS:             192.168.43.1
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------
 eth0              | Wired       | tg3    | unavailable | no      |           |              | <MAC eth0>
-------------------+-------------+--------+-------------+---------+-----------+--------------+-----------


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

NOKIA Lumia 800_1657 : ssid=NOKIA Lumia 800_1657 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Saavi                : ssid=Saavi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Saavi 1              : ssid=Saavi | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
Sukkalaatikko        : ssid=Sukkalaatikko | mac-address=<MAC wlan0> | ipv4=auto | ipv6=ignore 
Univ Helsinki HUPnet : ssid=Univ Helsinki HUPnet | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
VR-junaverkko        : ssid=VR-junaverkko | mac-address=<MAC wlan0> | ipv6=auto | ipv4=auto 
Xperia Z             : ssid=Xperia Z | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 
ZyXEL_3D24           : ssid=ZyXEL_3D24 | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.43.1    0.0.0.0         UG    0      0        0 wlan0
192.168.43.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

--- 192.168.43.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 4.163/7.376/10.589/3.213 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.069/0.090/0.112/0.023 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "fi_FI.UTF-8")
country FI:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)

          Current Frequency:2.412 GHz (Channel 1)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 Xperia Z>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-39 dBm  
                    Encryption key:on
                    ESSID:"Xperia Z"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001951b2bca
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Sukkalaatikko>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"Sukkalaatikko"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000c1423cb37
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 Angi <MAC C-NA Angi <MAC ID removed> Co 1> Co>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"Angi & Co"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bf1721fe4
                    Extra: Last beacon: 4ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC C-04 Hindut haisee>
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Hindut haisee"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bf0e8eb99
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC C-05 dlink>
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000940f972a5
                    Extra: Last beacon: 4ms ago
          Cell 06 - Address: <MAC C-06 dd-wrt>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:off
                    ESSID:"dd-wrt"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bf10371a2
                    Extra: Last beacon: 18544ms ago
          Cell 07 - Address: <MAC C-07 Hamsterbackenkönigin>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"Hamsterbackenkönigin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000ced61913a
                    Extra: Last beacon: 12896ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: <MAC C-08 Andrea's>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Andrea's"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bf0880136
                    Extra: Last beacon: 460ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: <MAC C-09 uusi>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"uusi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000003bf2487158
                    Extra: Last beacon: 1588ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[acer_wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/acer-wmi.ko
srcversion:     15371DC0E403E93954B38E5
depends:        wmi,sparse-keymap,video
parm:           mailled:Set initial state of Mail LED (int)
parm:           brightness:Set initial LCD backlight brightness (int)
parm:           threeg:Set initial state of 3G hardware (int)
parm:           force_series:Force a different laptop series (int)
parm:           ec_raw_mode:Enable EC raw mode (bool)

[ath9k]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
srcversion:     7EAAD420ADF6B9354F0C8C1
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[ath9k_common]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
srcversion:     696B00A6C59713EC0966997
depends:        ath,ath9k_hw

[ath9k_hw]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
srcversion:     4809F3842A0542CD6B556D3
depends:        ath

[ath]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/net/wireless/ath/ath.ko
srcversion:     88A67C5359B02C5A710AFCF
depends:        cfg80211

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

[video]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/acpi/video.ko
srcversion:     274A2250DEAB415D412A67C
depends:        
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool
parm:           use_native_backlight:int

[wmi]
filename:       /lib/modules/3.13.0-32-generic/kernel/drivers/platform/x86/wmi.ko
srcversion:     CED5410F008DC70DF5F064B
depends:        
parm:           debug_event:Log WMI Events [0/1] (bool)
parm:           debug_dump_wdg:Dump available WMI interfaces [0/1] (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:04.0/0000:03:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:05.0/0000:06:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
ath9k.conf        : options ath9k nohwcrypt=1
iwlwifi.conf~     : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
iwlwifi.conf.dpkg-old: options iwlwifi lln_disable=1
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=70b3fcc9-8c73-4645-9ee5-b33006e0de86 ro quiet splash vt.handoff=7


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    0.669269] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.669758] audit: initializing netlink socket (disabled)
[    1.583731] tg3 0000:03:00.0 eth0: attached PHY is 5784 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[   23.285743] wmi: Mapper loaded
[   23.988427] ath: EEPROM regdomain: 0x65
[   23.988434] ath: EEPROM indicates we should expect a direct regpair map
[   23.988439] ath: Country alpha2 being used: 00
[   23.988441] ath: Regpair used: 0x65
[   24.367672] acer_wmi: Acer Laptop ACPI-WMI Extras
[   24.372872] acer_wmi: Function bitmap for Communication Device: 0x3
[   24.373370] acer_wmi: Brightness must be controlled by acpi video driver
[   24.758588] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   27.679468] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.908552] wlan0: authenticate with <MAC C-02 Sukkalaatikko>
[   28.925801] wlan0: send auth to <MAC C-02 Sukkalaatikko> (try 1/3)
[   28.927854] wlan0: authenticated
[   28.932075] wlan0: associate with <MAC C-02 Sukkalaatikko> (try 1/3)
[   28.936391] wlan0: RX AssocResp from <MAC C-02 Sukkalaatikko> (capab=0xc11 status=0 aid=2)
[   28.936457] wlan0: associated
[   28.936501] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.941700] ath: EEPROM regdomain: 0x833a
[   28.941706] ath: EEPROM indicates we should expect a country code
[   28.941709] ath: doing EEPROM country->regdmn map search
[   28.941711] ath: country maps to regdmn code: 0x37
[   28.941713] ath: Country alpha2 being used: GB
[   28.941714] ath: Regpair used: 0x37
[   28.941717] ath: regdomain 0x833a dynamically updated by country IE
[  121.724907] wlan0: deauthenticating from <MAC C-02 Sukkalaatikko> by local choice (reason=3)
[  122.761888] wlan0: authenticate with <MAC C-01 Xperia Z>
[  122.783927] wlan0: send auth to <MAC C-01 Xperia Z> (try 1/3)
[  122.788199] wlan0: authenticated
[  122.792073] wlan0: associate with <MAC C-01 Xperia Z> (try 1/3)
[  122.807116] wlan0: RX AssocResp from <MAC C-01 Xperia Z> (capab=0x431 status=0 aid=1)
[  122.807186] wlan0: associated
[ 6725.520906] wlan0: deauthenticating from <MAC C-01 Xperia Z> by local choice (reason=3)
[ 6725.532537] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6726.789955] wlan0: authenticate with <MAC C-02 Sukkalaatikko>
[ 6726.816379] wlan0: send auth to <MAC C-02 Sukkalaatikko> (try 1/3)
[ 6726.819190] wlan0: authenticated
[ 6726.820319] wlan0: associate with <MAC C-02 Sukkalaatikko> (try 1/3)
[ 6726.824740] wlan0: RX AssocResp from <MAC C-02 Sukkalaatikko> (capab=0xc11 status=0 aid=2)
[ 6726.824815] wlan0: associated
[ 6726.830672] ath: EEPROM regdomain: 0x833a
[ 6726.830680] ath: EEPROM indicates we should expect a country code
[ 6726.830682] ath: doing EEPROM country->regdmn map search
[ 6726.830684] ath: country maps to regdmn code: 0x37
[ 6726.830686] ath: Country alpha2 being used: GB
[ 6726.830688] ath: Regpair used: 0x37
[ 6726.830690] ath: regdomain 0x833a dynamically updated by country IE
[ 6761.972955] wlan0: deauthenticating from <MAC C-02 Sukkalaatikko> by local choice (reason=3)
[ 6763.017430] wlan0: authenticate with <MAC C-01 Xperia Z>
[ 6763.039796] wlan0: send auth to <MAC C-01 Xperia Z> (try 1/3)
[ 6763.044100] wlan0: authenticated
[ 6763.048118] wlan0: associate with <MAC C-01 Xperia Z> (try 1/3)
[ 6763.064208] wlan0: RX AssocResp from <MAC C-01 Xperia Z> (capab=0x431 status=0 aid=2)
[ 6763.064314] wlan0: associated

    ======== Done ========
```

---

### Post by markkasville on 2014-08-03
> Aside from that I wonder if the 2 cards are generating conflict? (anything is possible)

Look in your network interface file and make sure that the wireless option isn't blocked out by the (#) pound sign.

Mine was and Wired was uncommented.  As soon as I commented out 'Wired'  and made sure 'Wireless' was uncommented my wireless worked.

Now I got confused :D When I looked my network interfaces file, all it said was:
```
auto lo
iface lo inet loopback
```

And I don't know which driver to install. Looking those broadcomm drivers, I think I already have that tg3 that is made for linux. For my atheros card, I can't find any and really don't know which one to get..

I'm getting frustrated with this problem. I think I'll soon buy a new router since the problem only occurs with this one :mad:

---

