---
title: "HP N3270 Dapper Xubuntu won't talk to Linksys EtherFast CardBus PCM200"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by Builder on 2007-02-27
I'm new to Ubunto (and _very_ happy with U, K, & X, all Dapper :) but not to *nix.  I've had many years dabbling in Linux (preferred SuSE over RedHat until I stumbled on this), and a decade of professional suport for one of the SVR4 commerical varieties.

I'm running Kubuntu on a VMware workstation right now, and it does just what I want.  However, I have this antique HP N3270 laptop with only 64_MB of RAM (that much was a lot, long ago), and no interest in running Win98 any more.  By chance I discovered yesterday that Xubuntu would install & run (Alternate but not Desktop CDs) in that, and set it up today.

What I found was that everything worked but for the LAN ~card (that's a "Linksys EtherFast 10/100 Integrated CardBus PC Card", Model No. PCM200).  I couldn't seem to see anything wrong on the system, but the link LEDs never came on, DHCP timed out, _&c_....

Here are (hopefully useful) selected lines from "dmesg" & "sudo lspci -v" (I pieced the latter together from some Googling):

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[   30.502633] Memory: 46464k/57280k available (1976k kernel code, 10408k reserved, 606k data, 288k init, 0k highmem)
[   30.583867] CPU: AMD-K6(tm) 3D processor stepping 0c
[   38.300719] hda: IBM-DBCA-206480, ATA DISK drive
[   40.262699] hda: 12685680 sectors (6495 MB) w/420KiB Cache, CHS=13424/15/63, UDMA(33)
[   40.311396] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, DMA
[   72.957620] Yenta: CardBus bridge found at 0000:00:0a.0 [103c:000f]
[   72.957652] Yenta O2: res at 0x94/0xD4: 00/ea
[   72.957660] Yenta O2: old bridge, disabling read prefetch/write burst
[   73.084881] Yenta: ISA IRQ mask 0x0008, PCI irq 11
[   73.084903] Socket status: 30000821
[   73.795870] pccard: CardBus card inserted into slot 0
[   77.459726] Linux Tulip driver version 1.1.13 (December 15, 2004)
[   77.460783] tulip0:  MII transceiver #1 config 3000 status 7849 advertising 01e1.
[   77.468106] eth0: ADMtek Comet rev 17 at 00011800, 00:E0:98:8E:D4:12, IRQ 11.

0000:00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6812 CardBus Controller (rev 05)
	Subsystem: Hewlett-Packard Company: Unknown device 000f
	Flags: bus master, stepping, slow devsel, latency 168, IRQ 11
	Memory at 14000000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 10000000-11fff000 (prefetchable)
	Memory window 1: 12000000-13fff000
	I/O window 0: 00001800-000018ff
	I/O window 1: 00001c00-00001cff
	16-bit legacy interface ports at 0001

0000:02:00.0 Ethernet controller: Abocom Systems Inc 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)
	Subsystem: Abocom Systems Inc 21x4x DEC-Tulip compatible 10/100 Ethernet
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at 1800 [size=256]
	Memory at 12000000 (32-bit, non-prefetchable) [size=1K]
	Expansion ROM at 10000000 [disabled] [size=128K]
	Capabilities: [c0] Power Management version 2

Google is my friend, but I don't always understand what it's telling me.  [linksys tulip cardbus OR pccard site:ubuntu.com] suggested [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsPackardBell](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsPackardBell) which suggested "Breezy will by default detect the wrong tulip module as the network card module" (Win98 used an add-on tulip driver), so maybe this is the right track.  Another search turned up decidedly "downer" [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsLinksys](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsLinksys) which said that a similar PC Card was Auto-Detected Yes Works? No (but the chipset didn't seem to look right).

In desperation I played several more Google tunes (far better to let automation cruise through [http://ubuntuforums.org/tags/index.php/linksys/](http://ubuntuforums.org/tags/index.php/linksys/) than my eyes cross reading all the postings), but couldn't find anything, ditto a Ubuntu Forums search for PCM200.

And while I'm suspecting the Linksys itself, I don't rule out that it's the CardBus technology.  I just don't know how to further "test" either one of them (and don't have any more technology to switch around, isolate the failure to one or the other).  Also, the Linksys stopped working after the last Win98 reimage several years back, so it seems possible that this might be hardware; I'm doubtful though, as the procedure to set up Tulip on the Win98 was not straightforward (not like *nix as we know it :), and at the time I just blamed my _ad hoc_ procedure.

So is this laptop doomed to be a text editor, with I/O _via_ floppy, or might someone be able to shed light on how to put my Xubuntu Dapper Drake on the Internet Highway.  TIA....

Builder

---

### Post by Builder on 2007-03-05
CRACKED!  A friend in Colorado deduced / illustrated that there was nothing wrong with with the software config, that we _were_ talking to the PCM200 (thanks Duane).  So it had to be from the exterior connector outward.

I tried a different cable, but this time to a 10BT hub rather to my 100BT DSL router, and it worked!  It seems unlikely that the problem was the cable (it's back on the computer that I'm typing on right now), so perhaps the speed "throttling" effected by the hub has made the helpful difference (just a theory).

And Xubuntu is now on the Internet.  It's awesome...ly slow (with 64MB RAM, you bet!), but it works, and better than the previous Win98 did too.  8)

---

