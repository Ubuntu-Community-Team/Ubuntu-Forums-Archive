---
title: "VPN Issue in 15.10"
date: 2015-12-30
forum: Networking &amp; Wireless
---

### Post by Philip_Banta on 2015-12-30
I had a working VPN in 14.XX but since I did a clean upgrade I cannot get it to connect.

I am using the built in VPN, I have an Intel 7260 wireless card using firmware version 12 (tried 13 as well and it still didn't work).

I have tried [https://bbs.archlinux.org/viewtopic.php?id=194042](https://bbs.archlinux.org/viewtopic.php?id=194042), I have completing removed (purged) network-manager and network-manager-gnome and done a fresh install, and removed/recreated the vpn multiple times.

I have been monitoring the syslog and it ends with the following error:
Dec 30 13:23:10 bantap-xubuntu NetworkManager[815]: ** (nm-pptp-service:2273): WARNING **: pppd exited with error code 5

I do have the rest of the log if there is something else I should look for or if you would like me to post it I can attach the text file (Most likely too long for this post).

I know the VPN is up and running because I have a windows 8 VM running in openbox that the VPN connects with fine (using same credentials etc).

If there is any other information that would help please let me know!

---

### Post by Elishasmantle on 2015-12-31
Not sure if this will help:
[https://forums.opensuse.org/showthread.php/507157-NetworkManager-pptp-doesn-t-work-after-lastest-update](https://forums.opensuse.org/showthread.php/507157-NetworkManager-pptp-doesn-t-work-after-lastest-update)

Looks like it may be a kernel ver. issue or there is info in the article about a modprobe possible fix you can try.

elishasmantle

---

