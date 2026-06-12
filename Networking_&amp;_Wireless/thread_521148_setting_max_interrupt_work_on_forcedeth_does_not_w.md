---
title: "setting max_interrupt_work on forcedeth does not work?"
date: 2007-08-09
forum: Networking &amp; Wireless
---

### Post by butonic on 2007-08-09
I found [this]("http://ubuntuforums.org/showthread.php?t=335231&highlight=max_interrupt_work") Forum Post and [this]("https://help.ubuntu.com/community/NvNetInstallation") HowTo.

I'm currently trying the first solution, but simply creating a /etc/modprobe.d/forcedeth with
```
options forcedeth max_interrupt_work=20
```
in it does not seem to work at all. I still get an unending list of
```
eth0: too many iterations (6) in nv_nic_irq.
```
in dmesg.

The machine even hangs sometimes (thats why I updated the kernel to the gutsy one - no change either).

```
$ lspci
00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0a.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0b.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc ES1000 (rev 02)
02:00.0 PCI bridge: NEC Corporation uPD720400 PCI Express - PCI/PCI-X Bridge (rev 07)
02:00.1 PCI bridge: NEC Corporation uPD720400 PCI Express - PCI/PCI-X Bridge (rev 07)
```

```
$ uname -a
Linux feistyserver 2.6.22-7-server #1 SMP Mon Jun 25 17:32:49 GMT 2007 x86_64 GNU/Linux
```

I feel quite stupid at the moment ... why does the driver not respect the option? Can I somehow find out what the current option settings are? modinfo does not help there ...

thx in advance

butonic

---

