---
title: "Why do I get &quot;unable to enumerate USB device...&quot; error?"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by bwallum on 2009-01-22
I have no USB devices plugged in and the syslog reports the following alternating message:

......
hub 2-0:1-0: unable to enumerate USB device on Port 9
hub 1-0:1-0: unable to enumerate USB device on Port 9
hub 2-0:1-0: unable to enumerate USB device on Port 9
......

I'm running proposed updates. Anybody know what's happening? 

Thanks
Bob

---

### Post by Sealbhach on 2009-01-22
Hi, what does it show if you type lsusb in the terminal?


.

---

### Post by bwallum on 2009-01-22
> **Sealbhach said:**
> Hi, what does it show if you type lsusb in the terminal?

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Anlace on 2009-01-22
Greetings,

I am seeing the same error and it's on a port that apparently is not in use.  lsusb shows all the correct devices attached and working on my computer.

I am running Kubuntu 8.1/KDE 4.1 and everything is kept up to date.  This installation is about 1 1/2 weeks old and I saw this error for the first time this morning when booting up.

GL

---

### Post by MelentevPA on 2010-06-30
Hi, all!

I solve this problem by truning on guest OS (in my case it was WinXP) from VirtualBox. When the guest OS is running I can attach any usb device. Hope this help.

---

