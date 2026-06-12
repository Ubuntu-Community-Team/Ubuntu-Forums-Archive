---
title: "[SOLVED] Should I add anything to my interfaces?"
date: 2007-12-22
forum: Networking &amp; Wireless
---

### Post by mLes-_- on 2007-12-22
Okay, I have recently installed ndiswrapper for my Linksys WUSB54GSC.  The only problem is that when I start Linux it does not boot up the adapter.

I have added this to my /etc/udev/rules.d/99-custom.rules:
BUS=="usb", SYSFS{idProduct}=="0026", SYSFS{idVendor}=="13b1", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

Now if I type this in terminal w/ the device connected It starts:
sudo modprobe ndiswrapper

:lolflag: I dont know where I went wrong (maybe I should add wlan0 to my interfaces?), but if anyone has dealt with this before please let me know how to correct it.  Also, I want to thank everybody that helped me out on at least getting this thing WORKING AT ALL! YOU GUYS :guitar: !!!

---

### Post by wieman01 on 2007-12-22
You might have missed a step or two. Please take a look at my Ralink tutorial. Steps that might be missing:
> echo 'ndiswrapper' | sudo tee -a /etc/modules
> sudo ndiswrapper -m
Then reboot...

---

### Post by mLes-_- on 2007-12-22
The first command worked so now it is booting up with the machine.  Now all I have to do is set it up to connect automatically.  Also, last time i had this working I did all the updates and it stopped working after that!  Should I worry about that now? b/c the last method I used was not as in depth as this was.

---

### Post by mLes-_- on 2007-12-22
AH forget it i dont care manually connecting verytime... it takes 2 seconds.  well thanks man preeeeccciiaaaattee it haha.

---

