---
title: "Help with Belkin 54g PCI F5D7000 desktop wireless adapter along with other problems"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by xjarheadx1462 on 2007-11-16
Ok, for starters i cant connect using Ubuntu Gutsy's Network Manager, so i removed it then attempted to install the .deb package for Wicd i386, problem is though is that when i click install package it will ask for my password then it will load the window, load something, and then it will close out. I attempted to access it from the terminal at /opt/wicd/tray.py and it will tell me that path doesn't exist, and ill look through opt folder and find nothing named wicd as if it never even installed. So now i not only cannot connect my network because network manager is completely gone and my .deb will not install anything. I need an alternative to this because ive been stuck on it for 3 days now....im a bit of a nubby so dont expect me to know too complicated of things,

---

### Post by MrFSL on 2007-11-16
I would try removing and reinstalling wicd from the command line:

**REMOVAL:**
```
sudo apt-get --purge remove wicd
```

**INSTALL:**
```
sudo dpkg -i /path/to/wicd.deb/file
```

...and post the output if their is an error.

As far as the card goes you will probably want to install the firmware as I don't think it's available for that card.

I would suggest reading here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty)

I have used the "1.3. Using the native drivers" section with much success.

---

