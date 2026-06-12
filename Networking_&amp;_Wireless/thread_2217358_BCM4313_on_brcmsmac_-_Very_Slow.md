---
title: "BCM4313 on brcmsmac - Very Slow"
date: 2014-04-16
forum: Networking &amp; Wireless
---

### Post by Agnishom_Chattopadhyay on 2014-04-16
In the begining, I could connect to networks but not 
[LIST]
[*]Ping others (including other devices on the same wireless network, including the gateway/router)
[*]Resolve hosts
[*]Access any other external resource, whether on my own network or on the internet
[/LIST]
So, I did this
```
[FONT=Ubuntu Mono]sudo modprobe -rv wl[/FONT]
sudo apt-get remove --purge bcmwl-kernel-source
 [FONT=Ubuntu Mono]sudo modprobe -v brcmsmac[/FONT]
```

My wireless now worked and opened web resources but it is either very slow all the time or slows down after 2 minutes of connecting.
 
I've compared this to the wifi connectivity on the same network and same location on Windows as I dual boot it on the same machine. Thus, the connection is not the problem.

What should I do? Is there any better module that manages wifi better? Should I reinstall bcmwl-kernel-source?

Please Help me!!

---

### Post by Agnishom_Chattopadhyay on 2014-04-17
```


########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy

##### kernel #####

Linux chattopadhyayPC 3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: bcma-pci-bridge
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:1669]
    Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 003: ID 04f2:b249 Chicony Electronics Co., Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:21b4 Broadcom Corp. BCM2070 Bluetooth 2.1 + EDR
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy2: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### iw reg get #####

country US:
    (2402 - 2472 @ 40), (3, 27)
    (5170 - 5250 @ 40), (3, 17)
    (5250 - 5330 @ 40), (3, 20), DFS
    (5490 - 5600 @ 40), (3, 20), DFS
    (5650 - 5710 @ 40), (3, 20), DFS
    (5735 - 5835 @ 40), (3, 30)
    (57240 - 63720 @ 2160), (N/A, 40)

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan0     IEEE 802.11bgn  ESSID:"ENDEAVOR"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC address removed>   
          Bit Rate=58.5 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:4   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 8.8.8.8
nameserver 8.8.8.4

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [ENDEAVOR] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *ENDEAVOR:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 56 WPA WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             8.8.8.8
    DNS:             8.8.8.4

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
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"ENDEAVOR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000002458614fb8
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 0008454E444541564F52
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A2C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C332C181EFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3401000000000000000000000000000000000000000000
                    IE: Unknown: DD0600E04C020160
                    IE: Unknown: DD930050F204104A0001101044000102103B0001031047001063041253101920061228C0A0BBC7059210210012442D4C696E6B20436F72706F726174696F6E1023000D442D4C696E6B20526F75746572102400084449522D3630304C1042000D32303037303431332D303030311054000800060050F2040001101100084449522D3630304C1008000226881049000600372A000120

##### iwlist channel #####

wlan0     11 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### lsmod #####

brcmsmac              562904  0 
bcma                   46699  2 brcmsmac
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              597268  1 brcmsmac
cfg80211              480503  2 brcmsmac,mac80211

##### modinfo #####

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver.
author:         Broadcom Corporation
srcversion:     DB4E5CDF31AA9B12B2BA2C0
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
depends:        mac80211,bcma,brcmutil,cfg80211,cordic
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     67ADEA6E309FDB9FC19CBCF
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 

filename:       /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
license:        Dual BSD/GPL
description:    Broadcom 802.11n wireless LAN driver utilities.
author:         Broadcom Corporation
srcversion:     E81EE4CBB6A7A689150D93D
depends:        
intree:         Y
vermagic:       3.11.0-19-generic SMP mod_unload modversions 

##### modules #####

lp
rtc

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

##### udev rules #####

# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4727 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #####

[   18.828847] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   18.828886] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   18.828915] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   18.828967] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   18.847504] bcma: bus0: Bus registered
[   19.808568] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   19.808645] b43: probe of bcma0:0 failed with error -524
[   19.820418] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   19.827369] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 243
[   22.159237] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   22.159305] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   22.159572] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.159931] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.671077] wlan0: authenticate with <MAC address removed>
[   23.673160] wlan0: send auth to <MAC address removed> (try 1/3)
[   23.674687] wlan0: authenticated
[   23.678398] wlan0: associate with <MAC address removed> (try 1/3)
[   23.682394] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   23.685663] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[   23.685687] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[   23.685769] wlan0: associated
[   23.685863] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   32.985663] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[   63.518412] Modules linked in: nvram uvcvideo videobuf2_vmalloc videobuf2_memops videobuf2_core videodev parport_pc ppdev btusb rfcomm bnep bluetooth snd_hda_codec_hdmi snd_hda_codec_idt joydev arc4 brcmsmac cordic brcmutil b43 mac80211 intel_powerclamp coretemp kvm_intel kvm cfg80211 ssb hp_wmi sparse_keymap snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi snd_seq microcode snd_seq_device snd_timer psmouse serio_raw intel_ips rtsx_pci_ms fglrx(POF) i915 lpc_ich bcma memstick snd drm_kms_helper drm mei_me mei amd_iommu_v2 soundcore i2c_algo_bit wmi video mac_hid lp parport rtsx_pci_sdmmc ahci r8169 libahci rtsx_pci mii
[  623.989535] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  623.990648] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  623.990655] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  623.990657] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  624.158380] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[  624.224950] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  859.350405] ERROR @wl_dev_intvar_get : error (-1)
[  859.350415] ERROR @wl_cfg80211_get_tx_power : error (-1)
[ 1644.422739] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[ 1644.422774] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[ 1644.422800] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[ 1644.422850] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[ 1644.435634] bcma: bus0: Bus registered
[ 1644.443462] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[ 1644.444410] ieee80211 phy2: registered radio enabled led device: brcmsmac-phy2:radio gpio: 243
[ 1644.502868] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1644.505219] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[ 1644.507874] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1644.508466] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1645.815461] wlan0: authenticate with <MAC address removed>
[ 1645.817110] wlan0: send auth to <MAC address removed> (try 1/3)
[ 1645.818660] wlan0: authenticated
[ 1645.822913] wlan0: associate with <MAC address removed> (try 1/3)
[ 1645.826743] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[ 1645.828876] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 1645.830086] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 1645.831268] wlan0: associated
[ 1645.831276] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1649.510207] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)

########## wireless info END ############


```

---

### Post by praseodym on 2014-04-17
Hi,
I recommend upgrading/installing 14.04 LTS which is released today. The brcmsmac driver is sinificantly improved there

---

### Post by Agnishom_Chattopadhyay on 2014-04-17
How wonderful!! :D

Will I have to reinstall all my software and data again?

---

### Post by praseodym on 2014-04-17
Only the software from PPAs or locally installed software. Check first, if your PPAs are available for 14.04.

---

### Post by matt_symes on 2014-04-17
Hi

You have the same wireless card i have...

```
matthew-S206:/home/matthew:2 % lspci -nnk | pbl Wireless
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
        Subsystem: Broadcom Corporation Device [14e4:0587]
        Kernel driver in use: wl
matthew-S206:/home/matthew:2 %
``` 

As you can see, i am using the wl driver and was using it under the 13.10 stock kernel without any issues at all.

When you say the driver was not working, what symptoms were you getting ?

I had major connection issues using the open source driver.

Kind regards

---

### Post by Agnishom_Chattopadhyay on 2014-04-17
Hi;

Nice to find another person with the same card. :)

The bcmwl driver connects to the network but when I am trying to request any web-resource or lookup any website it does not work. (see post 1)

---

### Post by Agnishom_Chattopadhyay on 2014-04-17
> **praseodym said:**
> Only the software from PPAs or locally installed software. Check first, if your PPAs are available for 14.04.

I have got sage which probably has no 14.04 repos. I have installed a few things like my Catalyst Intel/AMD Switchable Graphics manually, they will be gone?

I live in India, and it is 7 o clock here. I still can't find the 'download' link to 14.04 LTS

---

### Post by praseodym on 2014-04-17
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Daily live, the catalyst driver fglrx should work instantly in switching VGA cards

---

### Post by Agnishom_Chattopadhyay on 2014-04-17
I am upgrading via do-release-upgrade right now.

---

### Post by Agnishom_Chattopadhyay on 2014-04-18
Upgrade done. I do not think that there is any improvement in the wireless.

---

### Post by praseodym on 2014-04-19
Change the encryption mode to pure WPA2-AES (CCMP) in you router. Thats more stable and safe than mixed mode.

---

### Post by Rob Sayer on 2014-04-19
You should install linux-firmware-nonfree.  I don't know if it's a sufficient condition in 14.04 at this point for brcmsmac but it's probably a necessary one.

---

