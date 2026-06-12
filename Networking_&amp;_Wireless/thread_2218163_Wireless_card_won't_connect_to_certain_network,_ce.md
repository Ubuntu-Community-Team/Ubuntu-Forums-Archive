---
title: "Wireless card won't connect to certain network, certain security, at certain times"
date: 2014-04-19
forum: Networking &amp; Wireless
---

### Post by Sandwiches on 2014-04-19
Hello all, I'm a bit confounded and frustrated here.

Have a new machine with a new install of Xubuntu 14.04 on it. Started with the final beta, everything worked out of the box for two days, during which I upgraded to the proper release and everything was great. Then, I stopped being able to connect to my home network. This continued for hours until it spontaneously reappared in the evening. Now it's gone again, and I'd like it back for good. I am connected on a laptop running Xubuntu on a live disc, it connects fine, as do my Chromebook and Android phone.

The home network is secured with WPA2. I was able to connect to it before, now I cannot. If I drop all security, I can connect to it. I've set up my phone as a wireless hotspot, I can connect to it with WPA2 and unencrypted. I tried a USB network adapter I had lying around, it had similar connectivity problems. I have since blacklisted its driver and disable the onboard ethernet. I have tried in Xubuntu 14.04, Fedora 20, OpenSUSE 13.1 (GNOME and KDE), and the April 2014 iso for Arch. None of them can connect. SUSE KDE won't let me enable wireless, Arch had wifi-menu refuse me instantly every time, wpa_supplicant would acquire and drop a host until it timed out.
 
I'm having a lot of trouble troubleshooting because everything that might be the problem has a counterpoint that suggests otherwise. It could be hardware, but I can connect to other networks with WPA2 and this network with no encryption. It could be software, but other distros don't work either. Could be the network, but other devices work fine. And this worked fine yesterday night and 2-3 days ago, so I'm stumped.

Anyway, here are some outputs that may help, more than happy to provide anything else that may be of use.

lspci

```
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:01.2 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x4 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z87 Express LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 660] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK106 HDMI Audio Controller (rev a1)
02:00.0 Audio device: Creative Labs EMU20k2 [X-Fi Titanium Series] (rev 03)
04:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 01)
05:00.0 Network controller: Ralink corp. RT5392 PCIe Wireless Network Adapter


```

sudo lshw -C network

```
  *-network               
       description: Wireless interface
       product: RT5392 PCIe Wireless Network Adapter
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 00:1a:ef:41:5c:60
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=3.13.0-19-generic firmware=0.34 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f5400000-f540ffff
```

ip link

```
ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 00:1a:ef:41:5c:60 brd ff:ff:ff:ff:ff:ff


```

dmesg | grep firmware

```
[    2.362837] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[    2.364594] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34


```

Edit: Here's the output of the script at the top of the forum.

```

########## wireless info START ##########

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux bigbird 3.13.0-19-generic #40-Ubuntu SMP Mon Mar 24 02:36:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

##### lspci #####

05:00.0 Network controller [0280]: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
    Subsystem: Ralink corp. RT5392 PCIe Wireless Network Adapter [1814:5392]
    Kernel driver in use: rt2800pci

##### lsusb #####

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 174c:2074 ASMedia Technology Inc. 
Bus 003 Device 003: ID 045e:028e Microsoft Corp. Xbox360 Controller
Bus 003 Device 002: ID 058f:6364 Alcor Micro Corp. AU6477 Card Reader Controller
Bus 003 Device 011: ID 059b:0370 Iomega Corp. 
Bus 003 Device 006: ID 1532:0109 Razer USA, Ltd Lycosa Keyboard
Bus 003 Device 005: ID 046d:c249 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

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

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

##### resolv.conf #####

##### nm-tool #####

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800pci
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    T7HB2:           Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 95 WPA WPA2
    Long Beach Island: Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 55 WPA2
    Dave & Jamie's Guest Network: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA WPA2
    hazejamie:       Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 45 WPA2

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

No way to aquire root rights found.

##### iwlist channel #####

wlan0     14 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz

##### lsmod #####

rt2800pci              13606  0 
rt2800mmio             20986  1 rt2800pci
rt2800lib              89076  2 rt2800pci,rt2800mmio
rt2x00pci              13287  1 rt2800pci
rt2x00mmio             13603  2 rt2800pci,rt2800mmio
rt2x00lib              55307  5 rt2x00pci,rt2800lib,rt2800pci,rt2800mmio,rt2x00mmio
mac80211              626584  3 rt2x00lib,rt2x00pci,rt2800lib
cfg80211              490477  2 mac80211,rt2x00lib
eeprom_93cx6           13344  1 rt2800pci
crc_ccitt              12707  1 rt2800lib

##### modinfo #####

filename:       /lib/modules/3.13.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2800pci.ko
license:        GPL
firmware:       rt2860.bin
description:    Ralink RT2800 PCI & PCMCIA Wireless LAN driver.
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     D876F002AA85529257D61EB
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Bsv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Asv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005360sv*sd*bc*sc*i*
alias:          pci:v00001814d0000359Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00003593sv*sd*bc*sc*i*
alias:          pci:v00001814d00003592sv*sd*bc*sc*i*
alias:          pci:v00001814d00003562sv*sd*bc*sc*i*
alias:          pci:v00001814d00003062sv*sd*bc*sc*i*
alias:          pci:v00001814d00003060sv*sd*bc*sc*i*
alias:          pci:v00001432d00007722sv*sd*bc*sc*i*
alias:          pci:v00001432d00007711sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003290sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001462d0000891Asv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        rt2x00lib,rt2800lib,rt2800mmio,rt2x00mmio,rt2x00pci,eeprom_93cx6
intree:         Y
vermagic:       3.13.0-19-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:DF:A0:B3:FD:11:5F:DB:0C:4A:5E:26:94:01:D4
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.13.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2800mmio.ko
license:        GPL
description:    rt2800 MMIO library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     F196893F5F72140CA847345
depends:        rt2800lib,rt2x00lib,rt2x00mmio
intree:         Y
vermagic:       3.13.0-19-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:DF:A0:B3:FD:11:5F:DB:0C:4A:5E:26:94:01:D4
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com, Bartlomiej Zolnierkiewicz
srcversion:     9BD0087B6943A41E7FD8EDA
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-19-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:DF:A0:B3:FD:11:5F:DB:0C:4A:5E:26:94:01:D4
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko
license:        GPL
description:    rt2x00 pci library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     9B9D0D0D0F8571AF43705FD
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-19-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:DF:A0:B3:FD:11:5F:DB:0C:4A:5E:26:94:01:D4
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00mmio.ko
license:        GPL
description:    rt2x00 mmio library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     07530604F5CE4EF69872C75
depends:        rt2x00lib
intree:         Y
vermagic:       3.13.0-19-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:DF:A0:B3:FD:11:5F:DB:0C:4A:5E:26:94:01:D4
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-19-generic/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         http://rt2x00.serialmonkey.com
srcversion:     C57F87A3569F5363E79FD42
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-19-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:DF:A0:B3:FD:11:5F:DB:0C:4A:5E:26:94:01:D4
sig_hashalgo:   sha512

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
blacklist rtl8192cu

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

# PCI device 0x8086:0x153b (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x1814:0x5392 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    1.812077] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5392, rev 0223 detected
[    1.816236] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5392 detected
[    2.362837] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[    2.364594] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[    2.487190] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.487383] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   18.053853] wlan0: authenticate with <MAC address removed>
[   18.073944] wlan0: send auth to <MAC address removed> (try 1/3)
[   18.075336] wlan0: authenticated
[   18.077486] wlan0: associate with <MAC address removed> (try 1/3)
[   18.080577] wlan0: RX AssocResp from <MAC address removed> (capab=0x431 status=0 aid=2)
[   18.080948] wlan0: associated
[   18.080960] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   63.172076] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  769.556922] Modules linked in: ctr ccm rfcomm bnep bluetooth xpad ff_memless joydev binfmt_misc snd_hda_codec_hdmi mxm_wmi x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper snd_hda_codec_realtek ablk_helper cryptd snd_ctxfi psmouse serio_raw snd_seq_midi snd_seq_midi_event snd_hda_intel snd_hda_codec snd_rawmidi snd_hwdep arc4 snd_pcm wmi rt2800pci nvidia(POF) video rt2800mmio rt2800lib rt2x00pci intel_smartconnect rt2x00mmio rt2x00lib drm mac80211 snd_seq snd_page_alloc snd_seq_device snd_timer lpc_ich cfg80211 snd eeprom_93cx6 crc_ccitt soundcore mei_me mei mac_hid parport_pc ppdev lp parport hid_generic usbhid hid usb_storage ahci libahci
[  956.699152] Modules linked in: ctr ccm rfcomm bnep bluetooth xpad ff_memless joydev binfmt_misc snd_hda_codec_hdmi mxm_wmi x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper snd_hda_codec_realtek ablk_helper cryptd snd_ctxfi psmouse serio_raw snd_seq_midi snd_seq_midi_event snd_hda_intel snd_hda_codec snd_rawmidi snd_hwdep arc4 snd_pcm wmi rt2800pci nvidia(POF) video rt2800mmio rt2800lib rt2x00pci intel_smartconnect rt2x00mmio rt2x00lib drm mac80211 snd_seq snd_page_alloc snd_seq_device snd_timer lpc_ich cfg80211 snd eeprom_93cx6 crc_ccitt soundcore mei_me mei mac_hid parport_pc ppdev lp parport hid_generic usbhid hid usb_storage ahci libahci
[ 2360.118804] Modules linked in: ctr ccm rfcomm bnep bluetooth xpad ff_memless joydev binfmt_misc snd_hda_codec_hdmi mxm_wmi x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper snd_hda_codec_realtek ablk_helper cryptd snd_ctxfi psmouse serio_raw snd_seq_midi snd_seq_midi_event snd_hda_intel snd_hda_codec snd_rawmidi snd_hwdep arc4 snd_pcm wmi rt2800pci nvidia(POF) video rt2800mmio rt2800lib rt2x00pci intel_smartconnect rt2x00mmio rt2x00lib drm mac80211 snd_seq snd_page_alloc snd_seq_device snd_timer lpc_ich cfg80211 snd eeprom_93cx6 crc_ccitt soundcore mei_me mei mac_hid parport_pc ppdev lp parport hid_generic usbhid hid usb_storage ahci libahci
[ 2488.287509] Modules linked in: ctr ccm rfcomm bnep bluetooth xpad ff_memless joydev binfmt_misc snd_hda_codec_hdmi mxm_wmi x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel aes_x86_64 lrw gf128mul glue_helper snd_hda_codec_realtek ablk_helper cryptd snd_ctxfi psmouse serio_raw snd_seq_midi snd_seq_midi_event snd_hda_intel snd_hda_codec snd_rawmidi snd_hwdep arc4 snd_pcm wmi rt2800pci nvidia(POF) video rt2800mmio rt2800lib rt2x00pci intel_smartconnect rt2x00mmio rt2x00lib drm mac80211 snd_seq snd_page_alloc snd_seq_device snd_timer lpc_ich cfg80211 snd eeprom_93cx6 crc_ccitt soundcore mei_me mei mac_hid parport_pc ppdev lp parport hid_generic usbhid hid usb_storage ahci libahci

########## wireless info END ############


```

---

### Post by varunendra on 2014-04-20
You don't need to blacklist the rtl8192cu driver if you are not going to use the USB adapter (and you won't be able to use the adapter if you have blacklisted the driver it depends on). So please remove it from the blacklist, it may not be related to a solution, but the blacklisting is almost pointless.

Have you tried the "nohwcrypt=Y" parameter with your current driver yet? Here's how -
```
sudo modprobe -rv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
It will be a temporary change that will be lost at next boot. If it helps, we can make it permanent.

It seems you didn't supply your password when asked by the script, so it couldn't produce the results of "sudo iwlist scan" command. Could you manually run the command and post its output (with MAC IDs removed if you are concerned about that) so we can be sure there is no problem with scanning and encryption settings on the router's part?

Please also state clearly which one is _Your_ router/access-point among the listed ones in the output.

---

