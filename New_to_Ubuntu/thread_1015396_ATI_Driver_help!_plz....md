---
title: "ATI Driver help! plz..."
date: 2008-12-18
forum: New to Ubuntu
---

### Post by mag1strate on 2008-12-18
I've just recently purchased ET: Quake Wars and I have been playing it for a bit, but I have some performance issues...I know my card can more than handle the game (I have an ATI Radeon HD 4670), but I have to run it on low, with a bunch of hickups. My question is if I should keep using the default ATI drivers that you use, or should I get the ATI drivers that ATI have created? Would it help? Since I am new, should I take the risk?:confused:

---

### Post by DaGrimReefah on 2008-12-19
ATI is notorious for not having the best Linux support. However, you are not running any risk by installing the newest ATI provided drivers if you do it correctly. In fact, I encourage installing the ATI-provided drivers, as they will provide you with much better 3-D capabilities than the restricted drivers can, as I've seen first hand when my brother installed the ATI-provided drivers.

First, uninstall your restricted ATI driver by opening the terminal:
```
sudo apt-get remove xorg-driver-fglrx
```

Then, go to the ATI site and DL the latest drivers. Download the latest .run file for your card. After DLing, in terminal, change to the directory where the freshly downloaded .run file resides, usually the desktop. Then, just simply execute.

```
./ati-driver-installer-whatever-version-you're-installing.run
```

I don't remember if you need a "sudo" before that, but if you do, it will tell you. Then, to configure X, type in the terminal:

```
sudo aticonfig -initial
```

Then, just restart X. I hope that helps.

---

### Post by zika on 2008-12-19
there might be a command missing:```
sudo chmod +x ./ati-driver-installer-whatever-version-you're-installing.run
./ati-driver-installer-whatever-version-you're-installing.run
```

dont' be afraid of ATI original drivers ... they are good. visit that site from time to time to get newest version. AtiCatalystCenter is very nice.

---

