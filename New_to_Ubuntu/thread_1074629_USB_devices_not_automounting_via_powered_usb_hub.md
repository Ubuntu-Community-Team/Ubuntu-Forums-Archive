---
title: "USB devices not automounting via powered usb hub"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by candtalan on 2009-02-19
Ubuntu, kubuntu 8.04
I am using a couple of powered usb hubs, type D-Link DUB-H4,
and I find that usb devices are not recognised, (nor auto mounted) when inserted into this hub. 
However, if the hub usb connection is disconnected and reinserted, then the devices already in the hub, such as usb stick or usb card reader, are then suddenly recognised etc etc.

1) How can I investigate this?
2) any suggestions for a fix please?

tia

---

### Post by blueridgedog on 2009-02-22
A way to investigate it would be to use the 

```
lsusb
```

Command.  This will display the device the PC sees on the USB system.

You can also try:
```

lshw 
```

And review the USB section.

---

