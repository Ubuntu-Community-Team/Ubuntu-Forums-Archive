---
title: "Linux Newbie, Need help with setup."
date: 2009-07-09
forum: New to Ubuntu
---

### Post by spiketheguitarist on 2009-07-09
Hi Everyone,
 
After recently getting pissed off at having to reinstall windows I decided to try Linux. I talked to a computer programmer friend of mine and he suggested that I try Ubuntu Studio 9.04(since I do audio production). I downloaded the .Iso file from the torrent that the Ubuntu Studio website provided, Burned it, Installed it, and had it up and running. But I have ran into a few problems. But first things first: Here are the specs for my PC:
 
 
 
 
[FONT=Arial][SIZE=2]Emachine W3118[/SIZE][/FONT]
[FONT=Arial][SIZE=2]* Processor: AMD Sempron 3100+ 1.8GHz [/SIZE][/FONT]
[SIZE=2][FONT=Arial]* Memory: 768MB RAM[/FONT][/SIZE]
[SIZE=2][FONT=Arial]* Hard drives: 80GB running XP, 40GB for Ubuntu (dual boot)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]* Graphics: ATI Radeon X550 256MB (dual monitor setup: Dell 15 inch and Sony 27 inch)[/FONT][/SIZE]
[SIZE=2][FONT=Arial]* Sound: M-Audio Delta 1010LT[/FONT][/SIZE]
[SIZE=2][FONT=Arial]* Internet: TP-Link TL-WN821N 802.11n Wireless USB 2.0 Adapter, 300Mbps [/FONT][/SIZE]
 
[FONT=Arial][SIZE=2]Now here is my list of problems:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]1. Cannot connect to Internet:[/SIZE][/FONT]
 
 
[FONT=Arial][SIZE=2]When I ran the Ubuntu install it did not detect my wireless adaptor, but it did detect my old onboard ethernet port. And like I said I am a newb. So I have no idea how to set it up.[/SIZE][/FONT]
 
 
2. No Sound:
 
 
I found the sound setup but didn't know how/if I needed to change anything in there. I did read somewhere that my soundcard is supported by Ubuntu, But once again, like I have stated before, I am a newb and don't know 
 
 
3. Resolution problems
 
 
When I got into the GNOME destop, I found the display options and set it to dual display and upped the resolution on the Sony monitor. A message came on screen that said that Ubuntu to change the "virtual resolution" to change the setting. So I did and it told me to log out to activate the changes. When I did, my Dell monitor(the one that I didn't change the settings on) did not show anything at all. My monitor itself said it could not display the setting, and the main panel was on that monitor and I didn't know how to move it to my Sony monitor.
 
 
Im really excited about using Ubuntu, I just need some help on getting these issues fixed. 
 
Thanks.

---

### Post by iver2435 on 2009-07-09
please post the output of this command:

```
lspci -v
```

This will tell us what kind of hardware is in your computer.  Once we know that we should be able to help more.

---

### Post by spiketheguitarist on 2009-07-10
spiketheguitarist@Slave1:~$ lspci -v
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00009000-00009fff
    Memory behind bridge: fd800000-fd8fffff
    Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00008000-00008fff
    Memory behind bridge: fdd00000-fddfffff
    Prefetchable memory behind bridge: 00000000fdc00000-00000000fdcfffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: fd900000-fd9fffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    Capabilities: <access denied>

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel, IRQ 11
    I/O ports at 1c00 [size=64]
    I/O ports at 1c40 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 10)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
    Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci_hcd

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2) (prog-if 20)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
    Subsystem: Device f509:6006
    Flags: bus master, 66MHz, fast devsel, latency 0
    [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
    [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
    [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
    I/O ports at f400 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_amd

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at 09f0 [size=8]
    I/O ports at 0bf0 [size=4]
    I/O ports at 0970 [size=8]
    I/O ports at 0b70 [size=4]
    I/O ports at e000 [size=16]
    Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: sata_nv

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
    Flags: bus master, 66MHz, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    I/O behind bridge: 0000b000-0000cfff
    Memory behind bridge: fdb00000-fdbfffff
    Prefetchable memory behind bridge: fda00000-fdafffff
    Capabilities: <access denied>

00:10.2 Multimedia audio controller: nVidia Corporation MCP51 AC97 Audio Controller (rev a2)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=256]
    I/O ports at d800 [size=256]
    Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
    Subsystem: FIRST INTERNATIONAL Computer Inc Device 6006
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
    Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at d400 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    Flags: fast devsel
    Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Flags: fast devsel
    Kernel driver in use: k8temp
    Kernel modules: k8temp

03:00.0 VGA compatible controller: ATI Technologies Inc RV370 [Sapphire X550 Silent]
    Subsystem: Diamond Multimedia Systems Device 0430
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at ac00 [size=256]
    Memory at fd9f0000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at fd900000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeonfb

03:00.1 Display controller: ATI Technologies Inc RV370 secondary [Sapphire X550 Silent]
    Subsystem: Diamond Multimedia Systems Device 0431
    Flags: fast devsel
    Memory at fd9e0000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>

04:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
    Subsystem: VIA Technologies Inc. Device d63b
    Flags: bus master, medium devsel, latency 32, IRQ 18
    I/O ports at cc00 [size=32]
    I/O ports at c800 [size=16]
    I/O ports at c400 [size=16]
    I/O ports at c000 [size=64]
    Capabilities: <access denied>
    Kernel driver in use: ICE1712
    Kernel modules: snd-ice1712

04:07.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
    Subsystem: ADMtek Device 0570
    Flags: bus master, medium devsel, latency 32, IRQ 19
    I/O ports at bc00 [size=256]
    Memory at fdbff000 (32-bit, non-prefetchable) [size=1K]
    [virtual] Expansion ROM at fda00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: tulip
    Kernel modules: tulip

---

### Post by spiketheguitarist on 2009-07-10
I'm replying again because I didn't know how to use the code box on the forum in the previous reply. But I just wanted to say that I had to bring my PC downstairs and hard-wire it, but I am now online with Ubuntu as I type. I used the update manager and downloaded the most recent updates, but I still don't think Ubuntu is detecting my wireless network adaptor. After doing more research i found that people have had the same problem with that model usb adaptor as well, and the solution was to "compile the kernel". I've been researching on how to do that but wanted to wait because I don't exactly know what I am doing, lol.  Also, I only have my sony monitor hooked up right now and its displaying a resolution of 1920 x 1200 (16:10) and I am having no problem with just a single display.

---

### Post by pablolie on 2009-07-10
give it time after the update - the new wireless functionality that is packaged in does an amazing job most of the time. if it doesn't, let us know.

these days it is pretty straight forward to intsall windows .inf files *if* you really need to.

---

### Post by spiketheguitarist on 2009-07-10
> **pablolie said:**
> give it time after the update - the new wireless functionality that is packaged in does an amazing job most of the time. if it doesn't, let us know.

these days it is pretty straight forward to intsall windows .inf files *if* you really need to.


does ubuntu have usb plug and play like windows? and i have no idea what a .inf file is. lol i hate being a newb! I'm not used to typing in dos-style commands, but i want to learn. I'm thinking about getting one of Linux for dummies books sometime soon. But I can say this already looks and feels better than windows to me. I can't wait to learn how everything works.

---

### Post by PGScooter on 2009-07-10
.inf are windows drivers I think.

Yes, ubundu does have usb plug and play and most of the time it works a lot better than in Windows.

---

### Post by Peter09 on 2009-07-10
Your card does not seem to be supported yet. My advice would be to get a cheap usb wireless dongle and use that. As a beginner you really do not want to be into building custom kernels.

---

### Post by Talon2 on 2009-07-10
> **Peter09 said:**
> My advice would be to get a cheap usb wireless dongle and use that. As a beginner you really do not want to be into building custom kernels.

I'll second this suggestion.  I'll throw out a suggestion that is plug and play:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022](http://www.newegg.com/Product/Product.aspx?Item=N82E16833166022)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812339023](http://www.newegg.com/Product/Product.aspx?Item=N82E16812339023)

If this isn't available where you live maybe others can offer suggestions.

Wifi support is getting better but it is an area where support is not perfect yet.

---

### Post by spiketheguitarist on 2009-07-10
well i found this link on aircrack-ng that says it is supported.

[http://forum.aircrack-ng.org/index.php?PHPSESSID=7b783bbeb2071a1b50ae3e8afd7d319e&topic=5530.0](http://forum.aircrack-ng.org/index.php?PHPSESSID=7b783bbeb2071a1b50ae3e8afd7d319e&topic=5530.0)

and i read that it is a atheros chipset that is used in my dongle. so i used lsusb and got this:

```
Bus 001 Device 002: ID 0cf3:9170 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```so does all this still mean that it isn't supported?

---

### Post by earthpigg on 2009-07-10
using aircrack-ng involves compiling your own drivers. aircrack is used to crack encryption on wifi networks - this requires giving your wireless network card abilities the manufacturer did not intend for it to have. making hardware do things it was not originally intended to do is sometimes called 'hacking' -- which is neither illegal nor immoral in itself, but it may void a warranty or two. something to keep in mind.

it very well may be supported, _if_ you want to get into compiling your own drivers and whatnot.

if time is money for you, then the most cost-effective solution is to buy a dongle, as suggested above.

if you are willing/want to learn to compile your own drivers and/or Linux kernel, then go for it... i will humbly submit, however, that it is probably a bit beyond the scope of 'absolute beginner talk'.

:D

---

### Post by LewRockwell on 2009-07-10
> **earthpigg said:**
> 

...

i will humbly submit, however, that it is probably a bit beyond the scope of 'absolute beginner talk'.



vastly understated

.

---

### Post by spiketheguitarist on 2009-07-10
well thanks for the help guys, does anyone have any ideas about my other questions on dual monitor support and my soundcard not working?

---

### Post by earthpigg on 2009-07-10
> **spiketheguitarist said:**
> 
 
2. No Sound:
 
 
I found the sound setup but didn't know how/if I needed to change anything in there. I did read somewhere that my soundcard is supported by Ubuntu, But once again, like I have stated before, I am a newb and don't know 
 

click on the speaker thingie in upper right corner -> volume control -> preferences

check every damn thing you see, even if it looks silly. that will result in extra setting options being displayed. unmute everything, turn everything all the way up.

if that made it work, start unchecking and muting things you dont want, and adjusting volume to more sane levels.

if it didn't then we have eliminated the obvious and we can start looking more in depth.


 > 
3. Resolution problems
 
 
When I got into the GNOME destop, I found the display options and set it to dual display and upped the resolution on the Sony monitor. A message came on screen that said that Ubuntu to change the "virtual resolution" to change the setting. So I did and it told me to log out to activate the changes. When I did, my Dell monitor(the one that I didn't change the settings on) did not show anything at all. My monitor itself said it could not display the setting, and the main panel was on that monitor and I didn't know how to move it to my Sony monitor.
 
 
Thanks.

which display settings app did you use, exactly? be as specific as you can, please, about everything you have done and tried.

there are often a dozen ways to skin a cat in ubuntu -- different methods work best with different hardware.

any idea what graphics card you have?

---

### Post by spiketheguitarist on 2009-07-10
> **earthpigg said:**
> click on the speaker thingie in upper right corner -> volume control -> preferences
 
check every damn thing you see, even if it looks silly. that will result in extra setting options being displayed. unmute everything, turn everything all the way up.
 
if that made it work, start unchecking and muting things you dont want, and adjusting volume to more sane levels.
 
if it didn't then we have eliminated the obvious and we can start looking more in depth.
 
 
 
 
which display settings app did you use, exactly? be as specific as you can, please, about everything you have done and tried.
 
there are often a dozen ways to skin a cat in ubuntu -- different methods work best with different hardware.
 
any idea what graphics card you have? 
 
the graphics card i have is a ATI Radeon X550 Diamond 256MB DDR2. the only app i used was system>preferences>display. as far as the sound goes i'll try what you suggested.

---

### Post by earthpigg on 2009-07-10
> **spiketheguitarist said:**
> the graphics card i have is a ATI Radeon X550 Diamond 256MB DDR2. the only app i used was system>preferences>display. as far as the sound goes i'll try what you suggested.

try going to system -> administration -> hardware drivers -> click around a bit, and tell us if you get any results.

if you can enable proprietary drivers and it finds any, try them out. for my video card, it found two proprietary drivers. 

you will have to restart in order to try any of them out.

---

### Post by spiketheguitarist on 2009-07-10
> **earthpigg said:**
> try going to system -> administration -> hardware drivers -> click around a bit, and tell us if you get any results.
 
if you can enable proprietary drivers and it finds any, try them out. for my video card, it found two proprietary drivers. 
 
you will have to restart in order to try any of them out.
 
 
ok, will do, i'm having to switch between windows and ubuntu since my wifi doesn't work in ubuntu. as for my audio issue, i tried switching things around like you said and didnt get alot of results. i did, however, see my soundcard in the preferences. there were a few choices for it. one had pulseaudio next to it and the other alsa.

---

### Post by spiketheguitarist on 2009-07-11
i just checked the hardware drivers and it was blank. it said i had no proprietary drivers at all.

---

### Post by egalvan on 2009-07-11
> **earthpigg said:**
> using aircrack-ng involves compiling your own drivers. aircrack is used to crack encryption on wifi networks - this requires giving your wireless network card abilities the manufacturer did not intend for it to have. making hardware do things it was not originally intended to do is sometimes called 'hacking' -- which is neither illegal nor immoral in itself, but it may void a warranty or two. something to keep in mind.
. i will humbly submit, however, that it is probably a bit beyond the scope of 'absolute beginner talk'.

:D

I have used aircrack-ng on two different laptops, running Hardy.
And both setups worked well. No "kernel compiling" or "driver compiling" needed.

The capabilities needed for this are not something esoteric, just not often used.
Network sniffers/analyzers use them.
No warranties should be voided.
It mainly requires NICs to enter promiscuous mode.

(
P.S.
I use these laptops to convince WiFi customers that, yes, their systems ARE vulnerable in default mode using an older B-type setup...
nothing convinces better than setting up a laptop on the owner/CEO/CFO's desk and watching it crack their B in five to ten minutes.
( a record was 1"28' flat , talk about stammering and stuttering from their "network guru" )
Jaws will drop, and heads will roll...
They really need to upgrade to avoid liability
)

---

### Post by Cato2 on 2009-07-11
For the sound problems, see the link in my sig.

---

