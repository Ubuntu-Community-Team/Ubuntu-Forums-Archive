---
title: "Installation does not detect my network. Possible I/O range conflicts"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by godrox on 2007-01-04
I originally posted this [here]("http://ubuntuforums.org/showthread.php?p=1966905"), but think now that it might be more appropriate under the networking forum.

I have an old computer someone gave me that was running Windows 98 (850 MHz, 128 MB), which I promptly removed to install Ubuntu. Because of it's low memory, I'm using the text installation from the alternate 6.10 CD, but after trying to detect network devices, it stops and says, "Configure the network - No network interfaces found." I can continue with the installation, but of course there's no network connection after Ubuntu finishes installing either. (The Xubuntu alternate installation gives the same error message.)

I've tried three different PCI network cards (Belkin, D-link, and Network Everywhere) all with the same results. I've tried each card in different PCI slots, as well. Both the NIC and the router light up appropriately, but for some reason the Ubuntu still misses it.

Now, for what it's worth, I don't know much about IRQs, but I noticed during the BIOS boot screen that both the network adapter and the VGA were both set at IRQ 11. I tried different IRQ settings in the BIOS (not really knowing what I was doing), but it made no difference.

I installed Ubuntu with the D-link wired NIC and then ran lspci. It returned the following:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] System Controller (rev 25)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-751 [Irongate] AGP Bridge (rev 01)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ISA (rev 01)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-756 [Viper] IDE (rev 07)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-756 [Viper] ACPI (rev 03)
00:07.4 USB Controller: Advanced Micro Devices [AMD] AMD-756 [Viper] USB (rev 06)
00:0a.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Rage XL AGP 2X (rev 65)
```

I did more searching trying to find some leads and came across this when I do dmesg:

```
[17179595.580000] 8139too Fast Ethernet driver 0.9.27
[17179595.580000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179595.580000] PCI: setting IRQ 10 as level-triggered
[17179595.580000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179595.580000] PCI: Unable to reserve I/O region #1:100@de00 for device 0000:00:0a.0
[17179595.580000] Trying to free nonexistent resource <0000de00-0000deff>
[17179595.580000] Trying to free nonexistent resource <efffff00-efffffff>
[17179595.580000] 8139too: probe of 0000:00:0a.0 failed with error -16
```

Apparently that's bad. I ran "cat /proc/ioports" which returned the following:

```
0000-001f : dma1
0020-0021 : pic1
0040-0043 : timer0
0050-0053 : timer1
0060-006f : keyboard
0070-0077 : rtc
0080-008f : dma page reg
00a0-00a1 : pic2
00c0-00df : dma2
00f0-00ff : fpu
0170-0177 : ide1
01f0-01f7 : ide0
02f8-02ff : serial
0376-0376 : ide1
0378-037a : parport0
037b-037f : parport0
03c0-03df : vga+
03f6-03f6 : ide0
03f8-03ff : serial
0778-077a : parport0
0cf8-0cff : PCI conf1
5000-5003 : ACPI PM1a_EVT_BLK
5004-5005 : ACPI PM1a_CNT_BLK
5008-500b : ACPI PM_TMR
5010-5015 : ACPI CPU throttle
5020-5023 : ACPI GPE0_BLK
50e0-50ef : amd756_smbus
b000-cfff : PCI Bus #01
  c800-c8ff : 0000:01:05.0
dc00-dc03 : 0000:00:00.0
  dc00-dc00 : ACPI PM2_CNT_BLK
de00-deff : 0000:00:0a.0
  de00-de03 : motherboard
    de00-de03 : pnp 00:01
f000-f00f : 0000:00:07.1
  f000-f007 : ide0
  f008-f00f : ide1
```

The latest BIOS version was already loaded, but I re-flashed it anyway just to make sure. The ioports list remained the same.

I looked around in the BIOS for something about I/O settings, but didn't see anything. Only IRQ and PnP/PCI settings. Nothing I saw looked relevant, but I still tried making some changes with no reportable results.

Any ideas on how I can get the network working? Thanks for your help and your time! I appreciate it.

---

### Post by spd106 on 2007-01-04
lloyd_b seems to know far more than I. 

All I can suggest is trying a different distro's live cd such as Knoppix or DS Linux.

---

### Post by godrox on 2007-01-04
So it's not hardware related? It's software related? I figured I'd probably have these same issues with any OS I tried, but I guess I can try something else and see what happens.

---

