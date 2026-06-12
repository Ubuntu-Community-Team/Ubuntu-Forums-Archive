---
title: "Can't enable desktop effects"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-01-20
Tried searching the forums but no answer to my specific problem. I have a Toshiba Satellite Pro running Maverick with Nvidia Nv17 GeForce4 420 Go card, but additional driver search shows no proprietary drivers in use on my system (System-Administration-Additional Drivers). Is the card just too old to be recognized or do I have a more serious problem ? Thanks in advance for the help.

---

### Post by amsterdamharu on 2011-01-20
Just to be sure could you run the following command and post the output here?

```
sudo lspci -k
```

To execute the command you can press alt + F2, type gnome-terminal and click run. Then copy the command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by jerrynewt on 2011-01-21
Output from lspci -k

jen@jennifer1:~$ sudo lspci -k
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: uhci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
	Kernel modules: shpchp
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: ata_piix
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel modules: snd-intel8x0m
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb, rivafb
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
	Subsystem: Toshiba America Info Systems EtherExpress PRO/100 VE
	Kernel driver in use: e100
	Kernel modules: e100
02:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
	Subsystem: Lucent Technologies Device ab01
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems Device 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device 0001

---

### Post by sandyd on 2011-01-21
> **jerrynewt said:**
> Tried searching the forums but no answer to my specific problem. I have a Toshiba Satellite Pro running Maverick with Nvidia Nv17 GeForce4 420 Go card, but additional driver search shows no proprietary drivers in use on my system (System-Administration-Additional Drivers). Is the card just too old to be recognized or do I have a more serious problem ? Thanks in advance for the help.
[http://www.nvidia.com/object/linux-display-amd64-96.43.19-driver.html](http://www.nvidia.com/object/linux-display-amd64-96.43.19-driver.html)

Youll have to reinstall it each time you update to a new kernel.

---

