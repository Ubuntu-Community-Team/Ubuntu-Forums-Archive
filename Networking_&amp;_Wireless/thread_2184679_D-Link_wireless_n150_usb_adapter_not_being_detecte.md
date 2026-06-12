---
title: "D-Link wireless n150 usb adapter not being detected"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by phpzendguru on 2013-10-30
Hi


I recently purchased a D-Link Wireless N 150 USB Adapter and have plugged into my Ubuntu 13.04. But the problem is that it does not always detect the adapter. So I have to plug-in and plug-out multiple times and only after that it detects.


Please if anyone can give me a solution as it becomes very irritating.


PS: When I say "detect" I mean I see the list of available WiFi in the Network List and I can connect to them easily.


Thanks in advance

---

### Post by chili555 on 2013-10-30
What is its driver? Please run the command:```
lsusb
```Find the usb.id for the device; possibly like 2001:3c19. Google the ID and find the driver, possibly rt2800usb. We suspect that the driver isn't loading automagically. When it is *NOT* working, check:```
lsusb | grep rt2 <-- or whatever driver you found
```If the module is not loaded, start it:```
sudo modprobe rt2800usb
```If that fixes it, let's get rt2800usb to load automatically:```
sudo -i
echo rt2800usb >> /etc/modules
exit
```If that is not the problem, post back and we'll proceed.

---

