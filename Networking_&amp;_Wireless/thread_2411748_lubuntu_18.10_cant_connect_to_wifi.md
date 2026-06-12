---
title: "lubuntu 18.10 cant connect to wifi"
date: 2019-02-03
forum: Networking &amp; Wireless
---

### Post by leepreslan16 on 2019-02-03
I am running lubuntu 18.10 test environment from a usb drive before I fully install it but when I go to connect to my home wifi network, the nm-tray will generate a pop up on the desktop stating connection lost to "network name". I cant connect to wifi to fully install lubuntu 18.10.

---

### Post by praseodym on 2019-02-03
Please open a terminal with the Live-USB (CTRL+ALT+T) and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsusb
```

---

### Post by jeremy31 on 2019-02-03
You are not required to have an internet connection to install.  If you are installing using UEFI, I would suggest installing without internet

---

### Post by Rick St. George on 2019-02-05
If you'll notice all the people having problems with v18 ... its a good thing you tested it. If no internet, you can't get full updated software. Some people even after installing v18, such as myself, NEVER get internet access afterwards because of what Canonical did with the Network Manager. My recomendation is to try v16.04 FIRST, and as I am - watching the forums for when they fix the problems. No one is able to answer all the requests for the relevant problems ... other than - its the mfg of your NIC not providing drivers. While that may be true ... AGAIN - we must wait for it to be fully implemented. 

The problem is, when a new version upgrade is provided - how can "we" know and check all the mfg.s of all devices in all of our machines?
How many computers, laptops, DVDs, Tablets, etc. Do you have? Do you know of all NiCs, all VGAs, all etc. in all your devices?

Just saying. Its good you tested it first ! ! ! I wasted 4 days ([https://ubuntuforums.org/showthread.php?t=2411324](https://ubuntuforums.org/showthread.php?t=2411324)) trying to make v18 work. Gave up ... and RESTORED my main system.

Rick

---

