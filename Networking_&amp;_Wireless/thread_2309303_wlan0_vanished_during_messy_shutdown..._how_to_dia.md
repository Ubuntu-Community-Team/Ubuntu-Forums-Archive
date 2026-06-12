---
title: "wlan0 vanished during messy shutdown... how to diagnose and repair?"
date: 2016-01-09
forum: Networking &amp; Wireless
---

### Post by fivebells on 2016-01-09
Hi, my laptop suffered a sudden shutdown due to the battery running out, and now wlan0 doesn't exist, according to "ifconfig wlan0 up".  Wireless still works when the machine is booted from live cd (it's how I'm entering this question.)  "lspci" in the livecd says it's using kernel driver ath9k to control the wireless device ("Qualcomm Atheros AR9485 Wireless Network Adapter").  Booting from the drive, "modprobe ath9k" reports that it doesn't know where that driver is.  

...how can I diagnose and fix this problem?  Can I simply reinstall an ubuntu package or ten which likely contain the corrupted files?

---

### Post by chili555 on 2016-01-09
Let's see some specifics. Please open a terminal and do:```
sudo modprobe ath9k
uname -r
```Please post the exact results.

---

### Post by fivebells on 2016-01-09
```

root@uppekha:~# modprobe ath9k
modprobe: FATAL: Module ath9k not found.
root@uppekha:~# uname -a
Linux uppekha 3.13.0-73-generic #116-Ubuntu SMP Fri Dec 4 15:31:30 UTC 2015 x86_64 x86_64 GNU/Linux

```

"modprobe ath9k" runs without errors in the live cd.

---

### Post by chili555 on 2016-01-09
Running as root?  Tsk, tsk. Please don't bypass one of Ubuntu's strongest security safeguards.

I suggest you try:```
sudo apt-get install --reinstall linux-image-`uname -r`
sudo apt-get install --reinstall linux-image-extra-`uname -r`
```Of course, with a working internet connection.

Those backticks are on the left side of my US keyboard on the same key with ~.

---

### Post by fivebells on 2016-01-09
Thanks, that fixed my problem.

Couldn't use uname -r, because I did it in a chroot from the livecd, in order to have wireless working.

"sudo bash" is quite useful when you have to execute a string of commands as root, and results in "running as root."

---

