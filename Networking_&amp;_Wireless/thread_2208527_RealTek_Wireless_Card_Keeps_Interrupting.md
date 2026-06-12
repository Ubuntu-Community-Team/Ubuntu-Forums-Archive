---
title: "RealTek Wireless Card Keeps Interrupting?"
date: 2014-02-28
forum: Networking &amp; Wireless
---

### Post by bshatt1987 on 2014-02-28
Hey guys.  
Um, so I got a new laptop 6 days ago and it's working alright except for one thing...the wireless seems to keep getting interrupted or something?
Like, I'll be browsing around just fine and then randomly it will take forever to connect to anything.  I know it's not my router because my tablet's wifi connection works just fine and I've never had a problem with the router.
That laptop has a RealTek wireless card, I can't seem to find out the specific model.

Anyway, is there a way to make the connection more constant and steady?  It seriously drives me crazy.  
Sometimes it will take up to a minute before I can connect to any web pages.

---

### Post by praseodym on 2014-02-28
Hi,

please show the terminal outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
sudo iwlist scan
```

---

### Post by bshatt1987 on 2014-02-28
> **praseodym said:**
> Hi,

please show the terminal outputs of
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
sudo iwlist scan
```

Hello there.  Thanks for your reply.  Here we are - 

**uname -a** :```
 Linux ubuntu 3.11.0-17-generic #31~precise1-Ubuntu SMP Tue Feb 4 21:25:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```


**lsspci -nnk |grep -iA2 net** :```
 01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:188b]
    Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee
```

**lsusb** : ```
Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

**lsmod** : ```
Module                  Size  Used by
nls_iso8859_1          12713  0 
usb_storage            66567  0 
btrfs                 857559  0 
raid6_pq               97812  1 btrfs
zlib_deflate           27139  1 btrfs
xor                    21411  1 btrfs
ufs                    75386  0 
qnx4                   13396  0 
hfsplus               103553  0 
hfs                    54867  0 
minix                  40550  0 
ntfs                   97863  0 
msdos                  17332  0 
jfs                   186841  0 
xfs                   910633  0 
reiserfs              249085  0 
ext2                   73909  0 
vesafb                 13876  1 
bnep                   24107  2 
rfcomm                 74718  0 
parport_pc             32866  0 
bluetooth             391726  10 bnep,rfcomm
ppdev                  17711  0 
binfmt_misc            17508  1 
arc4                   12573  2 
fglrx                7505001  339 
snd_hda_codec_realtek    57149  1 
snd_hda_codec_hdmi     41736  1 
uvcvideo               82247  0 
videobuf2_core         40815  1 uvcvideo
snd_hda_intel          57134  5 
videodev              138562  2 uvcvideo,videobuf2_core
snd_hda_codec         194817  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videobuf2_vmalloc      13216  1 uvcvideo
rtl8188ee              96105  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_hwdep              13613  1 snd_hda_codec
rtl_pci                27261  1 rtl8188ee
snd_pcm               107140  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtlwifi                64035  2 rtl8188ee,rtl_pci
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
mac80211              623607  3 rtl8188ee,rtl_pci,rtlwifi
joydev                 17613  0 
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
edac_core              62944  0 
rtsx_pci_ms            18320  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
edac_mce_amd           22792  0 
hp_wmi                 18202  0 
memstick               16811  1 rtsx_pci_ms
sparse_keymap          13890  1 hp_wmi
psmouse               104093  0 
cfg80211              499466  2 rtlwifi,mac80211
snd                    73753  21 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13413  0 
i2c_piix4              22299  0 
fam15h_power           13166  0 
video                  19574  0 
k10temp                13173  0 
wmi                    19256  1 hp_wmi
amd_iommu_v2           19227  1 fglrx
mac_hid                13253  0 
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   106315  2 hid_generic,usbhid
rtsx_pci_sdmmc         23933  0 
r8169                  73299  0 
mii                    13981  1 r8169
ahci                   30063  2 
sdhci_pci              19146  0 
sdhci                  43292  1 sdhci_pci
libahci                32118  1 ahci
rtsx_pci               45723  2 rtsx_pci_ms,rtsx_pci_sdmmc
```

**iwconfig** : ```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HOME-7801"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: CC:35:40:6E:78:01   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:11038   Missed beacon:0
```


**cat /etc/resolv.conf** :```
 # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search home.network
```

**rfkill list** :```
 0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

**sudo iwlist scan** : ```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: CC:35:40:6E:78:01
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"HOME-7801"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000007b6d791a605
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0009484F4D452D37383031
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700106F313FC75E7F4A55C853C8D83A96DAD31021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180202F03C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 00:1A:2B:AD:2E:57
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Frontier5d33"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000039366a86a54
                    Extra: Last beacon: 184ms ago
                    IE: Unknown: 000C46726F6E7469657235643333
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```

---

### Post by praseodym on 2014-03-01
First: CHange the encryption mode to pure WPA2-AES (CCMP), check the router manual.

Second (if necessary): Update the driver:
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r)
wget http://media.cdn.ubuntu-de.org/forum/attachments/38/34/5443987-rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013_patc.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013 
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

### Post by varunendra on 2014-03-01
..and Third, bshatt1987, please edit your post to enclose the output within '**Code**' tags. I'm sure you'd be glad to see your post afterwards :D

Please follow the "Using Code Tags" link in my signature below to see how.

---

### Post by bshatt1987 on 2014-03-11
@[**[COLOR=#000000]praseodym[/COLOR]**]("http://ubuntuforums.org/member.php?u=1411497") - First of all, sorry I've taken  so long to respond.  
Anyway, I did both of those things, changed the router's encryption method and reinstalled the wireless driver, but I'm still having the issue.  

@[**[COLOR=#DD4814][B]varunendra**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1043629") - All coded.  Thanks for the suggestion.  :)

---

### Post by varunendra on 2014-03-11
> **bshatt1987 said:**
> Anyway, I did both of those things, changed the router's encryption method and reinstalled the wireless driver, but I'm still having the issue.

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates. It should be able to give us more clues.

---

### Post by bshatt1987 on 2014-03-11
Alright, here we go:
```

*************** info trace ***************

***** uname -a *****

Linux ubuntu 3.11.0-18-generic #32~precise1-Ubuntu SMP Thu Feb 20 17:52:10 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:188b]
    Kernel driver in use: r8169
--
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:197d]
    Kernel driver in use: rtl8188ee

***** lsusb *****

Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

***** PCMCIA Card Info *****


***** iwconfig *****

wlan0     IEEE 802.11bgn  ESSID:"HOME-7801"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:468   Missed beacon:0


***** rfkill *****

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

***** iw reg get *****


***** route -n *****

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         10.0.0.1        0.0.0.0         UG    0      0        0 wlan0
10.0.0.0        0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0

***** lsmod *****

rtl8188ee              96105  0 
rtl_pci                27261  1 rtl8188ee
rtlwifi                64035  2 rtl8188ee,rtl_pci
mac80211              623607  3 rtl8188ee,rtl_pci,rtlwifi
cfg80211              499466  2 rtlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: wlan0  [HOME-7801] ---------------------------------------------------
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
    *HOME-7801:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA2
    pattersons:      Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2

  IPv4 Settings:
    Address:         10.0.0.10
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             75.75.76.76
    DNS:             75.75.75.75


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

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"HOME-7801"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000336d8c0e1f
                    Extra: Last beacon: 8ms ago
                    IE: Unknown: 0009484F4D452D37383031
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32048C129860
                    IE: Unknown: 2D1AFD181BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: DD8C0050F204104A0001101044000102103B000103104700106F313FC75E7F4A55C853C8D83A96DAD31021000B546563686E69636F6C6F721023000B546563686E69636F6C6F721024000631323334353610420007303030303030311054000800060050F20400011011000D546563686E69636F6C6F724150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180203F03C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"pattersons-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000d17adc9bed
                    Extra: Last beacon: 3320ms ago
                    IE: Unknown: 0010706174746572736F6E732D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081500000000000000000000000000000000000000
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B081500000000000000000000000000000000000000


***** resolv.conf *****

nameserver 127.0.0.1
search home.network

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

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8188ee/rtl8188ee.ko
firmware:       rtlwifi/rtl8188efw.bin
description:    Realtek 8188E 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         zhiyuan_yang    <zhiyuan_yang@realsil.com.cn>
srcversion:     1808E366BB0231718E8B133
alias:          pci:v000010ECd00008179sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7492FC488AD8A6D43075535
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     9985D829F92712EC7AE7D4E
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 


***** udev rules *****

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:02.2/0000:01:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:02.3/0000:05:00.0 (rtl8188ee)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

***** dmesg *****

[   11.689663] rtl8188ee: Using firmware rtlwifi/rtl8188efw.bin
[   12.391375] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   12.391720] rtlwifi: wireless switch is on
[   20.140590] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.141016] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.809330] wlan0: authenticate with <MAC address removed>
[   22.828519] wlan0: send auth to <MAC address removed> (try 1/3)
[   22.831168] wlan0: authenticated
[   22.832209] wlan0: associate with <MAC address removed> (try 1/3)
[   22.836230] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[   22.836373] wlan0: associated
[   22.836392] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 9305.807415] wlan0: Connection to AP <MAC address removed> lost
[ 9307.198332] wlan0: authenticate with <MAC address removed>
[ 9307.209034] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9307.312414] wlan0: send auth to <MAC address removed> (try 2/3)
[ 9307.416468] wlan0: send auth to <MAC address removed> (try 3/3)
[ 9307.520483] wlan0: authentication with <MAC address removed> timed out
[ 9312.212900] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[ 9313.146179] wlan0: authenticate with <MAC address removed>
[ 9313.165579] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9313.167438] wlan0: authenticated
[ 9313.172861] wlan0: associate with <MAC address removed> (try 1/3)
[ 9313.176477] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 9313.176665] wlan0: associated
[ 9614.987390] wlan0: Connection to AP <MAC address removed> lost
[ 9616.362513] wlan0: authenticate with <MAC address removed>
[ 9616.380694] wlan0: send auth to <MAC address removed> (try 1/3)
[ 9616.382986] wlan0: authenticated
[ 9616.384194] wlan0: associate with <MAC address removed> (try 1/3)
[ 9616.391232] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[ 9616.391432] wlan0: associated
[16016.895433] wlan0: Connection to AP <MAC address removed> lost
[16018.277596] wlan0: authenticate with <MAC address removed>
[16018.297005] wlan0: send auth to <MAC address removed> (try 1/3)
[16018.400422] wlan0: send auth to <MAC address removed> (try 2/3)
[16018.504273] wlan0: send auth to <MAC address removed> (try 3/3)
[16018.608384] wlan0: authentication with <MAC address removed> timed out
[16023.299381] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[16024.233875] wlan0: authenticate with <MAC address removed>
[16024.253453] wlan0: send auth to <MAC address removed> (try 1/3)
[16024.255253] wlan0: authenticated
[16024.256709] wlan0: associate with <MAC address removed> (try 1/3)
[16024.260024] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[16024.260193] wlan0: associated
[28110.636902] wlan0: Connection to AP <MAC address removed> lost
[28112.007387] wlan0: authenticate with <MAC address removed>
[28112.027281] wlan0: send auth to <MAC address removed> (try 1/3)
[28112.031597] wlan0: authenticated
[28112.033734] wlan0: associate with <MAC address removed> (try 1/3)
[28112.044710] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28112.044858] wlan0: associated
[28123.197808] wlan0: Connection to AP <MAC address removed> lost
[28124.548030] wlan0: authenticate with <MAC address removed>
[28124.567359] wlan0: send auth to <MAC address removed> (try 1/3)
[28124.569597] wlan0: authenticated
[28124.570778] wlan0: associate with <MAC address removed> (try 1/3)
[28124.578868] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28124.579057] wlan0: associated
[28133.726516] wlan0: Connection to AP <MAC address removed> lost
[28135.114050] wlan0: authenticate with <MAC address removed>
[28135.131994] wlan0: send auth to <MAC address removed> (try 1/3)
[28135.133567] wlan0: authenticated
[28135.135587] wlan0: associate with <MAC address removed> (try 1/3)
[28135.147746] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28135.147896] wlan0: associated
[28160.328599] wlan0: Connection to AP <MAC address removed> lost
[28161.674854] wlan0: authenticate with <MAC address removed>
[28161.694351] wlan0: send auth to <MAC address removed> (try 1/3)
[28161.699108] wlan0: authenticated
[28161.701593] wlan0: associate with <MAC address removed> (try 1/3)
[28161.715912] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28161.716103] wlan0: associated
[28182.887401] wlan0: Connection to AP <MAC address removed> lost
[28184.259942] wlan0: authenticate with <MAC address removed>
[28184.280609] wlan0: send auth to <MAC address removed> (try 1/3)
[28184.282430] wlan0: authenticated
[28184.283327] wlan0: associate with <MAC address removed> (try 1/3)
[28184.286621] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28184.286762] wlan0: associated
[28203.463946] wlan0: Connection to AP <MAC address removed> lost
[28204.841418] wlan0: authenticate with <MAC address removed>
[28204.861188] wlan0: send auth to <MAC address removed> (try 1/3)
[28204.865181] wlan0: authenticated
[28204.868871] wlan0: associate with <MAC address removed> (try 1/3)
[28204.873720] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28204.873891] wlan0: associated
[28214.028852] wlan0: Connection to AP <MAC address removed> lost
[28215.400025] wlan0: authenticate with <MAC address removed>
[28215.418175] wlan0: send auth to <MAC address removed> (try 1/3)
[28215.420558] wlan0: authenticated
[28215.421684] wlan0: associate with <MAC address removed> (try 1/3)
[28215.431262] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28215.431411] wlan0: associated
[28224.581616] wlan0: Connection to AP <MAC address removed> lost
[28225.959739] wlan0: authenticate with <MAC address removed>
[28225.978983] wlan0: send auth to <MAC address removed> (try 1/3)
[28225.980635] wlan0: authenticated
[28225.982489] wlan0: associate with <MAC address removed> (try 1/3)
[28225.985855] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28225.985991] wlan0: associated
[28245.163143] wlan0: Connection to AP <MAC address removed> lost
[28246.157464] wlan0: authenticate with <MAC address removed>
[28246.176731] wlan0: send auth to <MAC address removed> (try 1/3)
[28246.178291] wlan0: authenticated
[28246.180090] wlan0: associate with <MAC address removed> (try 1/3)
[28246.189095] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28246.189286] wlan0: associated
[28271.217265] wlan0: Connection to AP <MAC address removed> lost
[28272.595527] wlan0: authenticate with <MAC address removed>
[28272.614503] wlan0: send auth to <MAC address removed> (try 1/3)
[28272.616766] wlan0: authenticated
[28272.618060] wlan0: associate with <MAC address removed> (try 1/3)
[28272.722290] wlan0: associate with <MAC address removed> (try 2/3)
[28272.729629] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28272.729818] wlan0: associated
[28280.571843] wlan0: deauthenticated from <MAC address removed> (Reason: 15)
[28281.919387] wlan0: authenticate with <MAC address removed>
[28281.939157] wlan0: send auth to <MAC address removed> (try 1/3)
[28281.940926] wlan0: authenticated
[28281.942775] wlan0: associate with <MAC address removed> (try 1/3)
[28281.946180] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[28281.946333] wlan0: associated
[30205.050658] Modules linked in: vesafb bnep rfcomm bluetooth parport_pc ppdev fglrx(POF) arc4 binfmt_misc snd_hda_codec_realtek uvcvideo snd_hda_codec_hdmi snd_hda_intel snd_hda_codec rtl8188ee videobuf2_core videodev videobuf2_vmalloc videobuf2_memops rtl_pci snd_hwdep snd_pcm rtlwifi joydev snd_seq_midi snd_rawmidi mac80211 snd_seq_midi_event snd_seq snd_timer snd_seq_device cfg80211 psmouse snd edac_core hp_wmi soundcore edac_mce_amd serio_raw sparse_keymap snd_page_alloc i2c_piix4 mac_hid video rtsx_pci_ms amd_iommu_v2 memstick fam15h_power wmi k10temp lp parport hid_generic usbhid hid rtsx_pci_sdmmc sdhci_pci sdhci ahci rtsx_pci libahci r8169 mii
[30205.050882] Modules linked in: vesafb bnep rfcomm bluetooth parport_pc ppdev fglrx(POF) arc4 binfmt_misc snd_hda_codec_realtek uvcvideo snd_hda_codec_hdmi snd_hda_intel snd_hda_codec rtl8188ee videobuf2_core videodev videobuf2_vmalloc videobuf2_memops rtl_pci snd_hwdep snd_pcm rtlwifi joydev snd_seq_midi snd_rawmidi mac80211 snd_seq_midi_event snd_seq snd_timer snd_seq_device cfg80211 psmouse snd edac_core hp_wmi soundcore edac_mce_amd serio_raw sparse_keymap snd_page_alloc i2c_piix4 mac_hid video rtsx_pci_ms amd_iommu_v2 memstick fam15h_power wmi k10temp lp parport hid_generic usbhid hid rtsx_pci_sdmmc sdhci_pci sdhci ahci rtsx_pci libahci r8169 mii
[44865.588704] wlan0: Connection to AP <MAC address removed> lost
[44866.975613] wlan0: authenticate with <MAC address removed>
[44866.994216] wlan0: send auth to <MAC address removed> (try 1/3)
[44866.995965] wlan0: authenticated
[44866.997582] wlan0: associate with <MAC address removed> (try 1/3)
[44867.008581] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[44867.008730] wlan0: associated
[44878.161717] wlan0: Connection to AP <MAC address removed> lost
[44879.500598] wlan0: authenticate with <MAC address removed>
[44879.519150] wlan0: send auth to <MAC address removed> (try 1/3)
[44879.520882] wlan0: authenticated
[44879.522507] wlan0: associate with <MAC address removed> (try 1/3)
[44879.532469] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[44879.532609] wlan0: associated
[45652.269051] wlan0: Connection to AP <MAC address removed> lost
[45653.653045] wlan0: authenticate with <MAC address removed>
[45653.670361] wlan0: send auth to <MAC address removed> (try 1/3)
[45653.675901] wlan0: authenticated
[45653.677974] wlan0: associate with <MAC address removed> (try 1/3)
[45653.681359] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45653.681505] wlan0: associated
[45662.837874] wlan0: Connection to AP <MAC address removed> lost
[45664.208350] wlan0: authenticate with <MAC address removed>
[45664.227236] wlan0: send auth to <MAC address removed> (try 1/3)
[45664.248564] wlan0: authenticated
[45664.250821] wlan0: associate with <MAC address removed> (try 1/3)
[45664.254980] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45664.255174] wlan0: associated
[45685.411517] wlan0: Connection to AP <MAC address removed> lost
[45686.797758] wlan0: authenticate with <MAC address removed>
[45686.817016] wlan0: send auth to <MAC address removed> (try 1/3)
[45686.826677] wlan0: authenticated
[45686.828538] wlan0: associate with <MAC address removed> (try 1/3)
[45686.840270] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45686.840405] wlan0: associated
[45734.063388] wlan0: Connection to AP <MAC address removed> lost
[45735.450194] wlan0: authenticate with <MAC address removed>
[45735.468759] wlan0: send auth to <MAC address removed> (try 1/3)
[45735.476957] wlan0: authenticated
[45735.480319] wlan0: associate with <MAC address removed> (try 1/3)
[45735.483862] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45735.483999] wlan0: associated
[45766.677877] wlan0: Connection to AP <MAC address removed> lost
[45768.068640] wlan0: authenticate with <MAC address removed>
[45768.087115] wlan0: send auth to <MAC address removed> (try 1/3)
[45768.088897] wlan0: authenticated
[45768.090773] wlan0: associate with <MAC address removed> (try 1/3)
[45768.097245] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45768.097395] wlan0: associated
[45779.254940] wlan0: Connection to AP <MAC address removed> lost
[45780.617900] wlan0: authenticate with <MAC address removed>
[45780.636299] wlan0: send auth to <MAC address removed> (try 1/3)
[45780.637867] wlan0: authenticated
[45780.639725] wlan0: associate with <MAC address removed> (try 1/3)
[45780.648106] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45780.648241] wlan0: associated
[45789.799571] wlan0: Connection to AP <MAC address removed> lost
[45791.189361] wlan0: authenticate with <MAC address removed>
[45791.209353] wlan0: send auth to <MAC address removed> (try 1/3)
[45791.213756] wlan0: authenticated
[45791.216523] wlan0: associate with <MAC address removed> (try 1/3)
[45791.220168] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45791.220309] wlan0: associated
[45818.405802] wlan0: Connection to AP <MAC address removed> lost
[45819.796060] wlan0: authenticate with <MAC address removed>
[45819.815570] wlan0: send auth to <MAC address removed> (try 1/3)
[45819.837265] wlan0: authenticated
[45819.838731] wlan0: associate with <MAC address removed> (try 1/3)
[45819.843734] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45819.843921] wlan0: associated
[45836.995215] wlan0: Connection to AP <MAC address removed> lost
[45838.344722] wlan0: authenticate with <MAC address removed>
[45838.364613] wlan0: send auth to <MAC address removed> (try 1/3)
[45838.366840] wlan0: authenticated
[45838.368269] wlan0: associate with <MAC address removed> (try 1/3)
[45838.371608] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45838.371759] wlan0: associated
[45861.557153] wlan0: Connection to AP <MAC address removed> lost
[45862.930724] wlan0: authenticate with <MAC address removed>
[45862.950566] wlan0: send auth to <MAC address removed> (try 1/3)
[45862.963838] wlan0: authenticated
[45862.966114] wlan0: associate with <MAC address removed> (try 1/3)
[45862.970729] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45862.970926] wlan0: associated
[45894.163805] wlan0: Connection to AP <MAC address removed> lost
[45895.546155] wlan0: authenticate with <MAC address removed>
[45895.565195] wlan0: send auth to <MAC address removed> (try 1/3)
[45895.575566] wlan0: authenticated
[45895.576594] wlan0: associate with <MAC address removed> (try 1/3)
[45895.589037] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[45895.589223] wlan0: associated
[46018.973359] wlan0: Connection to AP <MAC address removed> lost
[46020.340248] wlan0: authenticate with <MAC address removed>
[46020.358799] wlan0: send auth to <MAC address removed> (try 1/3)
[46020.361046] wlan0: authenticated
[46020.362137] wlan0: associate with <MAC address removed> (try 1/3)
[46020.374475] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[46020.374609] wlan0: associated
[46037.538667] wlan0: Connection to AP <MAC address removed> lost
[46038.912510] wlan0: authenticate with <MAC address removed>
[46038.932034] wlan0: send auth to <MAC address removed> (try 1/3)
[46038.962083] wlan0: authenticated
[46038.963657] wlan0: associate with <MAC address removed> (try 1/3)
[46038.971490] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[46038.971780] wlan0: associated
[46058.116346] wlan0: Connection to AP <MAC address removed> lost
[46059.494619] wlan0: authenticate with <MAC address removed>
[46059.513725] wlan0: send auth to <MAC address removed> (try 1/3)
[46059.515975] wlan0: authenticated
[46059.517138] wlan0: associate with <MAC address removed> (try 1/3)
[46059.543214] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[46059.543405] wlan0: associated
[46072.685512] wlan0: Connection to AP <MAC address removed> lost
[46074.054763] wlan0: authenticate with <MAC address removed>
[46074.074543] wlan0: send auth to <MAC address removed> (try 1/3)
[46074.077162] wlan0: authenticated
[46074.078362] wlan0: associate with <MAC address removed> (try 1/3)
[46074.084875] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[46074.085017] wlan0: associated
[46081.234020] wlan0: Connection to AP <MAC address removed> lost
[46082.592011] wlan0: authenticate with <MAC address removed>
[46082.611324] wlan0: send auth to <MAC address removed> (try 1/3)
[46082.612876] wlan0: authenticated
[46082.614923] wlan0: associate with <MAC address removed> (try 1/3)
[46082.636356] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=1)
[46082.636490] wlan0: associated

****************** done ******************


```

---

### Post by varunendra on 2014-03-11
Please try the suggestions in this post and report back if any of them seems to help or not (replace the "rtl8192ce" with "rtl8188ee" in commands) : [http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912](http://ubuntuforums.org/showthread.php?t=2180314&p=12815912#post12815912)

Note that all those will be temporary changes, so try the performance without rebooting after applying them. The changes would be lost after reboot (unless you make them permanent as mentioned in posts #16, #18 in the same thread).

Unless praseodym has other ideas (somehow he always has), I guess our last shot, without too much hope, would be to try one of the latest backported drivers ([reference post]("http://ubuntuforums.org/showthread.php?t=2203443&p=12926946#post12926946")).

---

### Post by bshatt1987 on 2014-03-11
Alright, so far I've used the second set of commands from there.  
```
sudo modprobe -rv rtl8188ee
sudo modprobe -v rtl8188ee fwlps=0
```
My eyes went to the wrong place as I was typing into the terminal, so that's why I didn't try the first one first.  lol
But, I've been surfing around a lot testing and so far I haven't encountered any downtime with the wireless, so I'm hoping that's helped.  
If nothing else, it's not caused any ill-effects, so I'm probably going to take the steps necessary to make it permanent.

---

### Post by bshatt1987 on 2014-03-11
I made the .conf file with that option, so we'll have to see what happens after my next boot.  

Thanks so much for your help and I'll post here again if it stops functioning again.  
I'll try the other two options you gave in that thread as well before posting, of course.  

Thanks again, to you and to praseodym!

---

