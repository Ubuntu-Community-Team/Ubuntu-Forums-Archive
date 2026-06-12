---
title: "uncheck wired connection in network-manager before using wireless?"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by chunchengch on 2007-10-20
It really annoys me that every time I need to use wireless, I have to uncheck the wired connection in network-manager and then reboot to make wireless work. :confused:

Is it necessary for wireless? or do I do something wrong? 
thanks for help!

---

### Post by dmizer on 2007-10-20
you should need to uncheck your wired before going wireless.

you shouldn't need to reboot for the settings to take effect.  are you putting a check in the wireless before unchecking wired?

try this command after putting a check in wireless:
```
sudo /etc/init.d/networking restart
```

sure, it's a command, but it's better than rebooting.

---

### Post by chunchengch on 2007-10-20
Thanks for quick reply,

I can not check the wireless option in the network-manager, so I have to reboot.

I will try to use this command to see if it works, will response few minutes later.

---

### Post by chunchengch on 2007-10-20
I checked the wired connection in network-manager before I wrote down the command, I lost the internet connection and I did not remember what command is, so I have no choice but to reboot again, after the machine starts up to the desktop, I enter the preference > network settings of Firestarter, and change the Ethernet Device from eth0 to eth1, the wireless connection is ready now, what a amazing discover for me!:)

However, thank you so much!:)

---

