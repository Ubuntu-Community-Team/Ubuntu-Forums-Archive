---
title: "huawei usb dongle"
date: 2013-10-19
forum: Networking &amp; Wireless
---

### Post by ronb19495 on 2013-10-19
I am using ubuntu 13.10 just tried my huawei usb dongle it wouldnt work.I then went into disks where it was mounted I turned it off on the disks menu up the top unplugged it and replugged it voila it works is this some kind of bug i have to say also I hit the eject button as well

---

### Post by praseodym on 2013-10-19
Hi,

did you install the package **usb-modeswitch**?

---

### Post by ronb19495 on 2013-10-19
yes allready installed thanks I think its a modemmanager problem well you rattled my cage I uninstalled modem manager rebooted and its working thank you

---

### Post by praseodym on 2013-10-19
Try to reinstall the NWM:
```

sudo apt-get install --reinstall network-manager network-manager-gnome modemmanager
```

---

### Post by Oshima_Kenji on 2014-01-19
Sorry If I was asking here.
But..

I have a modem which is the same brand, but different model. It's e172 model.
Does it works with ubuntu 12.04 or the newest version ?

Thanks for the advance.

---

### Post by praseodym on 2014-01-20
Please show
[B]
lsusb[/B]

---

