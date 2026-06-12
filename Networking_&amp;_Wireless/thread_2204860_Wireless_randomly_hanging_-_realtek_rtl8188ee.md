---
title: "Wireless randomly hanging - realtek rtl8188ee"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by samfraser on 2014-02-10
I'm running Ubuntu 13 on a HP Pavilion Laptop and I'm having a very strange problem with the wireless connectivity where the wireless loses it's IP connectivity for a few minutes and then just randomly returns!  I appear to be running the latest driver

dmesg | grep rtl
[   13.461807] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   13.535433] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   13.535654] rtlwifi: wireless switch is on

Any ideas as to what could be causing this?

---

### Post by varunendra on 2014-02-13
Hello samfraser,

We may need a more detailed info to be able to find the problem and troubleshoot it. Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by samfraser on 2014-02-14
```
samfraser@hp:~$ wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
--2014-02-14 20:59:22--  http://dl.dropbox.com/u/57264241/wireless_script
Resolving dl.dropbox.com (dl.dropbox.com)... 54.235.139.148
Connecting to dl.dropbox.com (dl.dropbox.com)|54.235.139.148|:80... connected.
HTTP request sent, awaiting response... 302 FOUND
Location: http://dl.dropboxusercontent.com/u/57264241/wireless_script [following]
--2014-02-14 20:59:22--  http://dl.dropboxusercontent.com/u/57264241/wireless_script
Resolving dl.dropboxusercontent.com (dl.dropboxusercontent.com)... 107.21.115.150
Connecting to dl.dropboxusercontent.com (dl.dropboxusercontent.com)|107.21.115.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4112 (4.0K) [text/plain]
Saving to: ‘wireless_script’

100%[======================================================================================================>] 4,112       --.-K/s   in 0.001s  

Last-modified header missing -- time-stamps turned off.
2014-02-14 20:59:23 (6.29 MB/s) - ‘wireless_script’ saved [4112/4112]


Results saved in "wireless-info.txt".

samfraser@hp:~$ 
samfraser@hp:~$ 
samfraser@hp:~$ ls
backports-3.11-rc3-1  Desktop    Downloads         glarocks                      Music      nasdrive  Pictures  Templates  wireless-info.txt
bkg_top.jpg           Documents  examples.desktop  linux-firmware_1.106_all.deb  nasbackup  nasmedia  Public    Videos     wireless_script
samfraser@hp:~$ cat wireless-info.txt

*************** info trace ***************

***** uname -a *****

Linux hp 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy

***** lspci *****

01:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:2185]
	Kernel driver in use: r8169

***** lsusb *****

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"frasers"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:162   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

***** lsmod *****

rtl8188ee             137939  0 
rtlwifi               120819  1 rtl8188ee
mac80211              494237  2 rtlwifi,rtl8188ee
cfg80211              469877  2 mac80211,rtlwifi
compat                 13139  4 cfg80211,mac80211,rtlwifi,rtl8188ee

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [frasers] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKYD8F8C:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 67 WPA2
    *frasers:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 63 WPA2
    BTWifi-with-FON: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 74

  IPv4 Settings:
    Address:         192.168.1.12
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=0 dBm  
                    Encryption key:on
                    ESSID:"frasers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000007fae9c0376
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 000766726173657273
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AEC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010E4476EE6BE7CA5A31A1A64837D9FB2611021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180207F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"TALKTALK-1631BC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001235861917b
                    Extra: Last beacon: 4184ms ago
                    IE: Unknown: 000F54414C4B54414C4B2D313633314243
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010040
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880283CE41631C4103C000101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2D1A8E1103FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000600000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05050015127A
                    IE: Unknown: DD07000C4304000000
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"SKYD8F8C"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e8228bc68
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0008534B594438463843
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 0B050200B10000
                    IE: Unknown: 2D1AAC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F03000008
                    IE: Unknown: DD800050F204104A0001101044000102103B000103104700107108B71508F331B94F0C1530192F71351021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004313233341054000800060050F20400011011000A42726F6164636F6D415010080002200C103C0001011049000600372A000120
                    IE: Unknown: DD090010180202000C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"BTWiFi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001cdfa93d80
                    Extra: Last beacon: 784ms ago
                    IE: Unknown: 0006425457694669
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AAC011BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101890003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.1.1
search Home

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

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
version:        backported from Linux (v3.11-rc3-0-g5ae90d8) using backports v3.11-rc3-1-0-g4e81a94
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         zhiyuan_yang	<zhiyuan_yang@realsil.com.cn>
srcversion:     2FC5815E992A98ED52FB6B0
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,compat,mac80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko
version:        backported from Linux (v3.11-rc3-0-g5ae90d8) using backports v3.11-rc3-1-0-g4e81a94
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     D3C065189679DEF714BBCBB
depends:        mac80211,compat,cfg80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8179 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   12.483330] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   12.740169] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.740399] rtlwifi: wireless switch is on
[   20.076019] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.005293] wlan0: authenticate with <MAC address removed>
[   23.024446] wlan0: send auth to <MAC address removed> (try 1/3)
[   23.026017] wlan0: authenticated
[   23.028087] wlan0: associate with <MAC address removed> (try 1/3)
[   23.031335] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[   23.031510] wlan0: associated
[   23.031525] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6987.476520] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 6991.448619] rtlwifi: wireless switch is on
[ 6994.703201] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6997.056335] wlan0: authenticate with <MAC address removed>
[ 6997.075207] wlan0: send auth to <MAC address removed> (try 1/3)
[ 6997.076816] wlan0: authenticated
[ 6997.078832] wlan0: associate with <MAC address removed> (try 1/3)
[ 6997.082294] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=6)
[ 6997.082549] wlan0: associated
[ 6997.082649] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15369.813452] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[15372.966299] rtlwifi: wireless switch is on
[15376.169064] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[15378.721755] wlan0: authenticate with <MAC address removed>
[15378.740480] wlan0: send auth to <MAC address removed> (try 1/3)
[15378.742097] wlan0: authenticated
[15378.743985] wlan0: associate with <MAC address removed> (try 1/3)
[15378.749170] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[15378.749362] wlan0: associated
[15378.749417] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[15388.858178] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[15390.242159] wlan0: authenticate with <MAC address removed>
[15390.260797] wlan0: send auth to <MAC address removed> (try 1/3)
[15390.262438] wlan0: authenticated
[15390.264309] wlan0: associate with <MAC address removed> (try 1/3)
[15390.267634] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=7)
[15390.267811] wlan0: associated

****************** done ******************

```

---

### Post by varunendra on 2014-02-14
You are running the backported driver from 3.11-rc3, while are using kernel 3.11 itself. As such, your current driver is older than what your kernel originally came with, it's not the latest (although latest is not always the greatest).

Please try a later one that has been reported to be working by a few users, following this answer on AU : [http://askubuntu.com/a/398749](http://askubuntu.com/a/398749)

---

### Post by samfraser on 2014-02-15
Ok i've installed backport wifi driver for 3.13, let see how it gets on.

---

### Post by samfraser on 2014-02-17
Ok, the verdict is that upgrading the wireless drivers to backports 3.13 has not stopped the wirelss hanging.

---

### Post by varunendra on 2014-02-18
Did you also try the backports-3.12.8-1 package? Not sure about rtl8188ee, but we have had some positive feedback with other drivers from that package.

I also remember failing with a driver from 3.13, while the one from 3.12 worked better, don't remember which one it was. So I still prefer 3.12 for all drivers, although others may be better in the latest one.

---

