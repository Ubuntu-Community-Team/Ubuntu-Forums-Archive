---
title: "Inspiron 6400 - broadcom wifi card"
date: 2013-09-08
forum: Networking &amp; Wireless
---

### Post by tl4 on 2013-09-08
Dell Inspiron 6400 laptop.  Stock, no addon hardware
Clean install of 13.04 (with/along side of Vista) and did all updates while connected to LAN.
Went to enable wireless, Not available. But being Broadcom BCM4311 -
went to find ADDITIONAL DRIVERS app in dash - not there anymore(Was in 12.04LTS[on another computer])
Installed Additional Drivers from Software Center.  Installed and ran and found the BCM4311 card.
Clicked on Activate.  After rebooting neither wired or wireless is available.
Yeah, it killed wired also.
Cannot find "Additional Drivers" in dash (applications) nor in system settings to 'undo' anything.
Software Center reports that it is installed.
Wireless works when I plug in an old Netgear USB wifi adapter and use it.  But I'd rather have the inboard working.  (Didn't need anything downloaded)
Edit: Also noticed now that the laptop will not automatically power down.  Hung on the purple screen.

---

### Post by squakie on 2013-09-08
In Unity, open system settings, select software and updates, and you'll see the additional drivers tab.

---

### Post by tl4 on 2013-09-08
under the aditional drivers tab is a blank rectangle.  None listed.  Below that is says No Proprietary drivers are in use.

---

### Post by wildmanne39 on 2013-09-08
*Thread moved to **Networking & Wireless**.*

---

### Post by squakie on 2013-09-08
Please follow [this]("http://ubuntuforums.org/showthread.php?t=2077104&highlight=") thread.

---

### Post by wildmanne39 on 2013-09-08
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by tl4 on 2013-09-09
Wild Man, with the netgear usb attached downloaded and ran script. outputted a txt file.  attached tar.gz (ZIP wouldn't go)
squakie, No offence, but I've tried. Had tried so many other threads my head spun.  I started over with formatting and reinstalling 13.04.

---

### Post by wildmanne39 on 2013-09-09
Please do:
```
sudo apt-get purge bcmwl-kernel-source
```
```
gksu gedit /etc/modprobe.d/blacklist.conf
```
Remove:
```
blacklist b43
blacklist ssb
blacklist bcma
blacklist b44
```
save, close gedit and reboot.
Now your wired connection should be working, please do:
```
sudo apt-get install linux-firmware-nonfree
```
if the wired connection is not working then follow the directions in the link given by squakie to get the wifi working.
Thanks

---

### Post by tl4 on 2013-09-09
following Wild Bills procedure
sudo apt-get purge bcmwl-kernel-source
then
gksu gedit /etc/modprobe.d/blacklist.conf - gksu not installed
used sudo gedit /etc/modprobe.d/blacklist.conf
placed a # in front of b43xx - it was the only listing in the list given.
wired works again, as does auto shutdown, but still no wireless. 
YAY, on the right path.
continuing with 
sudo apt-get install linux-firmware-nonfree
reboot + IT's WORKING!!! wireless connected right now.
Thankyou, Thankyou, Thankyou.

---

