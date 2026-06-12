---
title: "Netgear n300 (WNA3100M)"
date: 2016-04-15
forum: Networking &amp; Wireless
---

### Post by valeriogiuffrida on 2016-04-15
Dear all,I am trying to make this wifi dongle working so hard, with no luck.I installed ndiswrapper + windows driver and it worked once. Then I figured out that driver rtl8192cu are inside the operating system and I tried to use them (I also installed firmware-realtek), it worked once and when I pull the dongle out and put it back, basically I have the wlan0 interface, but it cannot find any network (which a minute ago were there).I have no clue how to fix the problem, since it was working and then not anymore, after I just took the dongle out from the computer.vg

---

### Post by praseodym on 2016-04-15
Uninstall the wrapper:
```

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndisgtk ndiswrapper*
```
Then change the driver. First, check which kernel is in use:
```

uname -a
```

Then install the appropriate driver:

[https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](https://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

and reboot. Check afterwards:
```

lsusb
```

---

