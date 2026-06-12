---
title: "Trying to 'read' NIC with Ubuntu Live Drive"
date: 2015-10-01
forum: Networking &amp; Wireless
---

### Post by Aaditto_Shen on 2015-10-01
Hello,

I am a total newbie with Linux - in fact, I am pretty much a 'keeg' when it comes to computers (I am an artist if you please).

However, I am also kinda DIY-bug-bitten... so, I keep poking my head into things that I should probably stay out of!

For the past month I have been struggling with trying to 'revive' our small-office desktop PC - which had suffered a series of hard-shut-downs (from the UPS button), thanks to a rural-staff who got totally confused with the new Windows 8.1 interface.

I could go into a detailed description of what all has been happening - if an expert on the forum feels there is a need for that - but, for the moment, let me keep this brief, and ask the specific question I am trying to solve at the moment:-

[CURRENT PROBLEM:
The on-board LAN (Realtek) is not being read]

SUGGESTION FROM ON-LINE FORUM:
"Try booting your system with a Linux Live Drive and see if that can read the LAN controller"

So, I downloaded and installed < UBUNTU 14.04 LTS > and am running that as a 'live-drive' from the USB stick.

MY CONFUSION:
[I have learnt (from online searches) about two different 'methods' for querying about hardware > "lshw" & "dmidecode" - and I have tried both options]

HOWEVER, THEY SEEM TO COME UP WITH DIFFERENT 'FINDINGS'!

```
ubuntu@ubuntu:~$ sudo lshw
This command (in the Terminal) returns a long list of hardware information (including PCI details) - BUT NOTHING ABOUT THE LAN

ubuntu@ubuntu:~$ sudo lshw -class network
This command starts displaying... <PCI (sysfs)> but then it DOES NOTHING... ubuntu@ubuntu:~$ and the command-prompt comes back - ALTHOUGH, the PROMPT GETS FROZEN (that is, it does not blink) after blinking a few times - and seems to stay frozen 'forever' - till I type something else.
```

ON THE OTHER HAND:
```
ubuntu@ubuntu:~$ sudo dmidecode
This command returns THE LAN DETAILS LISTED CLEARLY (at the VERY END of the long list of hardware details... I am including a few just for reference - please go to the very end of the following output-details to find the relevant details in blue text)

[INDENT=2]-->

Slot Entry 16: ID 00:00, on-board[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]ubuntu@ubuntu:~$ sudo dmidecode[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# dmidecode 2.12[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]# SMBIOS entry point at 0x7be82d98[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]SMBIOS 2.4 present.[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]51 structures occupying 2234 bytes.[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]Table at 0x000E84B0.[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]Handle 0x0000, DMI type 0, 24 bytes[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]BIOS Information[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Vendor: Intel Corp.[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Version: WVG4110H.86A.0018.2012.0510.1507[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Release Date: 05/10/2012[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Address: 0xF0000[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Runtime Size: 64 kB[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    ROM Size: 1024 kB[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Characteristics:[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        PCI is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        BIOS is upgradeable[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        BIOS shadowing is allowed[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        ESCD support is available[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        Boot from CD is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        Selectable boot is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        BIOS ROM is socketed[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        EDD is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        5.25"/1.2 MB floppy services are supported (int 13h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        3.5"/720 kB floppy services are supported (int 13h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        3.5"/2.88 MB floppy services are supported (int 13h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        Print screen service is supported (int 5h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        8042 keyboard services are supported (int 9h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        Serial services are supported (int 14h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        Printer services are supported (int 17h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        CGA/mono video services are supported (int 10h)[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        ACPI is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        USB legacy is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        LS-120 boot is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        ATAPI Zip drive boot is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        BIOS boot specification is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]        Targeted content distribution is supported[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2].............
....................
..........................[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]Handle 0x0004, DMI type 4, 35 bytes[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]Processor Information[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Socket Designation: PROCESSOR[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Type: Central Processor[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Family: Unknown[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]    Manufacturer: Intel(R) Corp.[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]....[/INDENT]
[INDENT=2].....[/INDENT]
[INDENT=2].........................[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]Handle 0x0025, DMI type 10, 6 bytes[/INDENT]
[INDENT=2]On Board Device Information[/INDENT]
[INDENT=2]    Type: Ethernet[/INDENT]
[INDENT=2]    Status: Enabled[/INDENT]
[INDENT=2]    Description: Realtek 8111DL Gigabit Ethernet Device[/INDENT]
```

So, what is the deal here??


[LIST=1]
[*]Do the two commands <lshw> & <dmidecode> find fundamentally *LESS* & *MORE* information respectively?
[*]Do the two commands query at two different 'levels' of some kind - so that one is more reliable in certain cases and not so in other cases?
[*]Since <dmidecode> is able to list the details about my on-board NIC, can I assume that there is nothing wrong with the LAN controller as such? (That is, it hasn't been shot-out)
[/LIST]

Thanks in advance, for any input/ advise/ possible course-of-action suggestions.

In case it might be required:
MY SYSTEM SPECS:
 

[LIST]
[*]Motherboard:-
Intel Desktop Board DG41WV - Essential Series - motherboard - micro ATX - LGA775 Socket - G41 ([Here's a CNET link with the specs]("http://www.cnet.com/products/intel-desktop-board-dg41wv-essential-series-motherboard-micro-atx-lga775-socket-g41-series/specs/"))
[*]Onboard Gigabit Ethernet:-
Integrated 10/100/1000 Network Connection: REALTEK RTL8111DL
[*]OS:-
Windows 8.1 Single Language (English) 32-bit - Full Version (OEM) [Now auto-upgraded to Win 10]
[/LIST]

---

### Post by howefield on 2015-10-01
Hello and welcome.

Thread moved to the "*Networking & Wireless*" forum.

---

### Post by tgalati4 on 2015-10-01
Welcome to the forums:

Post the output of:

```
lspci | grep Ethernet
```

It's possible that your network chip is burned up.  It happens.  Using an UPS means the ground is typically isolated, so any stray voltage will find its way out another way, like through the network chipset.  Anything over 30 volts will fry the chip.  Is your UPS plugged into an electrical outlet with a functioning ground?

If you have an extra slot in your PC, put in a new network card.

---

### Post by Aaditto_Shen on 2015-10-03
> **tgalati4 said:**
> Welcome to the forums:

Post the output of:

```
lspci | grep Ethernet
```

It's possible that your network chip is burned up.  It happens.  Using an UPS means the ground is typically isolated, so any stray voltage will find its way out another way, like through the network chipset.  Anything over 30 volts will fry the chip.  Is your UPS plugged into an electrical outlet with a functioning ground?

If you have an extra slot in your PC, put in a new network card.



Hello,

Thanks for the welcome - and thanks for the prompt response... Sorry, I got held-up yesterday with a thunder-storm-hit net-connection, so couldn't check this earlier.

First, (I've already mentioned I am a total noob at this!)...

What's the "|" (pipe-key?) supposed to mean, in the code you asked me to run?
```
lspci | grep Ethernet
```

Am I supposed to TYPE the pipe-key when typing the code into Terminal - or does that 'signify' something else?

I've tried typing the code in all three following manner...

```
lspci | grep Ethernet
```
Result: Nothing happens - the dot-prompt comes back in the next line

```
lspci \ grep Ethernet
```
```
lspci -grep Ethernet
```
Result: In both cases, it returns a LONG LIST OF 'options' (obviously for the lspci basic command) - "Basic display modes:" options... "Display options:" options... "Resolving of device ID's to names:" options... and so on.

Here's the output when I run just the lspci command...
```
sudo lspci


00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)

```

To answer your last question - YES, our UPS is plugged-into a GROUNDED (220V power-supply) plug-point... We do our own electrical work at the village-project and so, I know that the grounding is done with all seriousness - I even checked the 'grounding' a while back, with a 'test-lamp', and it seems okay.

HOWEVER, this is a back-of-beyond village-electrical-distribution-system (the main power-supply), in a 'third-world-country' - so, severe fluctuations, 'single-phasing', sudden surges/ outages are QUITE COMMON!
Every now and then (maybe twice a week) the UPS would TRIP - with a long beep - most probably due to a fluctiation which was too rapid for it to handle (it's a decent, and not-very-old UPS)

Yes, I do have a set of PCIe/PCI slots on my MoBo - I'll have to source a network-card from somewhere to see if that works... Will get back to you if I can manage to get that done.

Thanks again.

---

### Post by tgalati4 on 2015-10-03
The "pipe" command simply means "take the output of one command and pipe it to another command".  It's a simple way to filter a lot of output.

Typically, your network card would look like:

> tgalati4@Mint17 ~ $ lspci | grep Ethernet
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)


The fact that it doesn't show up means that it is missing.

It's possible that your UPS is damaged.  It has MOV's  (metal oxide varistors) just like a power strip and they wear out over time with too many hits.  I've pulled apart UPS's that have had lightning damage--they get pretty burned up.  And they didn't protect the equipment they were connected to because the burned up components left a nice coating of carbon dust on the inside. The soot acted as a fat resistor that allowed high voltage (but low current) to pass right through to the PC's that were plugged into it.  This is something that the UPS engineers failed to consider.

---

### Post by Aaditto_Shen on 2015-10-08
> **tgalati4 said:**
> The "pipe" command simply means "take the output of one command and pipe it to another command".  It's a simple way to filter a lot of output.

Typically, your network card would look like:

[COLOR=#000000]*tgalati4@Mint17 ~ $ lspci | grep Ethernet*[/COLOR]
[COLOR=#000000]*02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)*[/COLOR]

The fact that it doesn't show up means that it is missing.

It's possible that your UPS is damaged.  It has MOV's  (metal oxide varistors) just like a power strip and they wear out over time with too many hits.  I've pulled apart UPS's that have had lightning damage--they get pretty burned up.  And they didn't protect the equipment they were connected to because the burned up components left a nice coating of carbon dust on the inside. The soot acted as a fat resistor that allowed high voltage (but low current) to pass right through to the PC's that were plugged into it.  This is something that the UPS engineers failed to consider.



Okay, so just to clarify that I have got this right:-

I should run the line of code as follows, in my Terminal:

> ubuntu@ubuntu:~$ [COLOR=#000000]*lspci | grep Ethernet*[/COLOR]

... And that SHOULD return my Ethernet controller details, like the example you have given:> [COLOR=#000000]*tgalati4@Mint17 ~ $ lspci | grep Ethernet*[/COLOR]
[COLOR=#000000]*02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)*[/COLOR]

... And you are saying that _since NOTHING HAPPENS when I run that code_ (as well as the fact that it's not listed in the *basic lspci *command, without the |*grep Ethernet*?), _means that it is missing_?


Okay, got that. Thanks.

_However, I am *still confused *about the **original question** of mine_:-


**This command *DOES RETURN* THE LAN DETAILS** LISTED CLEARLY (at the VERY END of the long list of hardware details...


> ubuntu@ubuntu:**~$ sudo dmidecode**
.....
.........................
Handle 0x0025, DMI type 10, 6 bytes
On Board Device Information
Type: Ethernet
Status: Enabled
**Description: Realtek 8111DL Gigabit Ethernet Device**

So, how come <lspci> _DOES NOT SHOW_ and <dmidecode> _CLEARLY LISTS_ the details of my Ethernet controller??


About my **UPS** being damaged...

I sort-of know what you mean when you are talking about 'MOV's wearing-out over time' - we are *constantly/ *having to 'brush/ clean/ replace' various electrical fittings that get severely affected/ crusted/ damaged due to the weather/ lightening/ and so many other issues!

However, if the UPS was *burnt*, then it would *never *be able to do the job!
But our's will *usually *'back-up' pretty okay when there is a power-failure (which is like 3-10 times everyday, here in an Indian village!)

So, while the UPS may well be 'damaged' (and so is not at its optimum) - it is definitely still functioning.

**Do you suggest that I CHANGE the UPS in any case?**

Or do you think I could try opening the box to see if I can 'clean the soot' in there?
We are perpetually in a fund-crunch situation - and every penny is a nasty pinch, literally!

---

### Post by tgalati4 on 2015-10-09
There is no easy way to test an UPS.  I use a 100-watt incandescent lightbulb and measure the run time of the batteries.  If the bulb flickers or dims, then you know that the power is not consistent during the test.  That dirty power will cause problems with your computer when running on batteries.  Most UPS's are designed to handle perhaps 1 power outage every 6 months, not 3-times per day.  They are just not that robust.

If you have access to an oscilloscope, you can see the power wave of an UPS while on batteries.  It is not pretty.  Some look like a stepped pyramid.  Others (more expensive, better quality) are sine waves but with lots of noise.  Over time, several power outage hits will degrade the filters (capacitors, inductors, diodes, MOV's, etc) and the noise will increase.  So besides just battery charge (which is easy to measure), the actual filtering of noisy power is more difficult to measure and keep track of.

*dmidecode* is just reading from your BIOS; that doesn't mean that the network card is actually working.  Linux expects perfect hardware.  If it doesn't show up in *lspci* then you have no network card.  Simple.

In this environment, I would switch to low-power computers and use solar power and batteries and remove yourself from the grid completely.  And yes it takes money, but you have to weigh the cost versus inconvenience.

---

### Post by Aaditto_Shen on 2015-10-10
> **tgalati4 said:**
> There is no easy way to test an UPS.  I use a 100-watt incandescent lightbulb and measure the run time of the batteries.  If the bulb flickers or dims, then you know that the power is not consistent during the test.  That dirty power will cause problems with your computer when running on batteries.  Most UPS's are designed to handle perhaps 1 power outage every 6 months, not 3-times per day.  They are just not that robust.

If you have access to an oscilloscope, you can see the power wave of an UPS while on batteries.  It is not pretty.  Some look like a stepped pyramid.  Others (more expensive, better quality) are sine waves but with lots of noise.  Over time, several power outage hits will degrade the filters (capacitors, inductors, diodes, MOV's, etc) and the noise will increase.  So besides just battery charge (which is easy to measure), the actual filtering of noisy power is more difficult to measure and keep track of.

*dmidecode* is just reading from your BIOS; that doesn't mean that the network card is actually working.  Linux expects perfect hardware.  If it doesn't show up in *lspci* then you have no network card.  Simple.

In this environment, I would switch to low-power computers and use solar power and batteries and remove yourself from the grid completely.  And yes it takes money, but you have to weigh the cost versus inconvenience.


Thanks a tonne!
Got your point(s)!!!
Cheers...

---

