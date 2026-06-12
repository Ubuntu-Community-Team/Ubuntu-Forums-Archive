---
title: "Internet Stick Compatibility"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by mdesilets95 on 2011-05-23
hey everyone, 

new user of Ubuntu and trying to get online but i have a bell mobility USB stick that i use for my internet, it is an EVDO stick that accesses the cellular network in order to provide a connection however i couldn't get Ubuntu to recognize the USB stick when i inserted it, just wondering if anyone has any tips that can help me... Thanks folks

---

### Post by webofunni on 2011-05-23
what 

```
sudo dmesg | tail -50
```

says ?

---

### Post by mdesilets95 on 2011-05-23
Ubuntu does not recognize the usb internet stick, what am i doing wrong lol...

---

### Post by compmodder26 on 2011-05-23
> **mdesilets95 said:**
> Ubuntu does not recognize the usb internet stick, what am i doing wrong lol...

What version of ubuntu are you on?

---

### Post by mdesilets95 on 2011-05-23
Version 9.1

---

### Post by compmodder26 on 2011-05-23
Yikes, ok.  Well 9.10 is no longer supported. So first, I would recommend that you install a newer version of ubuntu.  If for some reason, you cannot do that, make sure the "usb_modeswitch" package is installed.

I can't remember what 9.10's network manager is like, but in 10.04 you can open network manager and there should be an option to set up a new mobile broadband connection.

---

### Post by mdesilets95 on 2011-05-23
ok thanks i will give it a try... cheers

---

