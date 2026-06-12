---
title: "Wireless Seems to Be working but not"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by k2pow on 2006-12-11
Hi I have a Truemobile 1180 and I used ndisgtk(Windows Wireless Drivers) to install the .inf file and then I manually had to move two .sys files to the /etc/ndiswrapper/netdelus file. Everything appears to be set up as when I look at the driver it says it is installed and hardware is installed. I have in the network settings it set to DHCP but I still have no internet. Any help would be greatly appreciated.

---

### Post by x64Jimbo on 2006-12-11
did you configure the interface to access your network? you have to tell it your SSID and such.

---

### Post by k2pow on 2006-12-11
Yeh it did not even ask for that(or I dont know where to find it) in the network configurations

Also on a side note when I type ndiswrapper -l it says "netdellus driver installed, hardware present" not sure if thats what its suppose to say since on the tutorial it says driver present

---

### Post by x64Jimbo on 2006-12-11
Just open up the network connection from your system tray, then click on the wireless interface and configure it. It will ask for your SSID, encryption key, etc.

---

### Post by k2pow on 2006-12-11
There is no wireless configuration from the system tray (I assume you mean the bottom right)

---

### Post by x64Jimbo on 2006-12-12
There should be a network interface configuration applet in your tray (doesn't matter what part of the screen)
Look there.

---

### Post by k2pow on 2006-12-12
If you mean the network configuration under administration then yes when I go to that theirs a wlan0 that I enabled and is under DHCP but I dont see anywhere to enter my SSID.

---

### Post by x64Jimbo on 2006-12-13
There's no "properties" or "configure" button or anything like that?

---

