---
title: "Broadcom BCM4311 / Dell Inspiron 1525"
date: 2013-11-24
forum: Networking &amp; Wireless
---

### Post by lukadam on 2013-11-24
Hi I have just installed UBUNTU 13.10 on my dell 1525 laptop and the wireless network is not working, i dont belive its active at all...I have tried installing b43, broadcom-wl and such following the post from people who had similar problems but with no results. PLS help.

I have run lspci -nn ¦ grep 0280

0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)

Please let me know if you know how to fix it.

Thanks for help in advance!

---

### Post by westie457 on 2013-11-24
Hello lukadam. Welcome to the Forum.

I trust your wired connection is working at the moment because it will make this easier.

Open a terminal (Ctrl+Alt+T is the quick way), and run the following commands```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

Click on the Network icon, any networks showing? If yes choose yours enter the password. If no post back here with the the terminal output from the commands copied and pasted into [code] brackets. Click on the # symbol and paste between the [code] [code]. This will preserve the formatting and make it easier to read.

---

### Post by lukadam on 2013-11-24
Thats the problem, I only have wireless at my home...i have one laptop that works. I can download files and copy it over to the unubtu one...

---

### Post by lukadam on 2013-11-24
I have found the package you were talking about here: 
[http://packages.ubuntu.com/lucid/linux-firmware-nonfree](http://packages.ubuntu.com/lucid/linux-firmware-nonfree) 

copied over broadcom folder to firmware then sudo modporobe b43 and it WORKS!!:)

Thanks for help!

---

### Post by westie457 on 2013-11-24
Glad that it is working. Could you mark this as 'solved' please using 'Thread Tools' at the top of the page.

---

