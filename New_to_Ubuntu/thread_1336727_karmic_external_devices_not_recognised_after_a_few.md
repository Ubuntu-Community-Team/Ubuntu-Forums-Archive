---
title: "karmic: external devices not recognised after a few days..."
date: 2009-11-24
forum: New to Ubuntu
---

### Post by infernus_crusher on 2009-11-24
i could plug and play my seagate external hdd (ntfs formatted) and logitech quickcam (working fine in cheese) on the first few days after installing karmic. but after a while they both stopped working. i tried fedora 12 and the same thing happened.

is there a reason behind this?

---

### Post by infernus_crusher on 2009-11-25
when it is plugged in, the light would come on for about 10 seconds then go away.

---

### Post by AndThenWhat on 2009-11-25
Try opening a Terminal window (Applications -> Accessories -> Terminal) and typing "dmesg" (no quotes) before you plug them in and then again after you plug them in to see if there are any error messages.

---

### Post by infernus_crusher on 2009-11-25
No changes in dmesg is visible before and after plugging it in. Could this be a problem with kernel 2-6.31.5?

---

### Post by infernus_crusher on 2009-11-25
Okay I ran `chkdsk /f` on the drive in Windows and it works now. But my webcam is still not working.

---

