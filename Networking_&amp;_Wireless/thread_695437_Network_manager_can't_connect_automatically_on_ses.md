---
title: "Network manager can't connect automatically on session startup"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by llebegue on 2008-02-13
Hi All,

I have just made a fresh install of ubuntu 7.10 on my computer.
Wifi connection is working great through the Network Manager panel applet but I must start it manually each time I open a session.

I've checked System -> Preferences -> Session -> Startup Programs and "Network manager" is  enabled.

Any idea about why it doesn't connect automatically ?

---

### Post by Bubba64 on 2008-02-13
When you say start a session what do you mean, has your computer been in hibernation logged off of a browser or when you turn it on and let it boot up. you might want to include the program your using and type of computer and a more detailed circumstance description for a better response. Sorry I didn't see you have Edgy listed good luck though in getting help.

---

### Post by Hightide on 2008-02-13
Hi llebegue

Bubba64 is right in that the more information we have the better the response.

If you are having problems with network manager which can be buggy , have a look at Kevdog's [tutorial. ]("http://ubuntuforums.org/showthread.php?t=571194")It may help

regards

:)

---

### Post by llebegue on 2008-02-14
More details on my configuration :

Computer : HP desktop m9170 (that is a desktop type computer)
WIFI : internal WIFI

A session is when I turn my computer on.

And here is the lspci :

```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fa000000-febfffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [88] Subsystem: Intel Corporation Unknown device 0000
	Capabilities: [80] Power Management version 3
	Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at b400 [size=32]
	Capabilities: [50] #13 [0306]

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at b480 [size=32]
	Capabilities: [50] #13 [0306]

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at f9dfec00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] #13 [0306]

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, fast devsel, latency 0, IRQ 23
	Memory at f9df4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f9f00000-f9ffffff
	Prefetchable memory behind bridge: 00000000cff00000-00000000cfffffff
	Capabilities: [40] Express Root Port (Slot+) IRQ 0
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
	Capabilities: [90] Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at b800 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 22
	I/O ports at b880 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at bc00 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at c000 [size=32]
	Capabilities: [50] #13 [0306]

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0, IRQ 21
	Memory at f9dff800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port
	Capabilities: [98] #13 [0306]

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	Memory behind bridge: f9e00000-f9efffff
	Capabilities: [50] Subsystem: Hewlett-Packard Company Unknown device 2a6f

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
	I/O ports at c880 [size=8]
	I/O ports at c800 [size=4]
	I/O ports at c480 [size=8]
	I/O ports at c400 [size=4]
	I/O ports at c080 [size=32]
	Memory at f9dff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] #12 [0010]
	Capabilities: [b0] #13 [0306]

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: medium devsel, IRQ 10
	Memory at f9dffc00 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0400 [size=32]

01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10 [OHCI])
	Subsystem: Hewlett-Packard Company Unknown device 2a6f
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at f9eff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f

04:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1) (prog-if 00 [VGA])
	Subsystem: ASUSTeK Computer Inc. Unknown device 034e
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at ec00 [size=128]
	[virtual] Expansion ROM at febe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint IRQ 0


```

---

### Post by llebegue on 2008-02-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133486](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/133486) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Solved with a workaround because the automatic connection was not the only problem here:

1 - updated my rt73 driver to the latest daily build (according to this post : [http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73))
2 - Removed "Network Manager" at gnome session startup.

It's ok now.

---

### Post by patihk19 on 2008-07-03
I  have  ubuntu 8.04 Network manager was  working  fine.
I added a  second network card to use on 2 networks.
I would  like both  network cards to work and  I read about the bug  in the  GUI where both cards can't work simultaneously.
I  have done some testing  and  I would  like to reenable the Gui.

When I run sudo aptitude install network-manager it does  not  work as neither of the network cards are getting an IP address. I  would  like  to get the  GUI working again instead of a reinstall.

---

