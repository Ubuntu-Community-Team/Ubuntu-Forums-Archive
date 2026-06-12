---
title: "Question about hardware"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by jermza on 2010-01-19
My current system is old and having a fight with Ubuntu, so I'm back on Windows while I wait for my new PC to arrive.

Just a question about hardware and optimal compatibility...

If I run an Intel i5 / i7 chip, and a recently released Nvidia graphics card, can I assume that I won't have too much stick with Ubuntu and open source drivers?

---

### Post by lotharmat on 2010-01-19
As always, I'd recommend trying the Live CD first to ensure there are no problems.

---

### Post by shreepads on 2010-01-19
IMHO its the motherboard that is more important in terms of hardware compatibility than the processor. So if you can state your motherboard and Nvidia graphics card details that would help...

---

### Post by SteveNorman on 2010-01-19
with a live cd try and run this on your old computer

```
sudo lshw
```

and post results.

for your new computer, to get 3d graphics you will have to enable the drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by cascade9 on 2010-01-19
You shouldnt have any issues with i5/i7 chipsets or CPUs. Or nVidia video drivers. Like SteveNorman said, you will need to install the drivers to get 3d (and in some cases, you will need the drivers just to get full resolution) 

> **shreepads said:**
> IMHO its the motherboard that is more important in terms of hardware compatibility than the processor. So if you can state your motherboard and Nvidia graphics card details that would help...

Chipset, but yes.

---

### Post by inobe on 2010-01-19
> **jermza said:**
> My current system is old and having a fight with Ubuntu, so I'm back on Windows while I wait for my new PC to arrive.

Just a question about hardware and optimal compatibility...

If I run an Intel i5 / i7 chip, and a recently released Nvidia graphics card, can I assume that I won't have too much stick with Ubuntu and open source drivers?

install with wubi

[http://www.ubuntu.com/getubuntu/download-wubi](http://www.ubuntu.com/getubuntu/download-wubi)

or run the cd in windows, this will not harm windows as it's installed like a program, it can be un-installed in add and remove programs.

---

