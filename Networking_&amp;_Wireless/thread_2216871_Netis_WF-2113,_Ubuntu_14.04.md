---
title: "Netis WF-2113, Ubuntu 14.04"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by mbott on 2014-04-14
Round 1 can be found here: [http://ubuntuforums.org/showthread.php?t=2155822&p=12698196#post12698196]("http://ubuntuforums.org/showthread.php?t=2155822&p=12698196#post12698196")

Round 2 began this morning with the following steps takes;

Hardware is the Netis WF-2113 and the system is an Asus H87M-Plus motherboard. CPU is a Intel i5. My router is a Belkin N600 DB.

1) Clean install of 14.04 beta 2.
2) Reboot and update 14.04
3) Enter net manager and set up to connect wirelessly
4) Nothing.  I can "see" my network but nothing else.  None of the other 17 networks I can "see" from 12.04 on my laptop are visible.

Here's the good stuff:

```
########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux mdesktop 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8554]
	Kernel driver in use: r8169

06:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178]
	Kernel driver in use: rtl8192ce

##### lsusb #####

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 003 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
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

wlan0     IEEE 802.11bgn  ESSID:"cz_2075"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC address removed>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #####

nameserver 127.0.1.1
```

```
##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0  [cz_2075] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
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
    *cz_2075:        Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 78 WPA WPA2

  IPv4 Settings:
    Address:         192.168.2.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.18
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

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
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000154889198
                    Extra: Last beacon: 220ms ago
                    IE: Unknown: 000700000000000000
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050401030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180204F0000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=26 dBm  
                    Encryption key:on
                    ESSID:"cz_2075"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000148fd8eef
                    Extra: Last beacon: 193496ms ago
                    IE: Unknown: 0007637A5F32303735
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000060d3c7e018a
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 000D00000000000000000000000000
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180201F4000000
```

```
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
          Current Frequency:2.437 GHz (Channel 6)

##### lsmod #####

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53172  1 rtl8192ce
mac80211              626489  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              484040  2 mac80211,rtlwifi

##### modinfo #####

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     BF8278DF19B67D7D6C6B8C5
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
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

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:47:4B:C5:C4:31:20:88:0C:1B:94:A5:39:F4:31
sig_hashalgo:   sha512

##### modules #####

lp
rtc
```

```
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

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[    9.421082] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[    9.491032] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.491151] rtlwifi: wireless switch is on
[   20.138697] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.138896] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  291.767855] wlan0: authenticate with <MAC address removed>
[  291.787235] wlan0: send auth to <MAC address removed> (try 1/3)
[  291.790077] wlan0: authenticated
[  291.790183] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  291.790186] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  291.790947] wlan0: associate with <MAC address removed> (try 1/3)
[  291.793080] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  291.793186] wlan0: associated
[  291.793193] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  291.854954] Modules linked in: ctr ccm joydev rfcomm bnep bluetooth snd_hda_codec_realtek snd_hda_codec_hdmi eeepc_wmi asus_wmi sparse_keymap arc4 x86_pkg_temp_thermal intel_powerclamp snd_hda_intel rtl8192ce snd_hda_codec coretemp rtl_pci rtlwifi snd_hwdep snd_pcm snd_page_alloc rtl8192c_common snd_seq_midi snd_seq_midi_event snd_rawmidi mac80211 snd_seq snd_seq_device snd_timer kvm_intel snd cfg80211 kvm soundcore i915 crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 drm_kms_helper drm lrw gf128mul glue_helper psmouse ablk_helper cryptd i2c_algo_bit serio_raw wmi mei_me lpc_ich mei video mac_hid parport_pc ppdev lp parport hid_logitech_dj usbhid hid usb_storage ahci r8169 libahci mii
[  291.855023]  [<ffffffffa02f33ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]

########## wireless info END ############
```

Any and all suggestions greatly appreciated.

-- 
Mike

---

### Post by praseodym on 2014-04-14
This driver is known to be "critical". Lets try these module parameters:
```

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```
Check:
```

dmesg | grep rtl
dmesg >> dmesg.txt #please upload this file
ifconfig -a
iwconfig
sudo iwlist scan
```
Is the network "hidden"? If yes, broadcast the ESSID. Which country do you live?

---

### Post by mbott on 2014-04-14
Network Unhidden ... In the US.

echo "options rtl8192ce swlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf

```
options rtl8192ce swlps=0 ips=0
```

sudo modprobe -rfv rtl8192ce

```
rmmod rtl8192ce
rmmod rtl8192c_common
rmmod rtl_pci
rmmod rtlwifi
rmmod mac80211
rmmod cfg80211
```

sudo modprobe -v rtl8192ce

```
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko swlps=0 ips=0 
```

Check: Wireless connection has been lost

dmesg | grep rtl

```
[   10.162511] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   10.409692] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   10.409804] rtlwifi: wireless switch is on
[   19.678042] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   19.678044] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   20.023223] Modules linked in: ctr ccm bnep rfcomm bluetooth snd_hda_codec_realtek snd_hda_codec_hdmi arc4 eeepc_wmi asus_wmi sparse_keymap x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper ablk_helper cryptd psmouse serio_raw snd_seq_midi rtl8192ce snd_seq_midi_event rtl_pci rtlwifi snd_rawmidi rtl8192c_common lpc_ich mac80211 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq cfg80211 snd_seq_device snd_page_alloc snd_timer snd i915 mei_me mei video drm_kms_helper drm wmi parport_pc mac_hid ppdev soundcore i2c_algo_bit lp parport hid_logitech_dj usbhid hid usb_storage ahci r8169 libahci mii
[   20.023273]  [<ffffffffa040b3ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]
[ 7087.211214] rtl8192ce 0000:06:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 7087.211218] rtl8192ce 0000:06:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 7281.180351] rtl8192ce: rtl8192ce: Power Save off (module option)
[ 7281.180355] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 7281.189376] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 7281.189550] rtlwifi: wireless switch is on

```

Uploaded dmesg.txt.tar.gz

ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 60:a4:4c:cb:4d:26  
          inet6 addr: fe80::62a4:4cff:fecb:4d26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:329009 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188063 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:467943374 (467.9 MB)  TX bytes:18821558 (18.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3723 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:556281 (556.2 KB)  TX bytes:556281 (556.2 KB)

wlan0     Link encap:Ethernet  HWaddr 08:10:74:da:9a:16  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

iwconfig

```
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
```

sudo iwlist scan

```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 08:86:3B:57:F2:85
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"cz_2075"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000002408eb8b
                    Extra: Last beacon: 12ms ago
                    IE: Unknown: 0007637A5F32303735
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F0000000
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```

-- 
Mike

---

### Post by praseodym on 2014-04-14
Is it your network shown there? If yes, change the encryption to WPA2-AES (CCMP) only.

```
[ 2453.321366] wlan0: deauthenticating from 08:86:3b:57:f2:85 by local choice (reason=3)
```
reason=3 is a network-manager issue. Did you deactivate IPv6 there? Have you tried Wicd instead?

---

### Post by mbott on 2014-04-14
> **praseodym said:**
> Is it your network shown there? If yes, change the encryption to WPA2-AES (CCMP) only. [COLOR="#FF0000"]<=Already set to WPA2-PSK AES.[/COLOR]

```
[ 2453.321366] wlan0: deauthenticating from 08:86:3b:57:f2:85 by local choice (reason=3)
```
reason=3 is a network-manager issue. Did you deactivate IPv6 there? [COLOR="#FF0000"]No.[/COLOR] Have you tried Wicd instead? [COLOR="#FF0000"]Yes.[/COLOR] 

-- 
Mike

---

### Post by praseodym on 2014-04-14
```
                    IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180202F0000000
                    IE: [COLOR="#FF0000"]WPA[/COLOR] Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
Still mixed mode!

---

### Post by mbott on 2014-04-14
No change:

```
eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 08:86:3B:57:F2:85
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:on
                    ESSID:"cz_2075"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000055749c58
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 0007637A5F32303735
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180203F0000000
```

-- 
Mike

Edited to add: I'm just going to abandon 14.04 beta for the mean time since wireless is an ongoing issue along with sharing.  :(

---

### Post by praseodym on 2014-04-15
Try this driver for 12.04.4 with kernel 3.11:

[http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/3/#post-6439727](http://forum.ubuntuusers.de/topic/realtek-rtl8188ce-treiber-installieren/3/#post-6439727)

---

### Post by mbott on 2014-04-15
We'll give it a shot.  Thanks again for all the help.

-- 
Mike

---

### Post by mbott on 2014-05-11
Just a quick update to this thread.  Been doing a bit more research on the Netis WF-2113 and came across a post where someone has decent results with the Ubuntu 12.04 remix Black Opal 64 bit, so I put a copy on a DVD and booted into their live version.  The card is very stable, something it wasn't under 12.04 and 14.04.  It's not 802.11n, but definitely has 802.11g working. Might have to image off Ubuntu 14.04 for a while and experiment with Black Opal.

-- 
Mike

---

### Post by praseodym on 2014-05-11
Which kernel is it?
```

uname -a
```

---

### Post by mbott on 2014-05-11
The live DVD:

opal@opal:~$ uname -a
Linux opal 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

-- 
Mike

---

### Post by praseodym on 2014-05-11
Ok, you can try 12.04.1, thats the same kernel:

[http://old-releases.ubuntu.com/releases/12.04.1/](http://old-releases.ubuntu.com/releases/12.04.1/)

---

### Post by mbott on 2014-05-12
With 12.04.1 I had some initial issues with my Logitech wireless mouse and keyboard.  (Same with the Black Opal remix, too, I've rediscovered)

-- 
Mike

---

### Post by mbott on 2014-10-02
Finally got around to dumping the Netis WF-2113 and replaced it with a TP-Link TL-WN951N which is Atheros based (AR922X Wireless Network Adapter (rev 01)). Took about 5 minutes to put in service and wireless is well again.

All smiles here.

-- 
Mike

---

