---
title: "Ralink rt5390 Backtrack 5 R3"
date: 2014-01-11
forum: Networking &amp; Wireless
---

### Post by blkcorv on 2014-01-11
Hi,[br]
[/br]I have been having a lot of trouble these past few weeks trying to get my wireless card on my HP envy m6 notebook to work on Backtrack 5 R3.[br]
[/br]I have tried installing the linux specified driver from [here]("http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501") but that didnt work.(with and without the patch, (rt5592sta_fix_64bit_3.8.patch))[br]
[/br]I followed these steps[br]
[/br]1. Downloaded driver from [here]("http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501") [br]
[/br]2. tar -xvf 2011_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO_v2.bz2.bz2[br]
[/br]3. cd 11_1007_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO[br]
[/br]apllied the patch using,[br]
[/br]4. patch -p1 < rt5592sta_fix_64bit_3.8.patch[br]
[/br]5. opened os/linux/config.mk and changed HAS_WPA_SUPPLICANT_SUPPORT=n to =y[br]
[/br]6. make[br]
[/br]7. sudo make install[br]
[/br]8. sudo modprobe rt5390sta[br]
[/br]after i restarted and it didnt work i blacklisted all of these drivers,[br]
[/br]blacklist rt2800pci [br]
[/br]blacklist rt2800lib [br]
[/br]blacklist rt2x00usb [br]
[/br]blacklist rt2x00pci [br]
[/br]blacklist rt2x00lib [br]
[/br]blacklist rt2860sta [br]
[/br]blacklist rt3090sta[br]
[/br]It still didnt work[br]
[/br][br]
[/br]i also tried using ndiswrapper with the correct windows driver. It installs correctly, software and hardware loaded correctly(so it says), with no load errors when i type the command sudo modprobe ndisswrapper.[br]
[/br][br]
[/br]no matter what i do the output of these commands stay the same[br]
[/br]
(been trying to make the format look nice but its not working for me sorry)[br]
[/br]```
lspci[br]
[br][/br]
[/br]00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)[br]
[br][/br]
[/br]00:02.0 VGA compatible controller: Intel Corporation Device 0166 (rev 09)[br]

[/br]00:14.0 USB Controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)[br]

[/br]00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)[br]

[/br]00:1a.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)[br]

[/br]00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)[br]

[/br]00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)[br]

[/br]00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)[br]

[/br]00:1d.0 USB Controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)[br]

[/br]00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)[br]

[/br]00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)[br]

[/br]00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)[br]

[/br]01:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)[br]

[/br]01:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 0a)[br]

[/br]02:00.0 Network controller: Ralink corp. Device 539b
```[br]

[/br][br]
[/br]```
lshw[br]

[/br] *-pci:0[br]

[/br]             description: PCI bridge[br]

[/br]             product: Panther Point PCI Express Root Port 1[br]

[/br]             vendor: Intel Corporation[br]

[/br]             physical id: 1c[br]

[/br]             bus info: pci@0000:00:1c.0[br]

[/br]             version: c4[br]

[/br]             width: 32 bits[br]

[/br]             clock: 33MHz[br]

[/br]             capabilities: pci pciexpress msi pm bus_master cap_list[br]

[/br]             configuration: driver=pcieport[br]

[/br]             resources: irq:17 ioport:2000(size=4096) memory:50600000-506fffff ioport:50400000(size=1048576)[br]

[/br]           *-generic UNCLAIMED[br]

[/br]                description: Unassigned class[br]

[/br]                product: Realtek Semiconductor Co., Ltd.[br]

[/br]                vendor: Realtek Semiconductor Co., Ltd.[br]

[/br]                physical id: 0[br]

[/br]                bus info: pci@0000:01:00.0[br]

[/br]                version: 01[br]

[/br]                width: 32 bits[br]

[/br]                clock: 33MHz[br]

[/br]                capabilities: pm msi pciexpress msix vpd bus_master cap_list[br]

[/br]                configuration: latency=0[br]

[/br]                resources: memory:50600000-5060ffff[br]

[/br]           *-network[br]

[/br]                description: Ethernet interface                product: RTL8111/8168B PCI Express Gigabit Ethernet controller                vendor: Realtek Semiconductor Co., Ltd.                physical id: 0.2                bus 
info: pci@0000:01:00.2                logical name: eth0                version: 0a                serial: 6c:3b:e5:82:2f:8d                size: 100MB/s                capacity: 1GB/s                width: 64 bits                clock: 33MHz                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.139 latency=0 link=yes multicast=yes port=MII speed=100MB/s                resources: irq:42 ioport:2000(size=256) memory:50404000-50404fff memory:50400000-50403fff        *-pci:1             description: PCI bridge             product: Panther Point PCI Express Root Port 2             vendor: Intel Corporation             physical id: 1c.1             bus info: pci@0000:00:1c.1             version: c4             width: 32 bits             clock: 33MHz             capabilities: pci pciexpress msi pm bus_master cap_list             configuration: driver=pcieport             resources: irq:16 memory:50500000-505fffff           *-network UNCLAIMED                description: Network controller                product: Ralink corp.                vendor: Ralink corp.                physical id: 0                bus info: pci@0000:02:00.0                version: 00                width: 32 bits                clock: 33MHz                capabilities: pm msi pciexpress bus_master cap_list                configuration: latency=0                resources: memory:50500000-5050ffff
``````
iwconfiglo        no wireless extensions.eth0      no wireless extensions.
``````
lsmodModule                  Size  Used bynls_iso8859_1          12713  1 nls_cp437              16991  1 vfat                   17382  1 fat                    60034  1 vfatrt5390sta            1570551  0 snd_hda_codec_hdmi     31994  1 joydev                 17457  0 snd_hda_codec_idt      69962  1 lp                     17789  0 parport                44368  1 lpsnd_hda_intel          33175  2 snd_hda_codec         110336  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intelsnd_hwdep              13554  1 snd_hda_codecsnd_pcm                92879  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codecsnd_seq_midi           13324  0 snd_rawmidi            29179  1 snd_seq_midisnd_seq_midi_event     14436  1 snd_seq_midihid_logitech_dj        18378  0 snd_seq                60549  2 snd_seq_midi,snd_seq_midi_eventsnd_timer              28838  2 snd_pcm,snd_seqsnd_seq_device         14129  3 snd_seq_midi,snd_rawmidi,snd_seqhp_accel               25976  0 hp_wmi                 18048  0 snd                    64384  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_devicemei                    40623  0 uvcvideo               67221  0 videodev               93508  1 uvcvideov4l2_compat_ioctl32    20896  1 videodevlis3lv02d              19401  1 hp_accelpsmouse                72820  0 soundcore              12598  1 sndsnd_page_alloc         18101  2 snd_hda_intel,snd_pcmserio_raw              13211  0 sparse_keymap          13526  1 hp_wmiinput_polldev          13646  1 lis3lv02daufs                  183689  0 usb_storage            55911  1 uas                    17756  0 usbhid                 46275  1 hid_logitech_djhid                    97618  2 hid_logitech_dj,usbhidr8169                  56455  0 wmi                    18697  1 hp_wmivideo                  18858  0 
``````
ifconfig wlan0 upwlan0: ERROR while getting interface flags: No such device
``````
 uname -aLinux bt 3.2.6 #1 SMP Fri Feb 17 10:34:20 EST 2012 x86_64 GNU/Linux
```PS: I do not have the linux driver and ndiswrapper installed at the same time, mostly because i feel they would interfere with each other. Right now i only have the Linux driver with the patch. my code output is based off of thatThank you very much in advance :))

---

### Post by praseodym on 2014-01-11
Try the 2.4.0.4 driver for this old kernel:

[http://forum.ubuntuusers.de/topic/wlan-auf-asus-a73s-laptop-einrichten/#post-2960487](http://forum.ubuntuusers.de/topic/wlan-auf-asus-a73s-laptop-einrichten/#post-2960487)

---

