---
title: "Removing Ndiswrapper, compiled from source?"
date: 2008-05-10
forum: Networking &amp; Wireless
---

### Post by Eax.exe on 2008-05-10
**EDIT**
Okay, so I managed to get it working :)
But every time I reboot i have to 

```

sudo modprobe ath_pci
sudo modprobe wlan_scan_sta

```

Any way to avoid this?
I'm using feisty with Fluxbox:)

Hello :)

Some time ago I compiled Ndiswrapper from source via this guide:
[http://ubuntuforums.org/showthread.php?t=512828&highlight=ar5007](http://ubuntuforums.org/showthread.php?t=512828&highlight=ar5007)

Now I'd like to use Madwifi instead:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html)

But how do I remove ndiswrapper when it's compiled from source?

Thanks in advance :D

---

### Post by kevdog on 2008-05-10
If you remove ndiswrapper from /etc/modules and add the ath_pci and  wlan_scan_sta to the /etc/modules file then everything will work how you want it.  If you want to remove ndiswrapper:

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

---

### Post by Eax.exe on 2008-05-10
> **kevdog said:**
> If you remove ndiswrapper from /etc/modules and add the ath_pci and  wlan_scan_sta to the /etc/modules file then everything will work how you want it.  If you want to remove ndiswrapper:

sudo aptitude purge ndiswrapper
sudo rm /etc/modprobe.d/ndiswrapper
sudo sh -c "sed '/^ndiswrapper$/d' /etc/modules > /etc/modules.temp.rm; mv /etc/modules.temp.rm /etc/modules"
sudo rmmod ndiswrapper
sudo /lib/modules/`uname -r`/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
sudo rm -rf /etc/ndiswrapper
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko

Thanks a lot :D

---

