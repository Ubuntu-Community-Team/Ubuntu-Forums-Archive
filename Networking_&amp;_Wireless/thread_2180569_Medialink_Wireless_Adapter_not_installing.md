---
title: "Medialink Wireless Adapter not installing"
date: 2013-10-13
forum: Networking &amp; Wireless
---

### Post by infenity23 on 2013-10-13
I don't know how to install my drivers for my new Medialink Wireless Adapter on my Ubuntu system.  There's no plug in and play option on this kernel, obviously, and I'm new to linux so I don't know how to manually install the drivers from the cd-rom drive.  The adapter is compatible with ubuntu, there's a linux folder on the cd-rom drive for installing the files, I just don't know how to go about it.  If anyone could help, I'd be elated.  Thanks.

---

### Post by wildmanne39 on 2013-10-13
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by infenity23 on 2013-10-14
I've attached the wireless info.  If anyone can help with the information I've provided, I'd truly be thankful.

---

### Post by wildmanne39 on 2013-10-14
I do not see any wireless device in the file you attached, it is an usb device correct? did you have it plugged it? I believe this is a new device and I do not think there is a driver for it.

Also you are using an old version of ubuntu, a newer version would have much better support for new devices.

---

