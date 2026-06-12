---
title: "Netgear Rangemax wireless usb 2.0"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by wwk2310 on 2007-03-18
I have been to the forums and possibly didn't search properly, but I cannot get this working with ndiswrapper.
After using ndiswrapper -i to install the wpn111.sys file, the message at ndiswrapper -l is driver not valid.
I know that this device is difficult, maybe impossible to set up, but I am hoping someone has had success.

Wendell

---

### Post by Floppyjoe on 2007-03-18
> **wwk2310 said:**
> I have been to the forums and possibly didn't search properly, but I cannot get this working with ndiswrapper.
After using ndiswrapper -i to install the wpn111.sys file, the message at ndiswrapper -l is driver not valid.
I know that this device is difficult, maybe impossible to set up, but I am hoping someone has had success.

Wendell

The sudo ndiswrapper -i command should be preformed on the .inf file with .sys and possible .bin files in the same directory. Be careful because it is case sensitive.

You can delete the invalid driver with the:
```
sudo ndiswrapper -e drivername
```

---

