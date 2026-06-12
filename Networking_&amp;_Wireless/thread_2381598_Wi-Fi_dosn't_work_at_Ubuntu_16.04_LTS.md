---
title: "Wi-Fi dosn't work at Ubuntu 16.04 LTS"
date: 2018-01-02
forum: Networking &amp; Wireless
---

### Post by dale918918 on 2018-01-02
Hi.
I have a problem with Network Card "broadcom netlink (tm) gigabit ethernet" , on windows it works perfectly , but on ubuntu it won't search any network.
This ubuntu is working at 3-4 computers and all works , but not this one. 
Please Help.
Best Regards.

---

### Post by jeremy31 on 2018-01-02
Please see the wireless script link in my signature and post results

---

### Post by dale918918 on 2018-01-02
I just write it because i can't copy this.

Resolving github.com (github.com... failed: Temporary failure in name resolution.
wget: unable to resolve host address 'github.com'

---

### Post by jeremy31 on 2018-01-02
Try method 2 without internet access

---

### Post by dale918918 on 2018-01-03
I can't execute it :/

---

### Post by QIII on 2018-01-03
Hello!

When you say you can't execute it, what happens?

---

### Post by dale918918 on 2018-01-03
I tick "Allow executing this file as program" and it unticks same without my ingeration..

Ok , i completed this but i can't open it with terminal :/

---

### Post by jeremy31 on 2018-01-03
Is there a wireless-info.txt in the same directory as wireless-info?  Where did you put the wireless-info file?

---

### Post by dale918918 on 2018-01-03
I don't know where it must to be .-. Im using Ubuntu for like 2 months , but only for creating HTML pages, i installed it on old computer and i didn't know where i must put it. I have it at start screen.

---

### Post by jeremy31 on 2018-01-03
try in terminal ```
locate wireless-info
```

---

### Post by dale918918 on 2018-01-03
0 Information from terminal

---

### Post by jeremy31 on 2018-01-03
You might want to follow the instructions again and copy the file to your desktop

---

### Post by dale918918 on 2018-01-04
0 Info from it , It only say "######### wireless info START ##########" nothing else.

---

### Post by jeremy31 on 2018-01-04
Just post results from terminal for ```
lspci -nnk | grep -iA3 net
rfkill list
iwconfig
```

---

### Post by dale918918 on 2018-01-04
```
tomek@Tomek-Aspire-5710Z:~$ lspci -nnk | grep -iA3 net04:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
    Subsystem: Acer Incorporated [ALI] NetLink BCM5787M Gigabit Ethernet PCI Express [1025:012e]
    Kernel driver in use: tg3
    Kernel modules: tg3
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. BCM4311 802.11b/g WLAN [1468:0422]
    Kernel modules: ssb, wl
06:00.0 FLASH memory [0501]: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller [1524:0730]
tomek@Tomek-Aspire-5710Z:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
tomek@Tomek-Aspire-5710Z:~$ iwconfig
lo        no wireless extensions.


enp4s0    no wireless extensions.


tomek@Tomek-Aspire-5710Z:~$ 





```

---

### Post by jeremy31 on 2018-01-04
See a post from my friend Hadaka [https://ubuntuforums.org/showthread.php?t=2316978](https://ubuntuforums.org/showthread.php?t=2316978)
That should get the wifi working

---

### Post by dale918918 on 2018-01-04
And it seems to be working! :) Thanks dude for help! :)

---

