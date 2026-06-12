---
title: "ubuntu wusb54g freeze"
date: 2007-07-30
forum: Networking &amp; Wireless
---

### Post by killzoneman00 on 2007-07-30
I have a wusb54g ver.4  wireless router set up in ubuntu which is connected to a D-link Dl-524 access point.  Everything is set to use a static ip.  the problem is that whenever I use torrent or online programs, such as azureus or gaim, my internet will simply cease working after awhile.  when it does stop working, i just change the ip address and everything works fine for awhile until it freezes again.      

any ideas on what is wrong?

---

### Post by kevdog on 2007-07-30
Driver issue perhaps??? What driver are you using for your stick?

---

### Post by killzoneman00 on 2007-07-30
I'm not quite sure which driver,  all that i had to do was plug it in and configure it.  how would i find out which driver it is?

---

### Post by kevdog on 2007-07-30
lshw -C network

This should list the driver currently assigned to the stick -- maybe

---

### Post by killzoneman00 on 2007-07-30
RT2500USBSTA       version- 1.0.0

---

### Post by kevdog on 2007-07-30
If you are working in feisty, I think the old rt2500 drivers are broken, hence the need to download and compile the serial monkey rt2500 drivers.

Here are a couple of posts you want to look at

#1 - deals wtih rt73 driver, however just substitute 2500 for 73 and you should be able to work with the post:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serial+monkey)

#2 - Serial Monkey website:
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

---

### Post by killzoneman00 on 2007-07-30
thanks for the info

---

