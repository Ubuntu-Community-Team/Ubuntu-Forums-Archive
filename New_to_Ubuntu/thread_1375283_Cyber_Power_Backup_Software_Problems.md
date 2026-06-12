---
title: "Cyber Power Backup Software Problems"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Excedio on 2010-01-07
Hey guys...need some help please with my Cyber Power CP550SLG battery backup. The backup itself is functioning, and my computer is recognizing it, but the software is not working for me.

> 
excedio@excedio-desktop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 013: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 011: ID 045e:0721 Microsoft Corp. LifeCam NX-3000
(UVC-compliant)
Bus 001 Device 010: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop
Laser
Bus 001 Device 009: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 003 Device 005: ID 0764:0501 Cyber Power System, Inc. CP1500 AVR UPS**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
excedio@excedio-desktop:~$
I do think that it's odd that the computer is seeing the backup as a different model. Here are the errors that I'm getting:

> 
excedio@excedio-desktop:~$ pwrstat -status
**Daemon service is not found.**
excedio@excedio-desktop:~$ pwrstatd
**Segmentation fault**
excedio@excedio-desktop:~$
Does anyone have this backup or at the very least use this brand?

---

### Post by Methuselah on 2010-01-07
It is saying a daemon (service) needs to be running.
Did the software documentation say anything about a daemon process you have to start?

BTW, I don't have a backup battery so I can't help directly.

---

### Post by Excedio on 2010-01-07
> **Methuselah said:**
> Did the software documentation say anything about a daemon process you have to start?

I looked at all of the documentation and saw nothing about "starting" a daemon. I did the install through a .deb also, so I would assume that the daemon would have been started in that process.

---

### Post by Excedio on 2010-01-08
Well... does anyone have a battery backup that is recognized by the battery meter out of the box?

---

### Post by Excedio on 2010-01-09
No one....really?

---

