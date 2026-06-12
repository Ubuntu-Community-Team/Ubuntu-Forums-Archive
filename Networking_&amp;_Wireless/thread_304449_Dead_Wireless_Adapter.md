---
title: "Dead Wireless Adapter"
date: 2006-11-21
forum: Networking &amp; Wireless
---

### Post by tomuban on 2006-11-21
My SMC EZ connect wireless adapter does not work when i boot live ubuntu. it is in a usb port and the light never comes on. the mouse  works. The adapter works when i use windows.
?????????? thanks

---

### Post by FrodoB on 2006-11-21
Supply the output of:

lsusb

Then we can see what chipset it contains.

---

### Post by tomuban on 2006-11-21
2.4~2.5 Ghz
thx

---

### Post by FrodoB on 2006-11-22
The output of lsusb is something like this:

Bus 002 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0ace:1215 ZyDAS
Bus 001 Device 002: ID 1058:0901 Western Digital Technologies, Inc.
Bus 001 Device 001: ID 0000:0000

If we had that information we could determine what drivers you could use.

---

