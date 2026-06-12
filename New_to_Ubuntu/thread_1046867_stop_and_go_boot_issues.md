---
title: "stop and go boot issues"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by evrkusd on 2009-01-21
Hey

When I boot up my 8.10 (ever since i upgraded from .04) I literally have to hold down the return key in order for the different boot steps to display on the screen/ continue on to the next one. I have no idea how to work around this? would a reinstall of grub work?

when i upgraded i think i screwed it up by telling to to not replace or replace something or another that i had modified. Is there a way to reinstall only this section?
thanks.

---

### Post by yeats on 2009-01-21
Try booting into "recovery mode", which should show the output of all the startup commands and show you where it hangs.  I had a similar problem with Intrepid and have reverted to Hardy :-).

---

### Post by evrkusd on 2009-01-21
it hangs on nearly everything...? 

a lot of sata link down and sata things as well as a number of other things.

---

### Post by yeats on 2009-01-21
Can you post some of the messages that it's hanging on?  These are recorded by the way in /var/log/messages.

---

### Post by evrkusd on 2009-01-21
these are among them.
thanks.

Oct 21 23:32:38 evrkusd kernel: [   19.738753] usb usb1: configuration #1 chosen from 1 choice
Oct 21 23:32:38 evrkusd kernel: [   19.738843] hub 1-0:1.0: USB hub found
Oct 21 23:32:38 evrkusd kernel: [   19.738909] hub 1-0:1.0: 7 ports detected
Oct 21 23:32:38 evrkusd kernel: [   19.757118] SCSI subsystem initialized
Oct 21 23:32:38 evrkusd kernel: [   19.840894] ACPI: PCI Interrupt Link [Z014] enabled at IRQ 18



Oct 21 23:32:38 evrkusd kernel: [   21.239480] ata1: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484100 irq 221
Oct 21 23:32:38 evrkusd kernel: [   21.239556] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 221
Oct 21 23:32:38 evrkusd kernel: [   21.239631] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 221
Oct 21 23:32:38 evrkusd kernel: [   21.239705] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 221
Oct 21 23:32:38 evrkusd kernel: [   21.877014] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Oct 21 23:32:38 evrkusd kernel: [   21.878058] ata1.00: ATA-8: Hitachi HTS542512K9SA00, BB2OC32P, max UDMA/100
Oct 21 23:32:38 evrkusd kernel: [   21.878128] ata1.00: 234441648 sectors, multi 16: LBA48 
Oct 21 23:32:38 evrkusd kernel: [   21.879154] ata1.00: configured for UDMA/100
Oct 21 23:32:38 evrkusd kernel: [   22.196476] ata2: SATA link down (SStatus 0 SControl 300)
Oct 21 23:32:38 evrkusd kernel: [   22.515938] ata3: SATA link down (SStatus 0 SControl 300)
Oct 21 23:32:38 evrkusd kernel: [   22.835402] ata4: SATA link down (SStatus 0 SControl 300)
Oct 21 23:32:38 evrkusd kernel: [   22.835576] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BB2O PQ: 0 ANSI: 5
Oct 21 23:32:38 evrkusd kernel: [   22.835949] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.

---

### Post by yeats on 2009-01-21
kernel maintenance is really beyond my skill level, but a Google search for 
"SATA link down ubuntu" brought up some potentially useful links.

If no one responds here, try asking on the Hardware and Laptops board - perhaps there would be more expertise there . . .

Good luck!

---

### Post by evrkusd on 2009-01-21
so it seems like it isn't just freezing on particular ones because of some error. it seems like it just pauses either for a long time or indefinitely on almost every single listing 'reading files needed to boot, loading hardware drivers etc etc etc etc'

not sure what this would be. 
it basically needs me to prompt it to continue..?

---

