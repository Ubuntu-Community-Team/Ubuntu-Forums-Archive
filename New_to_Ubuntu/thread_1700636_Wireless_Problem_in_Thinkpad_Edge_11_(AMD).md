---
title: "Wireless Problem in Thinkpad Edge 11 (AMD)"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-03-05
Hi,

I am currently having problem with wireless connection. It does not work at all. After browsing about 2 hours on the internet + 2 hours tweaking, still problematic..

There is a solution suggested to install realtek driver ([http://blog.maniac.nl/2010/11/06/thinkpad-edge-11-amd-nile-and-using-it-with-ubuntu-gnulinux/](http://blog.maniac.nl/2010/11/06/thinkpad-edge-11-amd-nile-and-using-it-with-ubuntu-gnulinux/)), but I was trapped at the stage of "make". Below is the issued command and the output:
 
> 

zinnirah@zinnirah-ThinkPad-Edge:~/Downloads/rtl8192ce_linux_2.6.0005.1116.2010$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/zinnirah/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192/r8192ce_pci.mod.o
  LD [M]  /home/zinnirah/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192/r8192ce_pci.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic-pae'
zinnirah@zinnirah-ThinkPad-Edge:~/Downloads/rtl8192ce_linux_2.6.0005.1116.2010$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic-pae'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic-pae'
zinnirah@zinnirah-ThinkPad-Edge:~/Downloads/rtl8192ce_linux_2.6.0005.1116.2010$ 

Thanks in advance..

By the way, I'm on ubuntu 10.10.

Sorry, it's just solved! Thanks.

-alfa-

---

### Post by cprofitt on 2011-03-08
can you paste in the results of an lspci for us so we can make sure what model of wireless card you have.

---

### Post by alfa_80 on 2011-03-08
It has been solved already, BTW. It's Realtek

Here is the output:
```

zinnirah@zinnirah:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)


```

---

### Post by steve7777777 on 2011-03-08
How did  you resolve the problem?

---

### Post by alfa_80 on 2011-03-08
> **steve7777777 said:**
> How did  you resolve the problem?

Actually it was my mistake not following directly what has been written in the link that I provided as in the first post. It should be "sudo su", I run as sudo make straighway instead! That's it :-)

---

