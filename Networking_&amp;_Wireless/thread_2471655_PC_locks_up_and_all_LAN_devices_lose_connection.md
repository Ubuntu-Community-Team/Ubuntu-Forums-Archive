---
title: "PC locks up and all LAN devices lose connection"
date: 2022-02-05
forum: Networking &amp; Wireless
---

### Post by Dan Z on 2022-02-05
I have a Dell PC running 18.04. ETH connection in use.

This PC started to lock up randomly. When it did, all LAN devices, including Wireless would loose connectivity.

I started using WLAN on the Dell, it still locks up, but the other devices on LAN stay up. 

Could this be a symptom of a NIC card problem? 

Thanks DAN

---

### Post by TheFu on 2022-02-07
yes, it could. It could also be a wifi-ap issue or a router issue. In general, it is a bad idea to have both wired connectivity and wifi enabled at the same time, unless you understand networking more than a typical home user does.

What do the system log files show?  Can you change to a different tty and check the logs?   If not, you can always boot from any Ubuntu Desktop (lubuntu/xubuntu/whatever) Installer flash drive, mount the storage with the logs (usually in /var/log/, but you can't mount there in a temporary environment - mount to /mnt/ , so the logs from the SSD/HDD (not the flash you booted) are in /mnt/var/log/ and look for errors or warnings in those files. I'd use egrep, but do it however you like.

There are $20 wifi USB devices that are well-supported by Linux (pull them in and they "just work"). I find having one of those can be handy to rule out some issues related to different hardware from time to time.  But really, avoiding the use of wifi is my best advice. None of my computers uses wifi at home. Most don't have wifi capability. 1 laptop that boots does, but wifi only gets used when away from home or work locations.

---

### Post by Dan Z on 2022-02-08
root cause was found to be a memory issue  in the PC that was locking up. Cards needed to be reseated, all ok now.

---

### Post by TheFu on 2022-02-08
**Thread Tools** button ---> SOLVED.

Please. Only the user that creates a thread can do that.

---

