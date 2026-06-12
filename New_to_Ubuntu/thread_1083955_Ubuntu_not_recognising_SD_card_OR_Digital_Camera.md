---
title: "Ubuntu not recognising SD card OR Digital Camera"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by patches23 on 2009-03-01
Hi there

Absoloute newbie here so hope Im posting in the right section, and please be gentle. [-o<

Ubuntu will not recognise my sd card at all ( Ive had a good read on this and it would appear its a bug with Ubuntu?)

But Im confused as to why when I plug the camera in via USB ( in place of SD card), still nothing!

Any clues, any obvious terminal commands I can try and show you to help?

Cheers
Michelle

---

### Post by tea for one on 2009-03-01
Good evening

A little more detail is required to find a solution to your problem. For example:-

The make and model of your camera?
Which software are you using - F Spot - Digikam or other?
Does you camera appear as a Mass Storage Device under Places?
If you put the SD card in a card reader, is it recognised automatically by Ubuntu?

F Spot completely failed for my camera but Digikam works perfectly, yet I do not know why one software package performs and the other does not?

My first advice would be to try another package but if that fails then please supply some more details and I am sure the answer will be forthcoming in a few minutes.

---

### Post by neu2buntu on 2009-03-01
try what i did ,boot up with your sd card in the slot,i had to do this on my acer aspire one netbook,there are 2 sd slots on it and whichever slot i boot with the card in is recognised and it can be removed and put in and it is still seen,but only on the slot i booted with card in ...the other slot doesnt see the sd card , not sure if this a ubuntu bug or just the acer!!!!.................................also if im already up and running (booted) the sd card is not seen by either slot or command ```
lspci
``` (maybe lspci wont show what is in sd slot,not too sure about that!!!):lolflag:

---

### Post by patches23 on 2009-03-01
> **tea for one said:**
> Good evening

A little more detail is required to find a solution to your problem. For example:-

The make and model of your camera?
Which software are you using - F Spot - Digikam or other?
Does you camera appear as a Mass Storage Device under Places?
If you put the SD card in a card reader, is it recognised automatically by Ubuntu?.

Hi

Thankyou for the reply, I wasnt aware of Digikam software so have installed that and now have cannot detect camera under auto-detect..
SD card doesnt appear anywhere...ever!

( Camera is Coolpix L5)

---

### Post by patches23 on 2009-03-01
> **neu2buntu said:**
> try what i did ,boot up with your sd card in the slot,i had to do this on my acer aspire one netbook,there are 2 sd slots on it and whichever slot i boot with the card in is recognised and it can be removed and put in and it is still seen,but only on the slot i booted with card in ...the other slot doesnt see the sd card , not sure if this a ubuntu bug or just the acer!!!!.................................also if im already up and running (booted) the sd card is not seen by either slot or command ```
lspci
``` (maybe lspci wont show what is in sd slot,not too sure about that!!!):lolflag:

Hey :)

Ive tried booting with/without the card before now, no joy .

Here is my lspci output which I have looked at before and have concluded that ubuntu can see the SD slot, just not the card?  ( However cannot see any notification of slot at all in 'Places'  ( Im assuming thats where it would appear?

patches@patches-laptop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
patches@patches-laptop:~$ 


Cheers for the response.

---

### Post by neu2buntu on 2009-03-01
hmmm give me a minute to i see what i can come up with.... and my sd card from my digital camera loads onto desktop...........might actually show in places too,havnt checked that,.. im thinking its maybe something to do with your user privileges.....be back in 5

---

### Post by neu2buntu on 2009-03-01
right try this (as im not sure if this is default setting)............... goto > system > administration > users and groups > unlock (type password) > click on your username > properties > user privileges > and make sure that "access external storage devices automatically" is ticked on................  as the sd card is seen as a storage device!!!!

---

### Post by patches23 on 2009-03-01
Cheers, just tried, was already ticked, unticked and re-ticked.  No joy - good thinking though Batman :)

---

### Post by neu2buntu on 2009-03-01
to the bat mobile robin...lol... i will solve this one way or another....as an earlier post asked "is it an external or internal card reader?" this might help somewhat!!!!!!!!

---

### Post by patches23 on 2009-03-01
Ah, yes, internal.  ( on a Compaq nx9105 if that helps)

Cheers B ;)

---

### Post by neu2buntu on 2009-03-01
just back from gotham city...lol... here we go try ...> system > administration > synaptic package manager > click search (magnifying glass icon) > type "mount" 
   if not already installed ...tick 
[1] gnome-mount
[2] gnome-volume-manager
[3] usbmount    (just incase the card is also seen as an "usb" device)
[4] pmount ----- i dont have this installed myself but looking at the description it might help--try the 1st 3 before installing this one to see!!   its possible that theses are already installed by default,as im forever installing stuff and not taking note of it...


..
also right click all the above in the package manager and install any recomended packages too...it will say "mark recommended for installation" and also "mark suggested for installation" will do no harm to install these either

---

### Post by tea for one on 2009-03-01
Hello again

Not much luck yet but I am pretty sure this can be solved.

My previous camera was a Coolpix L4 and that worked fine with Digikam but I see that your camera Coolpix L5 does not appear in the drop down list of supported devices (I'm using Ubuntu 8.04 LTS).

Anyway, here are a couple of suggestions:-

(a) Turn off your camera, plug the camera into the PC via USB, then turn on the camera - Is it recognised by Ubuntu?

(b) Install gThumb Image Viewer via Applications then Add/Remove programs. gThumb is a pretty reliable failsafe application.

---

### Post by patches23 on 2009-03-01
Cheers both, I have tried all of the above, nothing working as of yet.  I really appreciate you taking the time to help me though.  Keep em coming!

Yes I noted that L5 wasnt listed, hmmm.

Anyway I can check if SD slot is ok? ( or does this come under the lspci command I assume)  ( just to rule that out)

I guess Im just a bit shocked that neither the SD or USB are working, makes me not love ubuntu :(   ( or my lack of knowledge may be to blame! )

Chars!

---

### Post by tea for one on 2009-03-01
Does your camera have a "mode" selection switch? 

On some cameras, I have noticed that you have to change the mode from "shooting" to "viewing" before the software will recognise the camera?

---

### Post by patches23 on 2009-03-01
Ah, Nah, I know what you mean, mine has just always auto-recognised, I tried that before posting too, just to make sure I wasnt being a complete d'ck.!

---

### Post by psychomichael on 2009-03-01
#disregard...issue corrected itself.

---

### Post by neu2buntu on 2009-03-01
from ```
lspci -vv
``` im getting ```
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```  which looks like my sd card slot..... from your earlier "lspci" i think your card reader is showing as in ```
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
``` am by no means any expert on this!!!!   so i think the problem of not being able to mount the card is just round the corner.... as for the camera im clueless,..i will work at the "sd" card issue!!!

---

### Post by neu2buntu on 2009-03-01
looking at "man lspci" try command ```
lspci -k
``` to see if the drivers are running for your card bus..... heres my example 

```
04:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
04:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
    Kernel modules: sdhci-pci
04:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
04:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

```     although my sd card wont work other than from booting with it in slot, the drivers are loaded...as in ```
Kernel driver in use: sdhci-pci
``` ... post the output of ```
lspci -k 
```to we see whats going on there....:rolleyes:

---

### Post by patches23 on 2009-03-01
Heres the whole lot -

patches@patches-laptop:~$ lspci -k
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
	Kernel driver in use: agpgart-amd64
	Kernel modules: amd64-agp
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
	Kernel driver in use: ohci_hcd
	Kernel modules: ohci-hcd
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
	Kernel modules: snd-intel8x0m
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
	Kernel driver in use: pata_amd
	Kernel modules: pata_amd
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
	Kernel modules: shpchp
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
	Kernel modules: shpchp
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Kernel driver in use: k8temp
	Kernel modules: k8temp
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
	Kernel modules: nvidiafb, rivafb
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)


Any joy from that Mr B? ;)

Im off for tonight, head hurty.... lol

Thanks very much for your help this far, will check in tomorrow ;)

---

### Post by Hobgoblin on 2009-03-01
Just a thought.

Do **any** USB devices work?

---

### Post by patches23 on 2009-03-02
> **Hobgoblin said:**
> Just a thought.

Do **any** USB devices work?

Hmm, well I have another camera I can check, but no other USB devices off the top of my head, just got to find the usb cable now.. :rolleyes:

---

### Post by patches23 on 2009-03-02
Right, well cant lay my hands on the other USB lead for the other camera at the mo. Will keep hunting and/or buy a new one!

Any more suggestions peeps?  particularly regarding the SD card issue.

Thanks once again

---

### Post by tea for one on 2009-03-02
I think that we should test the read/write ability of the SD card and the card reader.

Therefore, I suggest that you should:-

Insert the card
Copy a text or picture file to the card
Unmount the card (Right click icon on Desktop and select Unmount Volume)
Re-insert the card to view the recently copied file

If you can see the new file, then we may be able eliminate the card and the card reader as the problem area.

Secondly, can you also read and write to a memory stick via USB?

Again, this will help to eliminate hardware difficulties.

---

### Post by patches23 on 2009-03-02
Errmmm,  Cant see the card to copy an image too!  That was my problem, it just doesnt exist..!  Cant see the reader or card.


Heres hoping you are just going to call me a muppet and tell me I should have done 'so and so' first!

---

### Post by tea for one on 2009-03-02
Please confirm that your SD card and reader have previously functioned perfectly before you installed Ubuntu. 

Which operating system were you using before Ubuntu?

Using Ubuntu, can you read and write to a memory stick (flash drive) via a USB port?

---

### Post by patches23 on 2009-03-02
> **tea for one said:**
> Please confirm that your SD card and reader have previously functioned perfectly before you installed Ubuntu. 

Which operating system were you using before Ubuntu?

Using Ubuntu, can you read and write to a memory stick (flash drive) via a USB port?


Hey :)

I have never used the laptop with any other OS so a hardware issue is always a possibility, however I would have thought the likelihood of the the SD card reader and all the USBs being out would be very slim.  Ive no reason to think they dont work.

Just finding out if other half has USB stick on him.

---

### Post by patches23 on 2009-03-02
Just found his IPOD, plugged in, Ubuntu recognised instantly.

---

### Post by neu2buntu on 2009-03-02
u still not got any further...lol?    im starting to think that the sd/mmc card is using the wrong driver and the right 1 is being blacklisted can u post output of ```
dmesg
``` ```
lsmod
``` and copy and paste the file ```
gedit /etc/modprobe.d/blacklist
``` do these commands with the sd card in slot.


and also a screeshot of > system > administration > hardware drivers ... use keys [alt and prtsc] with this window opened.,

---

### Post by tea for one on 2009-03-03
Good morning

I have never encountered blacklisted SD cards before and I must admit that I am curious to see how this solution develops.

I regret that I am unable to help further but I am interested to see the final result.

---

### Post by patches23 on 2009-03-03
DMESG - 

[    0.920031] EISA bus registered
[    0.920031] ACPI: bus type pci registered
[    0.920031] PCI: PCI BIOS revision 2.10 entry at 0xfd8bc, last bus=2
[    0.920031] PCI: Using configuration type 1 for base access
[    0.921605] ACPI: EC: Look up EC in DSDT
[    0.925524] ACPI: Interpreter enabled
[    0.925533] ACPI: (supports S0 S3 S4 S5)
[    0.925564] ACPI: Using IOAPIC for interrupt routing
[    0.930810] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    1.000233] ACPI: EC: GPE = 0x21, I/O: command/status = 0x66, data = 0x62
[    1.000241] ACPI: EC: driver started in interrupt mode
[    1.000370] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.000505] PCI: 0000:00:00.0 reg 10 32bit mmio: [f0000000, f7ffffff]
[    1.000620] PCI: 0000:00:01.1 reg 20 io port: [2040, 207f]
[    1.000629] PCI: 0000:00:01.1 reg 24 io port: [2000, 203f]
[    1.000648] pci 0000:00:01.1: PME# supported from D3hot D3cold
[    1.000656] pci 0000:00:01.1: PME# disabled
[    1.000687] PCI: 0000:00:02.0 reg 10 32bit mmio: [e8000000, e8000fff]
[    1.000719] pci 0000:00:02.0: supports D1
[    1.000724] pci 0000:00:02.0: supports D2
[    1.000729] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.000736] pci 0000:00:02.0: PME# disabled
[    1.000760] PCI: 0000:00:02.1 reg 10 32bit mmio: [e8001000, e8001fff]
[    1.000792] pci 0000:00:02.1: supports D1
[    1.000797] pci 0000:00:02.1: supports D2
[    1.000802] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.000809] pci 0000:00:02.1: PME# disabled
[    1.000834] PCI: 0000:00:02.2 reg 10 32bit mmio: [e8004000, e80040ff]
[    1.000867] pci 0000:00:02.2: supports D1
[    1.000871] pci 0000:00:02.2: supports D2
[    1.000876] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold
[    1.000883] pci 0000:00:02.2: PME# disabled
[    1.000919] PCI: 0000:00:06.0 reg 10 io port: [1400, 14ff]
[    1.000928] PCI: 0000:00:06.0 reg 14 io port: [1c00, 1c7f]
[    1.000937] PCI: 0000:00:06.0 reg 18 32bit mmio: [e8002000, e8002fff]
[    1.000963] pci 0000:00:06.0: supports D1
[    1.000967] pci 0000:00:06.0: supports D2
[    1.000991] PCI: 0000:00:06.1 reg 10 io port: [1800, 18ff]
[    1.001000] PCI: 0000:00:06.1 reg 14 io port: [1c80, 1cff]
[    1.001009] PCI: 0000:00:06.1 reg 18 32bit mmio: [e8003000, e8003fff]
[    1.001036] pci 0000:00:06.1: PME# supported from D3cold
[    1.001043] pci 0000:00:06.1: PME# disabled
[    1.001086] PCI: 0000:00:08.0 reg 20 io port: [2080, 208f]
[    1.001320] PCI: 0000:02:00.0 reg 10 32bit mmio: [e8108000, e81087ff]
[    1.001331] PCI: 0000:02:00.0 reg 14 32bit mmio: [e8100000, e8103fff]
[    1.001371] pci 0000:02:00.0: supports D1
[    1.001375] pci 0000:02:00.0: supports D2
[    1.001380] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot
[    1.001387] pci 0000:02:00.0: PME# disabled
[    1.001418] PCI: 0000:02:01.0 reg 10 io port: [7000, 70ff]
[    1.001428] PCI: 0000:02:01.0 reg 14 32bit mmio: [e8108800, e81088ff]
[    1.001466] pci 0000:02:01.0: supports D1
[    1.001471] pci 0000:02:01.0: supports D2
[    1.001476] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    1.001483] pci 0000:02:01.0: PME# disabled
[    1.001503] PCI: 0000:02:02.0 reg 10 32bit mmio: [e8104000, e8105fff]
[    1.001566] PCI: 0000:02:04.0 reg 10 32bit mmio: [e8106000, e8106fff]
[    1.001585] pci 0000:02:04.0: supports D1
[    1.001589] pci 0000:02:04.0: supports D2
[    1.001594] pci 0000:02:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    1.001602] pci 0000:02:04.0: PME# disabled
[    1.001633] PCI: 0000:02:04.1 reg 10 32bit mmio: [e8107000, e8107fff]
[    1.001651] pci 0000:02:04.1: supports D1
[    1.001656] pci 0000:02:04.1: supports D2
[    1.001661] pci 0000:02:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    1.001668] pci 0000:02:04.1: PME# disabled
[    1.001697] PCI: 0000:02:04.2 reg 10 io port: [7400, 743f]
[    1.001780] PCI: bridge 0000:00:0a.0 io port: [3000, 7fff]
[    1.001788] PCI: bridge 0000:00:0a.0 32bit mmio: [e8100000, e97fffff]
[    1.001868] PCI: 0000:01:00.0 reg 10 32bit mmio: [ea000000, eaffffff]
[    1.001879] PCI: 0000:01:00.0 reg 14 32bit mmio: [f8000000, fbffffff]
[    1.001890] PCI: 0000:01:00.0 reg 18 32bit mmio: [fc000000, fc07ffff]
[    1.001916] PCI: 0000:01:00.0 reg 30 32bit mmio: [0, 1ffff]
[    1.001984] PCI: bridge 0000:00:0b.0 32bit mmio: [ea000000, eaffffff]
[    1.001993] PCI: bridge 0000:00:0b.0 32bit mmio pref: [f8000000, fc0fffff]
[    1.002008] bus 00 -> node 0
[    1.002020] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.002213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P0._PRT]
[    1.002318] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP0._PRT]
[    1.036002] ACPI: PCI Interrupt Link [LNK1] (IRQs 16 18 19) *0
[    1.036488] ACPI: PCI Interrupt Link [LNK2] (IRQs 16 18 19) *0
[    1.036934] ACPI: PCI Interrupt Link [LNK3] (IRQs 17) *0
[    1.037381] ACPI: PCI Interrupt Link [LNK4] (IRQs 16 18 19) *0, disabled.
[    1.037831] ACPI: PCI Interrupt Link [LNK5] (IRQs 16 18 19) *0
[    1.038270] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22) *0
[    1.038709] ACPI: PCI Interrupt Link [LUS0] (IRQs 20 21 22) *0
[    1.039163] ACPI: PCI Interrupt Link [LUS1] (IRQs 20 21 22) *0
[    1.039603] ACPI: PCI Interrupt Link [LUS2] (IRQs 20 21 22) *0
[    1.040052] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22) *0, disabled.
[    1.040492] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22) *0
[    1.040938] ACPI: PCI Interrupt Link [LMCI] (IRQs 20 21 22) *0
[    1.041383] ACPI: PCI Interrupt Link [LPID] (IRQs 20 21 22) *0, disabled.
[    1.041840] ACPI: PCI Interrupt Link [LTID] (IRQs 20 21 22) *0, disabled.
[    1.042189] Linux Plug and Play Support v0.97 (c) Adam Belay
[    1.042262] pnp: PnP ACPI init
[    1.042280] ACPI: bus type pnp registered
[    1.072643] pnp: PnP ACPI: found 13 devices
[    1.072650] ACPI: ACPI bus type pnp unregistered
[    1.072657] PnPBIOS: Disabled by ACPI PNP
[    1.073373] PCI: Using ACPI for IRQ routing
[    1.073584] NET: Registered protocol family 8
[    1.073584] NET: Registered protocol family 20
[    1.073584] NetLabel: Initializing
[    1.073584] NetLabel:  domain hash size = 128
[    1.073584] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.073584] NetLabel:  unlabeled traffic allowed by default
[    1.073584] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    1.073584]    actual entries 65620
[    1.073584] AppArmor: AppArmor Filesystem Enabled
[    1.073584] ACPI: RTC can wake from S4
[    1.073584] system 00:01: ioport range 0x8000-0x807f has been reserved
[    1.073584] system 00:01: ioport range 0x8080-0x80ff has been reserved
[    1.073584] system 00:01: ioport range 0x8400-0x847f has been reserved
[    1.073584] system 00:01: ioport range 0x8480-0x84ff has been reserved
[    1.073584] system 00:01: ioport range 0x8800-0x887f has been reserved
[    1.073584] system 00:01: ioport range 0x8880-0x88ff has been reserved
[    1.073584] system 00:01: ioport range 0x2040-0x207f has been reserved
[    1.073584] system 00:01: ioport range 0x2000-0x203f has been reserved
[    1.073584] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    1.073584] system 00:02: iomem range 0xfec00000-0xfec00fff has been reserved
[    1.073584] system 00:02: iomem range 0xfee00000-0xfeefffff has been reserved
[    1.073584] system 00:02: iomem range 0xfed00000-0xfed00fff has been reserved
[    1.073584] system 00:03: ioport range 0x200-0x20f has been reserved
[    1.073584] system 00:03: ioport range 0x680-0x6ff has been reserved
[    1.073584] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    1.073584] system 00:03: ioport range 0xfe00-0xfe01 has been reserved
[    1.110664] pci 0000:02:04.0: BAR 10: can't allocate mem resource [0xec000000-0xe97fffff]
[    1.110674] pci 0000:02:04.1: BAR 10: can't allocate mem resource [0xec000000-0xe97fffff]
[    1.110684] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    1.110691] pci 0000:02:04.0:   IO window: 0x003000-0x0030ff
[    1.110699] pci 0000:02:04.0:   IO window: 0x003400-0x0034ff
[    1.110707] pci 0000:02:04.0:   PREFETCH window: 0x50000000-0x53ffffff
[    1.110716] pci 0000:02:04.1: CardBus bridge, secondary bus 0000:07
[    1.110722] pci 0000:02:04.1:   IO window: 0x003800-0x0038ff
[    1.110729] pci 0000:02:04.1:   IO window: 0x003c00-0x003cff
[    1.110737] pci 0000:02:04.1:   PREFETCH window: 0x54000000-0x57ffffff
[    1.110745] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    1.110752] pci 0000:00:0a.0:   IO window: 0x3000-0x7fff
[    1.110759] pci 0000:00:0a.0:   MEM window: 0xe8100000-0xe97fffff
[    1.110767] pci 0000:00:0a.0:   PREFETCH window: 0x00000050000000-0x00000057ffffff
[    1.110778] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:01
[    1.110784] pci 0000:00:0b.0:   IO window: disabled
[    1.110792] pci 0000:00:0b.0:   MEM window: 0xea000000-0xeaffffff
[    1.110801] pci 0000:00:0b.0:   PREFETCH window: 0x000000f8000000-0x000000fc0fffff
[    1.110821] pci 0000:00:0a.0: setting latency timer to 64
[    1.111494] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    1.111511] pci 0000:02:04.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    1.112117] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[    1.112129] pci 0000:02:04.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    1.112147] bus: 00 index 0 io port: [0, ffff]
[    1.112152] bus: 00 index 1 mmio: [0, ffffffff]
[    1.112158] bus: 02 index 0 io port: [3000, 7fff]
[    1.112163] bus: 02 index 1 mmio: [e8100000, e97fffff]
[    1.112169] bus: 02 index 2 mmio: [50000000, 57ffffff]
[    1.112174] bus: 02 index 3 mmio: [0, 0]
[    1.112179] bus: 03 index 0 io port: [3000, 30ff]
[    1.112185] bus: 03 index 1 io port: [3400, 34ff]
[    1.112190] bus: 03 index 2 mmio: [50000000, 53ffffff]
[    1.112196] bus: 03 index 3 mmio: [0, 0]
[    1.112201] bus: 07 index 0 io port: [3800, 38ff]
[    1.112206] bus: 07 index 1 io port: [3c00, 3cff]
[    1.112212] bus: 07 index 2 mmio: [54000000, 57ffffff]
[    1.112217] bus: 07 index 3 mmio: [0, 0]
[    1.112222] bus: 01 index 0 mmio: [0, 0]
[    1.112227] bus: 01 index 1 mmio: [ea000000, eaffffff]
[    1.112232] bus: 01 index 2 mmio: [f8000000, fc0fffff]
[    1.112237] bus: 01 index 3 mmio: [0, 0]
[    1.112259] NET: Registered protocol family 2
[    1.112493] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.113086] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.114164] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.114700] TCP: Hash tables configured (established 131072 bind 65536)
[    1.114707] TCP reno registered
[    1.114882] NET: Registered protocol family 1
[    1.115129] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.951192]  it is
[    2.851839] Freeing initrd memory: 8014k freed
[    2.852085] Simple Boot Flag at 0x37 set to 0x1
[    2.853244] audit: initializing netlink socket (disabled)
[    2.853269] type=2000 audit(1236063738.852:1): initialized
[    2.868079] highmem bounce pool size: 64 pages
[    2.868093] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.873358] VFS: Disk quotas dquot_6.5.1
[    2.873541] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.873741] msgmni has been set to 1761
[    2.874006] io scheduler noop registered
[    2.874012] io scheduler anticipatory registered
[    2.874018] io scheduler deadline registered
[    2.874045] io scheduler cfq registered (default)
[    2.874235] pci 0000:01:00.0: Boot video device
[    2.874889] isapnp: Scanning for PnP cards...
[    3.228654] isapnp: No Plug & Play device found
[    3.309842] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.311782] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[    3.311800] serial 0000:00:06.1: PCI INT B -> Link[LMCI] -> GSI 22 (level, low) -> IRQ 22
[    3.311812] serial 0000:00:06.1: PCI INT B disabled
[    3.314964] brd: module loaded
[    3.315117] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.315356] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.325091] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.332253] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.332263] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.332269] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.332275] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.332282] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.333217] mice: PS/2 mouse device common for all mice
[    3.333499] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.333529] rtc0: alarms up to one year, y3k
[    3.333772] EISA: Probing bus 0 at eisa.0
[    3.333785] Cannot allocate resource for EISA slot 1
[    3.333791] Cannot allocate resource for EISA slot 2
[    3.333796] Cannot allocate resource for EISA slot 3
[    3.333801] Cannot allocate resource for EISA slot 4
[    3.333807] Cannot allocate resource for EISA slot 5
[    3.333812] Cannot allocate resource for EISA slot 6
[    3.333817] Cannot allocate resource for EISA slot 7
[    3.333822] Cannot allocate resource for EISA slot 8
[    3.333827] EISA: Detected 0 cards.
[    3.333833] cpuidle: using governor ladder
[    3.333839] cpuidle: using governor menu
[    3.335011] TCP cubic registered
[    3.335061] Using IPI No-Shortcut mode
[    3.335510] registered taskstats version 1
[    3.335748]   Magic number: 1:905:14
[    3.335774] tty ttycb: hash matches
[    3.335956] rtc_cmos 00:06: setting system clock to 2009-03-03 07:02:19 UTC (1236063739)
[    3.335964] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.335969] EDD information not available.
[    3.336482] Freeing unused kernel memory: 424k freed
[    3.336630] Write protecting the kernel text: 2580k
[    3.336720] Write protecting the kernel read-only data: 940k
[    3.360701] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.816075] fuse init (API version 7.9)
[    4.136024] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.144029] processor ACPI0007:00: registered as cooling_device0
[    4.178476] Marking TSC unstable due to TSC halts in idle
[    4.187660] thermal LNXTHERM:01: registered as thermal_zone0
[    4.201189] ACPI: Thermal Zone [THRM] (20 C)
[    5.045325] usbcore: registered new interface driver usbfs
[    5.045376] usbcore: registered new interface driver hub
[    5.072123] usbcore: registered new device driver usb
[    5.104184] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.104230] ohci_hcd 0000:00:02.0: enabling device (0004 -> 0006)
[    5.104989] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    5.105006] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, low) -> IRQ 21
[    5.105027] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    5.105034] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    5.105122] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    5.308148] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe8000000
[    5.336139] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    6.268373] No dock devices found.
[    6.506691] SCSI subsystem initialized
[    6.567264] 8139too Fast Ethernet driver 0.9.28
[    6.642296] usb usb1: configuration #1 chosen from 1 choice
[    6.642359] hub 1-0:1.0: USB hub found
[    6.642379] hub 1-0:1.0: 3 ports detected
[    6.744454] ohci_hcd 0000:00:02.1: enabling device (0004 -> 0006)
[    6.745117] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[    6.745135] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 20 (level, low) -> IRQ 20
[    6.745156] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    6.745163] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    6.745217] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    6.948904] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe8001000
[    7.006532] usb usb2: configuration #1 chosen from 1 choice
[    7.006595] hub 2-0:1.0: USB hub found
[    7.006614] hub 2-0:1.0: 3 ports detected
[    7.016456] libata version 3.00 loaded.
[    7.111078] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    7.111090] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    7.111112] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    7.111119] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    7.111178] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[    7.111224] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    7.111252] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe8004000
[    7.120045] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.120300] usb usb3: configuration #1 chosen from 1 choice
[    7.120369] hub 3-0:1.0: USB hub found
[    7.120386] hub 3-0:1.0: 6 ports detected
[    7.224529] pata_amd 0000:00:08.0: version 0.3.10
[    7.224608] pata_amd 0000:00:08.0: setting latency timer to 64
[    7.224727] scsi0 : pata_amd
[    7.224902] scsi1 : pata_amd
[    7.226500] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    7.226508] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    7.388667] ata1.00: ATA-6: HTS541040G9AT00, MB2OA60A, max UDMA/100
[    7.388677] ata1.00: 78140160 sectors, multi 16: LBA 
[    7.388718] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    7.404635] ata1.00: configured for UDMA/100
[    7.568347] ata2.00: ATAPI: HL-DT-ST DVD-RW GWA-4080N, 0C09, max MWDMA2
[    7.568387] ata2: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:600:0x12)
[    7.584311] ata2.00: configured for MWDMA2
[    7.584502] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2O PQ: 0 ANSI: 5
[    7.588239] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4080N 0C09 PQ: 0 ANSI: 5
[    7.589808] 8139too 0000:02:01.0: PCI INT A -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    7.590760] eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:6b:c2:9c, IRQ 18
[    7.590767] eth0:  Identified 8139 chip type 'RTL-8101'
[    7.600901] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[    7.600920] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[    7.604856] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    7.604894] ohci1394 0000:02:00.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    7.654723] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e8108000-e81087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.656367] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    8.372202] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    8.372290] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    8.432218] Driver 'sd' needs updating - please use bus_type methods
[    8.436407] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    8.436445] sd 0:0:0:0: [sda] Write Protect is off
[    8.436452] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.436504] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.436641] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    8.436672] sd 0:0:0:0: [sda] Write Protect is off
[    8.436678] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.436728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.436738]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    8.494908]  sda5 >
[    8.495192] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.512379] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    8.512390] Uniform CD-ROM driver Revision: 3.20
[    8.512569] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    8.813359] PM: Starting manual resume from disk
[    8.813369] PM: Resume from partition 8:5
[    8.813373] PM: Checking hibernation image.
[    8.813616] PM: Resume from disk failed.
[    8.906038] kjournald starting.  Commit interval 5 seconds
[    8.906065] EXT3-fs: mounted filesystem with ordered data mode.
[    8.928242] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[533f0200533f0200]
[   16.689656] udevd version 124 started
[   18.330735] Linux agpgart interface v0.103
[   18.500275] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[   18.500339] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[   18.509960] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   18.580151] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2040
[   18.580220] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   18.810076] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.916187] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.852506] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.864045] ACPI: Power Button (FF) [PWRF]
[   19.864297] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   19.876024] ACPI: Power Button (CM) [PWRB]
[   19.876202] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   19.883283] ACPI: Lid Switch [LID]
[   20.162194] ACPI: WMI: Mapper loaded
[   20.612546] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   23.290555] ACPI: AC Adapter [ACAD] (on-line)
[   24.120162] ACPI: Battery Slot [BAT1] (battery absent)
[   24.389367] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/device:19/input/input6
[   24.400033] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.736304] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006d]
[   24.736331] yenta_cardbus 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[   24.736339] yenta_cardbus 0000:02:04.0:   IO window: 0x003000-0x0030ff
[   24.736348] yenta_cardbus 0000:02:04.0:   IO window: 0x003400-0x0034ff
[   24.736357] yenta_cardbus 0000:02:04.0:   PREFETCH window: 0x50000000-0x53ffffff
[   24.736365] yenta_cardbus 0000:02:04.0:   MEM window: 0xe8400000-0xe87fffff
[   24.736375] Yenta: Enabling burst memory read transactions
[   24.736382] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.736387] Yenta: Routing CardBus interrupts to PCI
[   24.736395] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[   24.973654] Yenta: ISA IRQ mask 0x0cf0, PCI irq 19
[   24.973663] Socket status: 30000086
[   24.973669] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   24.973680] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   24.973687] cs: IO port probe 0x3000-0x7fff: clean.
[   24.975618] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[   24.975625] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x57ffffff
[   24.975940] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006d]
[   24.975964] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.975969] Yenta: Routing CardBus interrupts to PCI
[   24.975978] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[   25.004747] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   25.004760] Intel ICH 0000:00:06.0: PCI INT A -> Link[LACI] -> GSI 21 (level, low) -> IRQ 21
[   25.004794] Intel ICH 0000:00:06.0: setting latency timer to 64
[   25.116032] AC'97 0 analog subsections not ready
[   25.209164] Yenta: ISA IRQ mask 0x0cf0, PCI irq 18
[   25.209173] Socket status: 30000006
[   25.209179] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   25.209191] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   25.209198] cs: IO port probe 0x3000-0x7fff: clean.
[   25.211141] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[   25.211148] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x57ffffff
[   25.227970] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input7
[   25.262088] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
[   25.684038] intel8x0_measure_ac97_clock: measured 55304 usecs
[   25.684047] intel8x0: clocking to 48000
[   25.792407] parport_pc 00:0b: reported by Plug and Play ACPI
[   25.792466] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   26.465735] b43-phy0: Broadcom 4306 WLAN found
[   26.518144] phy0: Selected rate control algorithm 'pid'
[   26.718182] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   29.377412] cs: IO port probe 0x100-0x3af: clean.
[   29.379318] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.380195] cs: IO port probe 0x820-0x8ff: clean.
[   29.380912] cs: IO port probe 0xc00-0xcf7: clean.
[   29.381917] cs: IO port probe 0xa00-0xaff: clean.
[   29.392227] cs: IO port probe 0x100-0x3af: clean.
[   29.394126] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.394980] cs: IO port probe 0x820-0x8ff: clean.
[   29.395697] cs: IO port probe 0xc00-0xcf7: clean.
[   29.396734] cs: IO port probe 0xa00-0xaff: clean.
[   30.650769] lp0: using parport0 (interrupt-driven).
[   30.757721] b43-pci-bridge 0000:02:02.0: PCI INT A disabled
[   30.902039] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   30.908691] usbcore: registered new interface driver ndiswrapper
[   30.945478] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   30.948896] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[   31.345182] b43-phy0: Broadcom 4306 WLAN found
[   31.393340] phy0: Selected rate control algorithm 'pid'
[   31.394116] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   31.592864] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[  140.670778] EXT3 FS on sda1, internal journal
[  141.767953] type=1505 audit(1236063878.324:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4952
[  142.268229] type=1505 audit(1236063878.828:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4957
[  142.268679] type=1505 audit(1236063878.828:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4957
[  142.434698] ip_tables: (C) 2000-2006 Netfilter Core Team
[  143.840107] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 2800+ processors (1 cpu cores) (version 2.20.00)
[  143.840180] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6
[  143.840187] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18
[  144.108021] Clocksource tsc unstable (delta = 263791955 ns)
[  144.487898] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  144.548183] apm: BIOS not found.
[  144.620957] ppdev: user-space parallel port driver
[  146.160043] Bluetooth: Core ver 2.13
[  146.161783] NET: Registered protocol family 31
[  146.161789] Bluetooth: HCI device and connection manager initialized
[  146.161793] Bluetooth: HCI socket layer initialized
[  146.189235] Bluetooth: L2CAP ver 2.11
[  146.189241] Bluetooth: L2CAP socket layer initialized
[  146.218898] Bluetooth: SCO (Voice Link) ver 0.6
[  146.218904] Bluetooth: SCO socket layer initialized
[  146.241245] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  146.241252] Bluetooth: BNEP filters: protocol multicast
[  146.274890] Bridge firewalling registered
[  146.364967] Bluetooth: RFCOMM socket layer initialized
[  146.365560] Bluetooth: RFCOMM TTY layer initialized
[  146.365565] Bluetooth: RFCOMM ver 1.10
[  150.496527] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  150.571162] input: b43-phy0 as /devices/virtual/input/input9
[  150.632050] firmware: requesting b43/ucode5.fw
[  150.669183] firmware: requesting b43/pcm5.fw
[  150.694785] firmware: requesting b43/b0g0initvals5.fw
[  150.718289] firmware: requesting b43/b0g0bsinitvals5.fw
[  150.860064] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  151.021059] Registered led device: b43-phy0::tx
[  151.021544] Registered led device: b43-phy0::rx
[  151.021915] Registered led device: b43-phy0::radio
[  151.344204] NET: Registered protocol family 17
[  153.127014] NET: Registered protocol family 10
[  153.129109] lo: Disabled Privacy Extensions
[  153.131008] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  164.088042] eth0: no IPv6 routers present
[  402.668266] ppdev0: registered pardevice
[  402.716373] ppdev0: unregistered pardevice
[  403.502271] ppdev0: registered pardevice
[  403.560169] ppdev0: unregistered pardevice
[  403.628142] ppdev0: registered pardevice
[  403.676045] ppdev0: unregistered pardevice
[  415.632604] eth0: link down
[ 1068.178533] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 8416.249738] eth0: link down
[ 8423.349796] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
patches@patches-laptop:~$

---

### Post by patches23 on 2009-03-03
lsmod -

[    1.073584] system 00:02: iomem range 0xfee00000-0xfeefffff has been reserved
[    1.073584] system 00:02: iomem range 0xfed00000-0xfed00fff has been reserved
[    1.073584] system 00:03: ioport range 0x200-0x20f has been reserved
[    1.073584] system 00:03: ioport range 0x680-0x6ff has been reserved
[    1.073584] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    1.073584] system 00:03: ioport range 0xfe00-0xfe01 has been reserved
[    1.110664] pci 0000:02:04.0: BAR 10: can't allocate mem resource [0xec000000-0xe97fffff]
[    1.110674] pci 0000:02:04.1: BAR 10: can't allocate mem resource [0xec000000-0xe97fffff]
[    1.110684] pci 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[    1.110691] pci 0000:02:04.0:   IO window: 0x003000-0x0030ff
[    1.110699] pci 0000:02:04.0:   IO window: 0x003400-0x0034ff
[    1.110707] pci 0000:02:04.0:   PREFETCH window: 0x50000000-0x53ffffff
[    1.110716] pci 0000:02:04.1: CardBus bridge, secondary bus 0000:07
[    1.110722] pci 0000:02:04.1:   IO window: 0x003800-0x0038ff
[    1.110729] pci 0000:02:04.1:   IO window: 0x003c00-0x003cff
[    1.110737] pci 0000:02:04.1:   PREFETCH window: 0x54000000-0x57ffffff
[    1.110745] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02
[    1.110752] pci 0000:00:0a.0:   IO window: 0x3000-0x7fff
[    1.110759] pci 0000:00:0a.0:   MEM window: 0xe8100000-0xe97fffff
[    1.110767] pci 0000:00:0a.0:   PREFETCH window: 0x00000050000000-0x00000057ffffff
[    1.110778] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:01
[    1.110784] pci 0000:00:0b.0:   IO window: disabled
[    1.110792] pci 0000:00:0b.0:   MEM window: 0xea000000-0xeaffffff
[    1.110801] pci 0000:00:0b.0:   PREFETCH window: 0x000000f8000000-0x000000fc0fffff
[    1.110821] pci 0000:00:0a.0: setting latency timer to 64
[    1.111494] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 19
[    1.111511] pci 0000:02:04.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    1.112117] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 18
[    1.112129] pci 0000:02:04.1: PCI INT B -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    1.112147] bus: 00 index 0 io port: [0, ffff]
[    1.112152] bus: 00 index 1 mmio: [0, ffffffff]
[    1.112158] bus: 02 index 0 io port: [3000, 7fff]
[    1.112163] bus: 02 index 1 mmio: [e8100000, e97fffff]
[    1.112169] bus: 02 index 2 mmio: [50000000, 57ffffff]
[    1.112174] bus: 02 index 3 mmio: [0, 0]
[    1.112179] bus: 03 index 0 io port: [3000, 30ff]
[    1.112185] bus: 03 index 1 io port: [3400, 34ff]
[    1.112190] bus: 03 index 2 mmio: [50000000, 53ffffff]
[    1.112196] bus: 03 index 3 mmio: [0, 0]
[    1.112201] bus: 07 index 0 io port: [3800, 38ff]
[    1.112206] bus: 07 index 1 io port: [3c00, 3cff]
[    1.112212] bus: 07 index 2 mmio: [54000000, 57ffffff]
[    1.112217] bus: 07 index 3 mmio: [0, 0]
[    1.112222] bus: 01 index 0 mmio: [0, 0]
[    1.112227] bus: 01 index 1 mmio: [ea000000, eaffffff]
[    1.112232] bus: 01 index 2 mmio: [f8000000, fc0fffff]
[    1.112237] bus: 01 index 3 mmio: [0, 0]
[    1.112259] NET: Registered protocol family 2
[    1.112493] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    1.113086] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    1.114164] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    1.114700] TCP: Hash tables configured (established 131072 bind 65536)
[    1.114707] TCP reno registered
[    1.114882] NET: Registered protocol family 1
[    1.115129] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.951192]  it is
[    2.851839] Freeing initrd memory: 8014k freed
[    2.852085] Simple Boot Flag at 0x37 set to 0x1
[    2.853244] audit: initializing netlink socket (disabled)
[    2.853269] type=2000 audit(1236063738.852:1): initialized
[    2.868079] highmem bounce pool size: 64 pages
[    2.868093] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    2.873358] VFS: Disk quotas dquot_6.5.1
[    2.873541] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.873741] msgmni has been set to 1761
[    2.874006] io scheduler noop registered
[    2.874012] io scheduler anticipatory registered
[    2.874018] io scheduler deadline registered
[    2.874045] io scheduler cfq registered (default)
[    2.874235] pci 0000:01:00.0: Boot video device
[    2.874889] isapnp: Scanning for PnP cards...
[    3.228654] isapnp: No Plug & Play device found
[    3.309842] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    3.311782] ACPI: PCI Interrupt Link [LMCI] enabled at IRQ 22
[    3.311800] serial 0000:00:06.1: PCI INT B -> Link[LMCI] -> GSI 22 (level, low) -> IRQ 22
[    3.311812] serial 0000:00:06.1: PCI INT B disabled
[    3.314964] brd: module loaded
[    3.315117] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    3.315356] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    3.325091] i8042.c: Detected active multiplexing controller, rev 1.1.
[    3.332253] serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.332263] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    3.332269] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    3.332275] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    3.332282] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    3.333217] mice: PS/2 mouse device common for all mice
[    3.333499] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    3.333529] rtc0: alarms up to one year, y3k
[    3.333772] EISA: Probing bus 0 at eisa.0
[    3.333785] Cannot allocate resource for EISA slot 1
[    3.333791] Cannot allocate resource for EISA slot 2
[    3.333796] Cannot allocate resource for EISA slot 3
[    3.333801] Cannot allocate resource for EISA slot 4
[    3.333807] Cannot allocate resource for EISA slot 5
[    3.333812] Cannot allocate resource for EISA slot 6
[    3.333817] Cannot allocate resource for EISA slot 7
[    3.333822] Cannot allocate resource for EISA slot 8
[    3.333827] EISA: Detected 0 cards.
[    3.333833] cpuidle: using governor ladder
[    3.333839] cpuidle: using governor menu
[    3.335011] TCP cubic registered
[    3.335061] Using IPI No-Shortcut mode
[    3.335510] registered taskstats version 1
[    3.335748]   Magic number: 1:905:14
[    3.335774] tty ttycb: hash matches
[    3.335956] rtc_cmos 00:06: setting system clock to 2009-03-03 07:02:19 UTC (1236063739)
[    3.335964] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    3.335969] EDD information not available.
[    3.336482] Freeing unused kernel memory: 424k freed
[    3.336630] Write protecting the kernel text: 2580k
[    3.336720] Write protecting the kernel read-only data: 940k
[    3.360701] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    3.816075] fuse init (API version 7.9)
[    4.136024] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    4.144029] processor ACPI0007:00: registered as cooling_device0
[    4.178476] Marking TSC unstable due to TSC halts in idle
[    4.187660] thermal LNXTHERM:01: registered as thermal_zone0
[    4.201189] ACPI: Thermal Zone [THRM] (20 C)
[    5.045325] usbcore: registered new interface driver usbfs
[    5.045376] usbcore: registered new interface driver hub
[    5.072123] usbcore: registered new device driver usb
[    5.104184] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    5.104230] ohci_hcd 0000:00:02.0: enabling device (0004 -> 0006)
[    5.104989] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 21
[    5.105006] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 21 (level, low) -> IRQ 21
[    5.105027] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    5.105034] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    5.105122] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[    5.308148] ohci_hcd 0000:00:02.0: irq 21, io mem 0xe8000000
[    5.336139] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    6.268373] No dock devices found.
[    6.506691] SCSI subsystem initialized
[    6.567264] 8139too Fast Ethernet driver 0.9.28
[    6.642296] usb usb1: configuration #1 chosen from 1 choice
[    6.642359] hub 1-0:1.0: USB hub found
[    6.642379] hub 1-0:1.0: 3 ports detected
[    6.744454] ohci_hcd 0000:00:02.1: enabling device (0004 -> 0006)
[    6.745117] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20
[    6.745135] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 20 (level, low) -> IRQ 20
[    6.745156] ohci_hcd 0000:00:02.1: setting latency timer to 64
[    6.745163] ohci_hcd 0000:00:02.1: OHCI Host Controller
[    6.745217] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[    6.948904] ohci_hcd 0000:00:02.1: irq 20, io mem 0xe8001000
[    7.006532] usb usb2: configuration #1 chosen from 1 choice
[    7.006595] hub 2-0:1.0: USB hub found
[    7.006614] hub 2-0:1.0: 3 ports detected
[    7.016456] libata version 3.00 loaded.
[    7.111078] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    7.111090] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    7.111112] ehci_hcd 0000:00:02.2: setting latency timer to 64
[    7.111119] ehci_hcd 0000:00:02.2: EHCI Host Controller
[    7.111178] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[    7.111224] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported
[    7.111252] ehci_hcd 0000:00:02.2: irq 22, io mem 0xe8004000
[    7.120045] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.120300] usb usb3: configuration #1 chosen from 1 choice
[    7.120369] hub 3-0:1.0: USB hub found
[    7.120386] hub 3-0:1.0: 6 ports detected
[    7.224529] pata_amd 0000:00:08.0: version 0.3.10
[    7.224608] pata_amd 0000:00:08.0: setting latency timer to 64
[    7.224727] scsi0 : pata_amd
[    7.224902] scsi1 : pata_amd
[    7.226500] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x2080 irq 14
[    7.226508] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0x2088 irq 15
[    7.388667] ata1.00: ATA-6: HTS541040G9AT00, MB2OA60A, max UDMA/100
[    7.388677] ata1.00: 78140160 sectors, multi 16: LBA 
[    7.388718] ata1: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc6000000) ACPI=0x3f01f (20:600:0x13)
[    7.404635] ata1.00: configured for UDMA/100
[    7.568347] ata2.00: ATAPI: HL-DT-ST DVD-RW GWA-4080N, 0C09, max MWDMA2
[    7.568387] ata2: nv_mode_filter: 0x39f&0x39f->0x39f, BIOS=0x0 (0xc6000000) ACPI=0x39f (120:600:0x12)
[    7.584311] ata2.00: configured for MWDMA2
[    7.584502] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2O PQ: 0 ANSI: 5
[    7.588239] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RW GWA-4080N 0C09 PQ: 0 ANSI: 5
[    7.589808] 8139too 0000:02:01.0: PCI INT A -> Link[LNK2] -> GSI 18 (level, low) -> IRQ 18
[    7.590760] eth0: RealTek RTL8139 at 0x7000, 00:0f:b0:6b:c2:9c, IRQ 18
[    7.590767] eth0:  Identified 8139 chip type 'RTL-8101'
[    7.600901] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 17
[    7.600920] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[    7.604856] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[    7.604894] ohci1394 0000:02:00.0: PCI INT A -> Link[LNK1] -> GSI 19 (level, low) -> IRQ 19
[    7.654723] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[e8108000-e81087ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.656367] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    8.372202] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    8.372290] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    8.432218] Driver 'sd' needs updating - please use bus_type methods
[    8.436407] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    8.436445] sd 0:0:0:0: [sda] Write Protect is off
[    8.436452] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.436504] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.436641] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    8.436672] sd 0:0:0:0: [sda] Write Protect is off
[    8.436678] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    8.436728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    8.436738]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[    8.494908]  sda5 >
[    8.495192] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.512379] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    8.512390] Uniform CD-ROM driver Revision: 3.20
[    8.512569] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    8.813359] PM: Starting manual resume from disk
[    8.813369] PM: Resume from partition 8:5
[    8.813373] PM: Checking hibernation image.
[    8.813616] PM: Resume from disk failed.
[    8.906038] kjournald starting.  Commit interval 5 seconds
[    8.906065] EXT3-fs: mounted filesystem with ordered data mode.
[    8.928242] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[533f0200533f0200]
[   16.689656] udevd version 124 started
[   18.330735] Linux agpgart interface v0.103
[   18.500275] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]
[   18.500339] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP
[   18.509960] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000
[   18.580151] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x2040
[   18.580220] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x2000
[   18.810076] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   18.916187] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.852506] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   19.864045] ACPI: Power Button (FF) [PWRF]
[   19.864297] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   19.876024] ACPI: Power Button (CM) [PWRB]
[   19.876202] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input4
[   19.883283] ACPI: Lid Switch [LID]
[   20.162194] ACPI: WMI: Mapper loaded
[   20.612546] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   23.290555] ACPI: AC Adapter [ACAD] (on-line)
[   24.120162] ACPI: Battery Slot [BAT1] (battery absent)
[   24.389367] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/device:19/input/input6
[   24.400033] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.736304] Yenta: CardBus bridge found at 0000:02:04.0 [103c:006d]
[   24.736331] yenta_cardbus 0000:02:04.0: CardBus bridge, secondary bus 0000:03
[   24.736339] yenta_cardbus 0000:02:04.0:   IO window: 0x003000-0x0030ff
[   24.736348] yenta_cardbus 0000:02:04.0:   IO window: 0x003400-0x0034ff
[   24.736357] yenta_cardbus 0000:02:04.0:   PREFETCH window: 0x50000000-0x53ffffff
[   24.736365] yenta_cardbus 0000:02:04.0:   MEM window: 0xe8400000-0xe87fffff
[   24.736375] Yenta: Enabling burst memory read transactions
[   24.736382] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.736387] Yenta: Routing CardBus interrupts to PCI
[   24.736395] Yenta TI: socket 0000:02:04.0, mfunc 0x01111d22, devctl 0x64
[   24.973654] Yenta: ISA IRQ mask 0x0cf0, PCI irq 19
[   24.973663] Socket status: 30000086
[   24.973669] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   24.973680] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   24.973687] cs: IO port probe 0x3000-0x7fff: clean.
[   24.975618] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[   24.975625] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x57ffffff
[   24.975940] Yenta: CardBus bridge found at 0000:02:04.1 [103c:006d]
[   24.975964] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.975969] Yenta: Routing CardBus interrupts to PCI
[   24.975978] Yenta TI: socket 0000:02:04.1, mfunc 0x01111d22, devctl 0x64
[   25.004747] ACPI: PCI Interrupt Link [LACI] enabled at IRQ 21
[   25.004760] Intel ICH 0000:00:06.0: PCI INT A -> Link[LACI] -> GSI 21 (level, low) -> IRQ 21
[   25.004794] Intel ICH 0000:00:06.0: setting latency timer to 64
[   25.116032] AC'97 0 analog subsections not ready
[   25.209164] Yenta: ISA IRQ mask 0x0cf0, PCI irq 18
[   25.209173] Socket status: 30000006
[   25.209179] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   25.209191] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x7fff
[   25.209198] cs: IO port probe 0x3000-0x7fff: clean.
[   25.211141] pcmcia: parent PCI bridge Memory window: 0xe8100000 - 0xe97fffff
[   25.211148] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x57ffffff
[   25.227970] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input7
[   25.262088] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input8
[   25.684038] intel8x0_measure_ac97_clock: measured 55304 usecs
[   25.684047] intel8x0: clocking to 48000
[   25.792407] parport_pc 00:0b: reported by Plug and Play ACPI
[   25.792466] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   26.465735] b43-phy0: Broadcom 4306 WLAN found
[   26.518144] phy0: Selected rate control algorithm 'pid'
[   26.718182] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   29.377412] cs: IO port probe 0x100-0x3af: clean.
[   29.379318] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.380195] cs: IO port probe 0x820-0x8ff: clean.
[   29.380912] cs: IO port probe 0xc00-0xcf7: clean.
[   29.381917] cs: IO port probe 0xa00-0xaff: clean.
[   29.392227] cs: IO port probe 0x100-0x3af: clean.
[   29.394126] cs: IO port probe 0x3e0-0x4ff: clean.
[   29.394980] cs: IO port probe 0x820-0x8ff: clean.
[   29.395697] cs: IO port probe 0xc00-0xcf7: clean.
[   29.396734] cs: IO port probe 0xa00-0xaff: clean.
[   30.650769] lp0: using parport0 (interrupt-driven).
[   30.757721] b43-pci-bridge 0000:02:02.0: PCI INT A disabled
[   30.902039] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   30.908691] usbcore: registered new interface driver ndiswrapper
[   30.945478] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   30.948896] ssb: Sonics Silicon Backplane found on PCI device 0000:02:02.0
[   31.345182] b43-phy0: Broadcom 4306 WLAN found
[   31.393340] phy0: Selected rate control algorithm 'pid'
[   31.394116] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   31.592864] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[  140.670778] EXT3 FS on sda1, internal journal
[  141.767953] type=1505 audit(1236063878.324:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4952
[  142.268229] type=1505 audit(1236063878.828:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4957
[  142.268679] type=1505 audit(1236063878.828:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4957
[  142.434698] ip_tables: (C) 2000-2006 Netfilter Core Team
[  143.840107] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 2800+ processors (1 cpu cores) (version 2.20.00)
[  143.840180] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x6
[  143.840187] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x18
[  144.108021] Clocksource tsc unstable (delta = 263791955 ns)
[  144.487898] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[  144.548183] apm: BIOS not found.
[  144.620957] ppdev: user-space parallel port driver
[  146.160043] Bluetooth: Core ver 2.13
[  146.161783] NET: Registered protocol family 31
[  146.161789] Bluetooth: HCI device and connection manager initialized
[  146.161793] Bluetooth: HCI socket layer initialized
[  146.189235] Bluetooth: L2CAP ver 2.11
[  146.189241] Bluetooth: L2CAP socket layer initialized
[  146.218898] Bluetooth: SCO (Voice Link) ver 0.6
[  146.218904] Bluetooth: SCO socket layer initialized
[  146.241245] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  146.241252] Bluetooth: BNEP filters: protocol multicast
[  146.274890] Bridge firewalling registered
[  146.364967] Bluetooth: RFCOMM socket layer initialized
[  146.365560] Bluetooth: RFCOMM TTY layer initialized
[  146.365565] Bluetooth: RFCOMM ver 1.10
[  150.496527] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  150.571162] input: b43-phy0 as /devices/virtual/input/input9
[  150.632050] firmware: requesting b43/ucode5.fw
[  150.669183] firmware: requesting b43/pcm5.fw
[  150.694785] firmware: requesting b43/b0g0initvals5.fw
[  150.718289] firmware: requesting b43/b0g0bsinitvals5.fw
[  150.860064] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  151.021059] Registered led device: b43-phy0::tx
[  151.021544] Registered led device: b43-phy0::rx
[  151.021915] Registered led device: b43-phy0::radio
[  151.344204] NET: Registered protocol family 17
[  153.127014] NET: Registered protocol family 10
[  153.129109] lo: Disabled Privacy Extensions
[  153.131008] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  164.088042] eth0: no IPv6 routers present
[  402.668266] ppdev0: registered pardevice
[  402.716373] ppdev0: unregistered pardevice
[  403.502271] ppdev0: registered pardevice
[  403.560169] ppdev0: unregistered pardevice
[  403.628142] ppdev0: registered pardevice
[  403.676045] ppdev0: unregistered pardevice
[  415.632604] eth0: link down
[ 1068.178533] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[ 8416.249738] eth0: link down
[ 8423.349796] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
patches@patches-laptop:~$ LSMOD
bash: LSMOD: command not found
patches@patches-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  8 
af_packet              25728  2 
rfkill_input           12672  0 
binfmt_misc            16904  1 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
sco                    18308  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,bnep,sco,l2cap
ppdev                  15620  0 
powernow_k8            22148  0 
cpufreq_powersave       9856  0 
cpufreq_conservative    14600  0 
cpufreq_userspace      11396  0 
cpufreq_ondemand       14988  1 
cpufreq_stats          13188  0 
freq_table             12672  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
sbs                    19464  0 
pci_slot               12680  0 
sbshc                  13440  1 sbs
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
b43                   131356  0 
rfkill                 17176  2 rfkill_input,b43
mac80211              216820  1 b43
cfg80211               32392  1 mac80211
led_class              12164  1 b43
input_polldev          11912  1 b43
tifm_sd                18184  0 
mmc_core               58268  1 tifm_sd
tifm_core              16028  1 tifm_sd
b44                    35984  0 
ssb                    40580  2 b43,b44
ndiswrapper           196380  0 
sbp2                   29324  0 
lp                     17156  0 
joydev                 18368  0 
pcmcia                 43052  0 
arc4                    9984  2 
ecb                    10880  2 
crypto_blkcipher       25476  1 ecb
evdev                  17696  10 
parport_pc             39204  1 
parport                42604  3 ppdev,lp,parport_pc
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
psmouse                45200  0 
serio_raw              13444  0 
yenta_socket           31756  2 
rsrc_nonstatic         19072  1 yenta_socket
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
video                  25232  0 
output                 11008  1 video
battery                18436  0 
snd_seq_dummy          10884  0 
container              11520  0 
ac                     12292  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
pcspkr                 10624  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
wmi                    14504  0 
button                 14224  0 
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                 12416  0 
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 38036  0 
soundcore              15328  1 snd
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
i2c_nforce2            14468  0 
amd64_agp              18184  1 
i2c_core               31892  1 i2c_nforce2
agpgart                42184  1 amd64_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  3 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
ata_generic            12932  0 
pata_acpi              12160  0 
8139cp                 27520  0 
pata_amd               18692  2 
ohci1394               37936  0 
libata                178208  3 ata_generic,pata_acpi,pata_amd
8139too                31616  0 
mii                    13440  3 b44,8139cp,8139too
ieee1394               96324  2 sbp2,ohci1394
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
ohci_hcd               32016  0 
usbcore               149360  4 ndiswrapper,ehci_hcd,ohci_hcd
thermal                23708  0 
processor              42156  3 powernow_k8,thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 
patches@patches-laptop:~$

---

### Post by patches23 on 2009-03-03
blacklist info -

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
blacklist bcm43xx
blacklist wl

---

### Post by patches23 on 2009-03-03
Hope I have attached the drivers screenshot correctly..

---

### Post by neu2buntu on 2009-03-03
this is your driver for sd card ```
mmc_core               58268  1 tifm_sd
```  try commands ```
sudo modprobe mmc_block
``` and try sd card,then ```
sudo modprode sdhci
``` and try your sd card.    reading up on the mmc_core module there seems to be a bug where it doesnt always pull in mmc_block with it which looks like a dependency (ie it wont run without it). have also found a simpler command to show the sd/mmc card driver modules in lsmod do ```
lsmod | grep mmc
```......   and possibly another option search "manually mount sd card ubuntu"

---

### Post by patches23 on 2009-03-03
Hey :)

Right, tried all of the above, no joy, nothing happens.

I have searched for manually mount SD card but cant seem to get a conclusive way to do it,  WOuld you mind pointing me in the right direction?  Guide on how to mount it?  Or just a thread link to where I can get the info,

Not giving up..... yet!

Cheers!

---

### Post by denbeigh2000 on 2009-05-09
I'm having the same problem, done all the same things, no joy. I can't seem to manage to manually mount... Haven't got a clue xD. A bit of a newbie.

My USB drives all work, I am using a mouse right now

---

### Post by uBuddhu on 2010-08-17
I was having this problem, too. I was about to post, but a post led me to wonder about an error when I clicked on Places->Computer (Nautilus cannot handle computer: Locations)

The recommended course of action for that was:

> sudo mv /usr/local /usr/local.old
> sudo mkdir /usr/local
Reboot.

Lo and behold, after the reboot, my SD was appearing again and my new MP3 player was also. Hope this fixes someone else's problems, too.

---

