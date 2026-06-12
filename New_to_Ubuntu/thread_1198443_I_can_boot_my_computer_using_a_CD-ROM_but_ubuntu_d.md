---
title: "I can boot my computer using a CD-ROM but ubuntu does not detect it"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by legolas_w on 2009-06-27
Hi
Thank you for reading my post
I have ubuntu 9.04 installed in my computer and I do not know for what reason it does not detect my cd-rom (CD rom icon is not present in the Places=>Computer).

To ensure that My CD-ROM is fine, I tried and boot the computer using a bootable CD and I tried it several times to ensure that it always works. but as I said it does not works inside the ubuntu itself.

is there some sort of diagnosis which I can do to detect the problem?

thanks.

---

### Post by durand on 2009-06-27
Open a terminal (Applications > Accessories > Terminal) then run:
```
dmesg
```
Scan through it and see if there are any related errors.
Try loading the cdrom drive manually with a cd in:
```
sudo mount /dev/cdrom
```

---

### Post by presence1960 on 2009-06-27
your cdrom will not appear in the places menu until a disk in the drive. Up to that point it isn't mounted. When in Ubuntu and you put a cd/dvd in the drive does the cd-rom icon appear on your desktop?

---

