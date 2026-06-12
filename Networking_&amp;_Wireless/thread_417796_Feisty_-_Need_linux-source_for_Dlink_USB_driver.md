---
title: "Feisty - Need linux-source for Dlink USB driver"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by superyounan1 on 2007-04-21
Getting my Dlink WUA-1340 USB wifi card to work in Edgy was a biiiig headache, ndiswrapper didnt work.

I had to download railink drivers, modify the headers to include my device and vendor id, and compile my own drivers.

I upgraded to Feisty just now and off course my dlink dirivers dont work any more. So i figured I'd just recompile the drivers for the new kernel.

I need the source for the kernel thats running to compile the driver

```
uname -r 
2.6.20-15-generic
```

but the latest I find on the ubuntu site is [linux-source-2.6.20-14.23]("http://packages.ubuntu.com/feisty/devel/linux-source-2.6.20")

Does anyone know if it will be ok to use the source for that version instead? Or why the source for my kernel isnt avaliable?

---

