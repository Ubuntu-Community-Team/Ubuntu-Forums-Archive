---
title: "Hard disk not detected"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by webwiller on 2011-03-01
Hi guys,
my notebook stopped detect my hard drive. Even the bios says HARD DRIVE: (and leave the space blank. Is there anyway I can check it with ubuntu live cd (which is my only way to communicate with the pc as it says "Operative System not found") before buying a new hdd?
Thx a lot in advance!

---

### Post by grahammechanical on 2011-03-01
Can you set the boot order in the BIOS? If so, make sure the machine is set to boot from the CD/DVD drive before booting from the hard disc.

The Ubuntu Live CD is designed to do just what you want. It is our rescue disc as well as our install disc.

Have you considered that the problem rests with the BIOS program itself? It should be possible to reset the BIOS back to the factory default settings. What does the user manual say?

Consider all options before taking action. Think before jumping to a solution. You may cause more damage.

Regards.

---

### Post by webwiller on 2011-03-01
I dont have user manual but I managed to make live cd work, bios is set to cd drive and I did restore bios factory defaults but it is bios itself that does NOT see any hdd, neigher does gparted: no devices found.
Any clue?
Anythink I can do through terminal to ceck hdd status?

---

### Post by ajgreeny on 2011-03-01
If the BIOS sees nothing I doubt ubuntu will, but try ```
sudo fdisk -l
``` in terminal, lower case L at the end, not 1 or I.

---

### Post by pricetech on 2011-03-01
It does sound like you have a failed hard drive.  You said you already reset the BIOS to defaults.  I'd start with manufacturer's diagnostics for both the laptop and drive before I used anything else.

Hopefully you're still under warranty and have good backups of your data.

---

### Post by webwiller on 2011-03-01
> **ajgreeny said:**
> If the BIOS sees nothing I doubt ubuntu will, but try ```
sudo fdisk -l
``` in terminal, lower case L at the end, not 1 or I.


What I get as an anwer is absolutely nothing! Blank line.

---

### Post by srs5694 on 2011-03-01
I agree that this sounds like a hardware failure; however, it might not be the hard disk itself. It's possible that the hard disk has worked free of its connection, that a connecting cable is bad, or that the hard disk controller circuitry on the motherboard has died. Since this is a notebook computer, the easiest problem to fix would be if the drive has worked free of its connection; that can be fixed by removing and re-attaching the hard disk. (At least some modern computers have panels in their bottoms that provide easy access to the hard disk, so you can do this pretty easily. On other computers, you'd need to partially disassemble the machine to do this, which is obviously difficult.)

If re-attaching the hard disk doesn't work, then the next easiest problem to fix would be a dead hard drive. You can buy a replacement drive, but you'll need to re-install everything from a backup. (You *do* have backups of your important data, I hope!) Of course, since you don't know if the disk is bad, buying a new disk could be a pointless expense. You can remove the hard disk and attach it to another computer (even a desktop system), or us a USB-to-SATA or USB-to-PATA adapter to test the drive on your laptop (via a CD boot), in order to test the disk. If you don't have the hardware or expertise to do any of these things, you'll need to either get help from a friend or take the computer to a shop and pay them to do the diagnostics.

If you do the diagnostics, then that leaves the tricky internal problems: Bad cables (actually fairly cheap to fix) or bad motherboard disk controller (ridiculously expensive to fix; plan to buy a new laptop if this is the problem).

---

### Post by webwiller on 2011-03-03
> **srs5694 said:**
> I agree that this sounds like a hardware failure; however, it might not be the hard disk itself. It's possible that the hard disk has worked free of its connection, that a connecting cable is bad, or that the hard disk controller circuitry on the motherboard has died. Since this is a notebook computer, the easiest problem to fix would be if the drive has worked free of its connection; that can be fixed by removing and re-attaching the hard disk. (At least some modern computers have panels in their bottoms that provide easy access to the hard disk, so you can do this pretty easily. On other computers, you'd need to partially disassemble the machine to do this, which is obviously difficult.)

If re-attaching the hard disk doesn't work, then the next easiest problem to fix would be a dead hard drive. You can buy a replacement drive, but you'll need to re-install everything from a backup. (You *do* have backups of your important data, I hope!) Of course, since you don't know if the disk is bad, buying a new disk could be a pointless expense. You can remove the hard disk and attach it to another computer (even a desktop system), or us a USB-to-SATA or USB-to-PATA adapter to test the drive on your laptop (via a CD boot), in order to test the disk. If you don't have the hardware or expertise to do any of these things, you'll need to either get help from a friend or take the computer to a shop and pay them to do the diagnostics.

If you do the diagnostics, then that leaves the tricky internal problems: Bad cables (actually fairly cheap to fix) or bad motherboard disk controller (ridiculously expensive to fix; plan to buy a new laptop if this is the problem).

Thanx for your effort :), I got your point, I'll go through these check ups and let you know...:(

---

