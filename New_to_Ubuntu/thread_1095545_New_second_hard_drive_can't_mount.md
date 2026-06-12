---
title: "New second hard drive can't mount"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by unseenpower on 2009-03-13
I'm having difficulty getting a second hard drive recognized in 8.1.

The drive is a SATA WD 320 Gig and is recognized in the bios.   My machine is dual boot Vista (yuck, so my wife wouldn't protest about linux) and Ubuntu using GRUB as the bootloader

So I can

-See the drive in BIOS
-See the drive in Windows
-Cannot see the drive using Gparted

When I run sudo fdisk (found on the forum) I get the following

gamester@gamester-desktop:~$ sudo fdisk -l
[sudo] password for gamester: 

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1313    10485760    7  HPFS/NTFS
/dev/sda3   *        1313       17138   127112184    7  HPFS/NTFS
/dev/sda4           17139       30394   106478820    5  Extended
/dev/sda5           17139       29850   102109108+  83  Linux
/dev/sda6           29851       30394     4369648+  82  Linux swap / Solaris

Disk /dev/sdc: 128 MB, 128188416 bytes
8 heads, 32 sectors/track, 978 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         978      125167+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(976, 7, 32) logical=(977, 7, 31)

Any help?

---

### Post by martrn on 2009-03-13
When going through your BIOS is there any cool and quiet settings or any SpeedStep feature enabled Disabled in the BIOS of your motherboard ?

Is there any upgrades to your BIOS, Check and Install all/any BIOS updates available. Can you switch off any advances SpeedStep/CoolNQuiet feature ?

What is the chip-set of your motherboard ? (SATA controller), EG, what is the output from :

```
lspci
```

---

### Post by unseenpower on 2009-03-13
I have the cool and quiet-- let me try some of those settings

Here's the results from lspci

root@gamester-desktop:~# lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI

Thanks for the help---   The install of Ubuntu has been FLAWLESS with the exception of this

---

### Post by unseenpower on 2009-03-13
Flashed the bios and turned off cool and quiet-- gparted still doesn't see i....

---

