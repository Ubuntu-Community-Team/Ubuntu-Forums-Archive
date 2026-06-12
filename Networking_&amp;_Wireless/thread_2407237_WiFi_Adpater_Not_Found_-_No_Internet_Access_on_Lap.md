---
title: "WiFi Adpater Not Found - No Internet Access on Laptop"
date: 2018-12-01
forum: Networking &amp; Wireless
---

### Post by 15holtj on 2018-12-01
Hello, I recently installed ubuntu 18.04.1 on a laptop with a broadcom 43142 chip [14e4:4365] rev 01. The laptop does have an ethernet port. I've read through numerous forum posts on how to fix this by downloading the correct package onto a usb and transferring it over, but I have not been able to do so. I keep running into dependency problems. If this is something that has already been documented, could someone please point me in the right direction, if not do you have any advice or guidance? Thank you in advance.

---

### Post by jeremy31 on 2018-12-01
If you installed using a USB, plug the USB into the laptop and look in Driver Manager, install the Broadcom proprietary module, reboot and see if Secure Boot is disabled in BIOS

---

### Post by 15holtj on 2018-12-01
I did install from USB. Where would driver manager be located? When I search the USB for that file nothing comes up. I have tried install the bcmwl-kernel-source_6.30.223.271+bdcom-Oubuntu4_amd64.deb located on the USB in ubuntu/pool/restricted/b/bcmwl.

Thank you for your help

---

### Post by jeremy31 on 2018-12-01
The driver manager in Ubuntu system settings

---

### Post by 15holtj on 2018-12-01
I don't think I have the driver manager installed. Is this the program you're talking about? [https://www.noobslab.com/2014/01/linux-mint-driver-manager-and-device.html](https://www.noobslab.com/2014/01/linux-mint-driver-manager-and-device.html) . EDIT. That is for Mint, but I cannot find the driver manager in system settings.

---

### Post by jeremy31 on 2018-12-01
In Ubuntu it is in Software and Updates under Additional Drivers tab

---

### Post by 15holtj on 2018-12-01
In the Additional Drivers tab it shows "No additional drivers available."

---

### Post by jeremy31 on 2018-12-01
And that is with the USB with the ISO plugged in?

---

### Post by 15holtj on 2018-12-01
Yes

---

### Post by jeremy31 on 2018-12-01
Boot the ISO and see if installing the wifi there using additional drivers allows you to connect, then post results for ```
sudo parted -l
```

---

### Post by 15holtj on 2018-12-01
I booted from the ISO and went to the Additional Drivers. The Broadcom driver appears as propriety and I can select it (default selection is "not in use"), but when I click "apply changes" it reverts back to "not in use".

---

### Post by jeremy31 on 2018-12-01
Check ```
dpkg -l | grep build-essential
```

---

### Post by 15holtj on 2018-12-01
What am I checking for? Nothing comes up when I try that in terminal

---

### Post by jeremy31 on 2018-12-01
Build essential contains the compiling software for source code.
You might need to use Software and Updates in the Ubuntu Software tab, click the cdrom with Ubuntu Bionic Beaver, then go into Additional Drivers and see if Broadcom proprietary can be installed

---

### Post by 15holtj on 2018-12-01
When I have the USB that I used to boot and install from inserted, no cdroms are listed under "Installable from CD-ROM/DVD" when I am in the Ubuntu Software tab of the Software and Updates application.

---

### Post by jeremy31 on 2018-12-01
You don't see something like [https://www.pontikis.net/blog/media/2016/10/package-management-system-update-ubuntu-desktop/post/software-updates-01.png](https://www.pontikis.net/blog/media/2016/10/package-management-system-update-ubuntu-desktop/post/software-updates-01.png)

---

### Post by 15holtj on 2018-12-01
No, that box is blank.

---

### Post by jeremy31 on 2018-12-01
See if [https://askubuntu.com/questions/1068351/solved-difficulty-installing-bcm43142-offline-for-ubuntu-18-04](https://askubuntu.com/questions/1068351/solved-difficulty-installing-bcm43142-offline-for-ubuntu-18-04) helps any.
Actually the build-essential deb file is on the ISO in /pool/main/b

---

### Post by 15holtj on 2018-12-01
Hello Jeremy, I borrowed a phone and USB tethered to it to get wi-fi. I was then able to go to the Additional Drivers tab and install the propriety Broadcom driver. Thank you for all of your help troubleshooting. I'm bummed I couldn't figure out how to do it without an internet connection, but I am happy my machine is working now. 

For your curiosity: 
When I try to install the bcmwl-kernel I get an error that says the packages it is dependant on are not installed.

---

### Post by jeremy31 on 2018-12-01
Good, as I finally found the Ubuntu 18.04 ISO and was about to install it to a HDD to test on a laptop with a Broadcom wifi card

---

