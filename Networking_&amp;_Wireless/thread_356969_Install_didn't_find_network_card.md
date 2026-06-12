---
title: "Install didn't find network card"
date: 2007-02-09
forum: Networking &amp; Wireless
---

### Post by TANGUN on 2007-02-09
The 6.10 server didn't find my network card. I'd appreciate any help in gathering information to fix it so that this server can see my home network / internet and my other PC can see the server as a website.

PIII-500
512MB RAM
20GB + 8GB HD

Misc other hardware.
I suppose a manufacturer and model might be nice hmmm? What? No Plug-and-Play?

---

### Post by gradedcheese on 2007-02-09
There is plug and play, it just doesn't find the hardware 100% of the time :)  Conversely, on Windows if I plug in my Belkin WiFi card, it prompts me for a driver that I'd have to download or have on a CD or something.  If I do it in Ubuntu, the card just works right away (ie: the driver and info for my card happens to be included).  

Please open a terminal and run 'lspci' and then paste the output here.  Namely, the line(s) that start with something like 'Ethernet Controller'

---

### Post by TANGUN on 2007-02-09
Well, no line for 'Ethernet Controller', but it seems to have found all other hardware. Host bridge, PCI bridge, ISA bridge, IDE bridge, USB controller, Bridge, VGA controller.  No network. There are two network cards installed, I didn't know which one (if any) would work. What else can I scan?

---

### Post by gradedcheese on 2007-02-09
could you please paste the whole lspci output here?  There is also a graphical tool called Device Manager (in System->Administration) that you can look at.  It's basically a front end for the entries in /sys

---

### Post by TANGUN on 2007-02-09
When I get home I'll try to repost it. I should clarify that this isn't the graphical install so command line instructions are all I can use.

---

### Post by TANGUN on 2007-02-09
lspci
Host bridge: Intel 440BX - 82443BX/ZX/DX Host bridge (rev 03)
PCI bridge: Intel 440BX - 82443BX/ZX/DX AGP bridge (rev 03)
ISA bridge: Intel 82371AB/EB/MB PIIX4 ISA (rev 02)
IDE interface: Intel 82371AB/EB/MB PIIX4 IDE (rev 01)
USB controller: Intel 82371AB/EB/MB PIIX4 USB (rev 01)
Bridge: Intel 82371AB/EB/MB PIIX4 ACPI (rev 02)
VGA compatible controller: ATI Technologies Inc 3D Rage IIC 215IIC [Mach 64 GT IIC] (rev 7a)

---

### Post by gradedcheese on 2007-02-09
Alright.  Can you tell us about the network card itself?  (make, model, etc)  Perhaps we can find some driver info for it.

---

### Post by TANGUN on 2007-02-10
One is a 3COM Etherlink III. It's got lots of numbers on it. 3C509B-TPO and  ASSY: 03-0020-010 Rev A. 

The other is a 'Plug and Play' Ethernet adapter. Possibly a ESL-816V. It's so old it still has a BNC connecter on it. I may have one other NIC if neither of these will work.

Both are ISA not PCI.

I found [this thread]("http://www.linuxforums.org/forum/ubuntu-help/61408-installation-3com-etherlink-iii-isa.html") on another forum. Should I try that?

---

### Post by gradedcheese on 2007-02-10
Wow, those are old!  To be quiet honest, I don't even remember the last time I've set up anything with an ISA card :(  Do try that thread's recommendations.  Hey, at least we know why those cards didn't show up in ls**pci** now ;)

---

### Post by TANGUN on 2007-02-10
I think I got it by following the other thread. Sweet. Now let's see what I can do with it.

---

### Post by nokturnal on 2008-02-23
I hate to hijack this thread but I have a very similar issue (not an ISA one though :))

I am trying to install a second NIC into an existing install of Ubuntu Gusty... The new NIC is a D-Link DFE 530 TX.

Here is my lspci:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory                                                                               Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400]                                                                               (rev a1)
02:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:0a.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 42)
02:0c.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
02:0d.0 Communication controller: Conexant HCF 56k Data/Fax Modem (rev 08)

It shows up in the lspci, but nothing in ifconfig.  I have read about issues with the 530TX but haven't come across a solution yet.

Does anyone know of one?

Cheers :)

---

### Post by Iowan on 2008-02-24
Probably better to start your own thread...
Check System>Administration>Network to see if it shows up there.  Otherwise, you might be able to add one in **/etc/network/interfaces**.

I naively think all cards are supported, so this may not work at all...

---

