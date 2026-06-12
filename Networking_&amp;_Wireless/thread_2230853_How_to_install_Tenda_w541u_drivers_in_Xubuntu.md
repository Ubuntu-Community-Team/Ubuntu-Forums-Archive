---
title: "How to install Tenda w541u drivers in Xubuntu?"
date: 2014-06-21
forum: Networking &amp; Wireless
---

### Post by mehboob2 on 2014-06-21
Hello all. 
I'm totally new to xubuntu. I was Windows 7 user. Installing drivers in windows OS was quite easy. 
I found xubuntu more beautiful. And I've heard some people saying " once you try Linux OS you won't go back". So I am trying. 

MY question is" How do I install drivers of "tenda w541u" which is a wireless adapter. I've tried many threads like [http://ubuntuforums.org/showthread.php?t=1285828&page=13](http://ubuntuforums.org/showthread.php?t=1285828&page=13)
but I could not install drivers.

Can any 1 plz help me and teach me step by step as I'm a quite new user to Xubuntu. 

Thanks in advance

---

### Post by chili555 on 2014-06-21
First, let's identify your device. Please insert the device and open a terminal Ctrl+Alt+t and run:```
lsusb
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Post the result.

Thanks.

---

### Post by mehboob2 on 2014-06-21
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12627  1 rt2800lib
mac80211              546051  5 iwl3945,iwlegacy,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  4 iwl3945,iwlegacy,mac80211,rt2x00lib

---

### Post by mehboob2 on 2014-06-21
> **chili555 said:**
> First, let's identify your device. Please insert the device and open a terminal Ctrl+Alt+t and run:```
lsusb
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Post the result.

Thanks.
Bus 002 Device 002: ID 04f2:b015 Chicony Electronics Co., Ltd VGA 24fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


rt2800usb              26581  0 
rt2x00usb              20041  1 rt2800usb
rt2800lib              83150  1 rt2800usb
rt2x00lib              48886  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12627  1 rt2800lib
mac80211              546051  5 iwl3945,iwlegacy,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              409394  4 iwl3945,iwlegacy,mac80211,rt2x00lib

---

### Post by chili555 on 2014-06-21
Whoa!! The correct driver, rt2800usb is already loaded but so is another wireless driver, iwl3945. Do you have a non-working or, at least, not working well internal device? Anything you'd care to share???

I have and use an Intel 3945 that is perfect.

---

### Post by mehboob2 on 2014-06-21
> **chili555 said:**
> Whoa!! The correct driver, rt2800usb is already loaded but so is another wireless driver, iwl3945. Do you have a non-working or, at least, not working well internal device? Anything you'd care to share???

I have and use an Intel 3945 that is perfect.

Sir, my laptop is an old machine. Its "hp Dv6000". Its internal Wifi card is not working, that's why I've to use an external wifi adapter. The name of that Adapter is "Tenda w541u".I don't know which one's drivers are correctly installed.

---

### Post by Vladlenin5000 on 2014-06-21
Can you diable the internal (non-working) one in BIOS? It might help...

---

### Post by chili555 on 2014-06-21
Unless you think the internal is defective, I suggest you unplug the Tenda and we'll troubleshoot the internal. If you are quite sure the internal will never work, we need to blacklist its driver before we proceed.```
sudo -i
echo "blacklist iwl3945"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r iwl3945
exit
```Now see if the Tenda has created an interface, probably wlan1:```
iwconfig
rfkill list all
```Does it scan?```
sudo iwlist wlan1 scan
```If it scans and sees your network, it probably will connect.

---

### Post by mehboob2 on 2014-06-21
> **chili555 said:**
> Unless you think the internal is defective, I suggest you unplug the Tenda and we'll troubleshoot the internal. If you are quite sure the internal will never work, we need to blacklist its driver before we proceed.```
sudo -i
echo "blacklist iwl3945"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r iwl3945
exit
```Now see if the Tenda has created an interface, probably wlan1:```
iwconfig
rfkill list all
```Does it scan?```
sudo iwlist wlan1 scan
```If it scans and sees your network, it probably will connect.
 Bundle of thanks to you sir. 
Its working now. Thank you once again.

---

### Post by chili555 on 2014-06-21
Please use thread tools at the top to mark Solved.

Glad it's sorted.

---

