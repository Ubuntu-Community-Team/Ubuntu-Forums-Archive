---
title: "USB Stick problerms"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-11-11
i have a really small but annoying problem, a few days ago i hit my deadline for an assignment that was due, i was off to print it out and my usb stick didnt get picked up in ubuntu...i then went home to plug it into my chunky old desktop and it was not formatted, so i did that as fat32, i then went back to ubuntu and tried again and the stick still doesnt get picked up. If i plug it in while its booting, it finds it plugged in as "4.0gb Filesystem" but if i click on it or unmount it i get an error, and after a while it unmounts itself.
 
 
Is there anything i can do to fix this?

---

### Post by JamesParnell on 2009-11-11
i would post the error, but true to form, it doesnt want to tell me now
EDIT: i just rebooted with the stick in, it loaded up onto /media/Stick, i managed to open it, prepare to delete the lost+found folder, and then it vanished with "cannot delete.....maybe the device has been recently deleted" (that was close to the actual error)

---

### Post by 3rdalbum on 2009-11-11
After plugging in the USB device (well, preferably after it vanishes), can you please get the output of the "dmesg" command and send it to us?

---

### Post by JamesParnell on 2009-11-11
```
[ 2931.789867] ath5k phy0: unsupported jumbo
[ 3913.564070] usb 1-6: new high speed USB device using ehci_hcd and address 15
[ 3913.697236] usb 1-6: configuration #1 chosen from 1 choice
[ 3913.708552] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3913.717704] usb-storage: device found at 15
[ 3913.717720] usb-storage: waiting for device to settle before scanning
[ 3928.716306] usb-storage: device scan complete
[ 3950.100070] usb 1-6: reset high speed USB device using ehci_hcd and address 15
[ 3955.224082] usb 1-6: device descriptor read/64, error -71
[ 3960.448064] usb 1-6: device descriptor read/64, error -71
[ 3960.664065] usb 1-6: reset high speed USB device using ehci_hcd and address 15
[ 3965.784063] usb 1-6: device descriptor read/64, error -71
[ 3971.008075] usb 1-6: device descriptor read/64, error -71
[ 3971.224068] usb 1-6: reset high speed USB device using ehci_hcd and address 15
[ 3976.636057] usb 1-6: device not accepting address 15, error -71
[ 3976.748076] usb 1-6: reset high speed USB device using ehci_hcd and address 15

```i'm guessing that is all you need

---

### Post by JamesParnell on 2009-11-11
sorry for the bump, but it is quite vital that i get this stick working again A.S.A.P.

---

### Post by soapytheclown on 2009-11-11
Can it be found in the System>Admin>Disk Utility?

If not, I had a fun time after I decided to screw around with my USB.

I hope that chunky old desktop is a Windows XP+ machine if not the Disk Utility yields nothing..

(IN Windows)
I had to go into Control panel> administrative tools> computer management > disk manager

In here, delete the partition on the 4gb disk, and then rightclick make a new partition on it as just plain FAT. (using the disk management tool, not the format tool)

THEN use the format tool to make it FAT32 with default allocation size..

this is exactly what got mine working for me in linux again

---

### Post by wilee-nilee on 2009-11-11
Can gparted in ubuntu read the stick if so I would try using that to reformat it it would be unmounted for it to work anyway.

---

### Post by JamesParnell on 2009-11-11
ive already tried the XP method, with no luck, i will try agan soon just to be sure, and no, gparted does not pick up the device at all

---

### Post by JamesParnell on 2009-11-11
thats so strange, it has picked up the stick, i will see if it holds onto it, and will format anyway.

---

