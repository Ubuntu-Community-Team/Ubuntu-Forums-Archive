---
title: "Garmin Quest GPS USB not recognised"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by worlestone on 2011-07-11
I'm trying to get my Garmin Quest GPS to connect using Wine/Winetools, all going well, but I cannot get the laptop to recognized unit when connecting the USB.  In dmesg I get the following...

164.748085] usb 3-2: new full speed USB device using uhci_hcd and address 3

Any clues what to do?

Thanks

---

### Post by worlestone on 2011-07-12
No one?

---

### Post by worlestone on 2011-07-13
Bump?

---

### Post by fabricator4 on 2011-07-13
> **worlestone said:**
> I'm trying to get my Garmin Quest GPS to connect using Wine/Winetools, all going well, but I cannot get the laptop to recognized unit when connecting the USB.  In dmesg I get the following...

164.748085] usb 3-2: new full speed USB device using uhci_hcd and address 3

Any clues what to do?

Thanks

The only way I could get my TomTom to update under Ubuntu was by running XP in a virtual machine.  It's not too difficult and doesn't take too long (apart from installing XP in the virtual machine) and works very well for those few little apps that just don't have a Linux equivalent.

You'll need to get the PUEL version of VirtualBox from oracle rather than the the OSE version in the repositories as the OSE version does not have USB support.  You'll also want to install the extension pack for VB and the guest additions for XP once you've got it running.

Chris

---

### Post by bouncingwilf on 2011-07-13
If running under Wine you sometimes (but not always!) need to create a soft link to a "windows" com port. If the GPS is plugged into a USB port then something along the lines of

ln -s /dev/ttyUSB0  ~.wine/dosdevices/com1      should work

Then access com1: from the Windows program

Bouncingwilf

---

