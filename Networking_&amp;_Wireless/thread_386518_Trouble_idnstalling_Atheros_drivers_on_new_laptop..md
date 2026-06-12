---
title: "Trouble idnstalling Atheros drivers on new laptop."
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by godvalve on 2007-03-17
Hello all..
    I need a little help figuring out if I'm at fault for the non-functional state of my wifi card. These are the steps I've taken thus far..
1) Freshly installed Edgy 6.10.
2) update the software list (Sys>Admin>Update manager)
3) ensure that linux-restricted-modules-generic are installed 2.6.17.11-generic (uname -r returns 2.6.17.11-generic) through synaptic. Also, installed network-manager and network-manager-gnome through synaptic.

Now... for all intents and purposes, my wifi should be working, yes?

All right. dmesg returns 

....
[17179590.956000] wifi%: unable to attach hardware: 'Hardware revision not supported' (Hal status 13)
....

I'm guessing that my problem is a driver issue with the restricted-modules-generic 2.6.17.11-generic Atheros solution.

For your edification, the laptop was newly purchased last week. It's a Toshiba Satellite A100 - VA1.

How do I fix my problem? (I suspect that my next step will be to compile the latest driver set from the madwifi home page. Is this correct? If so, can anyone point me at a how to (setting up the compiler, what sources to grab, how to organize everything, what commands to type, etc) to get this done?) I'm really impressed with Ubuntu's native support for the majority of the hardware on this machine. I just need a little help with this hurdle.

Thank you all in advance!

---

### Post by chili555 on 2007-03-17
It would help us to know which Atheros you have. Please show us lspci -v | grep Network. If this command is unproductive, let's see the part of sudo lshw that relates to your wireless card.

---

### Post by godvalve on 2007-04-03
All right.. here is the info requested:

lspci -v | grep Network returned nothing. So I ran lspci -v. The relevant output from this is: 
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
        Subsystem: Askey Computer Corp. Unknown device 7106
        Flags: fast devsel, IRQ 217
        Memory at c0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: [40] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: 64bit- Queue=0/0 Enable-
        Capabilities: [60] Express Legacy Endpoint IRQ 0
        Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Capabilities: [100] Advanced Error Reporting
        Capabilities: [140] Virtual Channel

sudo lshw produced:
           *-network UNCLAIMED
                description: Ethernet controller
                product: Atheros Communications, Inc.
                vendor: Atheros Communications, Inc.
                physical id: 0
                bus info: pci@02:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:c0100000-c010ffff irq:217


Hopefully this helps. I still haven't got this thing working yet.

---

### Post by josephus on 2007-04-03
Seems like your Atheros card is not supported with the version of HAL loaded up with Edgy Eft.  I'm pretty sure the problem is solved with Feisty Fawn.  Compiling the newer version of Madwifi from source will probably fix the problem (go to madwifi.org, it's pretty clear what you need to do from ther).  If you don't want to compile stuff the other alternative is to use ndiswrapper with Microsoft drivers for your wireless card.

---

### Post by godvalve on 2007-04-03
Thx for the help. Hopefully I don't mess up the compile. *Points to noob self*

---

### Post by Linuturk on 2007-04-22
Actually, I just purchased a new Toshiba laptop that seems to have the same Atheros chipset. I've ran Feisty from the live cd, and the wireless seems to work, but after the install, it doesn't!!

Any help?

---

