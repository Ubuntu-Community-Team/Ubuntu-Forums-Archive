---
title: "Realtek 8139D PCI NIC, Feisty doesn't detect it"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by mikeymikec on 2007-05-21
Quick starting note - wired NIC, not wireless!

I've just done a default, clean install of Feisty on a desktop system (Athlon 1000 age) that has an otherwise identified Realtek 8139D NIC (PCI card, no other mention of manufacturer etc).  Feisty doesn't show a NIC installed in the Network setup window.

Device information lists the card as being there and as a 8139C+.

dmesg | grep 8139 results in saying that the 8139too driver didn't like it (error -16?), and the normal 8139 driver didn't like it either, perhaps try the 8139too driver :)

I tried a suggestion I found - 'sudo modprobe 8139too' but that made little difference.

I don't know how to install drivers under Linux.  I have enough spare systems and methods of getting data onto the Ubuntu system, so getting the necessary files onto the system shouldn't be a problem.  I don't have a spare PCI NIC.

---

