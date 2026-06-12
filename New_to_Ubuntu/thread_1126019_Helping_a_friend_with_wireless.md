---
title: "Helping a friend with wireless"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Haruki-kun on 2009-04-15
I was unable to help a friend install his wireless drivers. Apparently wireless worked on installation, but it doesn't work as well as it does on Windows. The only reason I could think of for that is that he needs to install a new driver.

I think it would be best to install the Windows driver using ndiswrapper, but I don't know what driver he needs.

This is the result of lspci -v, which if I remember correctly is what I was told to post when I first asked:

> (ICH7 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, medium devsel, latency 0, IRQ 18
 I/O ports at 1860 [size=32]
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, medium devsel, latency 0, IRQ 17
 I/O ports at 1880 [size=32]
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, medium devsel, latency 0, IRQ 20
 Memory at d0644000 (32-bit, non-prefetchable) [size=1K]
 Capabilities: <access denied>
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
 Flags: bus master, fast devsel, latency 0
 Bus: primary=00, secondary=0a, subordinate=0a, sec-latency=32
 Memory behind bridge: d0100000-d01fffff
 Capabilities: <access denied>
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, medium devsel, latency 0
 Capabilities: <access denied>
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
 I/O ports at 01f0 [size=8]
 I/O ports at 03f4 [size=1]
 I/O ports at 0170 [size=8]
 I/O ports at 0374 [size=1]
 I/O ports at 18b0 [size=16]
 Capabilities: <access denied>
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: medium devsel, IRQ 10
 I/O ports at 18c0 [size=32]
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, fast devsel, latency 0, IRQ 219
 I/O ports at 2000 [size=256]
 Memory at 50000000 (64-bit, non-prefetchable) [size=4K]
 [virtual] Expansion ROM at 50100000 [disabled] [size=128K]
 Capabilities: <access denied>
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
 Subsystem: Intel Corporation Unknown device 1100
 Flags: bus master, fast devsel, latency 0, IRQ 218
 Memory at 50200000 (64-bit, non-prefetchable) [size=8K]
 Capabilities: <access denied>
0a:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, medium devsel, latency 64, IRQ 17
 Memory at d0100000 (32-bit, non-prefetchable) [size=2K]
 Capabilities: <access denied>
0a:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: bus master, medium devsel, latency 64, IRQ 16
 Memory at d0100800 (32-bit, non-prefetchable) [size=256]
 Capabilities: <access denied>
0a:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: medium devsel, IRQ 11
 Memory at d0100c00 (32-bit, non-prefetchable) [disabled] [size=256]
 Capabilities: <access denied>
0a:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
 Subsystem: Toshiba America Info Systems Unknown device ff50
 Flags: medium devsel, IRQ 11
 Memory at d0101000 (32-bit, non-prefetchable) [disabled] [size=256]
 Capabilities: <access denied>
0a:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
 !!! Unknown header type 7f


Can you help me find what driver he needs?

---

### Post by jbrown96 on 2009-04-15
Intel has very good Linux support. They have open source drivers included in the kernel, so there's not much you can do. The driver should work just as well as in linux. 

What issues is he having? It's probably networkManager related.

---

### Post by Haruki-kun on 2009-04-15
> **jbrown96 said:**
> Intel has very good Linux support. They have open source drivers included in the kernel, so there's not much you can do. The driver should work just as well as in linux. 

What issues is he having? It's probably networkManager related.

He says he loses his connection all of a sudden a lot, which doesn't happen to him in windows.

EDIT: Also, he says sometimes the pages won't load.

---

### Post by jbrown96 on 2009-04-15
What type of wireless connection is he using? At my university, they use WPA2-EAP with PEAP and MSCHAPv2, and the connection does drop sometimes, espcially in some buildings. 
What version of Ubuntu is he using? Kernel version (check with ```
uname -a
```)?

There are some logs that you can look at: System--->Admin--->Logs. I can't remember right now, which section to look in, but if he is looking at them and makes a connection there will be a lot of messages. Posting that could help quite a bit. 


If there's nothing too obvious, then I would recommend waiting until the 24th and upgrade to 9.04. It will have a new version of NetworkManager and a new kernel (so new Intel drivers).

---

### Post by Haruki-kun on 2009-04-15
> Linux creategfx-laptop 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux


And he's working on Hardy.

---

### Post by jbrown96 on 2009-04-15
It probably is bad drivers then. Intel used to sponsor a project called ipw (Intel Pro Wireless) for several drivers (ipw3945 -- what I have and ipw4965). I liked these drivers; they worked well, even at my uni. However, Intel changed their project to iwl (iwl3945 and iwl4965); these drivers were very immature and caused a lot of problems. I couldn't connect at my uni, using the first gen iwl drivers (included in Hardy). However, the drivers have since matured, and I don't have any problems.

I understand why he would want to run the LTS version, but it would probably be a good idea to upgrade. Another solution would be to add the Ubuntu kernel ppa to get a new kernel. Manually installing just new drivers into the hardy kernel is fairly difficult, but you can find more info at the iwl driver website. 

[Here are instructions for the PPA]("https://launchpad.net/~kernel-ppa/+archive/ppa")

---

### Post by Augsburg on 2009-04-15
Try this:

sudo apt-get install pump

then run the command:

  $ sudo pump -i eth0

whenever he isn't connected or has lost his connection.

---

