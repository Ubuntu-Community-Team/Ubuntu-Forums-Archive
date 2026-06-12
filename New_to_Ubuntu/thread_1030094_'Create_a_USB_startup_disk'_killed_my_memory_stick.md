---
title: "'Create a USB startup disk' killed my memory stick"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by _sebastian_ on 2009-01-04
Hi all,

I'm a bit confused but I think my memory stick got killed while creating a [USB startup disk]("https://launchpad.net/usb-creator") with the new Ubuntu tool.

I started the usb creator and wanted to create a xubuntu USB dongle, for this I purchased a 4 GB stick. As I wanted it for
nothing serious I thought I go with the cheap USB dongle...

Well now after the USB creator got stuck on 'starting app' or something the USB dongle (straight from the packing) is dead.
I left the USB creator running for several hours as I thought it might need the time but nothing happened.

When I plug the USB dongle in nothing happens, neither in Ubuntu nor in Windows. NO empty partition, corrupted partition
just nothing.

my kernel log shows this and then lots of the FAT: Directory bred... errors

Can anyone tell me what happened here? did I do something wrong? was it just to cheap?
I use a CD for the source not a iso file, so I would think that the disc should spin... it did not!

By now I exchanged the dongle for a new one and ran the creator again. It says 'Starting up' and the kernel.log shows no errors by now. How log should I wait?

  - seb

```
usb 5-3: USB disconnect, address 8
Jan  1 13:00:45 snoopy kernel: [44469.080128] usb 5-3: new high speed USB device using ehci_hcd and address 9
Jan  1 13:00:45 snoopy kernel: [44469.216239] usb 5-3: configuration #1 chosen from 1 choice
Jan  1 13:00:45 snoopy kernel: [44469.218341] scsi5 : SCSI emulation for USB Mass Storage devices
Jan  1 13:00:45 snoopy kernel: [44469.230654] usb-storage: device found at 9
Jan  1 13:00:45 snoopy kernel: [44469.230665] usb-storage: waiting for device to settle before scanning
Jan  1 13:00:50 snoopy kernel: [44474.228253] usb-storage: device scan complete
Jan  1 13:00:50 snoopy kernel: [44474.229422] scsi 5:0:0:0: Direct-Access     Ut165    USB2FlashStorage 0.00 PQ: 0 ANSI: 2
Jan  1 13:00:50 snoopy kernel: [44474.230899] sd 5:0:0:0: [sdd] 7897088 512-byte hardware sectors (4043 MB)
Jan  1 13:00:50 snoopy kernel: [44474.233532] sd 5:0:0:0: [sdd] Write Protect is off
Jan  1 13:00:50 snoopy kernel: [44474.233539] sd 5:0:0:0: [sdd] Mode Sense: 00 00 00 00
Jan  1 13:00:50 snoopy kernel: [44474.233543] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Jan  1 13:00:50 snoopy kernel: [44474.238268] sd 5:0:0:0: [sdd] 7897088 512-byte hardware sectors (4043 MB)
Jan  1 13:00:50 snoopy kernel: [44474.242244] sd 5:0:0:0: [sdd] Write Protect is off
Jan  1 13:00:50 snoopy kernel: [44474.242253] sd 5:0:0:0: [sdd] Mode Sense: 00 00 00 00
Jan  1 13:00:50 snoopy kernel: [44474.242256] sd 5:0:0:0: [sdd] Assuming drive cache: write through
Jan  1 13:00:50 snoopy kernel: [44474.244995]  sdd:
Jan  1 13:00:50 snoopy kernel: [44474.449132] sd 5:0:0:0: [sdd] Attached SCSI removable disk
Jan  1 13:00:50 snoopy kernel: [44474.449525] sd 5:0:0:0: Attached scsi generic sg3 type 0
Jan  1 13:00:53 snoopy kernel: [44476.945749] FAT: Directory bread(block 15426) failed
Jan  1 13:00:53 snoopy kernel: [44476.946705] FAT: Directory bread(block 15427) failed
Jan  1 13:00:53 snoopy kernel: [44476.947576] FAT: Directory bread(block 15428) failed
Jan  1 13:00:53 snoopy kernel: [44476.948471] FAT: Directory bread(block 15429) failed
Jan  1 13:00:53 snoopy kernel: [44476.949330] FAT: Directory bread(block 15430) failed
```

---

### Post by northern lights on 2009-01-04
From within Linux, run```
gparted
```(if not installed, install first, available from the repositorries) and reformat USB flashdrive to FAT32.

Start over.

From within Windows, essentially do the same, but not via gparted, obviously. Open a "Run" dialog from the start menu and type "mmc". Choose "Add/Remove Snap-In" from the "File" menu and add "Disk Management". Format from here (still FAT, not ntfs!).

---

### Post by _sebastian_ on 2009-01-04
Hi,
will try that.

Is there a reason why the creator can't be shut down? I click cancle, then the 'Quit installation' question comes up and I click quit but nothing happens... Is that a bug? how can I investigate?

---

### Post by northern lights on 2009-01-04
It appears to be a bug indeed.

However not too critical, as this happens only with new out-of-the-box USB thumb drives and should not happen after you manually reformat.

I would recommend creating a new partition table as well as reformatting via gparted and subsequently removing and re-inserting the USB drive.

The Startup Disk wizard should now work.

---

### Post by _sebastian_ on 2009-01-04
> **northern lights said:**
> From within Linux, run```
gparted
```(if not installed, install first, available from the repositorries) and reformat USB flash drive to FAT32.
...

That solved it indeed. 
I had some trouble with the reformating but at the end I created a new partition table (type: msdos) and a FAT32 partition. Unplug, replug and the creator did his job.

Thanks again.

Next thing is that the **booting won't work**... I tried it on two machines and all I get are some weired ASCI caracters with no sense to me and nothing happens. Maybe this [bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/293083")([293083]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/293083")) does yield some help in the future...

PS: I would still be interested why the USB dongle died...

---

### Post by tomtom1982 on 2009-01-04
> Next thing is that the booting won't work... I tried it on two machines and all I get are some weired ASCI caracters with no sense to me and nothing happens. Maybe this bug(293083) does yield some help in the future...

Hope to understand right:

You've reformatted your stick and wonder why it doesn't boot?

Could be because there aren't any files on it?

Please also try this:

[http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

---

### Post by _sebastian_ on 2009-01-04
> **tomtom1982 said:**
> Hope to understand right:

You've reformatted your stick and wonder why it doesn't boot?

Could be because there aren't any files on it?

Well, maybe I was not clear. :-/

As suggested by 'northern lights' I've redone the partition and partition table and then used the [USB creator]("https://launchpad.net/usb-creator") (coming with 8.10) to install a live system to the stick. With the installation all went well but when selecting the stick on boot it gives me a cryptic message.

---

### Post by Captain_tux on 2009-01-04
I just created a USB start up disk and is in fact what I'm using to write this reply. I used GParted to delete the existing partition, then created a new partition using FAT32. I then made sure I could boot from a USB (changed some settings in the BIOS) and voila! Good to go...

EDIT: Sorry, forgot to add: I also used GParted to set the boot flag... then went ahead with the installation.

Buena suerte!

---

### Post by _sebastian_ on 2009-01-05
> **Captain_tux said:**
> ...
EDIT: Sorry, forgot to add: I also used GParted to set the boot flag... 

I checked this as well and it was set.

Now I try again from start and see what happens...

---

