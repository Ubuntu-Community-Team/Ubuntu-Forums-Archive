---
title: "Cannot Figure Out Wireless Drivers for Macbook"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by finbar800 on 2014-03-09
Today, I installed Lubuntu on a white Macbook 4,1. The intallation went fine, and I replaced OSX. However, the wifi did not work on the computer. As in, it did not show up as an option or show any wireles networks. After spending sometime on Google, I found that other people had the same problem, and I tried to follow some guides to install the Broadcom BCM4321 wireless driver, but none of them were successful. I'm not that experienced with Ubuntu, so if someone could walk me through fixing this issue that would be great.

Thanks in advance!

---

### Post by chili555 on 2014-03-09
Please open a terminal and give us a bit more information:```
rfkill list all
lsb_release -d
lspci -nn | grep 0280
```Thanks.

---

### Post by finbar800 on 2014-03-09
finbar@Romulus:~$ rfkill list all
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
finbar@Romulus:~$ lsb_release -d
Description:    Ubuntu 13.10
finbar@Romulus:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)

---

### Post by chili555 on 2014-03-09
You have one of the weirdest devices ever built by Broadcom in that the solution depends on your kernel version. Good news, eh?? Please get a temporary wired ethernet connection, open a terminal and do:```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet, reboot and let us have a good report.

---

### Post by finbar800 on 2014-03-09
Well, it works now. Not sure how, but hey, I'll take it! Thanks!

---

### Post by chili555 on 2014-03-09
Let me explain for the benefit of you and the searchers. Many sources, including Broadcom themselves, assert that the Broadcom STA driver, bcmwl-kernel-source, is correct for your device 14e4:4328. Painful trial and error by many of your predecessors proves that in later Ubuntu versions, it is not correct and that the native driver b43 and separately downloaded firmware is correct. Therefor, we removed bcmwl-kernel-source and installed the firmware. The result was, as I expected, "Well, it works now."

Glad it's working. Please use thread tools at the top to mark Solved.

---

