---
title: "Problem installing drivers for an EH102 desktop wireless card"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Troko22 on 2008-05-04
Hey guys, I'm new to the whole ubuntu scene, and i recently made my desktop computer a XP / ubuntu dual boot. However, due to the layout of our house, we bought a wireless adapter (an EH102 desktop adapter) so we could avoid a huge string of cables. of course, it uses a Windows-based driver, and because of that i was told to install it with ndiswrapper. I found another thread and did what it said to in there, namely:
```
cd /cdrom/driver/winxp_2k (browse to the location of the driver file)
sudo ndiswrapper -i mrv8335.inf (your INF file name may vary)
sudo ndiswrapper -l (shows if the driver installed successfully, this should show "mrv8335 - driver installed, hardware present)
sudo ndiswrapper -m (write the configuration to modprobe)
sudo modprobe ndiswrapper
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
However, once I entered the first modprobe line, i got the error message "Could not open 'lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko': No such file or directory". The ndiswrapper -l said that the driver was installed sucessfully, yet the error says something's up with ndiswrapper.
Help? D:

---

### Post by chili555 on 2008-05-05
In my machine, the path is not as listed here, but it's ```
/lib/modules/2.6.24-16-generic/ubuntu/misc/**ndiswrapper**/ndiswrapper.ko
```You might check your system:```
sudo updatedb
sudo locate ndiswrapper | grep .ko
```Updating your database will take a few seconds. Then try specifying the entire path:```
sudo modprobe /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
```Let us know.

---

