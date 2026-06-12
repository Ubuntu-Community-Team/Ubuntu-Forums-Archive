---
title: "Mount internal card reader"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by wlraider70 on 2011-06-19
I have a server (no gui) with an internal multi card reader. 
I'm not sure how to mount cards or if I mount the reader as a whole?

Lsusb shows the 8-in-1reader as a whole, but not a sd card or cf card. 



Thanks.

---

### Post by deconstrained on 2011-06-19
If there's no card in the reader then there's nothing to mount. When you insert a card it should be recognized as a block device, and from there you can either mount it manually or have HAL mount it in /media.

I don't know if you can mount more than one card at once while inserted into the reader, as distinct block devices, but it's probably worth a try (it might depend on the hardware itself).

---

### Post by wlraider70 on 2011-06-20
how can I tell what device is the card reader/ card?

---

### Post by wlraider70 on 2011-06-23
When the card is in the reader, I don't know what to mount.

---

### Post by deconstrained on 2011-06-25
Is it an internal USB card reader? Wait a few seconds, it should be mounted in /media automatically, and an icon/shortcut for it should appear on your desktop. If that doesn't happen, use the commands "lsusb" and "dmesg" after inserting the card and waiting some time, and the output should tell you if it's been recognized or not. Here's one way of seeing whether it shows up (in the case of a USB reader):

1. Before inserting:
```
lsusb > usb1
```
2. After inserting, and waiting a few seconds:
```
lsusb > usb2
```
3. Then:
```
diff usb1 usb2
```

FYI volumes on SCSI block devices show up in /dev with names like sd[a-z][0-9], where the letter distinguishes devices and the number at the end distinguishes the partition number (for instance, a typical SD card might be /dev/sde1). But again, you don't have to worry about this because typically Ubuntu should mount it automatically.

---

