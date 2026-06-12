---
title: "Drivers plsss"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by vishwasmeshram on 2010-06-11
hi.......
i have install newly ubuntu 10.4 on my SONY VAIO LAPPY MODEL IS "VGN-CR363"
i tried to find out the hardware drivers but cant get . I need drivers for my Motion Eye webcam and also for Fingerprint reader . 
Anybody can help.............

---

### Post by pizza-is-good on 2010-06-11
have you checked System >> Administration >> Hardware Drivers ??

If they exist, they are likely there. If they are not there, and they exist, you'll probably have a hard time finding them..

---

### Post by Chesamo on 2010-06-12
Have you checked and seen if your webcam model is listed here?
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Also, as for the fingerprint reader, I doubt you'll get that working under Ubuntu. But here's something you should look at:
[http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html](http://www.ubuntu-unleashed.com/2008/04/get-your-fingerprint-reader-to-work-in.html)

---

### Post by vishwasmeshram on 2010-06-14
hi...........
last week i install Ubuntu 10.4 in my lappy Sony Vaio model "VGN CR363".....
i have searched driver for it but didnt get....
i need drivers for inbuilt Motion Eye webcam and inbuilt Fingerprint reader and ATI Radeon Graphics card......as well as appication for it...............
plz help

---

### Post by Chesamo on 2010-06-14
Please don't multipost.

[http://ubuntuforums.org/showthread.php?t=1507690](http://ubuntuforums.org/showthread.php?t=1507690)

---

### Post by no2498 on 2010-06-14
try this for the webcam


in/on 910 and up cheese wecam booth is/shoule be loaded

look for it in sound & video try the cam in it first

if it does not come on

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1


hope this helps

---

### Post by vishwasmeshram on 2010-06-14
sorry for the multipost it will never happen again...
as you said i have done 
i got sound when i test for audio
but when i test for video it show this
"Video for Linux (v4l): Device "/dev/video0" does not exist"
and "Video for Linux 2 (v4l2): Cannot identify device '/dev/video0'."

---

### Post by Mark Phelps on 2010-06-15
> **vishwasmeshram said:**
> ...and ATI Radeon Graphics card......as well as appication for it...............
plz help

According to the Google search I just did, that model comes with onboard Intel graphics, not ATI.  Intel drivers are installed by default.

So, how do you know that you have an ATI card? Have you done an "lspci" command to verify that?

Also, if by "application for it", you mean the Catalyst Control Center that is used for ATI cards, that gets installed as a byproduct of installing the fglrx drivers.  But, until you provide us the make and model of your video adapter, we won't know if there are Catalyst drivers for your card/chip.

---

### Post by vishwasmeshram on 2010-06-16
> **Mark Phelps said:**
> According to the Google search I just did, that model comes with onboard Intel graphics, not ATI.  Intel drivers are installed by default.

So, how do you know that you have an ATI card? Have you done an "lspci" command to verify that?

Also, if by "application for it", you mean the Catalyst Control Center that is used for ATI cards, that gets installed as a byproduct of installing the fglrx drivers.  But, until you provide us the make and model of your video adapter, we won't know if there are Catalyst drivers for your card/chip.


for your knowledge i apply this command on my terminal and i got  this........... pls go through is

rocker@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory  Controller Hub (rev 0c)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI  Express Root Port (rev 0c)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: fc000000-fc0fffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #4 (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1800 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #5 (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1820 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI  Controller #2 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at fc404000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio  Controller (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: d6000000-d7ffffff
    Prefetchable memory behind bridge: 00000000de000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: fa000000-fbffffff
    Prefetchable memory behind bridge: 00000000f8000000-00000000f9ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express  Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=07, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: d2000000-d3ffffff
    Prefetchable memory behind bridge: 00000000da000000-00000000dbffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #1 (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #2 (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI  Controller #3 (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI  Controller #1 (rev 03) (prog-if 20)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fc404400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)  (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=0c, sec-latency=56
    I/O behind bridge: 00006000-00006fff
    Memory behind bridge: fc100000-fc1fffff
    Prefetchable memory behind bridge: 0000000080000000-0000000083ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface  Controller (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E)  SATA IDE Controller (rev 03) (prog-if 80 [Master])
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 18e0 [size=16]
    I/O ports at 18d0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller  (rev 03)
    Subsystem: Sony Corporation Device 9015
    Flags: medium devsel, IRQ 10
    Memory at 84000000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c00 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller: [SIZE=4][COLOR=Red]ATI  Technologies Inc Mobility Radeon X2300[/COLOR][/SIZE]
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f0000000 (32-bit, prefetchable) [size=128M]
    I/O ports at 2000 [size=256]
    Memory at fc000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at fc020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon
    Kernel modules: radeon

02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or  AGN [Kedron] Network Connection (rev 61)
    Subsystem: Intel Corporation Device 1100
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at d6000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, fast devsel, latency 0, IRQ 28
    I/O ports at 5000 [size=256]
    Memory at d2000000 (64-bit, non-prefetchable) [size=4K]
    [virtual] Expansion ROM at da000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 168, IRQ 20
    Memory at fc100000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
    Memory window 0: 80000000-83fff000 (prefetchable)
    Memory window 1: 88000000-8bfff000
    I/O window 0: 00006000-000060ff
    I/O window 1: 00006400-000064ff
    16-bit legacy interface ports at 0001
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket

08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant  IEEE 1394 Host Controller (prog-if 10)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at fc102000 (32-bit, non-prefetchable) [size=2K]
    Memory at fc104000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia  Card Reader (SD/MMC/MS/MS PRO/xD)
    Subsystem: Sony Corporation Device 9015
    Flags: bus master, medium devsel, latency 57, IRQ 20
    Memory at fc101000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1

---

### Post by clhsharky on 2010-06-16
vishwasmeshram

Lucid OSS driver default radeon for ATI cards is the correct driver
for your
> ATI Technologies Inc Mobility Radeon X2300
R515 chip.
Is already installed.

Sharky

---

### Post by philinux on 2010-06-16
Threads merged.

---

### Post by vishwasmeshram on 2010-06-16
if the driver is installed where can i find application Ctalyst Control Center?????
anyone suggest?

---

### Post by Mark Phelps on 2010-06-17
IF you're using the default drivers, CCC did NOT get installed -- which is why you won't see it.  To confirm that the fglrx drivers are not installed, open a terminal and enter "fglrxinfo".  That will provide some details about the fglrx driver.

---

### Post by vishwasmeshram on 2010-11-11
yes i got it...but yet not get driver and application for my webcam.
kindly help...
thanks

---

### Post by psahoo621 on 2011-11-13
Hi,

I too was facing the same issue [Ubuntu 10.10].
But i got the camera working by following the instructions at:
[]("https://launchpad.net/~r5u87x-loader/+archive/ppa")
Hope this works for you.

> **vishwasmeshram said:**
> yes i got it...but yet not get driver and application for my webcam.
kindly help...
thanks

---

