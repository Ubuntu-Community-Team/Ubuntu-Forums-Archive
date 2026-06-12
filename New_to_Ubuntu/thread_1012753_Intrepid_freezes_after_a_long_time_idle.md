---
title: "Intrepid freezes after a long time idle"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by thimad on 2008-12-16
Hello!

I have installed Ubuntu Intrepid and at least once a day I need to "hard power off" my notebook. Older versions of Ubuntu were blacklisting my video card (lspci bellow) and this time I was really happy. Was.

In 5 minutes, my computer shows screensaver.
In 10 minutes, it turns off my LCD screen.

If I leave it for a long time, when I move the mouse, sometimes it comes back perfectly, but at least once a day it will show the wallpaper and freeze (sometimes the mouse still moves, but nothing else appears).

CTRL-ALT-BACKSPACE does not work.
CTRL-ALT-F1 doesn't either.

It also happend once when I was watching a video on VLC Player in fullscreen. When I double-clicked the video to leave fullscreen mode, I just got my wallpaper (mouse moving) but I had to "hard power off".

My notebook: SONY VAIO VGN-FZ240E

Softwares i usually run: skype, azureus, pidgin, firefox, compiz, cairo-dock.

Memory usually used: 30% (600 MB of 2 GB)

My swap partition (4 GB) is never used.

Please, help me... I have uninstalled windows and I really want to keep using Linux, with Ubuntu.

Thank you,
Thiago.

lspci:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by DaGrimReefah on 2008-12-19
This sounds like a ACPI problem. You may have to disable ACPI.

---

### Post by thimad on 2008-12-28
Thanks! 

I will try and post the results.

---

### Post by thimad on 2008-12-29
I can't disable ACPI because my notebook stops booting!

I edited /boot/grub/menu.lst...

I changed this:

kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b552d2a4-0f40-4847-977d-1ed0165c9de7 ro locale=pt_BR quiet splash

To this (added "acpi=off" before "locale"):

kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=b552d2a4-0f40-4847-977d-1ed0165c9de7 ro acpi=off locale=pt_BR quiet splash

Then it didn't boot, saying something about getting a new BIOS version.

---

### Post by thimad on 2008-12-31
acpi=off (does not boot)

acpi=noirq (boots, but the problem persists)

pci=noacpi (boots normally, but the problems persists)

Actually, the computer never really FREEZES... I can see my wallpaper and move the mouse cursor, but nothing else.

I appreciate any help, because i'm afraid of harming my hard drive with the so often hard-power-off (every day).

Thanks.

---

### Post by zero244 on 2008-12-31
I use apic=off except I put it at the very end of the kernel line that your using.
This has worked for me for every version of Ubuntu since Edgy.
With Edgy I also included:
lnoapic
With Hardy just apic=no seems to work.

It does sound like a apic problem. If you can disable apic on boot up, it will likely solve your problem.

Another possiblity would be a plugin in Compiz if your running that.
Try resetting Compiz to the default settings.
If I run compiz full bore.....one of the pluggins will eventually freeze me. Im not sure which one yet.
The default compiz settings plus Scale seem to run stable.
Good luck

---

