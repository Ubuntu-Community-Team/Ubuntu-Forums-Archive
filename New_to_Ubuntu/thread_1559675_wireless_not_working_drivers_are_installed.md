---
title: "wireless not working drivers are installed"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by mainframe1987 on 2010-08-23
i manually installed the drivers and wirelesstools and it still says wireless disconnected and its grayed out so i cant click on it

---

### Post by anewguy on 2010-08-23
Is "Enable Wireless" checked when you right-click network manager?

Also -[LIST]
[*]what is your wireless adapter?
[*]what driver did you install?
[*]did you install the driver so it is available in System/Administration/Hardware Drivers, or did you use ndiswrapper or some other means to install your driver?
[*]can you post the output of:[LIST]
[*]ifconfig
[*]lspci
[*]if you're adapter is USB:  lsusb
[*]lshw -C network
[/LIST]
[/LIST]

Dave ;)

---

