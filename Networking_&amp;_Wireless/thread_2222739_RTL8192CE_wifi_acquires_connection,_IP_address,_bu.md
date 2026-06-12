---
title: "RTL8192CE wifi acquires connection, IP address, but cannot even ping router"
date: 2014-05-07
forum: Networking &amp; Wireless
---

### Post by waffles279 on 2014-05-07
Hello everyone. I don't have a lot of Linux expertise, but googling around hasn't seemed to reveal a single solution for my problem, or at least one that has worked. Here are my symptoms, followed by the wireless information usually requested.
[LIST]
[*]Wireless connection worked with live install of Kubuntu 
[*]Having installed it, I can acquire a wireless connection
[LIST]
[*]Get an IP address (192.168.0.25) 
[*]Cannot ping or access router in web browser 
[*]Cannot access the internet as a whole. I've tried google by name or IP 
[/LIST]
  
[*]Same wireless connection works in Windows 7. I'm given the same IP address 
[/LIST]

This makes me think that it's *not* a DNS issue and it's possibly an issue of interaction between my router and my computer. In addition to the standard information, I have also provided some configuration settings for my router. With my router, I have tried manually changing the channel to 1 rather than its original 2, changing the authentication type from AES/TKIP to just AES, and setting my router to 801.11b or g only. I have also downloaded and installed "firmware-realtek_0.36+wheezy.1~bpo60+1_all.deb" which I grabbed from the debian website, which I think contains the drivers I need. 

Having glanced through all the information provided here, I don't see  anything that stands out as a red flag. Thank you so much for your help,  everyone.

Router settings:
[TABLE]
[TR]
[TD]SSID:[/TD]
[TD]Chelonia[/TD]
[/TR]
[TR]
[TD]Channel:[/TD]
[TD]1[/TD]
[/TR]
[TR]
[TD]Best Available Channel:[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TD]Second Best Available Channel:[/TD]
[TD]3[/TD]
[/TR]
[TR]
[TD]Wireless Security Type:[/TD]
[TD]WPA2 Personal[/TD]
[/TR]
[TR]
[TD]SSID Broadcast:[/TD]
[TD]Enabled[/TD]
[/TR]
[TR]
[TD]MAC Authentication:[/TD]
[TD]Disabled[/TD]
[/TR]
[TR]
[TD]Wireless Model[/TD]
[TD]802.11b and 802.11g[/TD]
[/TR]
[TR]
[TD]WPS State:[/TD]
[TD]Enabled[/TD]
[/TR]
[TR]
[TD]WPS Type:[/TD]
[TD]PBC[/TD]
[/TR]
[TR]
[TD]WMM QoS:[/TD]
[TD]Disabled[/TD]
[/TR]
[TR]
[TD]WMM Power Save:[/TD]
[TD]Disabled[/TD]
[/TR]
[TR]
[TD]Wireless Packets Sent:[/TD]
[TD]10451226[/TD]
[/TR]
[TR]
[TD]Wireless Packets Received:[/TD]
[TD]7834576[/TD]
[/TR]
[/TABLE]

```

$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

```

```

Version: 2.0 (Development)
Wed May 7 19:24:12 MDT 2014

******************************************************************************************
Running networking services
******************************************************************************************
network-manager is installed
network-manager start/running, process 1663
network-manager is running
******************************************************************************************
    Ubuntu release 
******************************************************************************************

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"

******************************************************************************************
    Kernel
******************************************************************************************

Linux Prometheus-Linux 3.13.0-24-generic #47-Ubuntu SMP Fri May 2 23:30:00 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

******************************************************************************************
      lshw  List of network devices
******************************************************************************************

  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 40:61:86:4b:ef:76
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-1.fw latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:45 ioport:a800(size=256) memory:faeff000-faefffff memory:faef8000-faefbfff memory:fbbe0000-fbbfffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: 40:61:86:4b:ef:77
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:b800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbce0000-fbcfffff
  *-network
       description: Wireless interface
       product: RTL8192CE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: 30:85:a9:f4:84:e2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.13.0-24-generic firmware=N/A ip=192.168.0.25 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:e800(size=256) memory:fbffc000-fbffffff

******************************************************************************************
    pci devices
******************************************************************************************

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
        Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]
        Kernel driver in use: rtl8192ce
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7581]
        Kernel driver in use: r8169
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7581]
        Kernel driver in use: r8169

******************************************************************************************
    usb devices
******************************************************************************************

Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1532:010d Razer USA, Ltd 
Bus 001 Device 003: ID 046d:c048 Logitech, Inc. G9 Laser Mouse
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
******************************************************************************************
    List of drivers
******************************************************************************************

Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
rfcomm                 69160  0 
bnep                   19624  2 
bluetooth             395423  10 bnep,rfcomm
gpio_ich               13476  0 
wl                   4207846  0 
coretemp               13435  0 
kvm_intel             143060  0 
kvm                   451511  1 kvm_intel
arc4                   12608  2 
lib80211               14381  1 wl
rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
psmouse               102222  0 
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce
serio_raw              13462  0 
cfg80211              484040  3 wl,mac80211,rtlwifi
i7core_edac            24122  0 
edac_core              62291  2 i7core_edac
lpc_ich                21080  0 
snd_hda_codec_hdmi     46207  1 
joydev                 17381  0 
snd_hda_codec_realtek    61438  1 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30144  1 snd_seq_midi
snd_hda_intel          52355  10 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
parport_pc             32701  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
ppdev                  17671  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
lp                     17759  0 
snd_timer              29482  2 snd_pcm,snd_seq
parport                42348  3 lp,ppdev,parport_pc
snd                    69238  31 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mac_hid                13205  0 
soundcore              12680  1 snd
pata_acpi              13038  0 
hid_generic            12548  0 
usbhid                 52616  0 
hid                   106148  2 hid_generic,usbhid
mxm_wmi                13021  0 
radeon               1514165  4 
i2c_algo_bit           13413  1 radeon
ttm                    85115  1 radeon
drm_kms_helper         52758  1 radeon
firewire_ohci          40409  0 
drm                   302817  6 ttm,drm_kms_helper,radeon
firewire_core          68769  1 firewire_ohci
ahci                   25819  2 
r8169                  67581  0 
pata_jmicron           12758  0 
libahci                32168  1 ahci
crc_itu_t              12707  1 firewire_core
mii                    13934  1 r8169
wmi                    19177  1 mxm_wmi

******************************************************************************************
interfaces
******************************************************************************************
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


******************************************************************************************
resolv.conf
******************************************************************************************
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1

******************************************************************************************
Modules file
******************************************************************************************
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc

******************************************************************************************
Blacklist file
******************************************************************************************
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

******************************************************************************************
Files in folder /etc/modprobe.d/*
******************************************************************************************
/etc/modprobe.d/alsa-base.conf
/etc/modprobe.d/blacklist-ath_pci.conf
/etc/modprobe.d/blacklist-bcm43.conf
/etc/modprobe.d/blacklist.conf
/etc/modprobe.d/blacklist-firewire.conf
/etc/modprobe.d/blacklist-framebuffer.conf
/etc/modprobe.d/blacklist-modem.conf
/etc/modprobe.d/blacklist-oss.conf
/etc/modprobe.d/blacklist-rare-network.conf
/etc/modprobe.d/blacklist-watchdog.conf
/etc/modprobe.d/dkms.conf
/etc/modprobe.d/fbdev-blacklist.conf
/etc/modprobe.d/iwlwifi.conf
/etc/modprobe.d/mlx4.conf
/etc/modprobe.d/vmwgfx-fbdev.conf

******************************************************************************************
NetworkManager.state
******************************************************************************************
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
WiMAXEnabled=true

******************************************************************************************
nm_applet_file
******************************************************************************************
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

******************************************************************************************
  network info 
******************************************************************************************

wlan0     Link encap:Ethernet  HWaddr 30:85:a9:f4:84:e2  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3285:a9ff:fef4:84e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:248870 (248.8 KB)  TX bytes:155263 (155.2 KB)

******************************************************************************************
 rfkill list all Rfkill Blocks
******************************************************************************************

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

network-manager start/running, process 1663

******************************************************************************************
Using nm-tool
******************************************************************************************

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Chelonia] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           yes
  HW Address:        30:85:A9:F4:84:E2

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    HOME-A972:       Infra, CC:A4:62:F4:A9:70, Freq 2437 MHz, Rate 54 Mb/s, Strength 90 WPA WPA2
    CenturyLink1341: Infra, 40:8B:07:7A:19:05, Freq 2422 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    HOME-F758:       Infra, 00:26:F3:68:F7:58, Freq 2462 MHz, Rate 54 Mb/s, Strength 87 WPA WPA2
    *Chelonia:       Infra, 50:67:F0:F3:E0:CB, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA2

  IPv4 Settings:
    Address:         192.168.0.25
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             208.67.222.222


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        40:61:86:4B:EF:77

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             disconnected
  Default:           no
  HW Address:        40:61:86:4B:EF:76

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on



******************************************************************************************
Using iwlist scan
******************************************************************************************
wlan0     Scan completed :
          Cell 01 - Address: 50:67:F0:F3:E0:CB
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=64/70  Signal level=-46 dBm  
                    Encryption key:on
                    ESSID:"Chelonia"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000001a3b7dfc
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 00084368656C6F6E6961
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010555555550000C0A800015067F0F3E0CB102100055A7958454C1023000F5A7958454C2057464144657669636510240007504B353030305A1042000830303030303030311054000800060050F20400011011000A504B353030305A20415010080002008C
          Cell 02 - Address: CC:A4:62:F4:A9:70
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=11/70  Signal level=-99 dBm  
                    Encryption key:on
                    ESSID:"HOME-A972"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002a7749c9012
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0009484F4D452D41393732
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010016127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880CCA462F4A97010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 03 - Address: C2:A4:62:F4:A9:70
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002a774a19b0f
                    Extra: Last beacon: 836ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32048C98B060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0106
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010016127A
                    IE: Unknown: DD07000C4303000000


******************************************************************************************
******************************************************************************************
dmesg for interface wlan0 and rtl8192ce
******************************************************************************************
******************************************************************************************

[   13.107107] wlan0: associated
[   13.107130] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.602881] Modules linked in: ctr ccm rfcomm bnep bluetooth gpio_ich wl(POF) coretemp kvm_intel kvm arc4 lib80211 rtl8192ce rtl_pci rtlwifi rtl8192c_common psmouse mac80211 serio_raw cfg80211 i7core_edac edac_core lpc_ich snd_hda_codec_hdmi joydev snd_hda_codec_realtek snd_seq_midi snd_seq_midi_event snd_rawmidi snd_hda_intel snd_hda_codec snd_hwdep parport_pc snd_pcm snd_seq snd_page_alloc ppdev snd_seq_device lp snd_timer parport snd mac_hid soundcore pata_acpi hid_generic usbhid hid mxm_wmi radeon i2c_algo_bit ttm drm_kms_helper firewire_ohci drm firewire_core ahci r8169 pata_jmicron libahci crc_itu_t mii wmi
[  491.341795] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
[  512.165860] wlan0: authenticate with 50:67:f0:f3:e0:cb
[  512.175243] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
[  512.178761] wlan0: authenticated
[  512.179010] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  512.179015] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  512.181000] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
[  512.183347] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=2)
[  512.183468] wlan0: associated
[  543.705330] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
[  656.404871] wlan0: authenticate with 50:67:f0:f3:e0:cb
[  656.414469] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
[  656.416517] wlan0: authenticated
[  656.416742] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  656.416748] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  656.420228] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
[  656.423150] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=6)
[  656.423271] wlan0: associated
[  686.725938] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
[  731.675046] wlan0: authenticate with 50:67:f0:f3:e0:cb
[  731.684531] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
[  731.687055] wlan0: authenticated
[  731.687229] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  731.687237] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  731.690264] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
[  731.696798] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=6)
[  731.696918] wlan0: associated

******************************************************************************************
Route info
******************************************************************************************
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

******************************************************************************************
Checking connectivity
******************************************************************************************
_unsucessfully_ pinged 192.168.0.1     
******************************************************************************************
Ping failure to router

******************************************************************************************
******************************************************************************************
Log file: /var/log/syslog
******************************************************************************************
******************************************************************************************

May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Beginning IP6 addrconf.
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Withdrawing address record for fe80::3285:a9ff:fef4:84e2 on wlan0.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::3285:a9ff:fef4:84e2.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Interface wlan0.IPv6 no longer relevant for mDNS.
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May  7 19:19:42 Prometheus-Linux dhclient: Listening on LPF/wlan0/30:85:a9:f4:84:e2
May  7 19:19:42 Prometheus-Linux dhclient: Sending on   LPF/wlan0/30:85:a9:f4:84:e2
May  7 19:19:42 Prometheus-Linux dhclient: DHCPREQUEST of 192.168.0.25 on wlan0 to 255.255.255.255 port 67 (xid=0x5a1176c2)
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.25.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: New relevant interface wlan0.IPv4 for mDNS.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Registering new address record for 192.168.0.25 on wlan0.IPv4.
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> Policy set 'Chelonia' (wlan0) as default for IPv4 routing and DNS.
May  7 19:19:44 Prometheus-Linux avahi-daemon[1448]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::3285:a9ff:fef4:84e2.
May  7 19:19:44 Prometheus-Linux avahi-daemon[1448]: New relevant interface wlan0.IPv6 for mDNS.
May  7 19:19:44 Prometheus-Linux avahi-daemon[1448]: Registering new address record for fe80::3285:a9ff:fef4:84e2 on wlan0.*.
May  7 19:19:44 Prometheus-Linux wpa_supplicant[1944]: wlan0: WPA: Group rekeying completed with 50:67:f0:f3:e0:cb [GTK=TKIP]
May  7 19:19:53 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) successful, device activated.
May  7 19:19:54 Prometheus-Linux wpa_supplicant[1944]: wlan0: CTRL-EVENT-SCAN-STARTED 
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): IP6 addrconf timed out or failed.
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  7 19:23:51 Prometheus-Linux NetworkManager[1663]: <info> Policy set 'Chelonia' (wlan0) as default for IPv4 routing and DNS.

******************************************************************************************
******************************************************************************************
Log file: /var/log/kern.log
******************************************************************************************
******************************************************************************************

May  7 19:07:41 Prometheus-Linux kernel: [   13.107000] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=2)
May  7 19:07:41 Prometheus-Linux kernel: [   13.107107] wlan0: associated
May  7 19:07:41 Prometheus-Linux kernel: [   13.107130] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  7 19:15:39 Prometheus-Linux kernel: [  491.341795] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
May  7 19:16:00 Prometheus-Linux kernel: [  512.165860] wlan0: authenticate with 50:67:f0:f3:e0:cb
May  7 19:16:00 Prometheus-Linux kernel: [  512.175243] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:16:00 Prometheus-Linux kernel: [  512.178761] wlan0: authenticated
May  7 19:16:00 Prometheus-Linux kernel: [  512.179010] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May  7 19:16:00 Prometheus-Linux kernel: [  512.179015] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May  7 19:16:00 Prometheus-Linux kernel: [  512.181000] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:16:00 Prometheus-Linux kernel: [  512.183347] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=2)
May  7 19:16:00 Prometheus-Linux kernel: [  512.183468] wlan0: associated
May  7 19:16:31 Prometheus-Linux kernel: [  543.705330] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
May  7 19:18:24 Prometheus-Linux kernel: [  656.404871] wlan0: authenticate with 50:67:f0:f3:e0:cb
May  7 19:18:24 Prometheus-Linux kernel: [  656.414469] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:18:24 Prometheus-Linux kernel: [  656.416517] wlan0: authenticated
May  7 19:18:24 Prometheus-Linux kernel: [  656.416742] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May  7 19:18:24 Prometheus-Linux kernel: [  656.416748] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May  7 19:18:24 Prometheus-Linux kernel: [  656.420228] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:18:24 Prometheus-Linux kernel: [  656.423150] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=6)
May  7 19:18:24 Prometheus-Linux kernel: [  656.423271] wlan0: associated
May  7 19:18:54 Prometheus-Linux kernel: [  686.725938] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
May  7 19:19:39 Prometheus-Linux kernel: [  731.675046] wlan0: authenticate with 50:67:f0:f3:e0:cb
May  7 19:19:39 Prometheus-Linux kernel: [  731.684531] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:19:39 Prometheus-Linux kernel: [  731.687055] wlan0: authenticated
May  7 19:19:39 Prometheus-Linux kernel: [  731.687229] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May  7 19:19:39 Prometheus-Linux kernel: [  731.687237] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May  7 19:19:39 Prometheus-Linux kernel: [  731.690264] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:19:39 Prometheus-Linux kernel: [  731.696798] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=6)
May  7 19:19:39 Prometheus-Linux kernel: [  731.696918] wlan0: associated

******************************************************************************************
  network info 
******************************************************************************************

wlan0     Link encap:Ethernet  HWaddr 30:85:a9:f4:84:e2  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3285:a9ff:fef4:84e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:251002 (251.0 KB)  TX bytes:166001 (166.0 KB)

******************************************************************************************
 rfkill list all Rfkill Blocks
******************************************************************************************

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

network-manager start/running, process 1663
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.
Could not toggle power management for interface wlan0

******************************************************************************************
Checking connectivity
******************************************************************************************
_unsucessfully_ pinged 192.168.0.1     
******************************************************************************************
Ping failure to router

******************************************************************************************
******************************************************************************************
Log file: /var/log/syslog
******************************************************************************************
******************************************************************************************

May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Beginning IP6 addrconf.
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Withdrawing address record for fe80::3285:a9ff:fef4:84e2 on wlan0.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::3285:a9ff:fef4:84e2.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Interface wlan0.IPv6 no longer relevant for mDNS.
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
May  7 19:19:42 Prometheus-Linux dhclient: Listening on LPF/wlan0/30:85:a9:f4:84:e2
May  7 19:19:42 Prometheus-Linux dhclient: Sending on   LPF/wlan0/30:85:a9:f4:84:e2
May  7 19:19:42 Prometheus-Linux dhclient: DHCPREQUEST of 192.168.0.25 on wlan0 to 255.255.255.255 port 67 (xid=0x5a1176c2)
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
May  7 19:19:42 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.25.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: New relevant interface wlan0.IPv4 for mDNS.
May  7 19:19:42 Prometheus-Linux avahi-daemon[1448]: Registering new address record for 192.168.0.25 on wlan0.IPv4.
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
May  7 19:19:43 Prometheus-Linux NetworkManager[1663]: <info> Policy set 'Chelonia' (wlan0) as default for IPv4 routing and DNS.
May  7 19:19:44 Prometheus-Linux avahi-daemon[1448]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::3285:a9ff:fef4:84e2.
May  7 19:19:44 Prometheus-Linux avahi-daemon[1448]: New relevant interface wlan0.IPv6 for mDNS.
May  7 19:19:44 Prometheus-Linux avahi-daemon[1448]: Registering new address record for fe80::3285:a9ff:fef4:84e2 on wlan0.*.
May  7 19:19:44 Prometheus-Linux wpa_supplicant[1944]: wlan0: WPA: Group rekeying completed with 50:67:f0:f3:e0:cb [GTK=TKIP]
May  7 19:19:53 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) successful, device activated.
May  7 19:19:54 Prometheus-Linux wpa_supplicant[1944]: wlan0: CTRL-EVENT-SCAN-STARTED 
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> (wlan0): IP6 addrconf timed out or failed.
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
May  7 19:20:03 Prometheus-Linux NetworkManager[1663]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
May  7 19:23:51 Prometheus-Linux NetworkManager[1663]: <info> Policy set 'Chelonia' (wlan0) as default for IPv4 routing and DNS.

******************************************************************************************
******************************************************************************************
Log file: /var/log/kern.log
******************************************************************************************
******************************************************************************************

May  7 19:07:41 Prometheus-Linux kernel: [   13.107000] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=2)
May  7 19:07:41 Prometheus-Linux kernel: [   13.107107] wlan0: associated
May  7 19:07:41 Prometheus-Linux kernel: [   13.107130] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  7 19:15:39 Prometheus-Linux kernel: [  491.341795] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
May  7 19:16:00 Prometheus-Linux kernel: [  512.165860] wlan0: authenticate with 50:67:f0:f3:e0:cb
May  7 19:16:00 Prometheus-Linux kernel: [  512.175243] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:16:00 Prometheus-Linux kernel: [  512.178761] wlan0: authenticated
May  7 19:16:00 Prometheus-Linux kernel: [  512.179010] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May  7 19:16:00 Prometheus-Linux kernel: [  512.179015] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May  7 19:16:00 Prometheus-Linux kernel: [  512.181000] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:16:00 Prometheus-Linux kernel: [  512.183347] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=2)
May  7 19:16:00 Prometheus-Linux kernel: [  512.183468] wlan0: associated
May  7 19:16:31 Prometheus-Linux kernel: [  543.705330] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
May  7 19:18:24 Prometheus-Linux kernel: [  656.404871] wlan0: authenticate with 50:67:f0:f3:e0:cb
May  7 19:18:24 Prometheus-Linux kernel: [  656.414469] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:18:24 Prometheus-Linux kernel: [  656.416517] wlan0: authenticated
May  7 19:18:24 Prometheus-Linux kernel: [  656.416742] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May  7 19:18:24 Prometheus-Linux kernel: [  656.416748] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May  7 19:18:24 Prometheus-Linux kernel: [  656.420228] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:18:24 Prometheus-Linux kernel: [  656.423150] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=6)
May  7 19:18:24 Prometheus-Linux kernel: [  656.423271] wlan0: associated
May  7 19:18:54 Prometheus-Linux kernel: [  686.725938] wlan0: deauthenticating from 50:67:f0:f3:e0:cb by local choice (reason=3)
May  7 19:19:39 Prometheus-Linux kernel: [  731.675046] wlan0: authenticate with 50:67:f0:f3:e0:cb
May  7 19:19:39 Prometheus-Linux kernel: [  731.684531] wlan0: send auth to 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:19:39 Prometheus-Linux kernel: [  731.687055] wlan0: authenticated
May  7 19:19:39 Prometheus-Linux kernel: [  731.687229] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
May  7 19:19:39 Prometheus-Linux kernel: [  731.687237] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
May  7 19:19:39 Prometheus-Linux kernel: [  731.690264] wlan0: associate with 50:67:f0:f3:e0:cb (try 1/3)
May  7 19:19:39 Prometheus-Linux kernel: [  731.696798] wlan0: RX AssocResp from 50:67:f0:f3:e0:cb (capab=0x431 status=0 aid=6)
May  7 19:19:39 Prometheus-Linux kernel: [  731.696918] wlan0: associated

******************************************************************************************
  network info 
******************************************************************************************

wlan0     Link encap:Ethernet  HWaddr 30:85:a9:f4:84:e2  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3285:a9ff:fef4:84e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:252136 (252.1 KB)  TX bytes:174105 (174.1 KB)

******************************************************************************************
 rfkill list all Rfkill Blocks
******************************************************************************************

0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no

./wireless_script_2.1.sh: line 1802: return: ?$: numeric argument required
Finished <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<

http://wireless.kernel.org/en/users/Drivers

```

---

### Post by waffles279 on 2014-05-08
Investigating further, I seem to be able to connect to the wireless connection that I am able to create from my phone (Nexus 7) as a hotspot. Does anyone have any experience with this specific card having issues with certain wifi settings?

---

### Post by Craig_Finch on 2014-06-21
> **waffles279 said:**
> Investigating further, I seem to be able to connect to the wireless connection that I am able to create from my phone (Nexus 7) as a hotspot. Does anyone have any experience with this specific card having issues with certain wifi settings?

I have the same problem with a device with the rtl8192ce chipset. The device can connect to the wireless access point (AP) (verified at the access point) and even gets an IP address, but cannot ping the gateway (or anything else). I suspect the driver, which was provided by Realtek in 2012, is somehow incompatible with the latest 3.x series kernels used in Ubuntu. The issues may also be related to the chipset used in the AP--mine is an AT&T U-Verse modem/wifi router. However, other computers have no problems connecting to this AP, so the problems are Linux-specific.

I'm just giving up and buying an Ethernet bridge. Even if I got this working today, there's no guarantee it would work after the next Ubuntu update.

---

### Post by waffles279 on 2014-06-21
I did even more digging after this post and I believe this card which we both have has issues with the Kernel which are not yet fixed. Our options seem to be fixing a workaround or working with kernel developers to get a fix.

---

### Post by Craig_Finch on 2014-06-21
I agree-I just found the kernel bug, which I will post here for posterity: [https://bugzilla.kernel.org/show_bug.cgi?id=60713](https://bugzilla.kernel.org/show_bug.cgi?id=60713)
So, I might keep the card to see if the bug gets fixed sometime down the road.

---

### Post by praseodym on 2014-06-21
Hi,

there is a Broadcom driver loaded, module name "wl":
```

sudo modprobe -rfv wl
sudo apt-get remove --purge bcmwl-kernel-source
```
After that update the driver via:

```
sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/FreedomBen/rtl8188ce-linux-driver
cd rtl8188ce-linux-driver
make
sudo make install
sudo cp -r firmware/* /lib/firmware
echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
Reboot and check:
```

iwconfig
dmesg | egrep 'rtl8|wlan'
lsmod
cat /etc/modules
```

---

### Post by mike_3 on 2014-08-04
Took me a while to find this but it fixed my problem.

I have a new fibre installation. The BT hh5 that came with exhibited the resolution problem described, dropping back to the HH4 that preceded it, cured the Linux DNS problem but the range dropped off unacceptably. I went for a Netgear Nighthawk and the DNS problem reappeared. No problems when wired to the router, no DNS when using the wireless connection.

praesodym's driver solution has sorted it. Thank you.

---

### Post by praseodym on 2014-08-04
Glad it worked. Please note that the driver needs to be compiled again after a kernel upgrade:
```

cd rtl8188ce-linux-driver
make clean
make
sudo make uninstall
sudo make install
```

---

### Post by paul_courneyea on 2015-01-22
I have two ubuntu driven RTL8182CE wi-fi cards.  The wi-fis quit within minutes of each another. The triggering factor seems to have been a Software Updae, one remained in 10.04 + upgrade, the other was updatedated to 10.10 + upgrade.  Things work, then suddenly stop - usually because their product has reached its end of support period.

Symptoms: wi-fi card shows the wireless card connected but network traffic can not be sent or redeived.  Sites cannot be pinged.  Websites like GOOGLE cannto be reached.

I was really taken aback when I learned that ASUS re-rands Realtek.  ASUS always supported linux well.  Now, I will be looking for another OEM (solid caps notwithstanding.

I am wondering how many users are sitting around scratching theri heads wondering why they cannot connect.  After grabbing at several candidate patches, systems will be spagetti and clean installs will be necessary.


* Some users are reporting intermittent loss of connectivity problem; this is a different problem.

---

### Post by gbell12 on 2015-02-02
Need to pile on here, since this is one of the first Google results, and one of the most recently active threads.

Running Ubuntu 14.04 with the RTL8192CE driver, the connection would establish but hang for a few seconds every 20 seconds or so.

No dmesg or syslog messages.

Putting this:

```
options rtl8192ce ips=0 fwlps=0
```

In: ```
/etc/modprobe.d/rtl8192ce.conf
```

And rebooting solved it for me.  Larry Finger, the current maintainer, was actively engaging [this bug]("https://bugzilla.kernel.org/show_bug.cgi?id=46121"), but then dropped off and/or it got marked as obsolete.

---

### Post by paul_courneyea on 2015-02-20
I was one of many users who suddenly could not use wireless on **RTL8192CE** based network cards.  Both of my desktops failed within minutes of each other.  I had no choice but to buy a couple of ethernet cables.

After several weeks I returned my **CISCO** router to a Rogers (ISP) outlet and received a DPL3825 router in exchange.  When I first plugged in, everything worked well.  But when I configuring Access Configuration and MAC address filtering, the problem returtned.  I could not use wireless.  Enabeling MAC filtering made the network unavalable beyond 198.168.0.1 (router).  Disabiling both MAC filtering stacks opened up the WI-FI completely.

I found a configuration that allows filtering to work.

1) Enter Ethernet MAC Address into the MAC Address Filtering field.(s).

2) Enter WI-FI MAC address into both MAC Address Filtering AND the MAC Filter field(s).

Basically, place WI-FI MAC in both filter stacks.

I then spoke to Rogers (ISP) technical support who confirmed that router firmware upgrades are pushed out on occasion with no warning or release notes.

Both of my computers are working well now.

Testing your router is as simple as disabling **BOTH **MAC filter pages.  If you can see the network now, you have funny firmware on your router.

Regards

---

### Post by paul_courneyea on 2015-02-22
The continuing saga of the Realtek RTL8192CE.  Had I known that ASUS, the backbone of the Linux world was using Realtek hardware, I would have gone with Intel.
 

 In my last post, I had replaced my router and all was well.  Access filtering worked well.  But, since I moved a client desktop to another room, I began using WI-FI.  The WI-FI connection was stable for between 10 and 30 minutes when the desktop completely locked up.   

 

 I worked in IT for many years, most recently with HP-UX as a database administrator and systems administrator.  I know a memory leak when I see a memory leak.  This problem is a memory leak.  
 

 I scavenged a RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller form another box.  The memory leak disappeared.  I hit the new adapter with three streaming source, Zoomer Radio, youtube and CBC radio.  The first pass failed after 65 minutes.  The second and third pass continued for 2 hours when I terminated them.  In normal operation there is no apparent problem.
 

 The odd part of this problem is that Windows 7, double booting on the problem PC appeared to be be unaffected.  This indicates to me that there is a problem with firmware or drivers rather than hardware.

 

 I shall put the RTL8192CE into the junk drawer.  It is likely tol work again someday soon.

---

### Post by gbell12 on 2015-02-26
> The first pass failed after 65 minutes. The second and third pass continued for 2 hours when I terminated them. In normal operation there is no apparent problem.
I'm confused.  What's the first pass vs. the second and third?  If the first failed, doesn't that indicate there is a problem in normal operation?

---

