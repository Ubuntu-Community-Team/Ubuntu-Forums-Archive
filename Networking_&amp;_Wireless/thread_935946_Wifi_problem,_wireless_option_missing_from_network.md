---
title: "Wifi problem, wireless option missing from network manager"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by Fidel82 on 2008-10-02
Hi,

I've been using Ubuntu fine for a couple of months now but it has all gone wrong... (running AMD64 desktop)

I plugged in a new wireless PCI card (Net-lynx) and lost my internet connection. (the new card works fine in XP)

The wireless option in the network manager has gone missing

I have followed many instructions about how to install drivers using NDISwrapper, it seemed like i had managed but I still don't have the wirless option in NM. I am a novice, so it is possible I have been doing this wrong.

I have tried doing a fresh install of ubuntu but not even that solved the problem.

Can anyone provide easy to follow instructions on how to sort this out please? 

Cheers

PS ran this to see if it was recognized:

sudo lshw -C network

*-network UNCLAIMED     
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32

---

### Post by pytheas22 on 2008-10-02
Please post the output of the following commands so that we can figure out what's wrong:
```

ndiswrapper -l
uname -m
lspci -nn
dmesg | grep -e ndis -e wlan
```

---

### Post by Fidel82 on 2008-10-02
al@TV-desktop:~$ ndiswrapper -l
net8185x64 : driver installed
	device (10EC:8185) present
al@TV-desktop:~$ uname -m
x86_64
al@TV-desktop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a2)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a2)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a2)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a2)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a2)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev a1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.2 Multimedia audio controller [0401]: nVidia Corporation MCP51 AC97 Audio Controller [10de:026b] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV505 [Radeon X1550 64-bit] [1002:7147]
03:00.1 Display controller [0380]: ATI Technologies Inc Unknown device [1002:7167]
04:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller [10ec:8185] (rev 20)
al@TV-desktop:~$ dmesg | grep -e ndis -e wlan



This is what I get...

---

### Post by Fidel82 on 2008-10-02
Sorry, and the last bit...


al@TV-desktop:~$ dmesg | grep -e ndis -e wlan
[   49.457310] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   49.689654] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   49.690524] ndiswrapper: driver net8185x64 (Realtek,11/22/2006,5.1094.1122.2006) loaded
[   49.950408] ndiswrapper: using IRQ 16
[   56.080904] Modules linked in: snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss ndiswrapper snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device irtty_sir snd soundcore i2c_nforce2 shpchp sir_dev button snd_page_alloc k8temp evdev pci_hotplug irda parport_pc parport i2c_core pcspkr crc_ccitt ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic usbhid hid pata_amd floppy forcedeth sata_nv pata_acpi libata ohci_hcd ehci_hcd scsi_mod usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   56.081027]  [<ffffffff88292034>] :ndiswrapper:deserialized_irq_handler+0x14/0x30
[   56.081048]  [<ffffffff882a64f2>] :ndiswrapper:win2lin4+0x14/0x17
[   56.081064]  [<ffffffff882977a1>] :ndiswrapper:kdpc_worker+0xc1/0x140
[   56.081084]  [<ffffffff88297788>] :ndiswrapper:kdpc_worker+0xa8/0x140
[   56.081099]  [<ffffffff882976e0>] :ndiswrapper:kdpc_worker+0x0/0x140
al@TV-desktop:~$

---

### Post by pytheas22 on 2008-10-02
Where did you get the Windows driver that you loaded into ndiswrapper?  Was it a 64-bit Windows driver or 32-bit?  If it was 32-bit, you need to remove it and install a win64 driver (the driver architecture needs to match that of your Linux kernel, and you're running 64-bit Ubuntu).

---

### Post by Fidel82 on 2008-10-02
That was one of the first issues I came accross. I have already deleted the 32 bit XP driver and replaced it with the x64 driver that came on a cd with the pci card. It is doing something, the light started flashing on the card, but the wireless option is still missing from the network manager.

Cheers,

---

### Post by Fidel82 on 2008-10-02
Just realized the output of the original code I posted has now changed (after installing the x64 driver), it now reads:

 sudo lshw -C network
 
  *-network               
       description: Ethernet controller
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 20
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ndiswrapper latency=32 maxlatency=64 mingnt=32

---

### Post by pytheas22 on 2008-10-02
> Just realized the output of the original code I posted has now changed (after installing the x64 driver), it now reads:

Alright, that makes more sense now.  Could you please post the output also of:
```

iwconfig
ifconfig
sudo iwlist scan
```

---

### Post by Fidel82 on 2008-10-02
Thanks for the help, but I have given up.

Reinstalled with 32bit Ubuntu, installed the driver with ndsiwrapper and all is working fine.

Shame I couldn't get it working that easily with 64bit, but oh well.

Once again, thanks for your time and help.

---

### Post by pytheas22 on 2008-10-02
Well, I think we could have gotten it to work on 64-bit if we had tried hard enough--I don't think the 64-bit driver was the issue as much as the configuration, and in any case there are native Realtek drivers that would probably support your card on 64-bit as well.  But if you're happy enough with 32-bit, I suppose you may as well stick with that.  Your flash player will be more reliable, anyway...

---

