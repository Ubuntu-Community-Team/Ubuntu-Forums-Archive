---
title: "Belkin Adapter Issues"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by Bradness on 2008-06-08
Hi,

I recently installed Wubi 8.04 and am having troubles with the Belkin F5D6050. Anyone have a fix? PS: I do not have an available wired internet connection, and I have the driver files and installer handy in case I can find a working ndiswrapper version.

---

### Post by Bradness on 2008-06-08
Bump. Sorry, really want this to work... =\

---

### Post by prshah on 2008-06-10
> **Bradness said:**
> Hi,

I recently installed Wubi 8.04 and am having troubles with the Belkin F5D6050. Anyone have a fix? PS: I do not have an available wired internet connection, and I have the driver files and installer handy in case I can find a working ndiswrapper version.

Here's a good guide:

[http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html](http://www.astahost.com/info.php/configuring-belkin-f5d6050-802-11b-usb-wifi-device-mandriva-2007-using-ndiswrapper_t14333.html)

Or you can try a command-line approach, based on my (solved) thread (with expected outputs) ([http://ubuntuforums.org/showthread.php?t=756260](http://ubuntuforums.org/showthread.php?t=756260)), in which you can use ndiswrapper on the command line to install the INF file that you can get as detailed in the link above. Or, since you are using wubi you obviously have Windows, you can try to get the correct inf file from the windows/inf directory.

---

