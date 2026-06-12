---
title: "Selecting the right kernel for wireless"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2013-09-08
I have a Dell Inspiron 1150 laptop using xubuntu 12.04 with an ongoing wireless problem that I believe is related to the kernel. I fixed it by rolling back to kernel 3.2.0-37 which for some reason will work fine with my Broadcom 4306. The problem is the update manager keeps wanting to install later versions, such as 0.51, which I cannot make work. So, is there a way to keep what I have and block any kernel updates? And if I do that, will it cause me problems with other updates? I now have a newer laptop (two, actually) so this one definitely is headed for the recycle bin if I can't get a permanent fix....

---

### Post by chili555 on 2013-09-08
I think we should try to figure out why the driver only works in a specific kernel and fix it. If you'd like to proceed, please open a terminal and run and post:```
lspci -nn -d 14e4:
lsmod | grep -e b43 -e wl
```Thanks.

---

### Post by Lloydb39 on 2013-09-08
This is what it showed:
lloyd@lloyd-Inspiron-1150:~$ lspci -nn -d 14e4: 
02:01.0 Ethernet controller [0200]: Broadcom Corporation BCM4401  100Base-T [14e4:4401] (rev 01) 
02:02.0 Network controller [0280]: Broadcom Corporation BCM4306  802.11b/g Wireless LAN Controller [14e4:4320] (rev 03) 
lloyd@lloyd-Inspiron-1150:~$ lsmod | grep -e b43 -e wl 
b43                   342669  0 
mac80211              436493  1 b43 
cfg80211              178877  2 b43,mac80211 
bcma                   25651  1 b43 
ssb                    50691  2 b43,b44

---

### Post by chili555 on 2013-09-08
Do you have the newer kernel installed and available at the GRUB menu? I'd love to see what's going wrong:```
dmesg | grep -e wlan -e b43
```b43 and firmware is correct for your device 14e4:4320. Obviously, you have the firmware because it works now!

---

