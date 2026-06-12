---
title: "How to fix sound"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by lil_kid1333 on 2009-03-20
Well after doing this

[http://ubuntuforums.org/showthread.php?t=1099265](http://ubuntuforums.org/showthread.php?t=1099265)

The guy who was helping me by mistake mispelled the wrong driver and I installed it and I guess it mest up my audio cause after that I started getting this message

Sound server fatal error:
AudioSubSystem::handleIO: write failed
len = -1, can_write = 4096, errno = 111 (Connection refused)
This might be a sound hardware/driver specific problem (see aRts FAQ)

I get no sound only when I got to hardware testing I can hear the sound but other then that I can't hear nothing and Totem music player always crashes when I open a song and VLC will play but no sound please help I really need my sound back

---

### Post by arapa on 2009-03-20
not sure if the two are related but couldn't you remove the incorrect driver by typing:
```

sudo apt-get --purge remove rt2860-linux-sta
```

reboot, check if you have sound, then install the correct driver?

---

### Post by lil_kid1333 on 2009-03-20
> **arapa said:**
> not sure if the two are related but couldn't you remove the incorrect driver by typing:
```

sudo apt-get --purge remove rt2860-linux-sta
```

reboot, check if you have sound, then install the correct driver?

which driver?? install which driver??

---

### Post by UnknownFear on 2009-03-20
> **lil_kid1333 said:**
> which driver?? install which driver??

From looking at the thread you posted above, you have to update and upgrade the system, than run the correct driver.

> 1. Add additional repo:
```

deb http://ppa.launchpad.net/mieszkoslusarczyk/ppa/ubuntu intrepid main
```
See here if uncertain how: [https://help.ubuntu.com/8.04/add-app...es-adding.html](https://help.ubuntu.com/8.04/add-app...es-adding.html)

2. Update system:
```

sudo apt-get update
sudo apt-get upgrade

```
3. Install driver:
```

sudo apt-get install rt2860-linux-sta

```

It will complain about it being an unverified source. If you trust the package maintainer, just agree. I would suggest removing the repo afterwards, to ensure you don't install anything else from there with future updates.

Hopefully a reboot will then work.

Try that.

---

### Post by lil_kid1333 on 2009-03-20
I think that's the USB driver... After installing the wrong one I installed the correct one...

or is it a different one the one you telling me to download?

---

### Post by lil_kid1333 on 2009-03-20
the driver 2860 was the incorrect driver the correct one was the 2870 and I installed it and now I uninstalled the 2860 one

but I still don't have sound :( and anyways that driver was for my USB wifi...

idk if this will help but here

leo@chick3ns-pc:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
	Subsystem: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: b0000000-cfffffff
	Prefetchable memory behind bridge: 30000000-300fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
	Subsystem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d0800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at e300 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at e000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at e100 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at e200 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d0804000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: d0000000-d07fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
	Subsystem: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f000 [size=16]
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at e400 [size=8]
	I/O ports at e500 [size=4]
	I/O ports at e600 [size=8]
	I/O ports at e700 [size=4]
	I/O ports at e800 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 7046
	Flags: medium devsel, IRQ 11
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
	Subsystem: nVidia Corporation Device 0245
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at c1000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at 30000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

02:02.0 Communication controller: Intel Corporation 536EP Data Fax Modem
	Subsystem: Creatix Polymedia GmbH Device 1040
	Flags: bus master, medium devsel, latency 32, IRQ 10
	Memory at d0000000 (32-bit, non-prefetchable) [size=4M]
	Capabilities: <access denied>

02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 046d
	Flags: bus master, medium devsel, latency 32, IRQ 19
	Memory at d0400000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at d000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

02:06.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] (rev 8b)
	Subsystem: Micro-Star International Co., Ltd. Device 046c
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d100 [size=256]
	Memory at d0401000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

btw, when I restarted Ubuntu I could hear the sound and got happy but tried opening a song and it crashes :s and tried VLC and still no sound... man i'm getting aggravated without music >.<

---

### Post by UnknownFear on 2009-03-20
> **lil_kid1333 said:**
> the driver 2860 was the incorrect driver the correct one was the 2870 and I installed it and now I uninstalled the 2860 one

Sorry, my mistake. So you now installed the correct driver, yet you still don't have any sound? Hmm... You could try disabling the onboard audio chipset in the BIOS screen, this fixed my sound problem, but it may not work for you. To do this, restart your computer and as the computer boots up, you should see something like "Press F2 to enter setup" or press the DELETE key before boot up. If you do it correctly, you should be in the BIOS. In this screen, look for Audio and it should be enabled. Simply disable this, exit and save settings to restart the computer, than login to Ubuntu. This fixed my sound solution, but it may not for you. If it doesn't, I'd advise you to re-enable the audio chipset.

---

### Post by lil_kid1333 on 2009-03-20
well ill try but this is what happened...

The dude that was helping me mispelled the USB drive and spelled 2860 instead of 2870. So I installed the 2860 drive and then he told me he's mistake he meant 2870 so I installed the 2870 and after that is when I started getting the weird message about sound and then I noticed I didn't have sound other then when Ubuntu starts up...

And now I took off the 2860 driver but I guess I have to install the driver for my audio or something cause I don't get sound >.<

I'm going crazy... I need help :'(

---

### Post by lil_kid1333 on 2009-03-20
I can't even access my BIOS page :s I know it's F2 but for some reason it doesn't work...

I hold the button and nothing I tried different keys and nothing damn computer is going to hell :S :'(

---

### Post by lil_kid1333 on 2009-03-20
I don't mean to bug or anything but I REALLY need the help to get audio for my online class...

The teacher puts these lessons on flash videos and well obviously I can't learn with no audio...

Sorry if I disturb... :(

---

### Post by Art3mis on 2009-03-20
My soundcard is regocnized but there is still no sound pls help

---

### Post by lil_kid1333 on 2009-03-21
any help guys...?

on GNOME ALSA Mixer it says C-Media CMI9880

im guessing that's my audio driver that I need...

---

