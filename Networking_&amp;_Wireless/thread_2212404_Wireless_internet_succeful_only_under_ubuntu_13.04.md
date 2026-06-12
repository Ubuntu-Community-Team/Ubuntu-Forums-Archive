---
title: "Wireless internet succeful only under ubuntu 13.04"
date: 2014-03-21
forum: Networking &amp; Wireless
---

### Post by chamin69 on 2014-03-21
I have a Packard Bell easynote laptop, that it has access to internet under ubuntu 13.04 only.
I have also tried 12.04 LTS, 13.10 and 14.04 versions but it failed to connect to wireless internet, although it connects to wireless network and has full wired connection.
What kind of problem is it?
Any ideas about this problem?

---

### Post by varunendra on 2014-03-21
Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by chamin69 on 2014-03-21
```

Thank you Varun for the reply. This is the result:
########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu Trusty Tahr (development branch)
Release:    14.04
Codename:    trusty

##### kernel #####

Linux ubuntu 3.13.0-18-generic #38-Ubuntu SMP Mon Mar 17 21:40:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:020e]
    Kernel driver in use: tg3

##### lsusb #####

Bus 002 Device 003: ID 0951:1643 Kingston Technology DataTraveler G3
Bus 002 Device 002: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"CYTAEF198E"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-22 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.10.254  0.0.0.0         UG    0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
search lan

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.1
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.254

    DNS:             192.168.10.254

- Device: wlan0  [CYTAEF198E] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    CYTA 2FD5:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    OTE144C20:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA
    CYTA 6271:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    conn-x92da9c:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA
    CYTACAFF73:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA
    CYTA212302:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA
    *CYTAEF198E:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    ThomsonF57FB6:   Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA
    CYTA2AD268:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA
    conn-xfaad68:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA
    conn-x239610:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA
    CYTA1446:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    CYTA4BF681:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    conn-xfa3258:    Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA
    CYTA 0C29:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2

  IPv4 Settings:
    Address:         192.168.10.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.254

    DNS:             192.168.10.254

##### NetworkManager.state #####

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf #####

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### iwlist #####

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"CYTAEF198E"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000877666364
                    Extra: Last beacon: 212ms ago
                    IE: Unknown: 000A43595441454631393845
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD810050F204104A0001101044000102103B000103104700105F1BFA0EF2885E088E29C40123EED58D1021000754484F4D534F4E1023000A54686F6D736F6E2054471024000337383210420009303834364E544244591054000800060050F20400011011000D54686F6D736F6E20544737383210080002008410570001001041000100
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"CYTA212302"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000087d16f006
                    Extra: Last beacon: 192ms ago
                    IE: Unknown: 000A43595441323132333032
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD2C0050F204104A000110104400010210570001001047001094F2ECA61D715A25A91EED03AB4BA603103C000101
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"conn-x92da9c"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000069bd4547ac
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 000C636F6E6E2D78393264613963
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001197A12
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"CYTA 2FD5"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000087f2681a1
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0009435954412032464435
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"CYTA 6271"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000087f9f2713
                    Extra: Last beacon: 56ms ago
                    IE: Unknown: 0009435954412036323731
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

##### iwlist channel #####

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### lsmod #####

rtl8192se              63196  0 
rtl_pci                26641  1 rtl8192se
rtlwifi                63475  2 rtl_pci,rtl8192se
mac80211              626584  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              490477  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AF8A9B40BB7E302AD041422
alias:          pci:v000010ECd00008174sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008173sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008172sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008192sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D6:2C:08:4F:13:ED:04:76:26:63:9F:5A:10:89
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

filename:       /lib/modules/3.13.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     AB7DEAEBAD8DA95BC48A244
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D6:2C:08:4F:13:ED:04:76:26:63:9F:5A:10:89
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-18-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     A5B40DF72468675509E68EA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:D6:2C:08:4F:13:ED:04:76:26:63:9F:5A:10:89
sig_hashalgo:   sha512

##### modules #####

##### blacklist #####

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

[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb

##### udev rules #####

# PCI device 0x14e4:0x1698 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8174 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   23.200546] rtl8192se: FW Power Save off (module option)
[   23.200651] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   23.200651] Loading firmware rtlwifi/rtl8192sefw.bin
[   23.276087] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   25.805857] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.806949] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   69.032709] wlan0: authenticate with <MAC address removed>
[   69.042747] wlan0: send auth to <MAC address removed> (try 1/3)
[   69.045463] wlan0: authenticated
[   69.045702] rtl8192se 0000:04:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   69.048119] wlan0: associate with <MAC address removed> (try 1/3)
[   69.050131] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=2)
[   69.054020] wlan0: associated
[   69.054040] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   69.320131] Modules linked in: acer_wmi dm_crypt sparse_keymap snd_hda_codec_hdmi dm_multipath scsi_dh coretemp psmouse serio_raw snd_hda_codec_realtek snd_hda_intel uvcvideo snd_hda_codec videobuf2_vmalloc snd_hwdep joydev videobuf2_memops arc4 videobuf2_core snd_pcm videodev rtl8192se rtl_pci snd_page_alloc snd_seq_midi rtlwifi snd_seq_midi_event mac80211 snd_rawmidi cfg80211 lpc_ich snd_seq snd_seq_device snd_timer snd rfcomm bnep bluetooth mac_hid soundcore squashfs overlayfs nls_iso8859_1 dm_mirror dm_region_hash dm_log hid_generic usbhid hid usb_storage nouveau mxm_wmi ahci libahci tg3 ptp i2c_algo_bit pps_core ttm drm_kms_helper drm wmi video
[   69.320242]  [<ffffffffa031b3ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]

########## wireless info END ############

```

---

### Post by chamin69 on 2014-03-21
Dear Valun, the following information could also be useful:
I install ubuntu 14.04 LTS on a second laptop (Sony Vaio model of 1998) and wireless connect works perfect

---

### Post by varunendra on 2014-03-21
14.04 is still under development. A development version is never considered to be stable. If you are not using it for testing, helping (the developers) purpose, I'd recommend you revert to a currently supported stable version, 12.04.4 for example.

Apart from that, please try the following changes -

**1)** In the router, please change the encryption to pure WPA2-PSK with AES (CCMP) algorithm. Avoid **[COLOR="#FF0000"]TKIP[/COLOR]** or WPA/WPA2 mixed mode.
**2)** Try disabling "N" channel in the router by setting it to "b/g" or "g" only mode. Please refer to your router's user manual to see how to make these changes. Reboot the router after saving any changes.

**3)** In Ubuntu, please try available driver parameters as suggested in this post (replace "rtl8192**[COLOR="#FF0000"]ce[/COLOR]**" with "rtl8192**[COLOR="#0000CD"]se[/COLOR]**") : [http://ubuntuforums.org/showpost.php?p=12815912](http://ubuntuforums.org/showpost.php?p=12815912)

Even if these changes don't seem to help, keep the encryption in the router to as suggested.

Which country are you in? It may help to explicitly declare the country code in your regdomain settings, which is currently defaulted to "00".

---

### Post by chamin69 on 2014-03-22
Thank you Varun, I am from Greece.
The choice for selecting WPA2-PSK does not appear in the network manager.
How can I disable "N" channel in the router?
How can it be a modem problem when the other laptop has no problem under ubuntu 12.04 or 14.04?
My questions may sound weird but I am a begginer to networking and also to ubuntu
As far as  (replace "rtl8192**[COLOR=#FF0000]ce[/COLOR]**" with "rtl8192**[COLOR=#0000CD]se[/COLOR]**") this is the result: 
[post]
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se
05:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe [14e4:1698] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:020e]
    Kernel driver in use: tg3
[/post]

---

### Post by varunendra on 2014-03-22
> **chamin69 said:**
> Thank you Varun, I am from Greece.
Assuming your router/Access-Point was originally manufactured for Greece and is using the same RegDomain settings, please try this temporary change (will be reset to default again after a reboot) -
```
sudo iw reg set GR
```
Then confirm the change with -
```
iw reg get
```
It should show "**country GR:**" followed by its settings.

> The choice for selecting WPA2-PSK does not appear in the network manager.
That is not a change to be made in Network Manager, it has to be set in the router itself, using its Admin control web interface.

> How can I disable "N" channel in the router?
How can it be a modem problem when the other laptop has no problem under ubuntu 12.04 or 14.04?
Using the same Admin control web interface of your router. Refer to your router's manual to see how to do that. The admin password and the layout of options is different for different models, so it's not possible for me to tell you exactly how and where to find those options.

We are not sure if it is a problem of N-channel or not, it would be just for a test and you can revert the setting if it didn't help. The other laptop may have a different card and thus different driver which is able to handle it properly. Even with same cards and drivers, sometimes a difference in chip 'version' can make a significant difference in its ability to deal with certain kind of networks.

> As far as  (replace "rtl8192**[COLOR=#FF0000]ce[/COLOR]**" with "rtl8192**[COLOR=#0000CD]se[/COLOR]**") this is the result....
I meant to replace "rtl8192ce" in those commands that I linked to (for trying the parameters). If you did it correctly, your current driver "rtl8192se" would have been correctly reloaded with those parameters, thus helping whatever they could help. It won't display any change in the outputs you posted above, just an improvement in performance is *expected* (not guaranteed) if it was done correctly.

---

### Post by chamin69 on 2014-03-22
Dear Varun, I am overwelmed by your kidness and your advices.
I am sure that if I follow your advices I would solve the problem.
Nevertheless, I am tired and frustrated by my efforts for over a week to solve the problem and I decided to unistall ubuntu, leaving windows 7 as the only OS to the certain computer.
Unfortunately I am an absolute begginer to handle with this issue.
Thank you very much again!

---

### Post by varunendra on 2014-03-22
You're always welcome! :)

We all were beginners at some point. But maybe I was fortunate to have a better supported hardware that saved me any possible frustration like you suffered. Now I know enough about the OS to find my way around even if I get an unsupported hardware.

USB Wireless adapters are dirt-cheap these days so a non-working one shouldn't be so big an issue to keep you from using Ubuntu (or any Linux) distro if you otherwise like it. Nothing wrong with using Windows or any other OS, but if you can spare some time in tinkering/learning, Linux would certainly prove to be much more beneficial in long term.

Feel free to post back in this or a new thread if you wish to give it a try again. Hopefully, you'd be able to get some better help next time than I could offer this time here (I admit I was in a hurry while writing my last post, so maybe I couldn't make it easy and deliberate enough).

---

### Post by chamin69 on 2014-03-24
Thank you Varun,
I certainly love ubuntu and its community both are fantastic.
I am intended to try again in a few days using an external network card or changing the internal one.

---

### Post by chamin69 on 2014-03-26
A cheap usb wifi, compatible with linux, solved my problem.
Surely it is not the best solution for an ubuntu user but it is a good solution for a beginner.
Thank you again Varun.

---

### Post by varunendra on 2014-03-26
> **chamin69 said:**
> A cheap usb wifi, compatible with linux, solved my problem.

That's awesome!

It would help many of us helpers and many more like yourself if you could please also share with us the exact model no. of the adapter that is working for you. :)

To post its exact chip identity, please also show us the output of -
```
lsusb
```
..while it is plugged in. Thanks for the feedback in advance! :)

---

### Post by chamin69 on 2014-03-27
The wifi usb I used to restore the wireless internet can be seen in the site: [http://www.gembird.com/item.aspx?id=7551](http://www.gembird.com/item.aspx?id=7551)
Below is the result of the command lsusb:
```
chamin2@chamin2:~$ lsusbBus 002 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 004: ID 0bda:0159 Realtek Semiconductor Corp. Digital Media Card Reader
Bus 002 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
Bus 005 Device 002: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```

---

