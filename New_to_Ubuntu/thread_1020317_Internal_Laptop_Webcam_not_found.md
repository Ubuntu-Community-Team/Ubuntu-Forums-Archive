---
title: "Internal Laptop Webcam not found"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by MasterShihoChief on 2008-12-24
I have an Alienware m17x laptop. I have been trying for awhile to get the webcam operational, but it doesnt see anything at all. I have tried googleing help and I have gotten nowhere at all. I did have the following information to help, because honestly i dont know the brand of the webcam or anything, i thought ricoh or syntek, but im not sure. I called Alienware and its funny their techs have no idea either lol.

For:
```
lspci -v
```
I got:
```

mastershihochief@CortanaMobile:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=04, sec-latency=0
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: e3000000-ef2fffff
	Prefetchable memory behind bridge: 00000000a0e00000-00000000e0dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e080 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at e000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at effff400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d3
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at efff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: ef300000-ef3fffff
	Prefetchable memory behind bridge: 00000000e0e00000-00000000e0efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	Memory behind bridge: ef400000-ef4fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=08, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: ef500000-efcfffff
	Prefetchable memory behind bridge: 00000000e0f00000-00000000e2efffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: efd00000-efdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at dc00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at d880 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at d800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at effff000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=32
	Memory behind bridge: efe00000-efefffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 215
	I/O ports at ec00 [size=8]
	I/O ports at e880 [size=4]
	I/O ports at e800 [size=8]
	I/O ports at e480 [size=4]
	I/O ports at e400 [size=32]
	Memory at effff800 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

01:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
	Flags: bus master, fast devsel, latency 0
	Memory at ef2fc000 (32-bit, non-prefetchable) [size=16K]
	Bus: primary=01, secondary=02, subordinate=04, sec-latency=0
	I/O behind bridge: 00008000-00009fff
	Memory behind bridge: e3000000-ef1fffff
	Prefetchable memory behind bridge: 00000000a0e00000-00000000e0dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:00.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00008000-00008fff
	Memory behind bridge: e3000000-e90fffff
	Prefetchable memory behind bridge: 00000000a0e00000-00000000c0dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

02:01.0 PCI bridge: nVidia Corporation Device 01b3 (rev a3)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: e9100000-ef1fffff
	Prefetchable memory behind bridge: 00000000c0e00000-00000000e0dfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 1515
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at e6000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 8c00 [size=128]
	[virtual] Expansion ROM at e90e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

04:00.0 3D controller: nVidia Corporation GeForce 8600M GT (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 1515
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at ee000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at ec000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9c00 [size=128]
	[virtual] Expansion ROM at ef1e0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 16d5
	Flags: bus master, fast devsel, latency 0, IRQ 216
	I/O ports at a800 [size=256]
	Memory at ef3ff000 (64-bit, non-prefetchable) [size=4K]
	Memory at e0ef0000 (64-bit, prefetchable) [size=64K]
	Expansion ROM at ef3c0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
	Subsystem: Intel Corporation Device 1100
	Flags: bus master, fast devsel, latency 0, IRQ 214
	Memory at ef4fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

0a:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01)
	Subsystem: ASUSTeK Computer Inc. Device 16d8
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at cc00 [size=8]
	I/O ports at c880 [size=4]
	I/O ports at c800 [size=8]
	I/O ports at c480 [size=4]
	I/O ports at c400 [size=16]
	Memory at efdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

0c:01.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 02) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 64, IRQ 16
	Memory at efeff800 (32-bit, non-prefetchable) [size=2K]
	Memory at efef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

0c:03.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at efeff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0c:03.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: bus master, medium devsel, latency 0, IRQ 6
	Memory at efeff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel modules: ricoh_mmc

0c:03.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: medium devsel, IRQ 6
	Memory at efefec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

0c:03.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
	Subsystem: ASUSTeK Computer Inc. Device 16d7
	Flags: medium devsel, IRQ 6
	Memory at efefe800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>

mastershihochief@CortanaMobile:~$ 

```

For a: 
```
lsusb
```

I got:
```

mastershihochief@CortanaMobile:~$ lsusb
Bus 007 Device 040: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 007 Device 039: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 007 Device 038: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 007 Device 037: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 174f:8a51 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 187c:0511  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mastershihochief@CortanaMobile:~$ 

```

Any and all help appreciated, thanks.

---

### Post by halitech on 2008-12-24
I don't see anything on their site about the laptop having a built in webcam. Is it a built in webcam or an external?

I'm almost thinking its this:
[color=red]Bus 003 Device 002: ID 174f:8a51 Syntek[/color]

if it is, there's not much info out there about it other then people having trouble with it.

---

### Post by MasterShihoChief on 2008-12-24
If you look up information on the Alienware M17x you will see the webcam centered at the top of the screen, with two internal microphones (one on both sides of the webcam). Its definitely internal. If its a syntek webcam, what do I need to do to get it working?

---

### Post by halitech on 2008-12-24
I'm just going by the specs they have listed here [http://www.alienware.com/products/area-51-m17x-notebook.aspx](http://www.alienware.com/products/area-51-m17x-notebook.aspx)

if its a syntek then I don't know if it will work

---

### Post by albinootje on 2008-12-24
> **MasterShihoChief said:**
> 
```
lsusb
```

I got:
```

mastershihochief@CortanaMobile:~$ lsusb
Bus 007 Device 040: ID 13fe:1d00 Kingston Technology Company Inc. DataTraveler 2.0 1GB/4GB Flash Drive / Patriot Xporter 4GB Flash Drive
Bus 007 Device 039: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 007 Device 038: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 007 Device 037: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 174f:8a51 Syntek 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 187c:0511  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
mastershihochief@CortanaMobile:~$ 

```

You have one unknown line there in the lsusb output.
Can you run :
```

sudo update-usbids

```
And see whether that makes a difference ?

---

### Post by MasterShihoChief on 2008-12-24
ya i was wondering about that unknown. I ran that command and then ran lsusb again and nothing changed. I am pretty sure its that syntek one though. I am going to try and call Alienware again and press them for information

---

### Post by MasterShihoChief on 2008-12-24
lol alienware is just fail, right off the bat they threaten me with voiding my warranty T_T. Anyways they say its Alienware brand webcam, which is probobly BS since Alienware doesnt make anything themselves, or if they do its crap. All the guy told me is the program to use is quickcam express or something, which is the windows program. No help from any of their techs just trying to figure out what brand it really is T_T. I doubt anything can be done, but if anyone has any ideas let me know, otherwise there is probobly nothing i can do.

---

### Post by albinootje on 2008-12-24
> **MasterShihoChief said:**
> lol alienware is just fail, right off the bat they threaten me with voiding my warranty T_T. Anyways they say its Alienware brand webcam, which is probobly BS since Alienware doesnt make anything themselves, or if they do its crap. All the guy told me is the program to use is quickcam express or something, which is the windows program. No help from any of their techs just trying to figure out what brand it really is T_T. I doubt anything can be done, but if anyone has any ideas let me know, otherwise there is probobly nothing i can do.

This is maybe not for your specific webcam, but perhaps still interesting to read, esp. that last line :
[http://syntekdriver.sourceforge.net/index.php?mode=faq](http://syntekdriver.sourceforge.net/index.php?mode=faq)
> 
    *  Why is this project even here ?
      Because the hardware manufacturers , Syntek, D-Max and Asus refuse to support Linux.


---

### Post by MasterShihoChief on 2008-12-24
I think i installed the driver but i dont think it worked. I followed the README which said to 

```
6. Test experimental

To build and load the driver, follow the steps :

$ make -f Makefile.standalone clean
$ make -f Makefile.standalone
$ modprobe videodev
$ insmod stk11xx.ko

To test the driver with the V4L v1 API (map methode) :

$ camorama -D --width=640 --height=480 

To test the driver with the V4L v1 API (read methode) :

$ camorama -D -R --width=640 --height=480 

To test the driver with the V4L v2 :

$ xawtv

```

i did this and it made a bunch of stuff in the folder. The make standalone made the files, then i ran the modprobe and insmod commands and it didnt do anything but go to the next line but i assumed it did something since it didnt give me an error. I then tried to test the driver and webcam using the last 3 commands listed and it still says it cant find the webcam, so i guess i wait until they get the driver working, since it doesnt work for me. Thanks for the help, much appreciated.

---

### Post by albinootje on 2008-12-24
> **MasterShihoChief said:**
> 
```

$ modprobe videodev
$ insmod stk11xx.ko

```

i did this and it made a bunch of stuff in the folder. The make standalone made the files, then i ran the modprobe and insmod commands and it didnt do anything but go to the next line but i assumed it did something since it didnt give me an error. I then tried to test the driver and webcam using the last 3 commands listed and it still says it cant find the webcam, so i guess i wait until they get the driver working, since it doesnt work for me.

Okay. I assume that you used :
```

sudo modprobe videodev
sudo insmod stk11xx.ko

```
I read that the program "cheese" in the Ubuntu repositories is nice for testing a webcam. You could try that.
And after running those 2 commands, you can try for yourself :
```

dmesg

```
to see whether something interesting happened in the last 5 lines of that output.

---

### Post by MasterShihoChief on 2008-12-24
i indeed use sudo for all those commands and ran cheese and it says no camera found
I ran the dmesg and got the following output that was very long but i just copy pasted the last 10 lines

```

[392996.876879] FAT: Directory bread(block 16390) failed
[392996.876893] FAT: Directory bread(block 16391) failed
[392996.954354] scsi 18:0:0:0: rejecting I/O to dead device
[393004.475220] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[393004.728070] usb 7-2: new high speed USB device using ehci_hcd and address 41
[393004.868770] usb 7-2: configuration #1 chosen from 3 choices
[423596.187882] usb 7-2: USB disconnect, address 41
[437301.728560] stk11xx: Syntek USB2.0 webcam driver startup
[437301.728660] usbcore: registered new interface driver usb_stk11xx_driver
[437301.728668] stk11xx: v1.3.1 : Syntek USB Video Camera
mastershihochief@CortanaMobile:~/Builds/stk11xx-1.4.0$ 




```

---

### Post by MasterShihoChief on 2008-12-26
bump

---

### Post by MasterShihoChief on 2008-12-27
bump

---

### Post by albinootje on 2008-12-27
> **MasterShihoChief said:**
> i indeed use sudo for all those commands and ran cheese and it says no camera found
I ran the dmesg and got the following output that was very long but i just copy pasted the last 10 lines

```

[392996.876879] FAT: Directory bread(block 16390) failed
[392996.876893] FAT: Directory bread(block 16391) failed
[392996.954354] scsi 18:0:0:0: rejecting I/O to dead device
[393004.475220] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[393004.728070] usb 7-2: new high speed USB device using ehci_hcd and address 41
[393004.868770] usb 7-2: configuration #1 chosen from 3 choices
[423596.187882] usb 7-2: USB disconnect, address 41
[437301.728560] stk11xx: Syntek USB2.0 webcam driver startup
[437301.728660] usbcore: registered new interface driver usb_stk11xx_driver
[437301.728668] stk11xx: v1.3.1 : Syntek USB Video Camera
mastershihochief@CortanaMobile:~/Builds/stk11xx-1.4.0$ 




```

Why not email the authors of the Syntek webcam driver, and ask whether your webcam is already suppose to be supported or not, and how you can help them to improve the code to have your webcam running, in case it's not yet supported.

---

