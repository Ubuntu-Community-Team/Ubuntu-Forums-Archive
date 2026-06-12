---
title: "driver and device present but no connection?"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by gary201147 on 2006-08-02
ndiswrapper confirms that:

mn510 driver installed, hardware present 

in the network settings, it also confirms that the wlan0 interface is active. essid automatically detects my network and i enter in the WEP key.

then it tries activating the interface (although under Wireless Connection, it says that "The interface wlan0 is active) only to get hung up. No error messages of any sort but I can pull an IP from the DHCP. The error cannot be in the router because my other computers work (running on xp).

any ideas?

---

### Post by gary201147 on 2006-08-02
essentially, i followed the instructions from WifiDocs/Driver/Ndiswrapper tutorial offered by Ubuntu

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

However, i just noticed that i skipped one crucial step. I did not load the new module into the kernel via

$sudo modprobe ndiswrapper

receiveing the message:
insmod lib/../ndiswrapper.ko

once i did however, my wireless device was cut off. in the network settings, the wlan0 device was no longer there and the signal on my device was flashing intermittently, a sign that it was no longer working (in theory at least).

so i went back and removed the *.ko file and my device was responding as usual and linux recognized the device once again. but STILL no connection.

Do i have to insert the module into the kernel? Why would it shut off my device?

---

### Post by Sketch on 2006-08-30
I am having similar problems, Can someone please help

---

