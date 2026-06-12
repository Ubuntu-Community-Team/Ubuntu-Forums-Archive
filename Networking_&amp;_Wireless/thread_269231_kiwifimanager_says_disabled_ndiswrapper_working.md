---
title: "kiwifimanager says disabled ndiswrapper working"
date: 2006-10-01
forum: Networking &amp; Wireless
---

### Post by Skuggi on 2006-10-01
Ok, new to ubuntu, and i'm a moderate user of linux.  Still learning.  I have a Dell E1505 with the Broadcom 1390 chipset.  I have ndiswrapper working with it.
```
skuggi@skuggi-laptop:~/Driver$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
```

I installed KDE instead of gnome, I dont mind gnome, but I've had more experience in KDE as of late.

Now, when I go into the kwifimanager it tells me No-Interface and also says that it is disabled. I goto the Settings>Configuration Editor and it tells me (repeatedly) unable to autodetect wireless interface. I finally get to the KDE control module and am at a loss as to what to do next.  Any help would be greatly appriciated.

---

### Post by Skuggi on 2006-10-01
oh yea this also may help.

```
skuggi@skuggi-laptop:~$ sudo modprobe ndiswrapper
Password:
FATAL: Could not open '/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
skuggi@skuggi-laptop:~$ sudo ifup
ifup: Use --help for help
skuggi@skuggi-laptop:~$ sudo iwlist eth2 scan
eth2      Interface doesn't support scanning.

skuggi@skuggi-laptop:~$ sudo gedit /etc/network/interfaces
skuggi@skuggi-laptop:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
skuggi@skuggi-laptop:~$ sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.15-23-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko': No such file or directory
skuggi@skuggi-laptop:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

skuggi@skuggi-laptop:~$

```

---

