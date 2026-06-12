---
title: "wlan0 or eth1?!"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by Caligula on 2007-06-30
something weird is happening with my wireless. 
Sometimes the device is called wlan0 and sometimes it's called eth1.
Also, it looks like it tries to rename it from wlan0 to eth1 every boot, but sometimes there's an error message saying device is busy, I need to Ctrl + Alt + Del to kill the task and continue booting, needless to say, the device name stays wlan0.

I think that when it's named wlan0 it doesn't connect to any network. Sometimes I need to rmmod ndiswrapper && modprobe ndiswrapper, that changes the name to eth1 and sometimes it connects after that. Sometimes nothing works and I have to boot vista to get internet.

Has  anyone encountered that problem before?

Thanks,
Josh

---

### Post by Caligula on 2007-06-30
how could I forget? forgive me,

I use a dell inspiron 1501 with the built in wireless adapter: 
Dell Wireless 1390 802.11g Mini Card

and using feisty.

---

