---
title: "Wireless internet problem"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by pudi211 on 2010-12-26
I installed ubuntu 10.10 last night, and when I am in the system it does not recognize my wireless card. When I click on the connection manager, it says firmware needs to be installed. 
 
I also run windows on the same computer, because I did not want to switch to Linux completely yet, and my wireless card works when I am in windows.

---

### Post by TBABill on 2010-12-26
Linux is telling you that a proprietary driver is needed. Go to System>>Administration>>Additional Drivers to see the options for which drivers are available. They must be downloaded so you need to be connected via ethernet first.

If that doesn't work, type this into a terminal and paste the output here for further help ```
lspci
``` If it's a USB device, use this instead ```
lsusb
```

---

### Post by theozzlives on 2010-12-26
do:
```
lspci
```
in a terminal and post the output here.

---

### Post by pudi211 on 2010-12-26
downloading the driver worked...thanks

---

