---
title: "internet"
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by thealex on 2007-08-28
i haven't installed Ubuntu yet because when i put in the live cd it says i have no internet connection but when i take the CD out and run on windows XP i have internet
can someone please help me i don't want to install Ubuntu if my internet dosent work

---

### Post by al108 on 2007-08-29
It shouldn't hurt anything if you install Ubuntu on an empty partition or extra hard drive.

Anyway, maybe you can tell us what kind of hardware you have. 

If you can also post an output of ```
lspci
``` ```
dmesg | grep eth
``` and ```
ifconfig
```

That might help us figure it out.

---

### Post by al108 on 2007-08-31
Ok, going step by step
1. Load up Ububtu from live CD.
2. Go to "Applications" > "Accessories" > "Terminal"
3. In the terminal type in the commands and see what happens.
lspci - will list all devices on your PCI bus
dmesg | grep eth - will search for any strings in the system ouput that mention your ethernet controller, if it found any drivers for it and how it was initialized.
ifconfig is your command that will show configuration of any network adapters that were found

If there were any errors with the driver you'll probably see them in the dmesg output, in that case knowing chipset and model of your card (not necessary brand name that it was sold under) - now you will know if it's supported out of the box.

Here's some information to get you started [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)
note links at the bottom too with references to perhaps wider databases.

Depending on what kind of computer/network card you've got there's a lot of  posts with problems that people already have solved here in ubuntu forums

---

