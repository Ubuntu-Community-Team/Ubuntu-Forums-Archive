---
title: "External Card Reader Not Working"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by Teasdale on 2009-03-28
I purchased a Targus USB Memory Stick Card Reader/Writer for my SD card. I'm running Ubuntu 8.10. I installed pmount after reading some threads, but it still isn't working.

When I click Places > Computer, it shows the USB device, but I guess it won't mount? When I right-click and choose "mount volume," nothing happens. When I click "open," it says, 'can't mount volume."

I have a camera that does fine in the same USB slot.

---

### Post by LiamWilson on 2009-03-28
What error message do you get when you try to mount/open it?

---

### Post by Teasdale on 2009-03-28
I get a box that says "Unable to mount location - Can't mount file."

---

### Post by Sef on 2009-03-28
Applications > Accessories > Terminal 

then type in this command:

```
lsusb
```

That will list all your usb devices.  Your device should be listed.  Please copy and paste the results here.

---

### Post by Teasdale on 2009-03-28
Here's what it said:

Bus 005 Device 009: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:c30b Logitech, Inc. 
Bus 001 Device 004: ID 03f0:0d17 Hewlett-Packard LaserJet 1012
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I think the first one (Bus 005 Device 009: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device) is the correct device - not sure why it's misspelled, I copied and pasted from the terminal.

The card reader works fine with my card in my son's WinXP.

---

### Post by Teasdale on 2009-03-28
Per another search, I typed in the two commands see if any SD drivers have been loaded:
lsmod|grep sd
lsmod|grep tifm

lsmod|grep sd:

sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
scsi_mod              183160  5 usb_storage,sd_mod,sr_mod,sg,libata

lsmod|grep tifm: no results

I don't really understand why this won't work. The card reader doesn't work in any of three Ubuntu installations - Ubuntu 7.04, 8.10 and Xubuntu. It only works with Windows. All the posts I'm seeing in my searches say that internal card readers can be problematic, and the solution is usually to try a USB card reader because they usually work. So why doesn't my USB card work?

---

### Post by Teasdale on 2009-03-30
As an update for anyone else finding this thread later - I posted on another forum, and I think the problem is that the card itself, not the card reader, is incompatible with Ubuntu because it was formatted for a Palm device. Apparently Palm and Ubuntu don't play well together.

---

### Post by das280zx on 2009-06-23
I think it might be the card also.  I can't get my SD card for my Nikon to work in my targus device, but the XD card for my little fuji works fine.  Interesting.

---

### Post by lavezarez on 2010-11-23
> **das280zx said:**
> I think it might be the card also.  I can't get my SD card for my Nikon to work in my targus device, but the XD card for my little fuji works fine.  **Interesting**.

Interesting?  More like disappointing.  You would expect any decent OS not to give you pains on detecting SDCARDs.

---

