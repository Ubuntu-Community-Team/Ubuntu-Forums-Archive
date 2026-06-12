---
title: "have a wireless card?"
date: 2014-02-09
forum: Networking &amp; Wireless
---

### Post by smiletasticplus on 2014-02-09
Hi, good folk!
Can anyone tell me if I have a wireless card on my computer?

Here are some outputs:
  	 	 	 	   ```
r@r-System-Product-Name:~$ lsusb 
 Bus 002 Device 004: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler / Genius NetScroll 120 
 Bus 002 Device 003: ID 0566:3002 Monterey International Corp.  
 Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 r@r-System-Product-Name:~$  

```

```
  	 	 	 	   
r@r-System-Product-Name:~$ lspci -v 
 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09) 
 	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard 
 	Flags: bus master, fast devsel, latency 0 
 	Capabilities: <access denied> 
  
 00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09) (prog-if 00 [Normal decode]) 
 	Flags: bus master, fast devsel, latency 0 
 	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0 
 	I/O behind bridge: 0000e000-0000efff 
 	Memory behind bridge: fa000000-fb0fffff 
 	Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff 
 	Capabilities: <access denied> 
 	Kernel driver in use: pcieport 
  
 00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04) 
 	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard 
 	Flags: bus master, fast devsel, latency 0, IRQ 47 
 	Memory at fb107000 (64-bit, non-prefetchable)  
 	Capabilities: <access denied> 
 	Kernel driver in use: mei_me 
  
 00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05) (prog-if 20 [EHCI]) 
 	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard 
 	Flags: bus master, medium devsel, latency 0, IRQ 23 
 	Memory at fb106000 (32-bit, non-prefetchable)  
 	Capabilities: <access denied> 
 	Kernel driver in use: ehci-pci 
  
 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 
 	Subsystem: ASUSTeK Computer Inc. Device 8445 
 	Flags: bus master, fast devsel, latency 0, IRQ 48 
 	Memory at fb100000 (64-bit, non-prefetchable)  
 	Capabilities: <access denied> 
 	Kernel driver in use: snd_hda_intel 
  
 00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5) (prog-if 00 [Normal decode]) 
 	Flags: bus master, fast devsel, latency 0 
 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0 
 	Capabilities: <access denied> 
 	Kernel driver in use: pcieport 
  
 00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5) (prog-if 00 [Normal decode]) 
 	Flags: bus master, fast devsel, latency 0 
 	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0 
 	Capabilities: <access denied> 
 	Kernel driver in use: pcieport 
  
 00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5) (prog-if 00 [Normal decode]) 
 	Flags: bus master, fast devsel, latency 0 
 	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0 
 	I/O behind bridge: 0000d000-0000dfff 
 	Prefetchable memory behind bridge: 00000000d2100000-00000000d21fffff 
 	Capabilities: <access denied> 
 	Kernel driver in use: pcieport 
  
 00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5) (prog-if 00 [Normal decode]) 
 	Flags: bus master, fast devsel, latency 0 
 	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0 
 	Capabilities: <access denied> 
 	Kernel driver in use: pcieport 
  
 00:1c.4 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5) (prog-if 01 [Subtractive decode]) 
 	Flags: bus master, fast devsel, latency 0 
 	Bus: primary=00, secondary=06, subordinate=07, sec-latency=0 
 	Capabilities: <access denied> 
  
 00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5) (prog-if 00 [Normal decode]) 
 	Flags: bus master, fast devsel, latency 0 
 	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0 
 	Capabilities: <access denied> 
 	Kernel driver in use: pcieport 
  
 00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05) (prog-if 20 [EHCI]) 
 	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard 
 	Flags: bus master, medium devsel, latency 0, IRQ 23 
 	Memory at fb105000 (32-bit, non-prefetchable)  
 	Capabilities: <access denied> 
 	Kernel driver in use: ehci-pci 
  
 00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05) 
 	Subsystem: ASUSTeK Computer Inc. Device 844d 
 	Flags: bus master, medium devsel, latency 0 
 	Capabilities: <access denied> 
 	Kernel driver in use: lpc_ich 
  
 00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05) (prog-if 8f [Master SecP SecO PriP PriO]) 
 	Subsystem: ASUSTeK Computer Inc. Device 844d 
 	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20 
 	I/O ports at f0d0  
 	I/O ports at f0c0  
 	I/O ports at f0b0  
 	I/O ports at f0a0  
 	I/O ports at f090  
 	I/O ports at f080  
 	Capabilities: <access denied> 
 	Kernel driver in use: ata_piix 
  
 00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05) 
 	Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard 
 	Flags: medium devsel, IRQ 10 
 	Memory at fb104000 (64-bit, non-prefetchable)  
 	I/O ports at f000  
  
 00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05) (prog-if 85 [Master SecO PriO]) 
 	Subsystem: ASUSTeK Computer Inc. Device 844d 
 	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20 
 	I/O ports at f070  
 	I/O ports at f060  
 	I/O ports at f050  
 	I/O ports at f040  
 	I/O ports at f030  
 	I/O ports at f020  
 	Capabilities: <access denied> 
 	Kernel driver in use: ata_piix 
  
 01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 440] (rev a1) (prog-if 00 [VGA controller]) 
 	Subsystem: Gigabyte Technology Co., Ltd Device 3518 
 	Flags: bus master, fast devsel, latency 0, IRQ 16 
 	Memory at fa000000 (32-bit, non-prefetchable)  
 	Memory at c0000000 (64-bit, prefetchable)  
 	Memory at d0000000 (64-bit, prefetchable)  
 	I/O ports at e000  
 	Expansion ROM at fb000000 [disabled]  
 	Capabilities: <access denied> 
 	Kernel driver in use: nouveau 
 [SIZE=5] 
 [SIZE=5]01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1) 
 [SIZE=5]	Subsystem: Gigabyte Technology Co., Ltd Device 3518 
 [SIZE=5]	Flags: bus master, fast devsel, latency 0, IRQ 17 
 [SIZE=5]	Memory at fb080000 (32-bit, non-prefetchable) [size=16K] 
 [SIZE=5]	Capabilities: <access denied> 
 [SIZE=5]	Kernel driver in use: snd_hda_intel 
 [SIZE=5] 
 [SIZE=5]04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 06) 
 [SIZE=5]	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards 
 [SIZE=5]	Flags: bus master, fast devsel, latency 0, IRQ 46 
 [SIZE=5]	I/O ports at d000 [size=256] 
 [SIZE=5]	Memory at d2104000 (64-bit, prefetchable) [size=4K] 
 [SIZE=5]	Memory at d2100000 (64-bit, prefetchable) [size=16K] 
 [SIZE=5]	Capabilities: <access denied> 
 [SIZE=5]	Kernel driver in use: r8169 
 [SIZE=5] 
 [SIZE=5]06:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01) (prog-if 01 [Subtractive decode]) 
 [SIZE=5]	Flags: bus master, fast devsel, latency 0 
 [SIZE=5]	Bus: primary=06, secondary=07, subordinate=07, sec-latency=32 
 [SIZE=5]	Capabilities: <access denied> 
 [SIZE=5] 
 [SIZE=5]r@r-System-Product-Name:~$  
```
 

  Thank you in advance.

---

### Post by prasys on 2014-02-09
Your lspci output shows only 1 Ethernet Controller , which is your LAN.

As for your USB device , I am not sure what is this device. Is your WiFi adapter is an external adapter by any chance ?

```
 
 Bus 002 Device 003: ID 0566:3002 Monterey International Corp.  

```

---

### Post by varunendra on 2014-02-09
Nope, no Wireless card/adapter as per outputs. The 0566:3002 device is some HID device, most probably a USB mouse, as listed in an example on an [archlinux wiki]("https://wiki.archlinux.org/index.php/All_Mouse_Buttons_Working") page :
```
N: Name="Logitech USB Gaming Mouse"
H: Handlers=mouse0 event0 ts0 
N: Name="HID **0566:3002**"
H: Handlers=kbd event1
```

If doubtful, the output of "usb-devices" command will confirm what it is. More precisely -
```
usb-devices | grep -iA8 -B2 0566
```

---

### Post by praseodym on 2014-02-09
Please check also:
```

pccardctl info
```

---

### Post by smiletasticplus on 2014-02-09
Thank you. It seems I don't have a wi fi card. I'll check it today (it's a school computer) in about 14 hours.

[COLOR=#000000]

[/COLOR]

---

### Post by smiletasticplus on 2014-02-10
Here are the outputs. Can I be 100% sure that I don't have a wi fi card installed?
r@r-System-Product-Name:~$ [COLOR=#ff0000]usb-devices| grep -iA8 -B2 0566[/COLOR] 
r@r-System-Product-Name:~$
 

r@r-System-Product-Name:~$ [COLOR=#008000]pccardctlinfo[/COLOR] 
r@r-System-Product-Name:~$

---

### Post by praseodym on 2014-02-10
Check

```
lspci

```
without filter.

---

### Post by smiletasticplus on 2014-02-10
Thank you, people.

---

