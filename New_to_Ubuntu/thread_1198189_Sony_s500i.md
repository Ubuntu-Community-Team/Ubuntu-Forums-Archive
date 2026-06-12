---
title: "Sony s500i"
date: 2009-06-27
forum: New to Ubuntu
---

### Post by MrGill on 2009-06-27
I know there is an archived post about this already, but it doesn't solve my problem.

I have connected this phone up previously and it showed up as a USB device and I could access the memory card and shove files onto the card, but now around 18 months later it doesn't show up at all... 

it shows up in lsusb

Bus 002 Device 004: ID 0fce:e088 Sony Ericsson Mobile Communications AB 

but doesn't appear on my desktop or in media...

any ideas why it wouldn't, how to solve it, or to a walkthrough of how i need to set it up, now that I'm running Jaunty?

Any help would be great thanks

---

### Post by rraj.be on 2009-06-29
Could you post the output of the

```
sudo fdisk -l
```

---

### Post by MrGill on 2009-06-30
Tried it with and without the phone plugged in, i don't know if it was meant to show up, but it doesn't

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00018178

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2492    20016958+  83  Linux
/dev/sda2            2493       24321   175341442+   5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris
/dev/sda6            2493       16838   115234182   83  Linux
/dev/sda7           16839       24133    58597056   83  Linux

Partition table entries are not in disk order

---

