---
title: "Problem with Usb Wireless (WiFi) Adapter (by SignalKing)"
date: 2014-12-15
forum: Networking &amp; Wireless
---

### Post by Arahion on 2014-12-15
[COLOR=#333333][FONT=UbuntuRegular]I have bought a USB Wireless Adapter made by SignalKing because I broke my laptop's hardware switch of the embedded adapter. Despite the fact that I can use it on Windows without having any issue, while using Ubuntu (14.10) I get this message:

[/FONT][/COLOR]> [COLOR=#333333][FONT=UbuntuRegular]Wi-Fi Network (Ralink 802.11 nWlan) Wi-Fi is disabled by hardware switch[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]

[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]But there's no hardware switch on SignalKing. The green light showing the adapter is working, is on.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Here are some of the commands I used and the output:

```
[COLOR=#222222][FONT=Ubuntu Mono]sudo rfkill unblock all[/FONT][/COLOR]
```
But nothing happened

```
[COLOR=#222222][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
```

[/FONT][/COLOR]> 
[COLOR=#3C3B37][FONT=Monaco]02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Subsystem: Toshiba America Info Systems Device [1179:ff1e][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Kernel driver in use: r8169[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201][/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Kernel driver in use: iwlwifi[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
```
[COLOR=#222222][FONT=Ubuntu Mono]lsusb[/FONT][/COLOR]
```

[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]> 
[/FONT][/COLOR][COLOR=#3C3B37][FONT=Monaco]Bus 002 Device 003: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 005 Device 002: ID 1a2c:0040 China Resource Semico Co., Ltd [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 [/FONT][/COLOR]root[COLOR=#3C3B37][FONT=Monaco] hub[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]

```
[COLOR=#222222][FONT=Ubuntu Mono]sudo lshw -c network[/FONT][/COLOR]
```

[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]> 
[/FONT][/COLOR][COLOR=#3C3B37][FONT=Monaco]*-network               [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       description: Ethernet interface[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       physical id: 0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       bus info: pci@0000:02:00.0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       logical name: eth0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       version: 02[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       serial: 00:1e:33:55:fc:92[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       size: 10Mbit/s[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       capacity: 100Mbit/s[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       width: 64 bits[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       resources: irq:44 ioport:3000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]  *-network DISABLED[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       product: WiFi Link 5100[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       vendor: Intel Corporation[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       physical id: 0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       bus info: pci@0000:03:00.0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       logical name: wlan0[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       version: 00[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       serial: 00:16:ea:a7:23:94[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       width: 64 bits[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       configuration: broadcast=yes driver=iwlwifi driverversion=3.16.0-24-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       resources: irq:46 memory:d4200000-d4201fff[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]  *-network DISABLED[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       description: Wireless interface[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       physical id: 2[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       bus info: usb@2:2[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       logical name: wlan1[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       serial: 00:25:22:48:a8:8e[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       capabilities: ethernet physical wireless[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]       configuration: broadcast=yes driver=rt2800usb driverversion=3.16.0-24-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]

```
[COLOR=#222222][FONT=Ubuntu Mono]sudo rfkill list all[/FONT][/COLOR]
```

[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]> 
[/FONT][/COLOR]> [COLOR=#3C3B37][FONT=Monaco]0: phy0: Wireless LAN[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Soft blocked: no[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Hard blocked: yes[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]1: phy1: Wireless LAN[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Soft blocked: no[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]   Hard blocked: no[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]

```
lsmod
```
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
> 
[/FONT][/COLOR][COLOR=#3C3B37][FONT=Monaco]Module                  Size  Used by[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]bnep                   19543  2 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]rfcomm                 69509  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]bluetooth             446190  10 bnep,rfcomm[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]6lowpan_iphc           18702  1 bluetooth[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]hid_generic            12559  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]coretemp               13441  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]kvm_intel             143553  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_seq_midi           13564  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]kvm                   459843  1 kvm_intel[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_seq_midi_event     14899  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_rawmidi            30876  1 snd_seq_midi[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]joydev                 17344  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]uvcvideo               81065  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]videobuf2_vmalloc      13216  1 uvcvideo[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]videobuf2_memops       13362  1 videobuf2_vmalloc[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]radeon               1416372  3 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]serio_raw              13434  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]videobuf2_core         59104  1 uvcvideo[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_seq                67224  2 snd_seq_midi_event,snd_seq_midi[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]v4l2_common            15682  1 videobuf2_core[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_hda_codec_realtek    76887  1 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_hda_codec_generic    68914  1 snd_hda_codec_realtek[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]parport_pc             32741  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_hda_codec_hdmi     47547  2 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]videodev              149725  3 uvcvideo,v4l2_common,videobuf2_core[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]ppdev                  17671  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]r852                   18075  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]sm_common              16860  1 r852[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]media                  21963  2 uvcvideo,videodev[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]lp                     17759  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]parport                42299  3 lp,ppdev,parport_pc[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]usbhid                 52574  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_hda_intel          30379  5 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_hda_controller     35152  1 snd_hda_intel[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]hid                   110426  2 hid_generic,usbhid[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]nand                   68630  2 r852,sm_common[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_hda_codec         139675  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]nand_ecc               13312  1 nand[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_hwdep              17698  1 snd_hda_codec[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]nand_bch               13227  1 nand[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]bch                    17397  1 nand_bch[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]nand_ids               12723  1 nand[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_pcm               104102  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]arc4                   12608  4 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]mtd                    59628  2 nand,sm_common[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]ttm                    89406  1 radeon[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]drm_kms_helper         61627  1 radeon[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]r592                   18040  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]iwldvm                236430  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]memstick               16966  1 r592[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]lpc_ich                21093  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]toshiba_acpi           28320  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]drm                   310919  6 ttm,drm_kms_helper,radeon[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]iwlwifi               182909  1 iwldvm[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]i2c_algo_bit           13406  1 radeon[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]sparse_keymap          13948  1 toshiba_acpi[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]wmi                    19193  1 toshiba_acpi[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]toshiba_bluetooth      12867  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd_timer              29513  2 snd_pcm,snd_seq[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]snd                    87611  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]rt2800usb              27139  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]rt2x00usb              20742  1 rt2800usb[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]rt2800lib              93180  1 rt2800usb[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]rt2x00lib              55170  3 rt2x00usb,rt2800lib,rt2800usb[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]soundcore              15052  2 snd,snd_hda_codec[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]shpchp                 37040  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]video                  20128  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]mac80211              660592  4 rt2x00lib,rt2x00usb,rt2800lib,iwldvm[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]mac_hid                13227  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]cfg80211              510218  4 iwlwifi,mac80211,rt2x00lib,iwldvm[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]crc_ccitt              12707  1 rt2800lib[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]psmouse               106548  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]firewire_ohci          44323  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]ahci                   34062  4 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]libahci                32424  1 ahci[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]sdhci_pci              23261  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]sdhci                  43448  1 sdhci_pci[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]firewire_core          68671  1 firewire_ohci[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]r8169                  71471  0 [/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]crc_itu_t              12707  1 firewire_core[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco]mii                    13934  1 r8169[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]

```
[COLOR=#222222][FONT=Ubuntu Mono]dmesg | grep rt2[/FONT][/COLOR]
```
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
> 
[/FONT][/COLOR][COLOR=#3C3B37][FONT=Monaco][    6.208167] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco][    6.301516] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 0005 detected[/FONT][/COLOR]
[COLOR=#3C3B37][FONT=Monaco][    6.375882] usbcore: registered new interface driver rt2800usb[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]



[IMG]https://scontent-b-fra.xx.fbcdn.net/hphotos-xpf1/v/t1.0-9/10387382_1503304409922865_653852359882015761_n.jpg?oh=4b22403c41e212c68e28a4101cb7a390&oe=5516D16A[/IMG][/FONT][/COLOR]

---

### Post by slickymaster on 2014-12-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by Bucky Ball on 2014-12-16
Welcome. That appears to be the wrong driver. You might find [THIS]("http://ubuntuforums.org/showthread.php?t=2210930&p=12955680&viewfull=1#post12955680") of some help. 

I also found [this]("http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html"). It's lengthier and for 10.04 LTS, but may work if the above link doesn't. I think this driver is the one chili555 mentions in an earlier post on the first link I've given and goes for his method in preference. 

Good luck and let us know.

PS: Could you please keep all code output in [code] tags and attach large images in future posts? Neater and easier to read. Thanks.  ;)

---

