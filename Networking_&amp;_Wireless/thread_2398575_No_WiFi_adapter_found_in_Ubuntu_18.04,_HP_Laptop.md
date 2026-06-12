---
title: "No WiFi adapter found in Ubuntu 18.04, HP Laptop"
date: 2018-08-14
forum: Networking &amp; Wireless
---

### Post by bodya123 on 2018-08-14
[INDENT] 					I've installed my Ubuntu 18.04 with minimal installation mode with  keeping the option to install WiFi drivers along. But still I couldn't  use the WiFi, since the setting is showing that there is no WiFi devices  found. 
[ATTACH]280728[/ATTACH]Tried most of the solutions mentioned in forum but still can use the WiFi.

[/INDENT]

---

### Post by chili555 on 2018-08-14
Here is your wireless adapter:> 04:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
Please check here: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by bodya123 on 2018-08-15
Thanks for the reply but unfortunately it still can't find any WiFi. I also checked on Windows and the WiFi there is working

---

### Post by chili555 on 2018-08-15
> unfortunately it still can't find any WiFi.Did you install any new packages based on the link I referred you to? Did you try a reboot? Is the driver loaded?```
lsmod | grep wl
```If not, is there any clue if you try to load it?```
sudo modprobe wl
```Is the wireless switch, sometimes referred to as Airplane Mode, set to enable or disable wireless?```
rfkill list all
```

---

### Post by praseodym on 2018-08-15
SecureBoot is turned off?

---

