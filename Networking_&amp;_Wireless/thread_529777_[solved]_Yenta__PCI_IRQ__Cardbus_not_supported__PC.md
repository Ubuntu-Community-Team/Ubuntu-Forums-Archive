---
title: "[solved] Yenta / PCI IRQ / Cardbus not supported / PCMCIA Issues"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by anjin on 2007-08-19
I have been looking for weeks to solve this problem, so I'm posting this to help whoever else has it (and it seems to be a lot of folks. . .).

I am running Xubuntu (6.10) on an old Toshiba Satellite 335CDS and it works very well.  It's not fast, but it works.

I was using an old Cisco Aironet 340 wireless card and that worked well, too.  But it was a borrowed card and I needed to give it back to its owner, so I bought a Netgear WG511T PC card.  It didn't work!

First, I went through the painful Madwifi download/make/install/debug/remake/reinstall/swear/remake process and got that  (v0.9.3.2) installed on the box.

Then, I tried a bunch of other stuff, but kept getting this error on boot (from dmesg):

[x.y] PCI: No IRQ known for interrupt pin A of device 0000:00:13.1.
[x.y] Yenta: CardBus bridge found at 0000:00:13.1
[x.y] Yenta: no PCI IRQ, CardBus support disabled for this socket.
[x.y] Yenta: check your BIOS CardBus, BIOS IRQ or ACPI settings.

There are a whole bunch of posts with other folks who have that problem, but no answers.  :(

I finally went into BIOS (ESC while booting, then F1), and saw a setting for "PC Card" (on the second page of the BIOS settings).

I changed PC Card from "Auto-Selected" to "Cardbus/16-bit" and that solved the problem!

I had tried these other boot options, alone and in every combination, and they all failed to solve the problem:
acpi=off
pci=routeirq
pci=biosirq
acpi=gdmtywontuwork

I did NOT have to use acpi/pci boot settings after changing the BIOS setting.
This also fixed the "IRQ 11 Nobody Cared" problem.

I hope this helps someone.  I will happily answer any questions as best I can.

---

### Post by compuniversal on 2007-08-19
Hi, My name is Alex and i have ubuntu fetsy in my PC, i dont try to selling products but i work for some company and thath company give good prices in computer product. I buy friday the netgear WPN311NA and this one work very good with my PC desktop and my ubuntu. If you want you can contact me and i give you good prices. Remember i dont try to do marketing i just try to help ubuntu community to get good prices and hardward support Linux. Th U ):P

---

### Post by anjin on 2007-08-19
> **compuniversal said:**
> Hi, My name is Alex and i have ubuntu fetsy in my PC, i dont try to selling products but i work for some company and thath company give good prices in computer product. I buy friday the netgear WPN311NA and this one work very good with my PC desktop and my ubuntu. If you want you can contact me and i give you good prices. Remember i dont try to do marketing i just try to help ubuntu community to get good prices and hardward support Linux. Th U ):P


That still sounds like spam to me, Alex.  For a guy with two posts, you're awfully commercial.

Maybe this forum isn't for you. . .

---

### Post by compuniversal on 2007-08-20
:( i'm not try to do business i just try to help to the users from the comunnity to get product compatible with ubuntu a good prices. Th u :(

---

