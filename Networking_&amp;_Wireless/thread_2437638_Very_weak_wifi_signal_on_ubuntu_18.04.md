---
title: "Very weak wifi signal on ubuntu 18.04"
date: 2020-02-26
forum: Networking &amp; Wireless
---

### Post by linux-bioinfo on 2020-02-26
Hi. Need help in increasing my wifi signal strength. I am using a TPlink router (model TL-WR850N). and my desktop has Intel dual band wireless - AC 3168 hardware.

This is the output for lsmod | grep rtl

btrtl                  20480  1 btusb
bluetooth             573440  33 btrtl,btintel,btbcm,bnep,btusb,rfcomm

---

### Post by him610 on 2020-02-27
Hello linux-bioinfo,
I have an Intel AC3168 also; I have no issues with it at all. Your AC3168 is probably on the PCI bus, not the USB bus.
Please complete the recommended steps here, [https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108") 
It will provide a detailed analysis of your networking environment. 
Other members will need the output of *wireless-info.txt* to be able to best advise you.

---

### Post by linux-bioinfo on 2020-02-28
Thank You @him610. I have followed the instruction on the link provided by you and run the script. Here is the wireless-info.txt output. 
[https://pastebin.com/19s1LsQX](https://pastebin.com/19s1LsQX)


Please help

---

### Post by CelticWarrior on 2020-02-28
The old TL-WR850N router probably has something to do with it.
I didn't spot anything else wrong with your installation.

---

### Post by chili555 on 2020-02-28
> **linux-bioinfo said:**
> Thank You @him610. I have followed the instruction on the link provided by you and run the script. Here is the wireless-info.txt output. 
[https://pastebin.com/19s1LsQX](https://pastebin.com/19s1LsQX)


Please helpIf you boot into an earlier kernel from -40, is the problem resolved?

Is there a TX Power setting in the router? Is it set to the maximum?

---

