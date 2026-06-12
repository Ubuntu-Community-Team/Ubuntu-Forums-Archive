---
title: "No connection to the internet whatsoever?"
date: 2011-08-03
forum: New to Ubuntu
---

### Post by Kw16 on 2011-08-03
Hey guys, so I'm extremely new at ubuntu but I know how to get around a computer just fine.
So here's my problem. Yesterday I plugged my laptop into my modem and at first it didn't work so I found out I had to call and get the connection provisioned. Whatever. After that out worked but when I unplugged it and tried to connect to a wireless internet at a friends house it wouldn't connect, so I figure I'd take it home and see if I just needed to install drivers for the wireless card but now its not even recognizing the Ethernet.. I've tried power cycling and I've tried calling again. I have no idea what to do.. i currently have no internet so any and all help would be greatly appreciated. My wireless card is a ralink 3090 and the laptop is a hp g62

---

### Post by sanderd17 on 2011-08-03
Is this a fresh installation, or did you apply updates. In particular, did you apply a partial system upgrade?

---

### Post by Kw16 on 2011-08-03
Yes I did apply the partial system upgrade. Something like 215mbs?

---

### Post by sanderd17 on 2011-08-03
There is the problem. I also did it and now I also don't have any network abilities.

I don't know how to solve it without internet. Normally, I would check what packages were changed and download the old versions, but since I don't have internet, I don't feel like rebooting every time for a trial-and-error cycle. 

So I know what you have, but I don't have the time to solve it. It will cost less time reinstalling the OS. You can keep any files and settings anyway.

---

### Post by Kw16 on 2011-08-03
> **sanderd17 said:**
> There is the problem. I also did it and now I also don't have any network abilities.

I don't know how to solve it without internet. Normally, I would check what packages were changed and download the old versions, but since I don't have internet, I don't feel like rebooting every time for a trial-and-error cycle. 

So I know what you have, but I don't have the time to solve it. It will cost less time reinstalling the OS. You can keep any files and settings anyway.

Oh so it was just the upgrade? Hm odd. So if I just reinstall it will fix it?

---

### Post by josephmills on 2011-08-03
Hi there could you please open you terminal (ctrl+alt+t) and type in ```
lspci -nn 
``` then ```
lsusb
``` then ```
rfkill list all 
``` then ```
lsmod
``` this last one takes some time to load but will ```
sudo lshw -C network
``` then copy to cd or pendrive open what ever it is that you are connected to right now and paste all that here thanks

---

### Post by Kw16 on 2011-08-03
> **josephmills said:**
> Hi there could you please open you terminal (ctrl+alt+t) and type in ```
lspci -nn 
``` then ```
lsusb
``` then ```
rfkill list all 
``` then ```
lsmod
``` this last one takes some time to load but will ```
sudo lshw -C network
``` then copy to cd or pendrive open what ever it is that you are connected to right now and paste all that here thanks

Holy.. what will this do? And I'm on a phone right now so I don't know how this will work :/

---

### Post by Noncon on 2011-08-03
> **Kw16 said:**
> Holy.. what will this do? And I'm on a phone right now so I don't know how this will work :/

Part of the troubleshooting process.  

KJ

---

### Post by Kw16 on 2011-08-03
> **josephmills said:**
> Hi there could you please open you terminal (ctrl+alt+t) and type in ```
lspci -nn 
``` then ```
lsusb
``` then ```
rfkill list all 
``` then ```
lsmod
``` this last one takes some time to load but will ```
sudo lshw -C network
``` then copy to cd or pendrive open what ever it is that you are connected to right now and paste all that here thanks

thecrew@thecrew-HP-G62-Notebook-PC:~$ lspci -nn 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601] 00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602] 00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605] 00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606] 00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] 00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41) 00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40) 00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40) 00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40) 00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] 00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200] 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201] 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202] 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203] 00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204] 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712] 01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f] 02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090] 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) thecrew@thecrew-HP-G62-Notebook-PC:~$ lsusb Bus 007 Device 002: ID 148f:1000 Ralink Technology, Corp. Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub thecrew@thecrew-HP-G62-Notebook-PC:~$ rfkill list all 0: hci0: Bluetooth Soft blocked: no Hard blocked: no 1: phy0: Wireless LAN Soft blocked: no Hard blocked: no thecrew@thecrew-HP-G62-Notebook-PC:~$ lsmod Module Size Used by parport_pc 32111 0 ppdev 12849 0 vesafb 13449 1 joydev 17322 0 snd_hda_codec_hdmi 27535 1 snd_hda_codec_realtek 255882 1 snd_hda_intel 24140 2 rt2860sta 494649 0 snd_hda_codec 90901 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel snd_hwdep 13274 1 snd_hda_codec arc4 12473 2 snd_pcm 80042 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec snd_seq_midi 13132 0 rt2800pci 18119 0 rfcomm 38125 8 snd_rawmidi 25269 1 snd_seq_midi rt2800lib 43824 1 rt2800pci crc_ccitt 12595 2 rt2860sta,rt2800lib rt2x00pci 13986 1 rt2800pci rt2x00lib 39075 3 rt2800pci,rt2800lib,rt2x00pci snd_seq_midi_event 14475 1 snd_seq_midi snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event mac80211 257001 3 rt2800lib,rt2x00pci,rt2x00lib binfmt_misc 13213 1 sco 17827 2 bnep 17785 2 snd_timer 28659 2 snd_pcm,snd_seq l2cap 48656 16 rfcomm,bnep fglrx 2434640 51 hp_wmi 13418 0 snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq sparse_keymap 13666 1 hp_wmi btusb 18160 2 psmouse 73312 0 cfg80211 156212 2 rt2x00lib,mac80211 snd 55295 14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device bluetooth 65493 9 rfcomm,sco,bnep,l2cap,btusb video 18951 0 serio_raw 12990 0 sp5100_tco 13456 0 soundcore 12600 1 snd shpchp 32345 0 eeprom_93cx6 12653 1 rt2800pci i2c_piix4 13095 0 snd_page_alloc 14073 2 snd_hda_intel,snd_pcm k10temp 12951 0 lp 13349 0 parport 36746 3 parport_pc,ppdev,lp ahci 21591 2 r8169 42534 0 libahci 25548 1 ahci thecrew@thecrew-HP-G62-Notebook-PC:~$ sudo lshw -C network [sudo] password for thecrew: *-network description: Wireless interface product: RT3090 Wireless 802.11n 1T/1R PCIe vendor: Ralink corp. physical id: 0 bus info: pci@0000:02:00.0 logical name: wlan0 version: 00 serial: 00:27:13:f9:89:de width: 32 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn resources: irq:17 memory:d0100000-d010ffff *-network description: Ethernet interface product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller vendor: Realtek Semiconductor Co., Ltd. physical id: 0 bus info: pci@0000:03:00.0 logical name: eth0 version: 02 serial: 3c:4a:92:36:62:69 size: 10Mbit/s capacity: 100Mbit/s width: 64 bits clock: 33MHz capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s resources: irq:42 ioport:2000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d002ffff thecrew@thecrew-HP-G62-Notebook-PC:~$

---

### Post by gandaran on 2011-08-03
please paste the text output in code tags, click the # option.

---

### Post by Kw16 on 2011-08-03
```
> **gandaran said:**
> please paste the text output in code tags, click the # option.

thecrew@thecrew-HP-G62-Notebook-PC:~$ lspci -nn 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601] 00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602] 00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605] 00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606] 00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] 00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41) 00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40) 00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40) 00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40) 00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] 00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200] 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201] 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202] 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203] 00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204] 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712] 01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f] 02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090] 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) thecrew@thecrew-HP-G62-Notebook-PC:~$ lsusb Bus 007 Device 002: ID 148f:1000 Ralink Technology, Corp. Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub thecrew@thecrew-HP-G62-Notebook-PC:~$ rfkill list all 0: hci0: Bluetooth Soft blocked: no Hard blocked: no 1: phy0: Wireless LAN Soft blocked: no Hard blocked: no thecrew@thecrew-HP-G62-Notebook-PC:~$ lsmod Module Size Used by parport_pc 32111 0 ppdev 12849 0 vesafb 13449 1 joydev 17322 0 snd_hda_codec_hdmi 27535 1 snd_hda_codec_realtek 255882 1 snd_hda_intel 24140 2 rt2860sta 494649 0 snd_hda_codec 90901 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel snd_hwdep 13274 1 snd_hda_codec arc4 12473 2 snd_pcm 80042 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec snd_seq_midi 13132 0 rt2800pci 18119 0 rfcomm 38125 8 snd_rawmidi 25269 1 snd_seq_midi rt2800lib 43824 1 rt2800pci crc_ccitt 12595 2 rt2860sta,rt2800lib rt2x00pci 13986 1 rt2800pci rt2x00lib 39075 3 rt2800pci,rt2800lib,rt2x00pci snd_seq_midi_event 14475 1 snd_seq_midi snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event mac80211 257001 3 rt2800lib,rt2x00pci,rt2x00lib binfmt_misc 13213 1 sco 17827 2 bnep 17785 2 snd_timer 28659 2 snd_pcm,snd_seq l2cap 48656 16 rfcomm,bnep fglrx 2434640 51 hp_wmi 13418 0 snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq sparse_keymap 13666 1 hp_wmi btusb 18160 2 psmouse 73312 0 cfg80211 156212 2 rt2x00lib,mac80211 snd 55295 14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device bluetooth 65493 9 rfcomm,sco,bnep,l2cap,btusb video 18951 0 serio_raw 12990 0 sp5100_tco 13456 0 soundcore 12600 1 snd shpchp 32345 0 eeprom_93cx6 12653 1 rt2800pci i2c_piix4 13095 0 snd_page_alloc 14073 2 snd_hda_intel,snd_pcm k10temp 12951 0 lp 13349 0 parport 36746 3 parport_pc,ppdev,lp ahci 21591 2 r8169 42534 0 libahci 25548 1 ahci thecrew@thecrew-HP-G62-Notebook-PC:~$ sudo lshw -C network [sudo] password for thecrew: *-network description: Wireless interface product: RT3090 Wireless 802.11n 1T/1R PCIe vendor: Ralink corp. physical id: 0 bus info: pci@0000:02:00.0 logical name: wlan0 version: 00 serial: 00:27:13:f9:89:de width: 32 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn resources: irq:17 memory:d0100000-d010ffff *-network description: Ethernet interface product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller vendor: Realtek Semiconductor Co., Ltd. physical id: 0 bus info: pci@0000:03:00.0 logical name: eth0 version: 02 serial: 3c:4a:92:36:62:69 size: 10Mbit/s capacity: 100Mbit/s width: 64 bits clock: 33MHz capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s resources: irq:42 ioport:2000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d002ffff thecrew@thecrew-HP-G62-Notebook-PC:~$[CODE][CODE]
```[/CODE][/CODE]

---

### Post by Kw16 on 2011-08-03
```

```> **gandaran said:**
> please paste the text output in code tags, click the # option.

thecrew@thecrew-HP-G62-Notebook-PC:~$ lspci -nn 00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS880 Host Bridge [1022:9601] 00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx) [1022:9602] 00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605] 00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606] 00:11.0 SATA controller [0106]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] [1002:4391] 00:12.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:12.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:13.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:13.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41) 00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40) 00:14.3 ISA bridge [0601]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d] (rev 40) 00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40) 00:14.5 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399] 00:16.0 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397] 00:16.2 USB Controller [0c03]: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396] 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200] 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201] 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202] 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203] 00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204] 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712] 01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f] 02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090] 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02) thecrew@thecrew-HP-G62-Notebook-PC:~$ lsusb Bus 007 Device 002: ID 148f:1000 Ralink Technology, Corp. Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub thecrew@thecrew-HP-G62-Notebook-PC:~$ rfkill list all 0: hci0: Bluetooth Soft blocked: no Hard blocked: no 1: phy0: Wireless LAN Soft blocked: no Hard blocked: no thecrew@thecrew-HP-G62-Notebook-PC:~$ lsmod Module Size Used by parport_pc 32111 0 ppdev 12849 0 vesafb 13449 1 joydev 17322 0 snd_hda_codec_hdmi 27535 1 snd_hda_codec_realtek 255882 1 snd_hda_intel 24140 2 rt2860sta 494649 0 snd_hda_codec 90901 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel snd_hwdep 13274 1 snd_hda_codec arc4 12473 2 snd_pcm 80042 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec snd_seq_midi 13132 0 rt2800pci 18119 0 rfcomm 38125 8 snd_rawmidi 25269 1 snd_seq_midi rt2800lib 43824 1 rt2800pci crc_ccitt 12595 2 rt2860sta,rt2800lib rt2x00pci 13986 1 rt2800pci rt2x00lib 39075 3 rt2800pci,rt2800lib,rt2x00pci snd_seq_midi_event 14475 1 snd_seq_midi snd_seq 51291 2 snd_seq_midi,snd_seq_midi_event mac80211 257001 3 rt2800lib,rt2x00pci,rt2x00lib binfmt_misc 13213 1 sco 17827 2 bnep 17785 2 snd_timer 28659 2 snd_pcm,snd_seq l2cap 48656 16 rfcomm,bnep fglrx 2434640 51 hp_wmi 13418 0 snd_seq_device 14110 3 snd_seq_midi,snd_rawmidi,snd_seq sparse_keymap 13666 1 hp_wmi btusb 18160 2 psmouse 73312 0 cfg80211 156212 2 rt2x00lib,mac80211 snd 55295 14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device bluetooth 65493 9 rfcomm,sco,bnep,l2cap,btusb video 18951 0 serio_raw 12990 0 sp5100_tco 13456 0 soundcore 12600 1 snd shpchp 32345 0 eeprom_93cx6 12653 1 rt2800pci i2c_piix4 13095 0 snd_page_alloc 14073 2 snd_hda_intel,snd_pcm k10temp 12951 0 lp 13349 0 parport 36746 3 parport_pc,ppdev,lp ahci 21591 2 r8169 42534 0 libahci 25548 1 ahci thecrew@thecrew-HP-G62-Notebook-PC:~$ sudo lshw -C network [sudo] password for thecrew: *-network description: Wireless interface product: RT3090 Wireless 802.11n 1T/1R PCIe vendor: Ralink corp. physical id: 0 bus info: pci@0000:02:00.0 logical name: wlan0 version: 00 serial: 00:27:13:f9:89:de width: 32 bits clock: 33MHz capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn resources: irq:17 memory:d0100000-d010ffff *-network description: Ethernet interface product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller vendor: Realtek Semiconductor Co., Ltd. physical id: 0 bus info: pci@0000:03:00.0 logical name: eth0 version: 02 serial: 3c:4a:92:36:62:69 size: 10Mbit/s capacity: 100Mbit/s width: 64 bits clock: 33MHz capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s resources: irq:42 ioport:2000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d002ffff thecrew@thecrew-HP-G62-Notebook-PC:~$```
[CODE]
```[/CODE]```

```

---

### Post by Kw16 on 2011-08-03
I don't think I can.. like I said im on a phone..

---

