---
title: "Problems disabling wireless powersave"
date: 2015-09-12
forum: Networking &amp; Wireless
---

### Post by md11cf on 2015-09-12
I've just started using a new laptop running Ubuntu 14.04, and the wifi appears to disconnect itself every once in a while when I've been away for a while. The problem is that I'm trying to download files from a cloud backup, and the download keeps being interrupted.

I've read on a different thread that this might be to do with Ubuntu's default wireless powersave settings: [http://ubuntuforums.org/showthread.php?t=1844722](http://ubuntuforums.org/showthread.php?t=1844722)

But on the other hand, running "sudo iwconfig wlan0 power off" gives me the following error message:

```
 Error for wireless request "Set Power Management" (8B2C) :
     SET failed on device wlan0 ; Operation not supported.

```

Has anyone got any insight or any alternative solutions?

---

### Post by jeremy31 on 2015-09-12
What is the wifi card ```
lspci -nnk | grep -iA2 net
```

---

### Post by md11cf on 2015-09-12
```

03:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
    Subsystem: Dell Device [1028:020e]
    Kernel driver in use: ath9k

```

---

### Post by jeremy31 on 2015-09-12
Try ```
echo "options ath9k ps_enable=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
```
Reboot and see if the ```
sudo iwconfig wlan0 power off
``` works

---

### Post by md11cf on 2015-09-12
Actually what happened was kernel panic on reboot. Though luckily I managed to switch it on the second time and the second command was accepted. I'm not sure why the kernel panic happened, but "sudo iwconfig wlan0 power off" seems to be working now. Thanks.

---

