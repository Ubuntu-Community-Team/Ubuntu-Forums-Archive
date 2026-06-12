---
title: "Problem with old ISA network adapter"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by ubuntuuser on 2005-11-16
Hi. I have a quite old PC here and I can't get the network adapter to work. The adapter is an old ISA card, and is, as far as I remember, NE2000 compatible. No live CD I have tried so far recognized the device. To get it to work, I would like to load the ne2000 kernel module, but I need to specify the I/O adress, and maybe even some IRQ. I have _**NO**_ access to the BIOS of this computer. How can I find out the correct address of the adapter or maybe set the I/O and IRQ manually?

Thanks in advance

---

### Post by az on 2005-11-16
Does the device manager show it?

If not, try
lspci
from a terminal.

If you still get nothin', I am assuming that your bios is password protected?  You can open the case and usually set the jumper to clear the password, or clear the bios.  Is this so?

---

### Post by suRoot on 2005-11-16
Well if it's an old ISA card, it probably has jumpers on it that allow you to set these manually.  You should at least be able to pop the case off & see what the thing is currently set to, or change as best you can guess.

---

### Post by ubuntuuser on 2005-11-18
Thanks for your help, guys, and sorry for replying so late. I have opened the box and looked for jumpers of any kind, on the card and on the motherboard ('cause YES, the BIOS is password protected and the actual owner of the computer doesn't know the pw anymore). Neither the board manual nor the board itself show any sign of a "clear password"-jumper. I have heard about removing the battery for a few days would reset the BIOS, but I'm not sure if that would help.

On the network adapter is also no jumper of any kind. Maybe something printed on the card will help you to help me :-) :
LANTECH 9834
WIN95 PnP
Full-duplex Ethernet
FCC ID: L8G2000PP
S/N: 004081005089


lspci says:
```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP Bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE bridge: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation NV4 [RivaTNT] (rev 04)
```

No sign of the network adapter :-(

---

### Post by suRoot on 2005-11-18
Yeah, it's plug & play so no jumpers.

There are a few tools in the isapnptools package which may help you:

```
sudo apt-get install isapnptools
```

Try running pnpdump after you install isapnptools & see if it finds anything.

If all else fails & you've got another Windows box close by with an ISA slot, you could always just throw it in there & see what IO / IRQ it shows in device manager.

---

### Post by az on 2005-11-18
I think isapnptools is defunct - it is for older kernels.

Yes, removing the battery for ten minutes would probably help.  Your clock will think it is 1985, but you can fix that.

Is there a way you can include a photo of the MB (or the make, model and version of the *motherbord* - there may be a manual on the net for it)

---

### Post by ubuntuuser on 2005-11-18
It looks like pnpdump finds the card:

```
# $Id: pnpdump_main.c,v 1.27 2001/04/30 21:54:53 fox Exp $
# Release isapnptools-1.26
# 
# This is free software, see the sources for details.
# This software has NO WARRANTY, use at your OWN RISK
# 
# For details of the output file format, see isapnp.conf(5)
# 
# For latest information and FAQ on isapnp and pnpdump see:
# http://www.roestock.demon.co.uk/isapnptools/
# 
# Compiler flags:  -DREALTIME -DHAVE_PROC -DENABLE_PCI -DHAVE_SCHED_SETSCHEDULER -DHAVE_NANOSLEEP -DWANT_TO_VALIDATE
# 
# Trying port address 0273
# Board 1 has serial identifier 8a 00 00 1a 24 19 80 8c 4a

# (DEBUG)
(READPORT 0x0273)
(ISOLATE PRESERVE)
(IDENTIFY *)
(VERBOSITY 2)
(CONFLICT (IO FATAL)(IRQ FATAL)(DMA FATAL)(MEM FATAL)) # or WARNING

# Card 1: (serial identifier 8a 00 00 1a 24 19 80 8c 4a)
# Vendor Id RTL8019, Serial Number 6692, checksum 0x8A.
# Version 1.0, Vendor version 1.0
# ANSI string -->Realtek Plug & Play Ethernet Card<--
#
# Logical device id @@@1980
#     Device supports I/O range check register
#
# Edit the entries below to uncomment out the configuration required.
# Note that only the first value of any range is given, this may be changed if required
# Don't forget to uncomment the activate (ACT Y) when happy

(CONFIGURE RTL8019/6692 (LD 0
#     Compatible device id PNP80d6
#     Logical device decodes 10 bit IO address lines
#         Minimum IO base address 0x0200
#         Maximum IO base address 0x03e0
#         IO base alignment 32 bytes
#         Number of IO addresses required: 32
# (IO 0 (SIZE 32) (BASE 0x0200) (CHECK))
#         *** Bad resource data (Clarifications 4.6.2): IRQ 2 invalid, changing to 9
#     IRQ 3, 4, 5, 9, 10, 11, 12 or 15.
#         High true, edge sensitive interrupt
# (INT 0 (IRQ 3 (MODE +E)))
#     Memory is non-writeable (ROM)
#     Memory is non-cacheable
#     Memory decode supports high address
#     memory is 8-bit only
#     memory is an expansion ROM
#     Minimum memory base address 0x0c0000
#     Maximum memory base address 0x0dc000
#     Range base alignment mask 0xff4000 bytes
#     Range length 16384 bytes
# Choose UPPER = Range, or UPPER = Upper limit to suit hardware
# (MEM 0 (BASE 0x0c0000) (MODE bu) (UPPER 0x0c4000))
# (MEM 0 (BASE 0x0c0000) (MODE br) (UPPER 0x004000))
 (NAME "RTL8019/6692[0]{Realtek Plug & Play Ethernet Card}")
# (ACT Y)
))
# End tag... Checksum 0x00 (OK)

# Returns all cards to the "Wait for Key" state
(WAITFORKEY)
```
What exactly does that tell me?

---

### Post by ubuntuuser on 2005-11-28
Just to finish this:

I reset the BIOS, then enabled an obscure Plug-and-Pray setting. After that, I was able to successfully load the module ne and network is finally working. Thanks.

---

### Post by az on 2005-11-28
plug and play is a spec by which the OS can set irq and hardware addresses for isa hardware.  It relies on vendor information to do that.  Since this information is not made available to open source, you have to do it by hand, as you did.

---

