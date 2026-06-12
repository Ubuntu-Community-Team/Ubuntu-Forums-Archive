---
title: "Manually Finding a USB Printer"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by DazedandConfusedWithLinux on 2009-02-24
Hey I have a USB printer hooked up, which prints fine with my xp boot, but my Linux boot (Ubuntu 8.10) won't automatically recognize the printer, and there is no option (at the beginning) for a USB printer. What can I do?

---

### Post by taurus on 2009-02-24
Have you looked in System -> Administration -> Printing -> New to see if it shows up there?

---

### Post by DazedandConfusedWithLinux on 2009-02-24
> **taurus said:**
> Have you looked in System -> Administration -> Printing -> New to see if it shows up there?

yes, that's where it WASN'T showing up

---

### Post by halitech on 2009-02-24
whats the output of
```
lsusb
```

---

### Post by DazedandConfusedWithLinux on 2009-03-02
> **halitech said:**
> whats the output of
```
lsusb
```

```

Bus 002 Device 004: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 002 Device 002: ID 050d:0237 Belkin Components F5U237 USB 2.0 7-Port Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04df:0020 Interlink Electronics 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by halitech on 2009-03-02
is the printer by chance plugged into the hub? I don't see any printer on the usb list so just curious.

---

