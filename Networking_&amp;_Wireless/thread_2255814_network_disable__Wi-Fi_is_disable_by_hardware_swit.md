---
title: "network disable : Wi-Fi is disable by hardware switch"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by bit_zhai on 2014-12-07
what is hardware switch ? 
lshw show PCI:0 -network DISABLE
but check BIOS setting all turn on already.

Please kindly help

---

### Post by bit_zhai on 2014-12-07
used intel 7260/7265 WLAN
it's normal function under win8.1 and win7
intel chipset as Broadwell

---

### Post by chili555 on 2014-12-07
This is a hardware switch: [https://ccit.college.columbia.edu/sites/ccit/files/Hardware_Switch.png](https://ccit.college.columbia.edu/sites/ccit/files/Hardware_Switch.png) In some cases, it is a key combination: [https://ccit.college.columbia.edu/sites/ccit/files/keyboard.png](https://ccit.college.columbia.edu/sites/ccit/files/keyboard.png)

In some cases, the little helper module that translates key presses into action; e.g. unlock the wireless, doesn't work correctly and we have to find some way to bypass it. Let's see what you have. Please open a terminal and run and post:```
rfkill list all
lspci -nn | grep 0280
lsmod
```

---

### Post by rowdy2 on 2014-12-08
I have read and tried to fix this prob on my laptop (compaq presario C60 with ubuntu 14.04) with no luck.  I am a complete noob to linux but I just can't figure out why this all has to be so impossible.  when I open the terminal and then try to run a command like (sudo apt-get update) it comes up and wants my password but is locked and will accept no input.  I surely could use some help.

---

### Post by Bucky Ball on 2014-12-08
> **rowdy2 said:**
> I have read and tried to fix this prob on my laptop (compaq presario C60 with ubuntu 14.04) with no luck.  I am a complete noob to linux but I just can't figure out why this all has to be so impossible.  when I open the terminal and then try to run a command like (sudo apt-get update) it comes up and wants my password but is locked and will accept no input.  I surely could use some help.

Please post a new thread in the appropriate forum section outlining your issues. chili555 is attempting to help the original poster with their problem and it can get confusing when trying to fix more than one issue on the same thread. Thanks and good luck.

---

### Post by rowdy2 on 2014-12-08
Yeah well I don't understand why my problem, which is exactly this same problem only with a few extra issues isn't good enough for here.  If asking additional questions about the same problem is wrong just what or where exactly do you recommend is?

---

### Post by chili555 on 2014-12-08
> **rowdy2 said:**
> Yeah well I don't understand why my problem, which is exactly this same problem only with a few extra issues isn't good enough for here.  If asking additional questions about the same problem is wrong just what or where exactly do you recommend is?Bucky knows how hard it is for old Chili to juggle 2, 3 or more posters' details in one thread. I hope you will start a new question of your own so I or one of my colleagues can give you our full attention.

---

