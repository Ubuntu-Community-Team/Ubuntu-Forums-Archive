---
title: "Buffalo Air Station Turbo G, Not working in Ubuntu 8.10"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by tomcommathe on 2008-11-05
I (just tonight) installed Ubuntu 8.10, and I am having some trouble getting the wireless card to work.

I am running dual boot with Windows XP Pro and it works over there, I copied all of the Drivers that I found for this card on Drivers Guide

Using Wireless Network Drivers all of them came up as invalid.

I am pretty sure it is recognizing my PCI Bus.

I am new to Linux and am just lost, I guess.

Thanks for any help!

Model: Buffalo Air Station Turbo G
Model #: WLI-CD-G54S

**UPDATE**
Okay, I read somewhere in the forums that I needed my *.sys file to be with the *.inf file, so I brought that in aswell, and I the driver file no longer says "Invalid Driver," but it says "Hardware Present: No"

When lspci -v | less was used in Terminal it came up with a Wireless LAN Controller.

So, why can't I see my network?

---

### Post by tomcommathe on 2008-11-05
Brought in different files and it started working, ish.

So I rebooted, now my harddrive has a pretty nasty  knock to it. Oh well.

---

