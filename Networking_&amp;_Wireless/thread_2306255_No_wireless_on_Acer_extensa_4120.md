---
title: "No wireless on Acer extensa 4120"
date: 2015-12-13
forum: Networking &amp; Wireless
---

### Post by BoyGenius on 2015-12-13
**EDIT: I think I solved my problem. I went into Preferences->Additional Drivers and chose one for my wireless card and now it works.**


I'm trying the Live USB before installing and I'm not able to access the internet via Wi-Fi. Ethernet works fine. I would like to make sure I'll be able to get wireless to work before installing. I'm using Lubuntu-15.10-desktop-i386.iso.

The machine is an Acer Extensa 4120-1404.

There is what seems to be a physical wireless button on the front of the laptop, but it pressing it (sliding to the right, actually) doesn't do anything. Its light is not on and does not go on when I slide to the right, even if I hold it for many seconds.

EDIT: Just wanted to point out that wireless works fine in Windows.

---

### Post by Hadaka on 2015-12-13
Hi, please open a terminal ctrl/alt/t or click dash an type in terminal
then copy and paste..
```
lspci -nnk | grep -iA2 net
rfkill list all
```
post the output
thanks.

---

### Post by BoyGenius on 2015-12-13
I think I solved my problem. I went into Preferences->Additional Drivers and chose one for my wireless card and now it works.

---

### Post by Hadaka on 2015-12-13
Great ! glad you found the problem, be sure to
```
sudo apt-get update
sudo apt-get dist-upgrade
```
to bring your system up to date with security and other patches.
then, also please take the time to mark this thread SOLVED by
logging back in to your thread,first post and click TOOLS in the upper right area
then choose solved.
thanks.

---

