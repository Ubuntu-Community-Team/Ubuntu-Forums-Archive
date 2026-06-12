---
title: "Help with Acer laptop wireless"
date: 2014-08-24
forum: Networking &amp; Wireless
---

### Post by gregory-sech on 2014-08-24
You are my last Hope.

This is the output:
```

########## wireless info START ##########

Report from: 24 Aug 2014 22:33 CEST +0200

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:49:09 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash

##### desktop #####

Ubuntu

##### lspci #####

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Acer Incorporated [ALI] Device [1025:036d]
    Kernel driver in use: tg3

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192SE Wireless LAN Controller [10ec:8174] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8186]
    Kernel driver in use: rtl8192se

##### lsusb #####

Bus 002 Device 003: ID 1532:0036 Razer USA, Ltd RZ01-0075, Gaming Mouse [Naga Hex]
Bus 002 Device 007: ID 0bb4:0004 HTC (High Tech Computer Corp.) 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a219 Suyin Corp. 1.3M WebCam (notebook emachines E730, Acer sub-brand)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info #####

##### rfkill #####

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes

##### lsmod #####

rtl8192se              62187  0 
rtl_pci                26314  1 rtl8192se
rtlwifi                52835  2 rtl_pci,rtl8192se
mac80211              546051  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              409394  2 mac80211,rtlwifi
acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
mxm_wmi                12893  0 
wmi                    18673  2 acer_wmi,mxm_wmi
video                  18903  1 acer_wmi

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

usb0      Link encap:Ethernet  HWaddr <MAC addr usb0>  
          inet addr:192.168.42.254  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::8b:30ff:fe41:696c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20577 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14703 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25098610 (25.0 MB)  TX bytes:2037190 (2.0 MB)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

usb0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: usb0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            rndis_host
  State:             connected
  Default:           yes
  HW Address:        <MAC addr usb0>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.42.254
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129

    DNS:             192.168.42.129

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             unavailable
  Default:           no
  HW Address:        <MAC address>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>

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

##### iw reg get #####

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo        no frequency information.

eth0      no frequency information.

usb0      no frequency information.

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

##### iwlist scan #####

wlan0     Interface doesn't support scanning : Network is down

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

usb0      Interface doesn't support scanning.

##### module infos #####

[rtl8192se]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C53951858E34882052195CA
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
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

[rtl_pci]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     D5E4890DC428FA5A1BF92DF
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.13.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E1F4663325225EE8DBA54CA
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        1B:7C:0F:16:16:8C:4B:25:C3:A0:5A:6A:43:09:1C:85:06:E3:73:DF
sig_hashalgo:   sha512

##### module parameters #####

[rtl8192se]
debug: 0
fwlps: N
ips: Y
swenc: N
swlps: Y

##### /etc/modules #####

lp

##### blacklists #####

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

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   18.805349] rtl8192se: FW Power Save off (module option)
[   18.805413] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   18.805413] Loading firmware rtlwifi/rtl8192sefw.bin
[   19.107463] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   22.961430] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[   82.067764] wlan0: authenticate with <MAC address>
[   82.078566] wlan0: send auth to <MAC address> (try 1/3)
[   82.080598] wlan0: authenticated
[   82.082734] wlan0: associate with <MAC address> (try 1/3)
[   82.086354] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=3)
[   82.089120] wlan0: associated
[   82.089134] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   82.130797] Modules linked in: ctr ccm rfcomm bnep bluetooth snd_hda_codec_hdmi arc4 snd_hda_codec_realtek uvcvideo videobuf2_vmalloc videobuf2_memops snd_hda_intel videobuf2_core snd_hda_codec videodev snd_hwdep snd_pcm snd_page_alloc snd_seq_midi snd_seq_midi_event snd_rawmidi rtl8192se snd_seq rtl_pci rtlwifi intel_powerclamp coretemp kvm_intel snd_seq_device mac80211 snd_timer kvm cfg80211 nvidia(POF) serio_raw lpc_ich drm snd mei_me mei soundcore joydev acer_wmi sparse_keymap parport_pc mxm_wmi mac_hid wmi ppdev video lp parport hid_generic usbhid hid tg3 psmouse ptp ahci pps_core libahci
[   82.130841] CPU: 2 PID: 787 Comm: NetworkManager Tainted: PF          O 3.13.0-34-generic #60-Ubuntu
[  499.988730] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[  509.363864] wlan0: authenticate with <MAC address>
[  509.374196] wlan0: send auth to <MAC address> (try 1/3)
[  509.376092] wlan0: authenticated
[  509.378698] wlan0: associate with <MAC address> (try 1/3)
[  509.381764] wlan0: RX AssocResp from <MAC address> (capab=0x411 status=0 aid=3)
[  509.384679] wlan0: associated
[  515.760936] wlan0: deauthenticating from <MAC address> by local choice (reason=3)
[  520.906818] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############
```

---

### Post by howefield on 2014-08-25
Hello,

Post moved to it's own thread.

---

### Post by varunendra on 2014-08-25
Hello gregory-sech!

I was hesitating to reply your thread, since your problem may take extensive efforts to get solved, while I may not be able to dedicate that much time. But since no one else picked it up, I think... let's try..

Right now, in the report, your wireless is both hard and soft blocked. Means it is turned off by both the hardware switch (or Fn+ key combo or whatever mechanism you have to toggle it on/off), and by the software.

To remove the 'hard block', please try the switch (or key combo) that turns it on/off. Check with -
```
rfkill list
```
To remove the soft block, please make sure both "Enable Networking" and "Enable Wireless" options in the Network Manager have a tick mark beside them (click the option(s) to enable them if they are not already). If they are already enabled (have tick marks), try -
```
sudo rfkill unblock all
```

I believe your original problem is something different though, since the dmesg part in the script report shows at least one connection attempt when the system started. Means it was not blocked then.

So if the problem persists after removing the hard/soft blocks, please run the script again when it is no more blocked, and a connection attempt has been made/failed, then post back the fresh report showing that state.

---

