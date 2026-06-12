---
title: "USB drive detected (dmesg) but no entry in /dev?"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by josehg1979 on 2009-09-30
I have a usb external hard disk which used to be detected by ubuntu but now it's not detected but dmesg say me:
[31773.398740] usb 5-1: USB disconnect, address 29
[31773.398746] usb 5-1.1: USB disconnect, address 30

But it doesn't show up in /dev.

Is there a solution? Can you help me?

Thanks

---

### Post by halitech on 2009-09-30
does it show up in
```
sudo fdisk -l
```
or
```
lsusb
```

---

### Post by flyingsliverfin on 2009-09-30
maybe you could try mounting it manually? it would have to show up in fdisk for that though

---

