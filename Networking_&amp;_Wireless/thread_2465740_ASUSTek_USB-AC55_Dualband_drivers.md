---
title: "ASUSTek USB-AC55 Dualband drivers"
date: 2021-08-10
forum: Networking &amp; Wireless
---

### Post by jeffjr231 on 2021-08-10
I have a USB wireless adapter here that I've been having issues getting drivers for on 20.04.2 (Focal Fossa LTS). I have looked over the forum and saw fixes for older versions (like 16.04), and I've tried a few to no solution. I was wondering if there was any solid drivers that gave the adapter the ability to go above 200mbps, as in Windows on the same disk as the ubuntu install, gets near 600mbps on the same wifi network.
If anyone can point me to valid ones, please let me know!

EDIT: note: I've had a fix run on 18.04, but seems like it will not work in the newer LTS.

---

### Post by morrownr on 2021-08-11
I can't tell you exactly which chipset that adapter uses because a quick search makes me think ASUS has used more than one chipset for that product name.

What you can do is go here: [https://github.com/morrownr](https://github.com/morrownr)

I suggest you first look in the 88x2bu folder and if that isn't the right one, try 8812au. What you will find in the folders is a file called:

supported-device-IDs

Open that file, follow the directions and once you find your device ID, you will know which driver to use.

Before installing the new driver, you need to clean out any leftovers from previous installation attempts.

Let us know if you have any problems.

---

### Post by chili555 on 2021-08-11
Let's find out exactly what chipset you have and then we can more clearly identify the correct driver. Please run and post:

```
lsusb
```

Thanks.

---

