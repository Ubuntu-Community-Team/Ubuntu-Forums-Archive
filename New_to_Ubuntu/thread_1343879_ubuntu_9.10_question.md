---
title: "ubuntu 9.10 question"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2009-12-02
ok guys i just installed ubuntu  9.10 on my toshiba Satellite M300

and everything went pretty smoothly untill i tried to connect to the internet  it wont connect and im not sure what to do 


please help 


im using a windstream router and since my laptop is usually in other rooms i use a ethernet cord to connect i didnt have this problem with vista at all 

(not saying that i liked vista cuz anything microsoft can blow me running)

could somebody please help me?

---

### Post by empty_spaces on 2009-12-02
So let me get this straight. What does not work - wireless, wired, or both?

Googling the M300 seems to indicate that you have an Intel wireless chipset, in which case, it should work out of the box. Please post the output of lspci.

---

### Post by pyrofreak99 on 2009-12-02
welled its a wired router  the router isnt capable of wireless internet at all  


and how do i find the ispci?

---

### Post by empty_spaces on 2009-12-02
Go to Applications - Accessories - Terminal.
Enter **lspci** and copy/paste the output from the terminal.(and it's an "l", not an "i")
and while you are in the terminal, you should also post the output of **ifconfig**

---

### Post by pyrofreak99 on 2009-12-02
well that would be kinda hard since im using the living room computer to type this up


sooooo yeah this computer is in my living room and runs xp bleh

---

### Post by The Cog on 2009-12-02
FYI. **lspci** is a command to list all the devices on the PCI bus. 
Actually, **lspci -v** produces more verbose output, which might also prove useful.

You can copy/paste the text from the console window not by Ctrl-C, but right-click the window and choose copy, then Ctrl-V into the browser.

---

### Post by pyrofreak99 on 2009-12-02
ok i did the lspci-v command  and i got a bunch of stuff but the problem is


IM ON A DIFFERENT COMPUTER

---

### Post by sandyd on 2009-12-02
do "lspci -v >> ~/Desktop/lspci.txt" (without quotes) the copy the lspci.txt file thats now on the desktop to a usb drive or something. go to another computer and upload it

---

### Post by pyrofreak99 on 2009-12-02
oh der im stupid  thanks for that 



here ya go



mage@mage-laptop:~$ lispci=v
mage@mage-laptop:~$ lspci-v
lspci-v: command not found
mage@mage-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff51
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f4000000 (64-bit, non-prefetchable) [size=4M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
	Subsystem: Toshiba America Info Systems Device ff51
	Flags: bus master, fast devsel, latency 0
	Memory at f4400000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1820 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1840 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1860 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	Memory at f4a04800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f4800000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: b6000000-b60fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Memory behind bridge: b6100000-b61fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1880 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 18a0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 18c0 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f4a04c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
	Memory behind bridge: f4700000-f47fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 1818 [size=8]
	I/O ports at 180c [size=4]
	I/O ports at 1810 [size=8]
	I/O ports at 1808 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f4a04000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: medium devsel, IRQ 10
	Memory at b6200000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 1c00 [size=32]
	Kernel modules: i2c-i801

07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: fast devsel, IRQ 16
	Memory at b6000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 2000 [size=256]
	Capabilities: <access denied>
	Kernel modules: sky2

08:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
	Subsystem: Device 1a32:4105
	Flags: fast devsel, IRQ 17
	Memory at b6100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath5k

0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 16
	Memory at ff501000 (32-bit, non-prefetchable) [size=4K]
	Memory at f4700000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f4700800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: slow devsel, IRQ 255
	Memory at f4702000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by The Cog on 2009-12-02
So the wireless card is an Atheros AR5001 using the ath5k driver at the moment. I know nothing about those but searching these forums should turn something up. A couple of questions that might provide more info for people though - 

If you enter the command **ifconfig -a**, what interfaces are named? I expect eth0 and lo, but is there an eth1 or a wlan0?

If you right-click the network thingy in the system tray, does it admit to there being any wireless capability?

What does the command **iwconfig** say?

All these questions should help people who've dealt with atheros cards figure out how much is working and how much isn't.

---

### Post by Terl on 2009-12-02
I've read through this thread a couple times.  Are you trying to have your network work wired?  I see you have only a wired router; is that true?  If so your device as I see it is:

```
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
Subsystem: Toshiba America Info Systems Device ff50
Flags: fast devsel, IRQ 16
Memory at b6000000 (64-bit, non-prefetchable) [size=16K]
I/O ports at 2000 [size=256]
Capabilities: <access denied>
Kernel modules: sky2

```

So, before we go further, are you trying to connect to the internet with your laptop with a wired connection?

If it is the wired after all, I did find a link here: [on the forums]("http://ubuntuforums.org/showthread.php?t=781022") for 8.04 so I am not positive it still applies, but it seems as if this NIC has issues in the past anyway.

---

