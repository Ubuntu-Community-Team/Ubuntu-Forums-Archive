---
title: "ndiswrapper not detecting hardware, but drivers installed"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by kommissar on 2005-04-24
Hello all.  I have a D-Link DWL-650 revision P PCMCIA wireless network card that I am attempting to use in my old laptop.  Now there are two solutions to this.

1) Can someone please tell me where I can download the prism2_cs kernel module for ubuntu 5.04 since it's not included with any of the packages.  This is the correct module for my card.

OR 

2)  I downloaded the drivers from the D-Link site (as recommended by the ndiswrapper website) and installed them with the ndiswrapper -i option.  All went well.  The modprobe ndiswrapper works fine, it says the driver is present, but it does NOT say that hardware was detected.  It also does NOT create the wlan0 interface.

So... my problem is that although ndiswraper loads the modules fine it won't find the card in my PCMCIA slot.  Does anyone have any ideas??

All of the other things seem to be fine... here's some dmesg information for the modprobe:
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper (load_devices:479): Each driver can only support a single bustype
ndiswrapper: driver netprism (D-Link,07/17/2003, 3.0.8) added 

And here is ndiswrapper -l:
Installed ndis drivers:
netprism     driver present

---

### Post by kommissar on 2005-04-25
*bump*

---

### Post by telmo on 2005-04-25
Have you done sudo modprobe ndiswrapper??

If you get an error, you might need to copy the ndiswrapper.ko from /lib/modules/<kernel version>/misc to /lib/modules/<kernel version>/kernel/drivers/net/ndiswrapper/

Then try modprobe again.

That should do the trick!

---

### Post by az on 2005-04-25
Please explore this bug in the Hoary hotplug system:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)


There are actually three drivers for the prism2 chipset and you traditionally get the orinoco drivers with hotplug which work well.

Did the card ever work on that laptop?  Is it a really old laptop with 16-bit pcmcia?

---

### Post by kommissar on 2005-04-25
[QUOTE=azz]Please explore this bug in the Hoary hotplug system:

[https://bugzilla.ubuntu.com/show_bug.cgi?id=8575](https://bugzilla.ubuntu.com/show_bug.cgi?id=8575)


There are actually three drivers for the prism2 chipset and you traditionally get the orinoco drivers with hotplug which work well.

Did the card ever work on that laptop?  Is it a really old laptop with 16-bit pcmcia?[/QUOTE]
Thank you for the reply.  I think that the PCMCIA may be 16-bit but i'm not sure.  Is there a way to check?  I _did_ try `modprobe orinoco_cs` and that still did not give me any sort of iwconfig or anything in the Gnome Network Config Tool.  I was able to get this card to work under fedora core 3 at one point, I think using prism 2.  Doing an lspci does show the info for the two pcmcia slots (CardBus bridge...).  The light on the card is also on, it appears after the hotplug subsystem is started.  I really don't care about hotplugging, typing modprobe is not really a big deal for me.  Do you happen to have any other suggestions?

---

### Post by az on 2005-04-25
Okay, Ubuntu did a lot of work to unify hardware detection in Hoary.  Instead of using Hotplug, Discover and any other mechanism, they just rolled it all into hotplug.  At boot Hotplug loads all the modules you need.

So, perhaps the PCMCIA controller driver (not the wireless card driver) is not being loaded.
quote:
The issue is that the test for PCMCIA support is made in the init script before
any attempt to load drivers is made.  Unfortunately, it would not be safe to
change the test for Hoary, since this would cause the modules to be loaded in
situations where they otherwise would not be (and the reason for the test is
that these probes can hang the system).

You should be able to work around this by adding the appropriate module to
/etc/modules.  "yenta_socket" is the most common module, though you may need a
different one.  Check in lsmod and see which module is being loaded when you use
the older pcmcia-cs, and add that to /etc/modules.


This may or may not be the issue.  You need to know what module your pcmcia controller is.  One way to check would be to try the Warty live cd.  This problem did not exist in Warty.  Perhaps, just installing the Warty kernel would do the trick.  The Warty kernel will still recieve security updates for another year and a half...   If it turns out that this is your problem, please add to the bug report.  If not, never mind.

Did you ever use the card on that laptop successfully before?  If not, you may need to tell your bios to use 16-bit pcmcia if it can do both 16 and 32 bit (not at the same time!)

Your problem may be something different, too.

---

### Post by kommissar on 2005-04-26
The card _did_ work under the Fedora Core 3 distro.  I think it just used the prism2_cs driver but can't remember clearly.  I booted the livecd of warty warthog and as it was coming up cardmgr reported something like "unsupported hardware in slot 0" with the information about the card.  Once it was completely booted I did a 'modprobe orinoco_cs' just as a test, but that did not make it detect either.  

Both warty warthog and hoary hedgehog use the yentra_socket and pcmcia_core.  Both of these are loaded on boot.  There is no differences in the modules it loads.

---

### Post by az on 2005-04-26
Okay, then.  perhaps it is an acpi thing?

---

### Post by kommissar on 2005-04-27
[QUOTE=azz]Okay, then.  perhaps it is an acpi thing?[/QUOTE]
ACPI?  As in ACPI power management?  I'm not sure I know what you mean, sir  :)

---

### Post by kommissar on 2005-04-28
azz, did you give up on me?

---

### Post by az on 2005-04-28
Boot without the card inserted.  In a colsole do:

sudo tail -f /var/log/messages
and insert the card.  Post the output.

---

### Post by kommissar on 2005-04-29
[QUOTE=azz]Boot without the card inserted.  In a colsole do:

sudo tail -f /var/log/messages
and insert the card.  Post the output.[/QUOTE]
When i insert the card the following line appears at the end of messages:

Apr 29 10:04:55 localhost kernel: cs: memory probe 0xa0000000-0xa0ffffff: clean.

---

### Post by kommissar on 2005-05-01
If you don't have any more ideas don't worry about it.  I think I'm going to try and steal a Cisco wireless card from work that I know works.

---

### Post by Dillius on 2005-05-03
Hate to kinda slip in on someone elses problem, but I decided to try this with my Linksys WPC54G v.2 wireless pcmcia card. This is what I get, and it confuses the heck outa me. My ndiswrapper detects hardware and detects the driver with it, but power never goes to the card and I never get wlan0 to come up.

May  3 00:30:01 localhost pci.agent[7362]:      acx_pci: loaded successfully
May  3 00:30:01 localhost kernel: acx100: It looks like you've been coaxed into buying a wireless network card
May  3 00:30:01 localhost kernel: acx100: that uses the mysterious ACX100/ACX111 chip from Texas Instruments.
May  3 00:30:01 localhost kernel: acx100: You should better have bought e.g. a PRISM(R) chipset based card,
May  3 00:30:01 localhost kernel: acx100: since that would mean REAL vendor Linux support.
May  3 00:30:01 localhost kernel: acx100: Given this info, it's evident that this driver is quite EXPERIMENTAL,
May  3 00:30:01 localhost kernel: acx100: thus your mileage may vary. Visit [http://acx100.sf.net](http://acx100.sf.net) for support.
May  3 00:30:01 localhost kernel: acx100: Warning: compiled to use 16bit I/O access only (compatibility mode). Set Makefile ACX_IO_WIDTH=32 to use slightly problematic 32bit mode.
May  3 00:30:01 localhost kernel: acx_init_module: dev_info is: TI acx_pci
May  3 00:30:01 localhost kernel: acx_init_module: TI acx_pci.o: Ver 0.2.0pre8 Driver initialized, waiting for cards to probe...
May  3 00:30:01 localhost kernel: PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
May  3 00:30:01 localhost kernel: acx_probe_pci: WARNING: ACX111 support is quite experimental!
May  3 00:30:01 localhost kernel: Found ACX111-based wireless network card at 0000:02:00.0, irq:0, phymem1:0x10820000, phymem2:0x10800000, mem1:0xcfca4000, mem1_size:8192, mem2:0xcfe40000, mem2_size:131072
May  3 00:30:01 localhost kernel: initial debug setting is 0x001b
May  3 00:30:01 localhost kernel: acx_probe_pci: TI acx_pci: Can't get IRQ 0
May  3 00:30:01 localhost kernel: acx_probe_pci: TI acx_pci.o: Ver 0.2.0pre8 Loading FAILED
May  3 00:30:01 localhost kernel: acx_pci: probe of 0000:02:00.0 failed with error -5

pretty much looks like i'm doomed... but i've heard of plenty of successes with this card too...

---

### Post by az on 2005-05-03
[QUOTE=Dillius]Hate to kinda slip in on someone elses problem, but I decided to try this with my Linksys WPC54G v.2 wireless pcmcia card. This is what I get, and it confuses the heck outa me. My ndiswrapper detects hardware and detects the driver with it, but power never goes to the card and I never get wlan0 to come up.

May  3 00:30:01 localhost pci.agent[7362]:      acx_pci: loaded successfully
May  3 00:30:01 localhost kernel: acx100: It looks like you've been coaxed into buying a wireless network card
May  3 00:30:01 localhost kernel: acx100: that uses the mysterious ACX100/ACX111 chip from Texas Instruments.
May  3 00:30:01 localhost kernel: acx100: You should better have bought e.g. a PRISM(R) chipset based card,
May  3 00:30:01 localhost kernel: acx100: since that would mean REAL vendor Linux support.
May  3 00:30:01 localhost kernel: acx100: Given this info, it's evident that this driver is quite EXPERIMENTAL,
May  3 00:30:01 localhost kernel: acx100: thus your mileage may vary. Visit [http://acx100.sf.net](http://acx100.sf.net) for support.
May  3 00:30:01 localhost kernel: acx100: Warning: compiled to use 16bit I/O access only (compatibility mode). Set Makefile ACX_IO_WIDTH=32 to use slightly problematic 32bit mode.
May  3 00:30:01 localhost kernel: acx_init_module: dev_info is: TI acx_pci
May  3 00:30:01 localhost kernel: acx_init_module: TI acx_pci.o: Ver 0.2.0pre8 Driver initialized, waiting for cards to probe...
May  3 00:30:01 localhost kernel: PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
May  3 00:30:01 localhost kernel: acx_probe_pci: WARNING: ACX111 support is quite experimental!
May  3 00:30:01 localhost kernel: Found ACX111-based wireless network card at 0000:02:00.0, irq:0, phymem1:0x10820000, phymem2:0x10800000, mem1:0xcfca4000, mem1_size:8192, mem2:0xcfe40000, mem2_size:131072
May  3 00:30:01 localhost kernel: initial debug setting is 0x001b
May  3 00:30:01 localhost kernel: acx_probe_pci: TI acx_pci: Can't get IRQ 0
May  3 00:30:01 localhost kernel: acx_probe_pci: TI acx_pci.o: Ver 0.2.0pre8 Loading FAILED
May  3 00:30:01 localhost kernel: acx_pci: probe of 0000:02:00.0 failed with error -5

pretty much looks like i'm doomed... but i've heard of plenty of successes with this card too...[/QUOTE]


What is happening here is that the kernel already has adriver for your card (acx100)  That driver works fine, but does not do wep (the new version does - maybe Breezy will ship with it)  You must prevent the acx100 module from being loaded by hotplug since it is interfering with ndiswrapper)

(/etc/hotplug/blacklist)

---

### Post by Dillius on 2005-05-03
Well also I noticed at the end... Is it having IRQ conflicts?

---

### Post by az on 2005-05-03
[QUOTE=Dillius]Well also I noticed at the end... Is it having IRQ conflicts?[/QUOTE]

You are trying to use two drivers for the same hardware at the same time.  That is problematic.

---

### Post by atoponce on 2005-05-03
[QUOTE=kommissar]Hello all.  I have a D-Link DWL-650 revision P PCMCIA wireless network card that I am attempting to use in my old laptop.  Now there are two solutions to this.

1) Can someone please tell me where I can download the prism2_cs kernel module for ubuntu 5.04 since it's not included with any of the packages.  This is the correct module for my card.

OR 

2)  I downloaded the drivers from the D-Link site (as recommended by the ndiswrapper website) and installed them with the ndiswrapper -i option.  All went well.  The modprobe ndiswrapper works fine, it says the driver is present, but it does NOT say that hardware was detected.  It also does NOT create the wlan0 interface.

So... my problem is that although ndiswraper loads the modules fine it won't find the card in my PCMCIA slot.  Does anyone have any ideas??

All of the other things seem to be fine... here's some dmesg information for the modprobe:
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper (load_devices:479): Each driver can only support a single bustype
ndiswrapper: driver netprism (D-Link,07/17/2003, 3.0.8) added 

And here is ndiswrapper -l:
Installed ndis drivers:
netprism     driver present[/QUOTE]
 If you get it to work, I am having similar problems with an Orinoco Proxim card.  It is an Agere chipset.  However, I get the exact reverse of you.  When I type 'ndiswrapper -l', I get 'invalid driver!' and 'hardware present'.  I downloaded the driver directly from the manufacture website.

So if you get anything working, let me know.

---

### Post by Dillius on 2005-05-03
It's still displaying quite a message for me, even after I tried to blacklist the driver in hotplug. I put in acx_pci and acx100... maybe I'm missing something?

Also, now when I modprobe ndiswrapper, this message is shown in dmesg output:

ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
PCI: Setting latency timer of device 0000:02:00.0 to 64
ndiswrapper (ndis_init_one_pci:95): Windows driver couldn't initialize the device (C0000001)
lstinds: probe of 0000:02:00.0 failed with error -22
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.18 ) added

---

### Post by QuantumCowboy on 2005-05-08
I have the exact same problem, ndiswrapper installed airplus driver ok, but the hardware doesn't seem to be lighting up and I suspect PCMCIA driver is not loading.  Below is the output of lspci -v... lots of Texas Instruments "unknown device" lines near the bottom.  Can you tell which one is my PCMCIA and how I should acitvate it?  I would really appreciate the help, I've been at this for weeks...  hp zv5000, dwl-650+.

Thanks so much,
QC


> 0000:00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Capabilities: [44] #08 [0180]
        Capabilities: [c0] AGP version 2.0

0000:00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
        Subsystem: nVidia Corporation: Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 2040 [size=64]
        I/O ports at 2000 [size=64]
        Capabilities: [44] Power Management version 2

0000:00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation: Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at e0000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5) (prog-if 10 [OHCI])
        Subsystem: nVidia Corporation: Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at e0001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2) (prog-if 20 [EHCI])
        Subsystem: nVidia Corporation: Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at e0004000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at 1400 [size=256]
        I/O ports at 1c00 [size=128]
        Memory at e0002000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:06.1 Modem: nVidia Corporation: Unknown device 00d9 (rev a2) (prog-if 00 [Generic])
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: 66MHz, fast devsel, IRQ 22
        I/O ports at 1800 [size=256]
        I/O ports at 1c80 [size=128]
        Memory at e0003000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

0000:00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5) (prog-if 8a [Master SecP PriP])
        Subsystem: nVidia Corporation: Unknown device 0c80
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at 2080 [size=16]
        Capabilities: [44] Power Management version 2

0000:00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=128
        I/O behind bridge: 00003000-00007fff
        Memory behind bridge: e0100000-e17fffff

0000:00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 16
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=10
        Memory behind bridge: e2000000-e2ffffff
        Prefetchable memory behind bridge: f0000000-f80fffff

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel
        Capabilities: [80] #08 [2101]

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
        Flags: fast devsel

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at f8000000 (32-bit, prefetchable) [size=512K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 2.0

0000:02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at e0106000 (32-bit, non-prefetchable) [size=2K]
        Memory at e0100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2

0000:02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RT8139
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at 7000 [size=256]
        Memory at e0106800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

0000:02:04.0 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: bus master, medium devsel, latency 168, IRQ 19
        Memory at e0104000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: e0200000-e03ff000 (prefetchable)
        Memory window 1: e0400000-e05ff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

0000:02:04.1 CardBus bridge: Texas Instruments: Unknown device ac54 (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: bus master, medium devsel, latency 168, IRQ 18
        Memory at e0105000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=0a, sec-latency=176
        Memory window 0: e1000000-e13ff000 (prefetchable)
        Memory window 1: e0c00000-e0fff000
        I/O window 0: 00006000-00006fff
        I/O window 1: 00005000-00005fff
        16-bit legacy interface ports at 0001

0000:02:04.2 System peripheral: Texas Instruments: Unknown device 8201 (rev 01)
        Subsystem: Hewlett-Packard Company: Unknown device 006d
        Flags: bus master, medium devsel, latency 64
        I/O ports at 7400 [size=64]
        Capabilities: [44] Power Management version 2

---

### Post by xoros on 2005-06-05
To QuantumCowboy > 

Your problem is the TI1620 cardbus controller,  I had the exact same problem... see this thread: 

[http://ubuntuforums.org/showthread.php?t=39379](http://ubuntuforums.org/showthread.php?t=39379)

You need to make sure your card is unplugged then type:

sudo setpci -s 0:a.0 SUBORDINATE_BUS=0x0A

sudo /etc/init.d/pcmcia restart

Then insert card and it should work fine.  Hopefully we can get that patch in my thread (or something similar) added to the kernels...  developers, any comment?

---

### Post by beansbbq on 2005-07-16
[QUOTE=atoponce]If you get it to work, I am having similar problems with an Orinoco Proxim card.  It is an Agere chipset.  However, I get the exact reverse of you.  When I type 'ndiswrapper -l', I get 'invalid driver!' and 'hardware present'.  I downloaded the driver directly from the manufacture website.

So if you get anything working, let me know.[/QUOTE]



Aaron,   I too have a Proxim card.  Mine is suppose to be a "just works" card, however I can't get it to work.  THe card is recognized, the driver is installed, but it doesn't work.  Here are my tail logs.  Can anyone see anything wrong here?



Jul 16 08:36:35 localhost kernel: PCI: Enabling device 0000:06:00.0 (0000 -> 000 2)
Jul 16 08:36:35 localhost kernel: ACPI: PCI interrupt 0000:06:00.0[A] -> GSI 9 ( level, low) -> IRQ 9
Jul 16 08:36:35 localhost kernel: ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24M bps 36Mbps 48Mbps 54Mbps
Jul 16 08:36:35 localhost kernel: ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
Jul 16 08:36:35 localhost kernel: ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6M bps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
Jul 16 08:36:35 localhost kernel: ath0: turbo rates: 6Mbps 9Mbps 12Mbps 18Mbps 2 4Mbps 36Mbps 48Mbps 54Mbps
Jul 16 08:36:35 localhost kernel: ath0: mac 5.6 phy 4.1 5ghz radio 1.7 2ghz radi o 2.3
Jul 16 08:36:35 localhost kernel: ath0: 802.11 address: 00:20:a6:4c:4e:3a
Jul 16 08:36:35 localhost kernel: ath0: Use hw queue 0 for WME_AC_BE traffic
Jul 16 08:36:35 localhost kernel: ath0: Use hw queue 1 for WME_AC_BK traffic
Jul 16 08:36:35 localhost kernel: ath0: Use hw queue 2 for WME_AC_VI traffic
Jul 16 08:36:35 localhost kernel: ath0: Use hw queue 3 for WME_AC_VO traffic
Jul 16 08:36:35 localhost kernel: ath0: Atheros 5212: mem=0x10c00000, irq=9
Jul 16 08:36:36 localhost pci.agent[14892]:      ath_pci: already loaded



Thanks,

Jonto

---

