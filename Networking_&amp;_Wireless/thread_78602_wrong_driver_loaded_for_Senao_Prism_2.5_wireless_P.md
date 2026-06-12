---
title: "wrong driver loaded for Senao Prism 2.5 wireless PCMCIA card [Orinoco VS Hostap]"
date: 2005-10-18
forum: Networking &amp; Wireless
---

### Post by Azrael on 2005-10-18
I just posted a Bugzilla report here:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=18062]("http://bugzilla.ubuntu.com/show_bug.cgi?id=18062")

and would like to know if others are experiencing the same problem. Maybe someone even knows a solution? :-?

---

### Post by Azrael on 2005-10-19
Maybe I should recompile the breezy kernel and rip out all orinoco  bits?

[EDIT]

I have found at least two other persons, [http://ubuntuforums.org/showthread.php?t=66899]("http://ubuntuforums.org/showthread.php?t=66899") & [http://ubuntuforums.org/showthread.php?t=75402]("http://ubuntuforums.org/showthread.php?t=75402"), who have exactly the same problem with Ubuntu Breezy, and they also got ZERO reply.

How the hell is one supposed to get help with an issue like this? I'm not sure anyone of the Ubuntu developers is even looking at these bug reports.

---

### Post by Ubuntu_User on 2005-12-03
Hello, sorry to see you so fustrated...

I too have a Senao card, and was also feeling fustrated that I could not get kismet to work...

the simplest solution that I have found so far is adding hostap and hostap_pci (I have a miniPCI card) (hostap_cs if you have a pcmcia card) to /etc/modules

this however created two network interfaces eth0 and eth1, sorta silly, but eth1 does indeed work, and kismet is able to use it.

I'll see if I can't solve the two interfaces issue (I just now figured it out)

---

### Post by Ubuntu_User on 2005-12-03
Disregard last post

I read the bugzilla and saw the solution

---

### Post by noosphere on 2006-02-03
I dudes.
I´am a newbie in ubunto and i´ve the same problem with my pcmcia SENAO.
Anyone allready have the soluction?
Regards m8

Thanks for support

Noosphere

P.S - sorry for my poor english :rolleyes:

---

### Post by Lambert on 2006-02-03
If you can post the output of 

lspci -v

here I'll come back to this when I'm on my box. There should be a file in /etc/pcmcia that can be edited to tell what driver is bound to the device.

---

### Post by noosphere on 2006-02-03
Lambert,
Here my lspci -v
```
noosphere@ubuntu:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 11)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (r ev 11) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        Memory behind bridge: fd000000-fdffffff
        Prefetchable memory behind bridge: dbf00000-dfffffff

0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at efe0 [size=32]

0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at ef80 [size=32]

0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) US B UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1000 [size=32]

0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at 20000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 82) (prog-if 00 [Norm al decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fce00000-fcefffff

0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 0 2)
        Flags: bus master, medium devsel, latency 0

0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 I DE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at bfa0 [size=16]
        Memory at 20000400 (32-bit, non-prefetchable) [size=1K]

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4 -L/ICH4-M) AC'97 Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems: Unknown device 0203
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1400 [size=256]
        I/O ports at 1040 [size=64]
        Memory at 20000800 (32-bit, non-prefetchable) [size=512]
        Memory at 20000a00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem  Controller (rev 02) (prog-if 00 [Generic])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 11
        I/O ports at 1800 [size=256]
        I/O ports at 1080 [size=128]
        Capabilities: <available only to root>

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go ] (rev a3) (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device 0010
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 10
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at dc000000 (32-bit, prefetchable) [size=64M]
        Memory at dbf80000 (32-bit, prefetchable) [size=512K]
        Capabilities: <available only to root>

0000:02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000  Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at 20001000 (32-bit, non-prefetchable) [size=2K]
        Memory at 20004000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device 0002
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at ce00 [size=256]
        Memory at fcefff00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus  Bridge with ZV Support (rev 32)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at 20002000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=0
        Memory window 0: 20400000-207ff000 (prefetchable)
        Memory window 1: 20800000-20bff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus  Bridge with ZV Support (rev 32)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: bus master, slow devsel, latency 168, IRQ 11
        Memory at 20003000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=0
        Memory window 0: 20c00000-20fff000 (prefetchable)
        Memory window 1: 21000000-213ff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

0000:02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)
        Subsystem: Toshiba America Info Systems: Unknown device 0001
        Flags: medium devsel, IRQ 255
        Memory at 20000c00 (32-bit, non-prefetchable) [disabled] [size=512]
        Capabilities: <available only to root>

```

What is the file?
Here a screenshot ;)

[[IMG]http://img497.imageshack.us/img497/7407/13ir2.th.jpg[/IMG]](http://img497.imageshack.us/my.php?image=13ir2.jpg)

Regards

---

### Post by Lambert on 2006-02-03
1. I don't see your card in that output.

2. I'm not sure but think it's the config file. So here is what I suggest but first back up any file before editing so if this isn't the answer you can revert back to where we started.

With the card in type this command

```
cardctl ident
```

Hopefully your card's memory can be read and you'll get output.

Open up the config file and look for an entry with the same manfid, you'll see entries like this. 

```
card "dwl-g650 w/ Atheros ar5001 chipset"
  manfid 0x0271, 0x0012
  function: 6 (network)
  bind "ath_pci"
```

In this example this card is bound to the ath_pci module. 

We don't want to edit the config file, we want to edit the config.opts file

So copy over the entry from the config file to the config.opts file, and change the bind line to the driver you want. You may need to comment out the config file so it doesn't load two drivers. If it still loads the original driver add the original driver to /etc/hotplug/blacklist file to see if it helps.

Wrote this in a rush so if clarification is needed, just say so.

---

### Post by n0id on 2006-05-13
Hey Homies.  the wlan-g drivers are better suited for the prism chipset for things such as kismet.  If this doesn't help you, try to give a little more info on what is going wrong for you if you don't mind.  Hope that helps.

---

