---
title: "Ubuntu 12.04 connected to wifi but not internet"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by kyle_gags on 2014-03-13
Im running  Ubuntu 12.04 and windows 7 dual boot on my computer....had it running great for awhile...for some reason 2day when I load up Ubuntu and click on  firefox it doesn't load any pages....it also wont download any updates or apps but shows its connected to my wifi..I tried to disconnect and reconnect didn't help..so I switched over to my windows 7 and internet works fine connects to pages on firefox....its not my wifi or router...also got mint on a laptop and its still working and all other wifi devices working....its only the Ubuntu OS not working can u please help me

---

### Post by wildmanne39 on 2014-03-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by kyle_gags on 2014-03-13
[EMAIL="gagz@kyle-Ubuntu-570:~$"]gagz@kyle-Ubuntu-570:~$[/EMAIL] wget -N -t 5 -T 10 [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script) && chmod +x wireless_script && ./wireless_script
--2014-03-13 12:50:58--  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Resolving dl.dropbox.com (dl.dropbox.com)... 54.235.185.191
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.185.191|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.
--2014-03-13 12:51:09--  (try: 2)  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.185.191|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.
--2014-03-13 12:51:21--  (try: 3)  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.185.191|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.
--2014-03-13 12:51:34--  (try: 4)  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.185.191|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.
--2014-03-13 12:51:48--  (try: 5)  [http://dl.dropbox.com/u/57264241/wireless_script](http://dl.dropbox.com/u/57264241/wireless_script)
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.185.191|:80... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Giving up.

---

### Post by wildmanne39 on 2014-03-13
If you do not have a wired connection to the internet, follow the directions for running the script without internet.
Thanks

---

### Post by kyle_gags on 2014-03-13
```
*************** info trace ***************
***** uname -a *****
Linux kyle-Ubuntu-570 3.5.0-46-generic #70~precise1-Ubuntu SMP Thu Jan 9 23:56:40 UTC 2014 i686 athlon i386 GNU/Linux
***** lsb_release *****
Distributor ID: Ubuntu
Description: Ubuntu 12.04.4 LTS
Release: 12.04
Codename: precise
***** lspci *****
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57788 Gigabit Ethernet PCIe [14e4:1691] (rev 01)
 Subsystem: Dell Device [1028:043b]
 Kernel driver in use: tg3
***** lsusb *****
Bus 001 Device 005: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 008: ID 154b:005b PNY 
Bus 002 Device 002: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 004 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
***** PCMCIA Card Info *****

***** iwconfig *****
wlan0     IEEE 802.11bgn  ESSID:"HOME-18F2"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC address removed>   
          Bit Rate=40.5 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:15   Missed beacon:0

***** rfkill *****
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
***** modules *****
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
lp
***** iw reg get *****
country US:
 (2402 - 2472 @ 40), (3, 27)
 (5170 - 5250 @ 40), (3, 17)
 (5250 - 5330 @ 40), (3, 20), DFS
 (5490 - 5600 @ 40), (3, 20), DFS
 (5650 - 5710 @ 40), (3, 20), DFS
 (5735 - 5835 @ 40), (3, 30)
***** route -n *****
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
***** lsmod *****
rt2800usb              22487  0 
rt2800lib              57759  1 rt2800usb
crc_ccitt              12628  1 rt2800lib
rt2x00usb              20100  1 rt2800usb
rt2x00lib              49132  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              475546  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              181041  2 rt2x00lib,mac80211
***** nm-tool *****
NetworkManager Tool
State: connected (global)
- Device: wlan0  [HOME-18F2] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>
  Capabilities:
    Speed:           40 Mb/s
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points (* = current AP)
    xfinitywifi:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 72
    *HOME-18F2:      Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
  IPv4 Settings:
    Address:         10.0.0.7
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1
    DNS:             75.75.75.75
    DNS:             75.75.76.76

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off
 
***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
***** NetworkManager.conf *****
[main]
plugins=ifupdown,keyfile
dns=dnsmasq
[ifupdown]
managed=false
***** interfaces *****
auto lo
iface lo inet loopback

***** iwlist *****
wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"HOME-18F2"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a95d5f5fa0
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 0009484F4D452D31384632
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040010127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880E8892C3718F010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 02 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a95d5f6685
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040010127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
          Cell 03 - Address: <MAC address removed>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a95d5f8bc6
                    Extra: Last beacon: 920ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A8E1117FFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D1602050700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05040010127A
                    IE: Unknown: DD07000C4303000000

***** resolv.conf *****
nameserver 127.0.0.1
search hsd1.ma.comcast.net
***** blacklist *****
[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci
[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
***** modinfo *****
filename:       /lib/modules/3.5.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     3491B9A75F074353944FB6C
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2800lib,rt2x00usb
intree:         Y
vermagic:       3.5.0-46-generic SMP mod_unload modversions 686 
parm:           nohwcrypt:Disable hardware encryption. (bool)
filename:       /lib/modules/3.5.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     4627A4C7E050057E9DBCDFA
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.5.0-46-generic SMP mod_unload modversions 686 
filename:       /lib/modules/3.5.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     76DF3E9BBB78C390A941991
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.5.0-46-generic SMP mod_unload modversions 686 
filename:       /lib/modules/3.5.0-46-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     50E1A05E5303C84B098FDD7
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.5.0-46-generic SMP mod_unload modversions 686 

***** udev rules *****
# USB device 0x148f:0x5370 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:07.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
***** dmesg *****
[   18.603964] Registered led device: rt2800usb-phy0::radio
[   18.603983] Registered led device: rt2800usb-phy0::assoc
[   18.604002] Registered led device: rt2800usb-phy0::quality
[   20.314762] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.315016] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.541608] wlan0: authenticate with <MAC address removed>
[   23.582575] wlan0: send auth to <MAC address removed> (try 1/3)
[   23.583661] wlan0: authenticated
[   23.605104] wlan0: associate with <MAC address removed> (try 1/3)
[   23.612233] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   23.619695] wlan0: associated
[   23.619889] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
****************** done ******************
```

---

### Post by wildmanne39 on 2014-03-13
I have to leave now to go to the VA DR. I will be back ASAP.

---

### Post by kyle_gags on 2014-03-13
ok

---

### Post by wildmanne39 on 2014-03-13
Did this issue start after an update? or an upgrade to a newer version of ubuntu?

I recommend setting your router channel to 1 or 11, and encryption in the router to just wpa2 AES not TKIP. 

Also your link quality is low at 47.

I would turn power management off this is just temporary until you reboot.
```
sudo iwconfig wlan0 power off
``` 
Thanks

---

### Post by kyle_gags on 2014-03-13
I was away for a week I don't remember if I updated or not I think I did....how do I change the channel

---

### Post by wildmanne39 on 2014-03-13
You go into your router usually by typing 192.168.0.1 into your browser, sometimes the numbers will be different, if they are you will have to look at the documentation for your router. Once in look for a drop down menu with channels listed on it and set it to 1 or 11 then save the router configuration and it will reboot.

---

### Post by kyle_gags on 2014-03-13
ok so change channel to 1 or 11 first....than go to my Ubuntu type sudo iwconfig wlan0 power off   than reboot? that's all anything after that?

---

### Post by wildmanne39 on 2014-03-13
You can reboot your computer before you turn the power off, power off is temporary, it will come back on when you reboot.

There are a few other things to try after you try this first.
Thanks

---

### Post by kyle_gags on 2014-03-13
wow It worked!!!! all I did was change the channel to 1.....when I go to system info says theres updates to download should I do it?? or leave it alone...I don't wanna lose the internet again lol.....thanks so much btw

---

### Post by wildmanne39 on 2014-03-13
It should be okay to update 12.04 I have not had any trouble with it, but there is always a chance.

---

### Post by kyle_gags on 2014-03-13
im gonna leave it lol....thank you so much for all your help!!!!

---

