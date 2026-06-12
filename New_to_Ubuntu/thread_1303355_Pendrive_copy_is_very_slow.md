---
title: "Pendrive copy is very slow"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by sundar22in on 2009-10-28
Hello,

I use Ubuntu 9.04 and I found that If I copy files to/from pendrive it is very slow..i.e. Its very slow when compared to Vista.

Did you experience it? Is it because of the File system format (FAT32)? If I copy a 100 MB file it takes less than 5 mins in Vista and more than 10 mins in Ubuntu. 


Any pointers is appreciated. Thanks in advance.

Regards,
Sundar

---

### Post by John Bean on 2009-10-28
> **sundar22in said:**
> Is it because of the File system format (FAT32)? If I copy a 100 MB file it takes less than 5 mins in Vista and more than 10 mins in Ubuntu. 
I don't see a lot of difference with any of mine to be honest, although writing is perhaps a bit slower on Ubuntu than XP. But 5 or more minutes to copy 100MB??? What's it using, a hammer and chisel to carve the data in the silicon? That's s-l-o-w. The slowest of mine writes about five times faster than that and reads even faster - and that's on Ubuntu.

---

### Post by Sir Jasper on 2009-10-28
Hi,

Do you have USB 2 and if so are you using the correct slot for your pen drive?

That seems like USB 1 speed and almost more like parked than slow.

My regards

Copying from your pen drive to your hard drive should be hugely faster than copying from your hard drive to your pen drive.

Also, different models of pen drives have massive differences in speed, especially in writing speed, but this seems unlikely to be the cause of your experience.

---

### Post by strangedata on 2009-10-28
Same thing here. USB 2.0, really fast on windows, more than 40mins to copy 1.4GB from HD to pendrive on Ubuntu. ](*,)

It starts alright, and thanks just a few seconds to copy the first 400MBs or so, and then it gradually slows down... all they way down to 500 Bytes... and that's the end of story. It doesn't come up anymore.

What could possibly be wrong? I've seen this on many forums, and no one gave an answer.

I really hate to have to boot in to Windows just to copy my files.

On the other hand, copying FROM pendrive is OK.

---

### Post by Jazzy_Jeff on 2009-10-28
I am not sure what the problem is. I copy files all the time to my pen drives and it is fast. I use NTFS file system on my pen drive. Not sure if that makes a difference.

---

### Post by strangedata on 2009-10-28
More info:

[100040.961112] usb 2-1: new high speed USB device using ehci_hcd and address 3
[100041.097458] usb 2-1: configuration #1 chosen from 1 choice
[100041.098055] scsi6 : SCSI emulation for USB Mass Storage devices
[100041.098585] usb-storage: device found at 3
[100041.098590] usb-storage: waiting for device to settle before scanning
[100046.096478] usb-storage: device scan complete
[100046.096972] scsi 6:0:0:0: Direct-Access     SanDisk  SanDisk Cruzer   8.02 PQ: 0 ANSI: 0 CCS
[100046.099919] sd 6:0:0:0: [sdb] 15695871 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[100046.101100] sd 6:0:0:0: [sdb] Write Protect is off
[100046.101103] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[100046.101106] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[100046.104712] sd 6:0:0:0: [sdb] 15695871 512-byte hardware sectors: (8.03 GB/7.48 GiB)
[100046.105200] sd 6:0:0:0: [sdb] Write Protect is off
[100046.105203] sd 6:0:0:0: [sdb] Mode Sense: 45 00 00 08
[100046.105205] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[100046.105211]  sdb: sdb1
[100046.106653] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[100046.106728] sd 6:0:0:0: Attached scsi generic sg2 type 0

So, I was copying a file using Nautilus and the system came to a halt. Even the wireless net disconnected. I had to unplug the pendrive without unmounting it so that the system would become responsive once again.

Now I'm copying with dd. It's still taking a long time, but it's not grinding my system.

Edit: dd just finished copying:
2291200+1 records in
2291200+1 records out
1173094621 bytes (1.2 GB) copied, 1460.87 s, 803 kB/s

24 mins to copy 1.2 GB!!!

---

### Post by Arup on 2009-10-28
Turn off legacy USB support in BIOS, when there is a voltage issue on some boards USB slot, Ubuntu reverts to USB 1.1 mode thereby slowing down transfers. If you use a powered USB hub, you wouldn't experience these issues. Compared to Win, Ubuntu is a bit more sensitive and tends to slide down to USB 1.1 compatibility a bit sooner.

---

### Post by lavinog on 2009-10-28
check dmesg while copying and see if there are any messages

---

### Post by John Bean on 2009-10-29
> **Arup said:**
> Turn off legacy USB support in BIOS, when there is a voltage issue on some boards USB slot, Ubuntu reverts to USB 1.1 mode thereby slowing down transfers. If you use a powered USB hub, you wouldn't experience these issues. Compared to Win, Ubuntu is a bit more sensitive and tends to slide down to USB 1.1 compatibility a bit sooner.
That makes sense, and would explain why only some people experience the problem. It's got to be a hardware related issue.

As an aside I had a very similar problem a few years back that affected  USB disks and some other high speed devices like film scanners. It turned out to be an issue with the chipset (sorry, can't remember which) used for the motherboard USB; I added a USB card to the PC and used the onboard USB only for mice/printers/etc and everything then worked as it should.

---

