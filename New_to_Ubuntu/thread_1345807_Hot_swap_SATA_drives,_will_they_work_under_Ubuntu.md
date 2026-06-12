---
title: "Hot swap SATA drives, will they work under Ubuntu?"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by hankyknot on 2009-12-04
I am looking to creating a backup storage system that would have a dedicated SATA drive for each of my PC's that I plan to back up. I would like them to be removeable so that the initial full backup can be done by removing the drive and connecting it via USB before putting it back in the rack for the incremental backups. Small restores would be done over the network but in the event of a major restore I would like to pull the drive from the rack, stick it in a usb caddy and attach it directly to the machine. 


I have seen that Vantec offer an EX Swap tray and cartridge setup but they only mention that it works on Windows & Macs.

There is no software that comes with the units so is the mention of Linux compatibility an oversight on their part or is there something about Linux(Ubuntu) that would prevent these drives from functioning the way they were designed?

---

### Post by Paqman on 2009-12-04
So this is not an array, but instead a bunch of separately mounted drives on a Linux box, with the drives mounted as network shares? I would always unmount the drive before unplugging it.

---

### Post by hankyknot on 2009-12-04
Yes, the drives would not really be shared as they would only be accessed via the backup software. I don't mind, in the event of having to remove a drive, unmounting it before physically removing it I would just rather not take the server down.

---

