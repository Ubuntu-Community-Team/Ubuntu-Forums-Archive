---
title: "Backup computer when USB stick is plugged in"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-02-25
Here is my problem:

When I plug my usb stick into my computer I want it to automatically run a backup script.

I have written a rsync script that is set to run every hour or so. But, I want to basically be able to run a backup ONLY when it is plugged in, and then not after that.

I'm sure there is a way this can be done, but I'm not sure how to.

Thanks,

---

### Post by dje on 2009-02-25
you could set an if statement at the beginning of the the shell script that tests for the mount point of the USB drive, if it exists then the backup is run else it is not:
```
if [ ! -d /media/*mount_point*; then
    exit 1
fi
```

hope that helps,
dje

---

### Post by abhiroopb on 2009-02-25
But wouldn't this mean that I'd actually have to run the script itself? 

I mean this is on the right track but it does mean that it won't work (lets say) if I plug it in randomnly.

But this is useful for another query I had, thanks!

---

### Post by yther on 2009-02-25
I'm not an expert, but it's definitely possible to detect when certain devices are plugged in.  For example, monitor /var/log/messages using "tail -f" or similar.  Here's what happens when I plug in a USB stick:

```
Feb 25 17:57:18 hazuki kernel: [17859.516108] usb 7-1: new high speed USB device using ehci_hcd and address 3
Feb 25 17:57:18 hazuki kernel: [17859.650711] usb 7-1: configuration #1 chosen from 1 choice
Feb 25 17:57:18 hazuki kernel: [17859.794305] usbcore: registered new interface driver libusual
Feb 25 17:57:18 hazuki kernel: [17859.805852] Initializing USB Mass Storage driver...
Feb 25 17:57:18 hazuki kernel: [17859.809338] scsi4 : SCSI emulation for USB Mass Storage devices
Feb 25 17:57:18 hazuki kernel: [17859.810447] usbcore: registered new interface driver usb-storage
Feb 25 17:57:18 hazuki kernel: [17859.810450] USB Mass Storage support registered.
Feb 25 17:57:23 hazuki kernel: [17864.810648] scsi 4:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
Feb 25 17:57:23 hazuki kernel: [17864.816637] sd 4:0:0:0: [sdb] 2034688 512-byte hardware sectors (1042 MB)
Feb 25 17:57:23 hazuki kernel: [17864.818106] sd 4:0:0:0: [sdb] Write Protect is off
Feb 25 17:57:23 hazuki kernel: [17864.821206] sd 4:0:0:0: [sdb] 2034688 512-byte hardware sectors (1042 MB)
Feb 25 17:57:23 hazuki kernel: [17864.822078] sd 4:0:0:0: [sdb] Write Protect is off
Feb 25 17:57:23 hazuki kernel: [17864.822906]  sdb: sdb1
Feb 25 17:57:23 hazuki kernel: [17864.828752] sd 4:0:0:0: [sdb] Attached SCSI removable disk
Feb 25 17:57:23 hazuki kernel: [17864.831505] sd 4:0:0:0: Attached scsi generic sg2 type 0
```

Prior to that moment, there was no /dev/sdb1, but now there is.  Also, the messages tell me that a "USB flash disk" was attached.  Using this information and possibly output from "lsusb" you could have a script that either watches for this device, or maybe one that's triggered by a specific event (read up on **udev**, I think), to activate your backup.

I'm pretty sure the udev system can do things like that, just not exactly sure how to make it happen.

---

### Post by abhiroopb on 2009-02-25
Ah ok thanks, thats very helpful. I will certainly look up udev. However, if anyone has tried doing this, or knows of a way to do it, please let me know!

---

### Post by dje on 2009-02-25
i thought it was set to run every hour? if the stick was plugged in then once it came to the correct time to run it would run and when it wasn't plugged in and it came to the correct time it wouldn't run

dje

---

### Post by abhiroopb on 2009-02-25
Yes that is true it is set to run every hour (in fact it can get annoying sometimes as if the stick is not plugged in and the script runs it just creates a folder in the /media folder - thanks for the if command!).

However, what I am looking for is a simple solution where if I plug in the stick it backs up immediately.

I know this is a really specific thing, but something I've noticed is that I often don't have the most important documents on hand because they haven't been backed up. So, if I could do it when it is plugged in I wouldn't forget as often.

---

### Post by dje on 2009-02-25
ah ok, i understand, glad the if command worked in some way! i would think that what yther suggested above would work best although it may take some work. i wouldn't be able to help with that :)

dje

---

### Post by abhiroopb on 2009-02-25
thanks!

Any other suggestions?

---

