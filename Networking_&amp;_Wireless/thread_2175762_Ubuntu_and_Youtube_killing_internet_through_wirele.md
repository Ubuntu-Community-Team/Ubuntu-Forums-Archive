---
title: "Ubuntu and Youtube killing internet through wireless"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by ddubbz1979 on 2013-09-20
Ubuntu killed my internet during install in minutes and finally got an install (13.04 64bit.) hardwired ethernet.   Bypassed updates and third party during install but sudo get update / upgrade in the terminal after install complete.  Now works fine for a few minutes but keeps killing internet on whole network when I try to view a certain youtube vid.  Let's me watch others.  ???

---

### Post by praseodym on 2013-09-21
Please check some of the settings:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
iwlist chan
sudo iwlist scan
```
Did you install the adobe-flashplayer?
```

sudo apt-get install ubuntu-restricted-extras
```
The flash-plugin is "old" and no longer developed for Linux from Adobe (only security updates). Does it work with Google Chrome (not Chromium!!!)? Chrome brings the (latest?) adobe flash-plugin working in a sandbox.

---

### Post by ddubbz1979 on 2013-09-21
I did install restricted extras.  have not tried chrome.  firefox only.  seems to do fine except boot screen is shaky and sitting halfway off to the left of my monitor.  good thing i know where window and ubuntu are on the list cause can't read it to select.  and entire network dies after a few minutes online in ubuntu.  not just youtube after all.  must be something else going on.  will check settings and reply back soon.  thank you.

---

### Post by ddubbz1979 on 2013-09-21
Downloaded Chrome.  Everything works.  Was looking forward to Firefox though.  

Edited to delete original content.

---

### Post by ddubbz1979 on 2013-09-21
one thing i did not do was install updates and third party software during installation while i was hardwire ethernet connected.  went back to wireless after installation and then updated everything i knew of.  also, if theres anything in my previous post that could compromise security please let me know.  i'm a front end computer user so most of that is japanese to me.  thank you for your help.  i did change wireless setting to wpa2 and no help there.  internet still goes down after minutes on my whole network.  windows operates fine.

---

### Post by praseodym on 2013-09-22
Lets check these terminal outputs. Please show additionally
```

lspci -nnk | grep VGA
```

---

### Post by ddubbz1979 on 2013-09-23
$ lspci -nnk | grep VGA
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6530D] [1002:964a]

---

### Post by praseodym on 2013-09-23
Check in the "Update-manager"-> Additional drivers if the ATI-driver is recommended

---

### Post by ddubbz1979 on 2013-09-23
All three drivers listed are ATI.  I chose top driver.  Should I try maybe the middle one?  Top one says tested.

---

### Post by praseodym on 2013-09-23
Yes, try the tested/recommended one first

---

### Post by ddubbz1979 on 2013-09-23
One i'm using now is the open source/tested driver.  Other two below it are proprietary.

---

