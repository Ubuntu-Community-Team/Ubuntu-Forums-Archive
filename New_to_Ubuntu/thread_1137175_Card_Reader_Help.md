---
title: "Card Reader Help"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by waldo_phill on 2009-04-25
I just upgrade to Jaunty and now my internal card reader is not being detected. I am still rather new in regards to mounting devices and how to do so. Any help with my card reader would be appreciated

---

### Post by waldo_phill on 2009-04-26
bump :(

---

### Post by coldReactive on 2009-04-26
Since you tagged this with USB, are you having problems mounting USB Drives as well? If so...
```
gksudo gedit /etc/modules
```
Add **usb_storage** on its own line somewhere, Save and Reboot. If it's already there, then I don't know why it isn't doing it.

---

### Post by waldo_phill on 2009-04-26
Thanks! Everything works now except the usb port in the drive :confused: Does anyone have any ideas on that?

---

### Post by waldo_phill on 2009-04-27
bump :confused:

Help anyone?

---

### Post by waldo_phill on 2009-05-03
](*,)

bump

---

