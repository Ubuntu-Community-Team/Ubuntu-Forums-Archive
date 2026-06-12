---
title: "BCM4311 firmware install without internet connectivity"
date: 2014-10-11
forum: Networking &amp; Wireless
---

### Post by glentek on 2014-10-11
I use a cell phone wifi hotspot for my internet connectivity. I installed Ubuntu 14.04 on a Dell D520 Laptop. To do this I downloaded the Ubuntu installation files to a USB memory stick on another computer (Windows desktop with wireless connectivity to my cell phone wifi hotspot). After installing and booting Ubuntu on the laptop, the wireless was not working.  After some research, I downloaded b43-fwcutter.deb and firmware-b43-installer.deb to a USB memory stick (on the desktop Windows computer), and tried to install them on the Ubuntu laptop. b43-fwcutter.deb installed without error, but firmware-b43-installer.deb failed, because the installation process needs to access the internet.

The Catch-22 is that wireless is not working, and to fix that I need wireless to be working.  Any help?  Thanks.

---

### Post by jeremy31 on 2014-10-11
Try this link for info [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43_-_No_Internet_access)

---

### Post by Hadaka on 2014-10-11
Here ya go..no internet required..
be sure to do the zip file first..
post #7
[http://ubuntuforums.org/showthread.php?t=2098717](http://ubuntuforums.org/showthread.php?t=2098717)

---

### Post by glentek on 2014-10-11
I moved the zip file to the Ubuntu desktop, extracted the files and tried to execute the commands.

> sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43




"sudo rmmod -f ssb" produced the error message "device or resource busy", so I could not do that. I tried to execute "sudo modprobe b43" but nothing happened. By that I mean it did not return to the command prompt. I rebooted and tried again, but same result.

---

### Post by Hadaka on 2014-10-11
please try..
```
sudo modprobe -rf ssb
sudo modprobe -rf b43
sudo modprobe -v ssb
sudo modprobe -v b43
```
thanks.

---

### Post by glentek on 2014-10-11
Here are the results:

> $ sudo modprobe -rf ssb
modprobe: FATAL: Module ssb is in use.
$ sudo modprobe -rf b43
$ sudo modprobe -v ssb
$ sudo modprobe -v b43
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko 

---

### Post by glentek on 2014-10-11
.... and I logged out and logged back in, and the wifi is working.  Thanks for your help. Any idea what the rmmod and modprobe ssb errors were caused by?

---

### Post by Hadaka on 2014-10-11
Great ! glad that worked.
I have no idea what might have caused those errors
there could be one or several reasons, looks like all
is doing great now.
Please mark your thread solved
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

### Post by chili555 on 2014-10-11
> **Hadaka said:**
> Great ! glad that worked.
I have no idea what might have caused those errors
there could be one or several reasons, looks like all
is doing great now.
Please mark your thread solved
How to ->[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.The module *ssb* was likely in use by his ethernet device and b44. The expeditious method is a reboot.

---

