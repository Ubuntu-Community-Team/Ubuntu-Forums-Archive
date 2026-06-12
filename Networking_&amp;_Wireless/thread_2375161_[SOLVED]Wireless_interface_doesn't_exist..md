---
title: "[SOLVED]Wireless interface doesn't exist."
date: 2017-10-22
forum: Networking &amp; Wireless
---

### Post by meiaman on 2017-10-22
Hello, everyone. I have notebook with dualboot ubuntu 17.10 and windows 10.

Wifi is working normally on windows but not on linux.

Here is the scripted file with all the needed information.

[http://paste.ubuntu.com/25795955/](http://paste.ubuntu.com/25795955/)

Greatly appreciate any assistance.

Edit: bug solved by updating bios.
Assumed to be a bug on bios v1.25 which turned secure boot on, even if it is off.
wifi working normally and other missing things such as battery status are now working properly.

---

### Post by 1jarwolf on 2017-10-23
"[COLOR=#000000]##### NetworkManager.state ##############[/COLOR]
cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory"

I am no expert but it looks like there is no NetworkManager on your system. Try to install NetworkManager. [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

---

### Post by praseodym on 2017-10-23
The device seems to be blocked by the wrong driver:
```

sudo apt-get remove --purge broadcom-sta-dkms
```
Reboot

---

### Post by jeremy31 on 2017-10-23
> **1jarwolf said:**
> "[COLOR=#000000]##### NetworkManager.state ##############[/COLOR]
cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory"

I am no expert but it looks like there is no NetworkManager on your system. Try to install NetworkManager. [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)

If you have Ubuntu 17.10, can you post the result of ```
cat /var/lib/NetworkManager/NetworkManager.state
```
In Ubuntu 16.04 it contains
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
```

---

### Post by meiaman on 2017-10-23
Hello, everyone, I finally got it working after several days of exhaustive tries.

I tried everything you guys suggested, but nothing worked.

However, i updated my bios, and suddenly ubuntu started recognizing wifi and even the battery, as before, it did not show the battery status.

I assume there was a bug on the previous version that made secureboot always on, even if you disable it on the bios menu.

Marking thread as solved. Thanks for the help.

For future information:
Acer aspire e15 e5 573g
bug reported on bios v1.25. Secure boot seems to turn itself on. Updating bios solves the problem.

---

### Post by lisati on 2017-10-24
> **meiaman said:**
> 
Marking thread as solved. Thanks for the help.


Please use the "Thread tools" drop-down menu to mark threads solved.

---

