---
title: "add lines to fstab using terminal?"
date: 2009-07-18
forum: New to Ubuntu
---

### Post by drdave69 on 2009-07-18
In the file /etc/fstab

I need to add the following lines

usbfs /proc/bus/usb usbfs auto 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0




How do I do this ? I try & am told I do not have permissions.

---

### Post by MockY on 2009-07-18
Type this in terminal and type your password once prompted
```
sudo gedit /etc/fstab
```

---

### Post by andrew.46 on 2009-07-18
Hi drdave69,

> **drdave69 said:**
> How do I do this ? I try & am told I do not have permissions.

If you are set on the terminal a command such as this will do the trick:

```
sudo vim /etc/fstab
```

If you are not keen on vim just insert your own choice of editor such as nano or pico. Mind you a graphical editor such as gedit can more easily be used. Type Alt-F2 and then:

```
gksudo gedit /etc/fstab
```

All the best,

Andrew

---

