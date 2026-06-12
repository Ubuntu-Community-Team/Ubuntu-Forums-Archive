---
title: "Driver shown in list, no wireless in Network."
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by gneek on 2007-05-26
Hi, I installed ndiswrapper along with my driver (wusb54g.inf). When I invoke the ndiswrapper list (-l), it tells me that *wusb54g.inf is installed* and *hardware is present*, but when I go to the Network settings, it only shows Modem and Cable, no wireless.
If anyone had the same problem, or know what's happening, please enlighten the newb.
Thanks in advance, Nick Tsyukalo.

---

### Post by spd106 on 2007-05-27
Has the ndiswrapper kernel module been loaded? It should appear in the list if you run this command.
```
lsmod
```

If it's not loaded the try this command
```
sudo modprobe ndiswrapper
```

---

### Post by gneek on 2007-05-28
Yes, **ndiswrapper **is in the list. I still can't figure out why when I type in **iwconfig**, don't get **wlan0**. I have the driver installed...

---

### Post by spd106 on 2007-05-28
Ok then, does this command show you anything?
```
sudo lshw -class network
```

There should be an entry for your card and the driver should be ndiswrapper.

If that fails can you see the device listed with command?
```
lsusb
```

---

