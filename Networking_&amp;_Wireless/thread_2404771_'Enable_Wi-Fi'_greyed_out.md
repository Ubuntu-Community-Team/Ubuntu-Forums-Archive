---
title: "'Enable Wi-Fi' greyed out"
date: 2018-10-28
forum: Networking &amp; Wireless
---

### Post by sharkyleshark on 2018-10-28
Hi.  

I installed Lubuntu (18.04,1 LTS, kernel 4.15.0-34-generic i686) on an old Lenovo X100e ThinkPad and I can't get the wi-fi working.  There is no external hardware switch and I can't install windows, so I bought a USB wireless adapter, but still no joy.  I've seen many threads for this already, and followed the steps as best I can (for example [https://ubuntuforums.org/showthread.php?t=1895671](https://ubuntuforums.org/showthread.php?t=1895671), which led to a bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/782137)).  I can see the devices in the System Information panel, but for some reason 'rfkill list all' only shows '0: phy0: Wirelass Lan', which is hard blocked, and no amount of 'sudo rfkill unblock all' changes the status.  I have reached the limit of my expertise, and would be extremely grateful for any further suggestions.

Thanks very much.

---

### Post by jeremy31 on 2018-10-28
Quickest fix might be to remove the internal wifi card then the USB should function

---

### Post by sharkyleshark on 2018-10-29
Thanks, jeremy31.  Do you think there is a non-hardware solution?

---

