---
title: "no ipod connectivity"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by stevek123 on 2010-07-18
Running Hardy/8.04. Daughter bought 'new' ipod = model 1099 2022 = model 9829 = ipod photo (4th gen). When attached USB nothing happens at all. It does not turn on and does not charge. It is not recognized with lsusb in terminal. I have installed almost every ipod library, ipodslave, gtkpod-acc, etc. I could find in Synaptic. FWIW, I've successfully gotten gtkpod to detect her old (lost) ipod 4gen video last year. Our music player of choice is Rhythmbox. Nothing sees the 'new' player. I've followed instructions on this link and am stuck.

[http://ubuntuforums.org/showthread.php?t=103071](http://ubuntuforums.org/showthread.php?t=103071)

When I run dmesg in terminal it ends with this...

r/sbin/cupsd" namespace="default"
[619193.766638] audit(1279394752.047:14): type=1503 operation="inode_permission" requested_mask="::rw" denied_mask="::rw" name="/dev/tty" pid=25780 profile="/usr/sbin/cupsd" namespace="default"
[650393.413752] usb 3-4: new high speed USB device using ehci_hcd and address 2
[650393.547313] usb 3-4: configuration #1 chosen from 1 choice
[650393.549705] scsi5 : SCSI emulation for USB Mass Storage devices
[650393.550470] usb-storage: device found at 2
[650393.550480] usb-storage: waiting for device to settle before scanning
[650393.891471] usb 3-4: USB disconnect, address 2

What do I do next???

---

### Post by nothingspecial on 2010-07-18
1.  That how to was last edited in 2006, things have changed, but I`ve only skimmed it, so I don`t know if you have compounded your woes. Following outdated tutorials sometimes do.

2. Did you initialise your daughters iPod on a mac?

---

### Post by stevek123 on 2010-07-22
I dont know if it was initialized on a mac ( bought used) - but might assume it was M$ cuz the format is FAT32. 

I'm not sure what was going on... I ended up installing almost every lib & dev-lib for ipod I could find in Synaptic & then reinstalled gtkpod in Synaptic. I rebooted the system with gtkpod set to accept her model. Once it rebooted I plugged the ipod in and IT MOUNTED! Rhythmbox did not see it at first but gtkpod DID. Once gtkpod saw the thing, Rhythmbox did too, and now it works like a champ.

The whole thing seemed odd to me because my wifes ipod nano (older = 2GB) was instantly detected and mounted...and the .5GB shuffle. This 'new' ipod is several yrs old and I thought it would go right in too. I'm glad I've played on these ubuntu systems enough to hack my way through. Practice and experience help.

---

