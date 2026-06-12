---
title: "Will not see one of Sata Hard drives"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by tfrancis6666 on 2010-02-05
I recently installed Ubuntu 9.10 - the Karmic Koala and it sees all 4 SATA Hard drives connected to the Motherboard but it will not see my Hard dRive connected to the extra SATA controller in the PCI slot. I removed the controller and ran lspci -nnv and reinstalled the controller and ran that command again and it sees the controller
03:07.0 Mass storage controller [0180]: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller [1095:3512] (rev 01)
	Subsystem: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller [1095:3512]
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at cf00 [size=8]
	I/O ports at ce00 [size=4]
	I/O ports at cd00 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at cb00 [size=16]
	Memory at fdcff000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at fdb00000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
	Kernel driver in use: sata_sil
But it will not see the drive that is attached to it. please help

---

### Post by audiomick on 2010-02-05
Can you see the drive with
```
sudo fdisk -l
```?
The last character is a lower case L, not a figure one.

---

### Post by zerhacke on 2010-02-05
We have a similar card, the 3114 which uses sata_sil as the driver.  We found that flashing the BIOS on the card to non-raid mode solved our problem.

Good luck with doing it, though, you will need a spare floppy or several CDs to do it.

---

### Post by tfrancis6666 on 2010-02-05
Answer to audiomick comment using the fdisk command no I can not see the drive

And answering to zerhacke I have no floppy and then locating the BIOS update for this card will be the next challenge. When I was running windows it was set up as a non RAID application.

---

### Post by audiomick on 2010-02-05
I think zerhacke might have a point though. If fdisk can't see it, then I think that means that it really isn't there, i.e. the sata controller isn't passing it through.

---

### Post by tfrancis6666 on 2010-02-05
I have downloaded all the files to flash the bios on my controller card but how do I create a boot CD with this info on the CD. I also downloaded the the Free DOS boot disk stuff but it will not let me create a boot disk so I can boot off of so someone please help with this matter

---

### Post by zerhacke on 2010-03-22
Many apologies for the late reply.  I have had a lot of things going on in my personal life that made me forget about this thread.

As it is of questionable legalities, I cannot help you in finding proper boot disks to do so.  Google is your friend.  You could even Google for ISO files to burn to CD if you have no floppy.

When I obtained my DOS ISO CD and burned it to disk, I booted from the now Boot CD and not Boot Floppy, swapped CDs for another plain Jane data CD I made of the contents of the proper bios updates for the PCI card, and ran the updater.  All you have to do when it is finished is remove the CDs and reboot.

---

