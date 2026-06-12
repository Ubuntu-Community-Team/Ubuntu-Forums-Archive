---
title: "Connect Ubuntu to Windows Remote desktop"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by JacKeown on 2009-09-14
Hi I was wondering what's the easiest way to connect my Ubuntu laptop to my windows computer using Remote desktop

Thanks in advance

---

### Post by denver on 2009-09-14
Try:

Applications-->Internet-->Terminal Server Client

---

### Post by JacKeown on 2009-09-14
thanks but I tried krdc and avahi zeroconf browser wont start

---

### Post by nhasian on 2009-09-14
if you install UltraVNC on your windows desktop then you can connect to it by using Applications->Internet->Remote Desktop Viewer

---

### Post by whitethorn on 2009-09-14
have you tried using rdesktop? If it's not already installed just apt-get it.

in a terminal

```
rdesktop ip.address.0.0 -f
```

To read about more options
```
man rdesktop
```

---

