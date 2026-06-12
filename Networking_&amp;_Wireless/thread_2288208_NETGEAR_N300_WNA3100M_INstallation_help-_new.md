---
title: "NETGEAR N300 WNA3100M INstallation help- new"
date: 2015-07-25
forum: Networking &amp; Wireless
---

### Post by venkay26 on 2015-07-25
Hello Experts,

I am new to ubuntu OS, for the last 1 year i am working with ubunto 15.4 OS type 64.
 I have recently purchased NETGEAR N300 WNA3100M wifi adaptor, i am trying to install with below link i am not able to install the HW as per the doc.
[http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251).

venkatesh@VN26601:~$ lsusb
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:b728 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 5986:055d Acer, Inc 
Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 006: ID 0846:9021 NetGear, Inc. 
Bus 001 Device 005: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
venkatesh@VN26601:~$ 


i have installed ndiswrapper with bellow cmd. 
sudo apt-get install ndisgtk ndiswrapper-dkms dkms linux-headers-generic build-essential

i could not able to proceed further with driver installation. 

could you please hep me on this. what further setting needed and how do i ensure my net is working with net gear adaptor

Regards,
Venkatesh

---

### Post by Vladlenin5000 on 2015-07-25
Hi and welcome.
The link you posted is the one and only way to make it work. If it doesn't - and I'm not surprised, at all - tough luck...

You do understand the purpose of installing *ndiswrapper* is to use old XP drivers with an 'emulator' of some sort, don't you? It's a hack, a workaround... Even if it works we don't know for how long. The question isn't "if it breaks", it's "when"...
What exactly are you having trouble with?


PS - A newer, better, natively supported USB dongle costs $10 or less. I don't waste my time with non supported hardware, let alone help others just because... I hope you understand.

---

### Post by howefield on 2015-07-25
Thread moved to the "*Networking & Wireless*" forum.

---

