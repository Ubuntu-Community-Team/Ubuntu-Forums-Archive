---
title: "Disk problems with fat32 drive"
date: 2009-09-17
forum: New to Ubuntu
---

### Post by wynn22 on 2009-09-17
I have a media disk (has some pre-configured player software on it) that is formated fat32. Initially it connected without a problem, but now it is hit and miss as to whether it works or not (currently it is not working). 

If I scan the usb devices it does not show at all (lsusb).  Plug/unplug while monitoring and nothing appears.. (udevmonitor -kue). 

Now the strange thing is when I run a scsi scan script (rescan-scsi-bus.sh) it shows the devices including the problem drive, 

      OLD: Host: scsi0 Channel: 00 Id: 00 Lun: 00
      Vendor: ATA      Model: ST3802110AS      Rev: 3.AA
      Type:   Direct-Access                    ANSI SCSI revision: 05

So I wonder why it can see it on that scan but not see the drive to be able to mount it. 

Stop press.... case in point I just switched the drive off and on again while typing this and it has now auto-mounted /dev/sdh1 (I had tried that a number of times previously ... is an automount daemon or something timing out???)

I am struggling to find a pattern with this problem, any ideas on how I can monitor or track it down.  Should I create a specific mount entry in fstab for the device with some special parameters or something?  

Don't have any issues (at the moment) with ntfs drives.Machine is dual boot and the problem disk mounts fine within XP.

Any help much appreciated :)

---

### Post by quixote on 2009-09-18
It sounds to me like gnome is having trouble consistently automounting.  Although it's weird that lsusb doesn't see it.  That implies some bigger problem.  The first thing I'd try is giving it its own fstab entry, and point it to a mount point in, say, /mnt rather than /media, and see if that helps.

---

### Post by wynn22 on 2009-09-21
Adding an entry to the fstab made no difference, but I have sort of got a workaround of sorts. I don't know why this happens but I assume it has something to do with the pre-installed software/media drive enclosure/firmware  stuff (Inoi).  Have to power on the drive disconnected, then switch off with the remote control (used to play stuff when connected to TV) into a sort of standby mode.  Then attach the usb cable, which then appears to wake the drive up and it mounts without any issue.  

It works fine on windows, but I assume there might be a driver issue with linux. But at least I have a workaround so I am happy.

---

### Post by quixote on 2009-09-21
Wow.  How did you ever hit upon that series of steps?  That definitely sounds like a flaky linux driver issue, but at least you have a workaround.

---

### Post by wynn22 on 2009-09-21
Well it worked on times, so I kind of tracked back on the times it worked :).  Obviously not an ideal solution, but will do for now.  Plan to move my stuff off that disk, so I might reformat and see if it behaves after that!

---

