---
title: "How do I install a driver in lunbutu from a USB disk?"
date: 2016-09-15
forum: Networking &amp; Wireless
---

### Post by antoipod on 2016-09-15
I don't know if this is the right place to ask this but I recently installed lunbutu on my backup pc  and  I'd like to know how to install a driver or program on Linux manually, I need to install a dLink USB Wi-Fi dongle, I extracted the drivers to my desktop which are in a zip file, the instructions are to modify the install.sh file but that's about it. The install.sh file is filled with text and in the zip folder along with many other folders. BTW im a complete noob when it comes to linux

---

### Post by ian-weisser on 2016-09-15
Fair warning: 'Installing a driver' could mean any of several possible methods. Most require an understanding of the command line. Some require recompiling the entire kernel.
None are for beginners. You will find them cryptic and difficult, There is no guarantee of success.

Next time, buy a dongle that is Linux-compatible out-of-the-box. Lots of them available. We even have a [database of tested hardware]("http://www.ubuntu.com/certification/") that simply works with Ubuntu with zero hassle.

Please show us the entire instructions you are looking at.

---

### Post by Bucky Ball on 2016-09-15
*Thread moved to **Networking and Wireless**.*

Welcome. Wrong way, go back. Save yourself some time before getting elbow deep in the terminal. 

Wouldn't bother with the Linux driver on the CD. The drivers that come with the device are generally hopeless. Please open a terminal and give the output of these three commands, please, with the dongle plugged in:

```
sudo lshw -C network
lsusb
iwconfig
```

Please use [code] tags for the output (see green link in my signature below). 

PS: DON'T start installing drivers without much clue. That can cause major issues we will to have to unravel later. ;)

Also, have you actually just plugged the USB device in and tried it??? The drivers for many USB devices are already in the kernel. It's not like Win where you need to install drivers using 25 digit authentication codes everytime you buy a new piece of hardware. Lots of stuff 'just works'. 

Plug it in, give it a bit, click on the network icon, do you have available networks visible?

---

