---
title: "Linksys WUSB54G v4 in Hardy Heron"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by growingneeds on 2008-09-07
Linksys WUSB54Gv4

I had spent quite a bit of time sourcing the internet to make my wireless adapter work. Although the default setup of Heron detected the card and allowed me to see the wireless networks available in my region, I was unable to connect to any of them. It appears that the native driver supplied in Heron is at fault (rt2500usb). I hope this tutorial will be of help. Essentially, the solution requires ndiswrapper to load during boot and have it run the original Linksys drivers.

**Install ndiswrapper-utils-1.9:**
Insert Ubuntu Live CD. Permit the dialogue box. Install ndiswrapper from Synaptic Package Manager.

**Download latest driver from Linksys site:**
Extract and copy the 3 files from the WUSB54Gv4 directory to the home directory. be The 3 files are
[LIST=1]
[*]rt2500usb.cat
[*]rt2500usb.inf
[*]rt2500usb.sys
[/LIST]

**Ensure /etc/ndiswrapper directory is empty:**
```
~$ ndiswrapper -l
```
Uninstall listed drivers, if any.

**Install new Linksys driver:**
Make sure the .sys and .ca files are in same directory.
```
~$ sudo ndiswrapper -i rt2500usb.inf
```

**Install ndiswrapper as a module:**
```
~$ sudo depmod -a
~$ sudo modprobe ndiswrapper
~$ sudo ndiswrapper -m
```

**Prevent native driver from loading:**
```
~$ sudo modprobe -r rt2500usb
```

**Blacklist native kernel driver:**
This prevents it from overriding the ndiswrapper driver.
```
~$ gksudo gedit /etc/modprobe.d/blacklist
```
To the end of /etc/modprobe.d/blacklist, add as a new line: ```
blacklist rt2500usb
```

**Set ndiswrapper to load during boot:**
Edit /etc/modules:
```
~$ gksudo gedit /etc/modules
```
To the end of /etc/modules, add as a new line: ```
ndiswrapper
```

**Reboot.**

---

