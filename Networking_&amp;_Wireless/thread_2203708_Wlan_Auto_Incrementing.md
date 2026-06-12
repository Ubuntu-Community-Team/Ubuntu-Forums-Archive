---
title: "Wlan Auto Incrementing"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by mitch5 on 2014-02-04
Hello!

We are cloning some machines that are using xubuntu with small USB wifi cards.  Everything seems to work OK, however, the WLAN interface keeps incrementing on each device.  I'm assuming this is becuase the MACs are different for all the USB wifi devices.

Is there a way to reset or force the only wifi usb adapter to use wlan0?

Also, can I have it auto join our wifi network?  
- I have to rejoin with each usb wifi adaptor
- If I put in the wifi adapter that the machine was cloned with, it will auto join.

Thanks!

---

### Post by varunendra on 2014-02-06
Hello mitch5, Welcome to the forums !

Depending upon how you are cloning, you may choose to delete the **/etc/udev/rules.d/70-persistent-net.rules** file before/during or after the cloning. This is the file that defines the interface name and it gets automatically regenerated on next boot or as soon as a udev event with network devices occurs. The fresh file will always have fresh entries, for example, the wifi interface name will start with "wlan0" (unless the driver assigns its own custom name, which is probably not applicable to your case).

---

