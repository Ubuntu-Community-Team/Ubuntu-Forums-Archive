---
title: "netlis wf-2109 dongle off on every reboot"
date: 2013-09-06
forum: Networking &amp; Wireless
---

### Post by mrgreg55302 on 2013-09-06
I hope somone can help?  I purchased and inserted the wf-2109 netlis dongle.  Ubuntu 12.04 recognized and listed network but would not stay connected.  Downloaded the latest driver v3.4 and installed through terminal.  The wifi worked good until reboot.  If I open ifconfig, it does not show wlan0. Going into additional drivers, the message "this driver is activated but not in use".  If I deactivate and reactivate driver, the wifi is turned back on, and wifi works.  If I use ifconfig after the reactivation wlan0 is listed.

---

### Post by praseodym on 2013-09-07
Please show the following outputs:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
sudo iwlist scan
```

---

