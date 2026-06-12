---
title: "Error After Install On IDE Drive?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by ken0069 on 2009-12-04
[FONT=Times New Roman][SIZE=5]I have a P5K Pro Asus motherboard which has 6 SATA connectors and one IDE connector.  I also have a number of 80 to 120GB IDE drives that I want to put to some use.  I already have a multiboot system on this computer booting Windows XP and Vista which are both loaded on SATA drives and I select the boot device from within the BIOS.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[SIZE=5][FONT=Times New Roman]What I want to do is use one of the old IDE drives connected to the IDE channel cable along with the DVD ROM drive, which is at the end and set to “master”.  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]So, I disconnected ALL other hard drives and connected the 80GB IDE drive as a “slave” on the IDE cable with that same cable going to the DVD drive as “master”.  I loaded Ubuntu x86 9_10 on that drive and went well until it finished and rebooted, or tried to reboot.  Got the following error after the grub loader opened up and I hit enter to start Ubuntu:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]ERROR: no such device: d4c65fc-c0ae-4f5c-bo3b-930ed788bib[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[SIZE=5][FONT=Times New Roman]So can someone tell me why Ubuntu will not start?  I’ve loaded it twice and both times it’s done the same thing.  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]Oh, and this motherboard used a Marvell driver for the IDE channel, which may have something to do with it but I’ve already has Suse 11.1 running on that exact same drive with zero problems?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]Is there a simple fix for this one?[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]Thanks,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=5]Ken[/SIZE][/FONT]

---

### Post by ken0069 on 2009-12-06
UPDATE:  Went back and disconnected the DVD drive, set the IDE drive to "master" that I had loaded Ubuntu on then connected it to the end of the ribbon cable and it booted!  So, I guess this proves that Ubuntu won't boot to an IDE drive that is configured as a "slave" on an ASUS P5K Pro motherboard!

---

### Post by oldfred on 2009-12-07
I have been on Sata for so long I have forgotten but I thought that back in the day all motherboards booted from the first master in the ide chain. So you should be able to boot from your DVD if it looked like a Hard drive but the BIOS will never see the slave.

---

