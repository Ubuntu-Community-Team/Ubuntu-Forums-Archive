---
title: "Can't access the internet with installed ubuntu"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by zweiundzwei on 2006-08-20
I just installed ubuntu on my hard disk and I can't go online with it. When I use Windows or even the Live CD on the same computer, it works without any problems. 

Any ideas what to do to make it work with ubuntu?

Thank you.

---

### Post by noof on 2006-08-20
What network card are you using? wireless? usb?
paste the output of "lspci -v" if it's a pci card or "lsusb -v" if it's an usb one.

---

### Post by zweiundzwei on 2006-08-20
NVIDIA nForce Networking Controller (is that the name you need?), it's not wireless and no usb.

---

### Post by noof on 2006-08-20
paste the output of ```
sudo ifconfig -a
``` and ```
dig www.sunet.se
``` and ```
traceroute 130.242.80.31
```

---

### Post by zweiundzwei on 2006-08-20
Erm. For some reason I don't understand it works now ](*,) 

Thanks a lot for the help anyway :)

---

