---
title: "Uninstalling and reinstalling ALSA"
date: 2009-11-19
forum: New to Ubuntu
---

### Post by Darkness Falls on 2009-11-19
I've been having a few problems of late with getting the sound to work on my laptop (running 9.04): specifically, every time Update Manager updates Ubuntu, whatever it does causes the sound to go offline upon restart. I've solved the problem several different ways before now - installing backports, installing ALSA, updating ALSA to the newest version (1.0.21), and, most recently, getting rid of Pulseaudio and installing eSound in its place. The last time auto-update ran, I specifically removed the ticks from the packages relating to Pulseaudio - yet it still killed the sound upon reboot. To be more accurate, ALSA can't seem to find the sound card anymore. I know this is nonsense, because it was working fine under exactly the same setup before I ran the update, but it still says it can't find it.

I want to try and uninstall ALSA and reinstall it, to see if that helps it refresh its memory; however, I'm a beginner at Linux, and don't really know a huge amount about what I'm doing (all the previous fixes were gleaned and copied verbatim either from these forums or from various places over the 'net, without much understanding). Which specific packages do I need to uninstall, to make sure I do a thorough job on it? Is there an *uninstall* command, or does *apt-get remove* do it, or *purge*, or what?

Thanks in advance for your help - any advice you can give will be greatly appreciated!

D.F.

---

### Post by Hospadar on 2009-11-19
I don't know off the top of my head, but as for re-installing packages, you can do it in synaptic, or on the command line with 'apt-get install --reinstall', although I'd suggest you purge first 'apt-get remove --purge' because otherwise you'll keep the configuration files which are probably what is screwing you somewhere.

As for alsa, it most likely consists of many packages, I'd search around in synaptic for likely candidates and give it a shot.  I can't hurt to remove bunches of stuff so long as you keep track of what you removed so you can re-install it.  That's the approach I typically use when I think an installation may need to be re-done or cleaned up.

That said, I'd sort of be surprised if a re-install fixed it unless maybe you have some conflicting hand edited configs (which sounds possible given your audio history), could you provide a little info about your card?  Post the output of 'lspci' (lists pci bus info) and 'sudo lshw -C sound' (lists all kinds of hardware info, "-C sound" makes it list only audio/multimedia hardware).

---

### Post by Darkness Falls on 2009-11-19
Sure!* lspci* gives:-

```
df@df-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
```

*sudo lshw -C sound* gives this:-

```
  *-multimedia UNCLAIMED  
       description: Audio device
       product: R700 Audio Device [Radeon HD 4000 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0
  *-multimedia UNCLAIMED
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```

I'm guessing the big UNCLAIMED tags are probably not helping any?

D.F.

---

